FROM floui/switch.p4:P4_14-base

# build switch
RUN git clone https://github.com/p4lang/switch ; \
    cd switch ; \
    git submodule update --init --recursive ; \
    ./autogen.sh ; \
    ./configure --with-bmv2 --with-switchlink --prefix=/usr/local ; \
    make ; \
    make install ; ldconfig 

RUN cd /switch ; \
    echo "P4_SWITCH=\"/switch\"" > p4.bashrc ; \
    echo "" ; \
    echo "P4_TESTS=\"\$P4_SWITCH/tests\"" >> p4.bashrc ; \
    echo "P4_TOOLS=\"\$P4_SWITCH/tools\"" >> p4.bashrc ; \
    echo "P4_BMV2=\"\$P4_SWITCH/bmv2\"" >> p4.bashrc ; \
    echo "export PATH=\"\$P4_TESTS:\$P4_TOOLS:\$P4_BMV2:/usr/sbin:/usr/local/bin:\$PATH\"" >> p4.bashrc ; \
    echo "" ; \
    cat p4.bashrc >> /root/.bashrc
