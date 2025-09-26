# Analysis Cases Execution Report

## Basic Information
- Execution time: 20250925_171336
- Total cases: 2
- Successfully executed: 2
- Working directory: D:\Administrator\Documents\Github\tricys\test_example\analysis\ai_analysis

## Case Details

### 1. DIR_Analysis
- Status: ✓ Success
- Independent variable: tep_fep.to_SDS_Fraction[1]
- Sampling method: linspace:0:0.9:10
- Working directory: D:\Administrator\Documents\Github\tricys\test_example\analysis\ai_analysis\analysis_cases\20250925_171336\DIR_Analysis
- Configuration file: D:\Administrator\Documents\Github\tricys\test_example\analysis\ai_analysis\analysis_cases\20250925_171336\DIR_Analysis\config.json

### 2. SALIB_Morris_Analysis
- Status: ✓ Success
- Independent variable: ['plasma1.fb', 'tep_fep.to_SDS_Fraction[1]', 'i_iss.T', 'blanket.TBR']
- Sampling method: {'plasma1.fb': {'bounds': [0.02, 0.2], 'distribution': 'unif'}, 'tep_fep.to_SDS_Fraction[1]': {'bounds': [0.1, 0.99], 'distribution': 'unif'}, 'i_iss.T': {'bounds': [4.0, 12.0], 'distribution': 'unif'}, 'blanket.TBR': {'bounds': [1.05, 1.25], 'distribution': 'unif'}}
- Working directory: D:\Administrator\Documents\Github\tricys\test_example\analysis\ai_analysis\analysis_cases\20250925_171336\SALIB_Morris_Analysis
- Configuration file: D:\Administrator\Documents\Github\tricys\test_example\analysis\ai_analysis\analysis_cases\20250925_171336\SALIB_Morris_Analysis\config.json