**************
CGCI Data Set
**************

About the Cancer Genome Characterization Initiative
---------------

The `Cancer Genome Characterization Initiative <https://ocg.cancer.gov/programs/cgci>`_ is a series of studies sponsored by the `Office of Cancer Genomics <https://ocg.cancer.gov/>`_ (OCG) at the `National Cancer Institute <https://www.cancer.gov/>`_ (NCI). This program utilizes molecular characterization to uncover distinct features of rare cancers such as HIV+ associated cancers and rare pediatric cancers. The `Burkitt Lymphoma Genome Sequencing Project <https://ocg.cancer.gov/programs/cgci/projects/burkitt-lymphoma>`_ (BLGSP) is one of the projects available through `GDC <https://portal.gdc.cancer.gov>`_. It explores genetic changes in patients with Burkitt lymphoma (BL) that could lead to better prevention, detection, and treatment of this rare and aggressive cancer.

About the Cancer Genome Characterization Initiative Data
--------------------

CGCI data consists of 120 cases with RNA sequencing, miRNA sequencing, and whole-genome sequencing data. The NCI GDC houses all the clinical, biospecimen, and molecular characterization data with over 589 BAM, 339 TXT, 402 TSV, 237 BRC XML, 120 BRC PPS XML, and 93 BCR SSF XML files in around 50.28 TB of data. The Project ID in the GDC Data Portal is `CGCI-BLGSP <https://portal.gdc.cancer.gov/projects/CGCI-BLGSP>`_.

For more information on the CGCI data, please refer to these sites:

- `CGCI Data Matrix <https://ocg.cancer.gov/programs/cgci/data-matrix>`_
- `dbGaP site <https://www.ncbi.nlm.nih.gov/projects/gap/cgi-bin/study.cgi?study_id=phs000235.v14.p2>`_
- `GDC Data Portal <https://portal.gdc.cancer.gov/repository?facetTab=cases&filters=%7B%22op%22%3A%22and%22%2C%22content%22%3A%5B%7B%22op%22%3A%22in%22%2C%22content%22%3A%7B%22field%22%3A%22cases.project.program.name%22%2C%22value%22%3A%5B%22CGCI%22%5D%7D%7D%5D%7D>`_

Accessing Cancer Genome Characterization Initiative Data on the Cloud
--------------------------------

Besides accessing the files on the GDC Data Portal, you can also access them from the GDC Google Cloud Storage Bucket, which means that you don’t need to download them to perform analysis. ISB-CGC stores the cloud file locations in tables in the ``isb-cgc.GDC_metadata`` data set in BigQuery.

- To access these metadata files, go to the Google BigQuery console.
- Perform SQL queries to find the CGCI files. Here is an example:

.. code-block:: sql

  SELECT active.*, file_gdc_url
  FROM `isb-cgc.GDC_metadata.rel22_fileData_active` as active, `isb-cgc.GDC_metadata.rel22_GDCfileID_to_GCSurl` as GCSurl
  WHERE program_name = 'CGCI'
  AND active.file_gdc_id = GCSurl.file_gdc_id
