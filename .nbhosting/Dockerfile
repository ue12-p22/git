# --------
FROM nbhosting/minimal-notebook

# NOTE
# we cannot use jupyter nbextension enable/disable
# because we provide our own nbconfig/notebook.json
# and that is where is stored the enabled/disabled extensions
RUN true \
 && pip install nb-courselevels \
 && pip install nbautoeval \
 && pip install calysto_bash \
 && true
