---
{"dg-publish":true,"permalink":"/00.通用队列/脓毒症患者ICU信息/"}
---


```
SELECT
	mimiciv_derived.icustay_detail.subject_id, 
	mimiciv_derived.icustay_detail.hadm_id, 
	mimiciv_derived.icustay_detail.stay_id, 
	mimiciv_derived.icustay_detail.gender, 
	mimiciv_derived.icustay_detail.dod, 
	mimiciv_derived.icustay_detail.admittime, 
	mimiciv_derived.icustay_detail.dischtime, 
	mimiciv_derived.icustay_detail.los_hospital, 
	mimiciv_derived.icustay_detail.admission_age, 
	mimiciv_derived.icustay_detail.race, 
	mimiciv_derived.icustay_detail.hospital_expire_flag, 
	mimiciv_derived.icustay_detail.hospstay_seq, 
	mimiciv_derived.icustay_detail.first_hosp_stay, 
	mimiciv_derived.icustay_detail.icu_intime, 
	mimiciv_derived.icustay_detail.icu_outtime, 
	mimiciv_derived.icustay_detail.los_icu, 
	mimiciv_derived.icustay_detail.icustay_seq, 
	mimiciv_derived.icustay_detail.first_icu_stay, 
	mimiciv_derived.sepsis3.antibiotic_time, 
	mimiciv_derived.sepsis3.culture_time, 
	mimiciv_derived.sepsis3.suspected_infection_time, 
	mimiciv_derived.sepsis3.sofa_time, 
	mimiciv_derived.sepsis3.sofa_score, 
	mimiciv_derived.sepsis3.respiration, 
	mimiciv_derived.sepsis3.coagulation, 
	mimiciv_derived.sepsis3.liver, 
	mimiciv_derived.sepsis3.cardiovascular, 
	mimiciv_derived.sepsis3.cns, 
	mimiciv_derived.sepsis3.renal, 
	mimiciv_derived.sepsis3.sepsis3
FROM
	mimiciv_derived.sepsis3
	INNER JOIN
	mimiciv_derived.icustay_detail
	ON 
		mimiciv_derived.sepsis3.subject_id = mimiciv_derived.icustay_detail.subject_id AND
		mimiciv_derived.sepsis3.stay_id = mimiciv_derived.icustay_detail.stay_id
ORDER BY subject_id ASC
```