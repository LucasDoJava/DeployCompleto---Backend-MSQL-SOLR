FROM solr:9.10

USER root
RUN mkdir -p /var/solr/data
RUN chown -R solr:solr /var/solr
USER solr

# ⚡ Cria cores somente se não existirem
RUN test -d /var/solr/data/users || precreate-core users
RUN test -d /var/solr/data/habits || precreate-core habits

# Healthcheck
HEALTHCHECK --interval=30s --timeout=10s --start-period=5s --retries=3 \
  CMD curl -f http://localhost:8983/solr/ || exit 1