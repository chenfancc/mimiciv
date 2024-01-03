---
{"dg-publish":true,"permalink":"/00.通用队列/首入院入icu/"}
---


```
CREATE MATERIALIZED VIEW "public"."首入院入icu"
AS
SELECT subject_id,
    hadm_id,
    stay_id,
    gender,
    dod,
    admittime,
    dischtime,
    los_hospital,
    admission_age,
    race,
    hospital_expire_flag,
    hospstay_seq,
    first_hosp_stay,
    icu_intime,
    icu_outtime,
    los_icu,
    icustay_seq,
    first_icu_stay
   FROM mimiciv_derived.icustay_detail
  WHERE ((first_hosp_stay = true) AND (first_icu_stay = true))
  ORDER BY subject_id;

ALTER MATERIALIZED VIEW "public"."首入院入icu" OWNER TO "postgres";
```