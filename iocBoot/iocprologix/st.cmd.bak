#!../../bin/linux-x86_64/prologix

#- You may have to change prologix to something else
#- everywhere it appears in this file

< envPaths

epicsEnvSet("STREAM_PROTOCOL_PATH", "$(TOP)/db")
epicsEnvSet("PROLOGIX_ADDRESS", "$(PROLOGIX_ADDRESS=10.131.162.32)");
epicsEnvSet("P", "$(P=Prologix:)");
epicsEnvSet("R", "$(R=Test:)");
epicsEnvSet("A", "$(A=5)");
epicsEnvSet("B", "$(B=23)");

cd "${TOP}"

## Register all support components
dbLoadDatabase "dbd/prologix.dbd"
prologix_registerRecordDeviceDriver pdbbase

# Set up ASYN port
#prologixGPIBConfigure("L0", "$(PROLOGIX_ADDRESS)")
#asynOctetSetInputEos("L0", -1, "\n")
#asynSetTraceIOMask("L0_TCP", -1, 0x2)
#asynSetTraceMask("L0_TCP", -1, 0x9)
#asynSetTraceIOMask("L0", $(A), 0x2)
#asynSetTraceMask("L0", $(A), 0x9)

# Set up IP ASYN
drvAsynIPPortConfigure("B29","10.131.162.33:5025",0,0,1)
asynSetTraceIOMask("B29", $(A), 0x2)
asynSetTraceMask("B29", $(A), 0x9)

## Load record instances
#dbLoadRecords("db/xxx.db","user=epics")
#dbLoadRecords("db/gpib_win.db","P=$(IOC):,R=Test:,PORT=L0,A=11,B=23")
##############################################
#Uncomment to use E5270B !!!!
dbLoadRecords("db/gpib_e5270.db","PORT=L0,G=17")
dbLoadRecords("db/fastscan.db","PORT=L0,G=17")
##############################################
#dbLoadRecords("db/gpib_34401.db","PORT=L0,G=22")

#dbLoadRecords("db/gpib_b2912.db","PORT=B29")
#dbLoadRecords("db/fastscan_B2912.db","PORT=B29")

#dbLoadRecords("db/gpib_k220.db","PORT=L0,G=3")
cd "${TOP}/iocBoot/${IOC}"
iocInit

## Start any sequence programs
#seq sncxxx,"user=epics"
