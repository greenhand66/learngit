hello,everyone.


/* 各角度パラメータのsin,cos値を取得 */
	sinx = sin(alpha);		/* sin:Pitch	*/
	cosx = cos(alpha);		/* cos:Pitch	*/
	siny = sin(beta);		/* sin:Yaw		*/
	cosy = cos(beta);		/* cos:Yaw		*/
	sinz = sin(gamma);		/* sin:Roll		*/
	cosz = cos(gamma);		/* cos:Roll		*/

	
	mTemp1			= para->px * cosy + para->py * siny;	// MISRA-Cからの逸脱 [EntryAVM_QAC#1] M1.4.2  R-47, ID-852
	mTemp2			= para->px * siny - para->py * cosy;	// MISRA-Cからの逸脱 [EntryAVM_QAC#1] M1.4.2  R-47, ID-854
	
	output->m11		= cosy * cosz - sinx * siny * sinz;	// MISRA-Cからの逸脱 [EntryAVM_QAC#1] M1.4.2  R-47, ID-856
	output->m12		= sinx * cosy * sinz + siny * cosz;	// MISRA-Cからの逸脱 [EntryAVM_QAC#1] M1.4.2  R-47, ID-858
	output->m13		= -cosx * sinz;
	output->m14		= -cosz * mTemp1 + sinx * sinz * mTemp2 + para->pz * cosx * sinz;	// MISRA-Cからの逸脱 [EntryAVM_QAC#1] M1.4.2  R-47, ID-860
	output->m21		= -cosx * siny;
	output->m22		= cosx * cosy;
	output->m23		= sinx;
	output->m24		= cosx * mTemp2 - para->pz * sinx;	// MISRA-Cからの逸脱 [EntryAVM_QAC#1] M1.4.2  R-47, ID-862
	output->m31		= sinx * siny * cosz + cosy * sinz;	// MISRA-Cからの逸脱 [EntryAVM_QAC#1] M1.4.2  R-47, ID-864
	output->m32		= siny * sinz - sinx * cosy * cosz;	// MISRA-Cからの逸脱 [EntryAVM_QAC#1] M1.4.2  R-47, ID-866
	output->m33		= cosx * cosz;
	output->m34		= -sinz * mTemp1 - sinx * cosz * mTemp2 - para->pz * cosx * cosz;
