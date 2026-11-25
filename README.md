<h1 align="center">BUAN Compute Bundles Profiles</h1>

<p align="center">
  Bundle profiles of white matter pathways, computed with the DIPY Bundle Analytics (BUAN) workflow by comparing subject bundles with model bundles.
</p>

<p align="center">
  <a href="https://github.com/brainlife/abcd-spec"><img src="https://img.shields.io/badge/ABCD_Spec-v1.1-green.svg" alt="ABCD Spec v1.1"></a>
  <a href="https://doi.org/10.25663/brainlife.app.456"><img src="https://img.shields.io/badge/Brainlife-brainlife.app.456-blue.svg" alt="Run on brainlife.io"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-lightgrey.svg" alt="MIT license"></a>
</p>

## 🧠 At a glance

<!-- brainlife-app:begin (generated from the App manifest; edit the manifest, not this block) -->

> **Computes BUAN bundle profiles of white matter pathways with the DIPY 1.1.1 dipy_buan_profiles workflow, comparing subject bundles against model bundles and saving the profiles in HDF5 files.**

Wraps dipy_buan_profiles (Bundle Analytics, Chandio et al. 2020) with --no_disks, a model bundle folder and a subject folder read from config.json, writing results to output/. Note that the registry record defines no inputs, outputs or parameters, while main expects model_bundle_folder, subject_folder and no_disks in config.json, so the App cannot be run as registered (see report).

| | |
|---|---|
| 🐳 **Container** | `brainlife/dipy:1.1.1` |
| ⚙️ **Resources** | 8 CPUs · 16 GB memory |
| 🔗 **Run it** | [doi.org/10.25663/brainlife.app.456](https://doi.org/10.25663/brainlife.app.456) |

<!-- brainlife-app:end -->

## 🔬 How it works

This is a brainlife.io wrapper for the DIPY [`dipy_buan_profiles`](https://dipy.org/documentation/1.2.0./interfaces/buan_flow/) workflow. It creates bundle profiles of white matter pathways and saves them in HDF5 files, implementing the bundle profile method of Bundle Analytics (BUAN), a computational framework for investigating the shapes and profiles of brain pathways across populations (Chandio et al., 2020).

The App runs `dipy_buan_profiles` from the `brainlife/dipy:1.1.1` container on a folder of model bundles and a subject folder, with the number of disks along each bundle set by `no_disks`.

- More information about DIPY: [dipy.org](https://dipy.org/)
- Command-line reference: [`dipy_buan_profiles`](https://dipy.org/documentation/1.2.0./reference_cmd/dipy_buan_profiles/)

This repository holds DIPY workflow wrappers on separate branches: the registered BUAN App is built from the [`1.1.1`](https://github.com/brainlife/bl_apps_dipy_buan_profiles/tree/1.1.1) branch, while the default branch contains a wrapper for the `dipy_mask` workflow (`dipy_mask:dwi` on a DWI, or `dipy_mask:tensor` on an FA map). See the [DIPY Apps registered on brainlife.io](https://brainlife.io/apps#dipy).

## 🚀 Running the App

### ☁️ On brainlife.io

Open the App at [doi.org/10.25663/brainlife.app.456](https://doi.org/10.25663/brainlife.app.456), choose the datasets to run on and press **Execute**. The App's brainlife.io record does not yet define inputs, outputs or parameters, while `main` expects `model_bundle_folder`, `subject_folder` and `no_disks` in `config.json`.

### 💻 Locally

You need [Singularity/Apptainer](https://apptainer.org/) and [`jq`](https://jqlang.github.io/jq/).

1. Clone this repository and check out the App's branch: `git checkout 1.1.1`.
2. Create `config.json` (see `config.json.example`):

   ```json
   {
       "no_disks": 100,
       "model_bundle_folder": "test_data/model_bundles",
       "subject_folder": "test_data/subjects"
   }
   ```

3. Run the App:

   ```bash
   ./main
   ```

You can also run the workflow directly:

```bash
singularity exec -e docker://brainlife/dipy:1.1.1 dipy_buan_profiles [your_args]
```

See the [`dipy_buan_profiles` reference](https://dipy.org/documentation/1.2.0./reference_cmd/dipy_buan_profiles/) for all arguments.

## 📦 Outputs

`output/` holds the bundle profiles as HDF5 files, named as described in the [`dipy_buan_profiles` reference](https://dipy.org/documentation/1.2.0./reference_cmd/dipy_buan_profiles/).

## 📚 Citing

> [!TIP]
> If you use this App in your work, please cite the App, the software it builds on and brainlife.io (below). GitHub's **Cite this repository** button gives the App citation in APA and BibTeX.

- Chandio BQ, et al. Bundle analytics, a computational framework for investigating the shapes and profiles of brain pathways across populations. *Scientific Reports* 10:17149 (2020).
- BUAN Compute Bundles Profiles . brainlife.io App. [doi:10.25663/brainlife.app.456](https://doi.org/10.25663/brainlife.app.456)
- Chandio BQ, et al. Bundle analytics, a computational framework for investigating the shapes and profiles of brain pathways across populations. Scientific Reports 10, 17149 (2020).
- Garyfallidis et al. Dipy, a library for the analysis of diffusion MRI data. *Frontiers in Neuroinformatics* 8 (2014). [doi:10.3389/fninf.2014.00008](https://doi.org/10.3389/fninf.2014.00008)
- Hayashi S, Caron BA, Heinsfeld AS, et al. brainlife.io: a decentralized and open-source cloud platform to support neuroscience research. *Nature Methods* 21:809–813 (2024). [doi:10.1038/s41592-024-02237-2](https://doi.org/10.1038/s41592-024-02237-2)
- Avesani P, McPherson B, Hayashi S, et al. The open diffusion data derivatives, brain data upcycling via integrated publishing of derivatives and reproducible open cloud services. *Scientific Data* 6:69 (2019). [doi:10.1038/s41597-019-0073-y](https://doi.org/10.1038/s41597-019-0073-y)

## 👥 Authors

- [Bramsh Chandio](https://github.com/BramshQamar)

## 💰 Funding

[![Wellcome-226486/Z/22/Z](https://img.shields.io/badge/Wellcome-226486%2FZ%2F22%2FZ-purple.svg)](https://wellcome.org/)
[![NIH-NINDS-U24NS140384](https://img.shields.io/badge/NIH_NINDS-U24NS140384-green.svg)](https://reporter.nih.gov/project-details/11261037)
[![NIH-NINDS-UM1NS132207](https://img.shields.io/badge/NIH_NINDS-UM1NS132207-green.svg)](https://reporter.nih.gov/project-details/11411328)
[![NIH-NIBIB-R01EB029272](https://img.shields.io/badge/NIH_NIBIB-R01EB029272-green.svg)](https://reporter.nih.gov/project-details/10262925)
[![NIH-NIBIB-R01EB030896](https://img.shields.io/badge/NIH_NIBIB-R01EB030896-green.svg)](https://reporter.nih.gov/project-details/10428625)
[![NIH-NIMH-R01MH126699](https://img.shields.io/badge/NIH_NIMH-R01MH126699-green.svg)](https://reporter.nih.gov/project-details/10460628)
[![NIH-NIDCD-R01DC020088](https://img.shields.io/badge/NIH_NIDCD-R01DC020088-green.svg)](https://reporter.nih.gov/project-details/11140284)
[![NSF-BCS-1734853](https://img.shields.io/badge/NSF_BCS-1734853-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1734853)
[![NSF-BCS-2203524](https://img.shields.io/badge/NSF_BCS-2203524-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=2203524)
[![NSF-IIS-1636893](https://img.shields.io/badge/NSF_IIS-1636893-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1636893)
[![NSF-OAC-2148729](https://img.shields.io/badge/NSF_OAC-2148729-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=2148729)
[![NSF-IIS-1912270](https://img.shields.io/badge/NSF_IIS-1912270-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1912270)
[![NSF-IIS-2148700](https://img.shields.io/badge/NSF_IIS-2148700-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=2148700)
[![NSF-OAC-1916518](https://img.shields.io/badge/NSF_OAC-1916518-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1916518)

<sub>brainlife.io is publicly funded, and acknowledging that support helps keep it running. This App was developed with support from Wellcome, the U.S. National Institutes of Health (including the BRAIN Initiative BRAIN CONNECTS program: The Axonal Projectome EXchange, U24NS140384, and the Center for Mesoscale Connectomics, UM1NS132207) and the U.S. National Science Foundation.</sub>

DIPY is publicly funded. Please also acknowledge its funding in publications and code that reuse this code: NIH NIBIB R01EB027585, NIH NIMH RF1MH121868, NIH NIMH R01MH108467, NSF BCS-1734853, NSF EEC-1720625, NSF OAC-1916518, NSF IIS-1912270 and NSF IIS-1636893.

## ⚖️ License

[BSD 3-Clause](LICENSE), Copyright (c) 2020, DIPY. DIPY itself is licensed under the terms of the BSD license; see its [LICENSE file](https://github.com/dipy/dipy/blob/master/LICENSE).
