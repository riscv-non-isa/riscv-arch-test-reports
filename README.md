# The Arch Test Report Repository

This  riscv-arch-test-reports github repo is where vendors that wish to self-certify that their implementations are RISC-V compatible file their ACT test results.
The riscof framework will generate a test report file with the name
- \<instanceID\>-\<test-date\>.html,  where
  -  \<test-date\> is in YYYY-MM-DD format using GMT as the time zone, and
  -  \<instanceID\> is a string that identifies which version of an implementer's core is being tested
at the conclusion of running the tests, along with a coverage report. The coverage report is for the vendors use only, and is not needed for self certification.

In addition to pass/fail indications for each individual test that is run, the generated report includes:
-  For any failures, the test case that failed, the expected value, and the actual value found,
-  The ISA string that describes the ISA, extensions, and sub-extensions implemented,
-  Any optional feature and configuration parameters allowed by the architecture that are used, defined by listing a YAML formatted configuration file. The schema is defined by the riscv-config format (see https://riscv-config.readthedocs.io/en/latest/overview.html),
-  The vendor and implementation IDs that the DUT will report in those respective CSRs (should be defined in the YAML configuration file),
   -           Note that these may be zero if unimplemented	
-  Name, commit hash,  and either version tags or git commit date (in ISO 8601 UTC format w/ offset 00:00) of tools used :
   -   Toolchain 
   -   reference model (generally Sail, occasionaly Spike), 
   -   Architecture Compatibility Test (ACT) suite version (from https://github.com/riscv-non-isa/riscv-arch-test/blob/main/CHANGELOG.md ).
   -   Framework version (from https://github.com/riscv-software-src/riscof/blob/master/CHANGELOG.md ).
If the test reports are missing any of the above versioning information, then a plaintext file with that missing information should be created, named \<instanceID\>-\<test-date\>-tools.txt

Vendors should submit their test results by filing a Pull Request that adds the test report (named \<instanceID\>-\<test-date\>.html as above) and the tools report (named \<instanceID\>-\<test-date\>.html as above) into a directory named for the vendor \<vendorname\> into this repo:	 https://github.com/riscv/riscv-arch-test-reports. Note that the coverage reports should **not** be part of the Pull Request!

Questions about this policy should be directed to sig-arch-test@lists.riscv.org
