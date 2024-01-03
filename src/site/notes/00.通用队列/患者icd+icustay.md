---
{"dg-publish":true,"permalink":"/00.通用队列/患者icd+icustay/"}
---


[[00.通用队列/患者icd\|患者icd]] + icustay_detail
```
SELECT "患者icd".subject_id,
    "患者icd".hadm_id,
    "患者icd".seq_num,
    "患者icd".icd_code,
    "患者icd".icd_version,
    "患者icd".long_title,
    icustay_detail.stay_id,
    icustay_detail.gender,
    icustay_detail.dod,
    icustay_detail.admittime,
    icustay_detail.dischtime,
    icustay_detail.los_hospital,
    icustay_detail.admission_age,
    icustay_detail.race,
    icustay_detail.hospital_expire_flag,
    icustay_detail.hospstay_seq,
    icustay_detail.first_hosp_stay,
    icustay_detail.icu_intime,
    icustay_detail.icu_outtime,
    icustay_detail.los_icu,
    icustay_detail.icustay_seq,
    icustay_detail.first_icu_stay
   FROM ("患者icd"
     JOIN mimiciv_derived.icustay_detail ON ((("患者icd".subject_id = icustay_detail.subject_id) AND ("患者icd".hadm_id = icustay_detail.hadm_id))))
```
