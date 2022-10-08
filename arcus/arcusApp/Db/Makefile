TOP=../..
include $(TOP)/configure/CONFIG
#----------------------------------------
#  ADD MACRO DEFINITIONS AFTER THIS LINE

#----------------------------------------------------
#  Optimization of db files using dbst (DEFAULT: NO)
#DB_OPT = YES

#----------------------------------------------------
# Create and install (or just install) into <top>/db
# databases, templates, substitutions like this
#DB += xxx.db
DB += arcus_ACE-SDE.substitutions
DB += arcus_ACE-SDE.template
DB += arcus_PMX-2ED-SA.substitutions
DB += arcus_PMX-2ED-SA.template
DB += arcus_PMX-2ED-SA.template.basic
DB += arcus_PMX-2ED-SA.template.Axis
DB += arcus_SaveRestore.template
DB += arcus_SaveRestore_Axis.template
DB += arcus_SaveRestore_2Axis.template
#DB += *.template
#DB += *.substitutions
#
#----------------------------------------------------
# If <anyname>.db template is not named <anyname>*.template add
# <anyname>_template = <templatename>

include $(TOP)/configure/RULES
#----------------------------------------
#  ADD RULES AFTER THIS LINE

