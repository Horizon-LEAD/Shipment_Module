# Shipment_Synthesis

## Introduction 

This module Synthesize the shipments between origins and destinations of the commodities.

## Installation


## Installation

The `requirements.txt` and `Pipenv` files are provided for the setup of an environment where the module can be installed. The package includes a `setup.py` file and it can be therefore installed with a `pip install .` when we are at the same working directory as the `setup.py` file. For testing purposes, one can also install the package in editable mode `pip install -e .`.

After the install is completed, an executable `shipment-synthesis` will be available to the user.

Furthermore, a container image can be built by running `docker build -t shipment-synthesis:latest .` from the project's root directory.

## Usage

The executable's help message provides information on the parameters that are needed.

```
$ shipment-synthesis -h
usage: shipment-synthesis [-h] [-v] [--flog] [-e ENV]
                          SKIMTIME SKIMDISTANCE NODES ZONES SEGS PARCELNODES DISTRIBUTION_CENTRES
                          NSTR2LOGSEGMENTS MAKE_SHIPMENTS USE_SHIPMENTS SUP_COORDINATES CORRECTIONSTONNES
                          CEP_SHARES COST_PER_VEH_TYPE COST_OUTSRC NUTS2MRDH CARRYING_CAPACITY
                          LOG_FLOW_TYPE_SHARES TOD SHIPSIZE_VEHTYPE END_TOUR_FIRST END_TOUR_LATER
                          CONSOLIDATION_POTENTIAL ZEZ_SCENARIO FIRMS OUTPUTFOLDER

Shipment Synthesis

positional arguments:
  SKIMTIME              The path of the time skim matrix (mtx)
  SKIMDISTANCE          The path of the distance skim matrix (mtx)
  NODES                 The path of the logistics nodes shape file (shp)
  ZONES                 The path of the study area shape file (shp)
  SEGS                  The path of the socioeconomics data file (csv)
  PARCELNODES           The path of the parcel depot nodes file (shp)
  DISTRIBUTION_CENTRES  The path of the distribution centres file (csv)
  NSTR2LOGSEGMENTS      The path of the conversion NSTR to Logistics segments file (csv)
  MAKE_SHIPMENTS        The path of the Making Shipments per logistic sector file (csv)
  USE_SHIPMENTS         The path of the Using Shipments per logistic sector file (csv)
  SUP_COORDINATES       The path of the SUP coordinates file (csv)
  CORRECTIONSTONNES     The path of the Correction of Tonnes file (csv)
  CEP_SHARES            The path of the courier market shares file (csv)
  COST_PER_VEH_TYPE     The path of the costs per vehicles types file (csv)
  COST_OUTSRC           The path of the costs per vehicles types file (csv)
  NUTS2MRDH             The path of the conversion NUTS to MRDH file (csv)
  CARRYING_CAPACITY     The path of the carrying capacity file (csv)
  LOG_FLOW_TYPE_SHARES  The path of the markete share of logistic flow types file (csv)
  TOD                   The path of the Time Of Day choice model parameters file (csv)
  SHIPSIZE_VEHTYPE      The path of the shipment size and behicle type choice model parameters file (csv)
  END_TOUR_FIRST        The path of the End pf Tour model parameters file for the first visited location (csv)
  END_TOUR_LATER        The path of the End pf Tour model parameters file for the later visited location (csv)
  CONSOLIDATION_POTENTIAL
                        The path of the Consolidation Potentials for different logistics sectors file (csv)
  ZEZ_SCENARIO          The path of the specifications for zero emission zones in the study area file (csv)
  FIRMS                 The path of the specifications of synthesized firms file (csv)
  OUTPUTFOLDER          The output directory

optional arguments:
  -h, --help            show this help message and exit
  -v, --verbosity       Increase output verbosity (default: 0)
  --flog                Stores logs to file (default: False)
  -e ENV, --env ENV     Defines the path of the environment file (default: None)
```

Furthermore, the following parameters must be provided as environment variables either from the environment itself or through a dotenv file that is specified with the `--env <path-to-dotenv>` command line argument. An example of the `.env` file and some values is presented below.
```
# string parameters
LABEL="REF"
SHIPMENTS_REF=""
FAC_LS0=""
FAC_LS1=""
FAC_LS2=""
FAC_LS3=""
FAC_LS4=""
FAC_LS5=""
FAC_LS6=""
FAC_LS7=""
NEAREST_DC=""

# boolean parameters

# numeric parameters
YEARFACTOR=209
PARCELS_GROWTHFREIGHT=1.0

# string list parameters

# numeric list parameters

# json
```

```
python3 __module_SHIP__.py REF Input Output \
    skimTijd_new_REF.mtx \
    skimAfstand_new_REF.mtx \
    nodes_v5.shp \
    Zones_v6.shp \
    SEGS2020.csv \
    parcelNodes_v2.shp \
    distributieCentra.csv \
    nstrToLogisticSegment.csv \
    MakeDistribution.csv \
    UseDistribution.csv \
    SupCoordinatesID.csv \
    CorrectionsTonnes2016.csv \
    CEPshares.csv \
    Cost_VehType_2016.csv \
    Cost_Sourcing_2016.csv \
    NUTS32013toMRDH.csv \
    CarryingCapacity.csv \
    LogFlowtype_Shares.csv \
    Params_TOD.csv \
    Params_ShipSize_VehType.csv \
    Params_EndTourFirst.csv \
    Params_EndTourLater.csv \
    ConsolidationPotential.csv \
    ZEZscenario.csv \
    Firms.csv
```
