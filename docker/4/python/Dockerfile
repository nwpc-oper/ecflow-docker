FROM nwpc-oper/ecflow-base

LABEL maintainer="perillaroc@gmail.com"

RUN set -ex \
    && export WK=/tmp/ecFlow-${ECFLOW_VERSION}-Source \
    && export BOOST_ROOT=/tmp/boost_${BOOST_VERSION} \
    \
    && cd ${WK} \
    && mkdir build \
    && cd build \
    && cmake .. -DENABLE_SERVER=OFF -DENABLE_PYTHON=ON -DENABLE_UI=OFF -DENABLE_GUI=OFF -DCMAKE_CXX_FLAGS="-w" \
    || echo "cmake has error, but ignored" \
    && CPUS=$(lscpu -p | grep -v '#' | wc -l) \
    && make -j${CPUS} \
    && make install \
    \
    && rm -rf /tmp/*

CMD ["python"]
