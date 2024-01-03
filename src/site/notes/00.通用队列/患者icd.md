---
{"dg-publish":true,"permalink":"/00.通用队列/患者icd/"}
---


```
CREATE MATERIALIZED VIEW "public"."患者icd"
AS
SELECT diagnoses_icd.subject_id,
    diagnoses_icd.hadm_id,
    diagnoses_icd.seq_num,
    diagnoses_icd.icd_code,
    diagnoses_icd.icd_version,
    d_icd_diagnoses.long_title
   FROM (mimiciv_hosp.d_icd_diagnoses
     JOIN mimiciv_hosp.diagnoses_icd ON (((d_icd_diagnoses.icd_code = diagnoses_icd.icd_code) AND (d_icd_diagnoses.icd_version = diagnoses_icd.icd_version))));

ALTER MATERIALIZED VIEW "public"."患者icd" OWNER TO "postgres";
```