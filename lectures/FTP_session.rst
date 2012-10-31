Notes here: http://goo.gl/P55tZ
=========================================

In[1]:

.. code:: python

    # First, we import requied packages
    import ftplib # ftplib is an FTP client library
    import numpy as np # numpy is quite useful
    
    nasa_ftp =  "e4ftl01.cr.usgs.gov" # The location of the NASA FTP site
    ftp = ftplib.FTP( nasa_ftp )
    ftp.login("anonymous", "thisisme") # Username and password. Password is usually your email address
    ftp.cwd( 'MODIS_Composites/MOTA/MCD15A2.005' ) # Change directory
    data = []
    ftp.dir(data.append) # Get the listing. Note that this requires a method to fill each line

In[2]:

.. code:: python

    print data # Output is

.. parsed-literal::

    ['total 59664', 'drwxr-xr-x  2 90 122880 Jun 20  2008 2002.07.04', 'drwxr-xr-x  2 90 116736 Jun 20  2008 2002.07.12', 'drwxr-xr-x  2 90 118784 Jun 20  2008 2002.07.20', 'drwxr-xr-x  2 90 116736 Jun 20  2008 2002.07.28', 'drwxr-xr-x  2 90 118784 Jun 20  2008 2002.08.05', 'drwxr-xr-x  2 90 114688 Jun 20  2008 2002.08.13', 'drwxr-xr-x  2 90 118784 Jun 20  2008 2002.08.21', 'drwxr-xr-x  2 90 122880 Jun 20  2008 2002.08.29', 'drwxr-xr-x  2 90 116736 Jun 20  2008 2002.09.06', 'drwxr-xr-x  2 90 116736 Jun 20  2008 2002.09.14', 'drwxr-xr-x  2 90 116736 Jun 20  2008 2002.09.22', 'drwxr-xr-x  2 90 120832 Nov 30  2008 2002.09.30', 'drwxr-xr-x  2 90 116736 Nov 30  2008 2002.10.08', 'drwxr-xr-x  2 90 116736 Nov 30  2008 2002.10.16', 'drwxr-xr-x  2 90 118784 Nov 30  2008 2002.10.24', 'drwxr-xr-x  2 90 112640 Nov 30  2008 2002.11.01', 'drwxr-xr-x  2 90 120832 Nov 30  2008 2002.11.09', 'drwxr-xr-x  2 90 112640 Nov 30  2008 2002.11.17', 'drwxr-xr-x  2 90 116736 Nov 30  2008 2002.11.25', 'drwxr-xr-x  2 90 106496 Nov 30  2008 2002.12.03', 'drwxr-xr-x  2 90 114688 Nov 30  2008 2002.12.11', 'drwxr-xr-x  2 90 116736 Nov 30  2008 2002.12.19', 'drwxr-xr-x  2 90 116736 Nov 30  2008 2002.12.27', 'drwxr-xr-x  2 90 114688 Dec 16  2008 2003.01.01', 'drwxr-xr-x  2 90 118784 Dec 16  2008 2003.01.09', 'drwxr-xr-x  2 90 120832 Dec 16  2008 2003.01.17', 'drwxr-xr-x  2 90 108544 Dec 16  2008 2003.01.25', 'drwxr-xr-x  2 90 116736 Dec 16  2008 2003.02.02', 'drwxr-xr-x  2 90 116736 Dec 16  2008 2003.02.10', 'drwxr-xr-x  2 90 118784 Dec 16  2008 2003.02.18', 'drwxr-xr-x  2 90 120832 Dec 16  2008 2003.02.26', 'drwxr-xr-x  2 90 116736 Dec 16  2008 2003.03.06', 'drwxr-xr-x  2 90 116736 Dec 16  2008 2003.03.14', 'drwxr-xr-x  2 90 120832 Dec 16  2008 2003.03.22', 'drwxr-xr-x  2 90 114688 Dec 16  2008 2003.03.30', 'drwxr-xr-x  2 90 118784 Dec 16  2008 2003.04.07', 'drwxr-xr-x  2 90 122880 Dec 16  2008 2003.04.15', 'drwxr-xr-x  2 90 120832 Dec 16  2008 2003.04.23', 'drwxr-xr-x  2 90 110592 Sep  7  2011 2003.05.01', 'drwxr-xr-x  2 90 118784 Dec 16  2008 2003.05.09', 'drwxr-xr-x  2 90 124928 Dec 16  2008 2003.05.17', 'drwxr-xr-x  2 90 116736 Dec 16  2008 2003.05.25', 'drwxr-xr-x  2 90 118784 Dec 16  2008 2003.06.02', 'drwxr-xr-x  2 90 118784 Dec 16  2008 2003.06.10', 'drwxr-xr-x  2 90 112640 Dec 16  2008 2003.06.18', 'drwxr-xr-x  2 90 118784 Dec 16  2008 2003.06.26', 'drwxr-xr-x  2 90 118784 Dec 16  2008 2003.07.04', 'drwxr-xr-x  2 90 114688 Dec 16  2008 2003.07.12', 'drwxr-xr-x  2 90 118784 Dec 16  2008 2003.07.20', 'drwxr-xr-x  2 90 110592 Dec 16  2008 2003.07.28', 'drwxr-xr-x  2 90 118784 Dec 16  2008 2003.08.05', 'drwxr-xr-x  2 90 116736 Dec 16  2008 2003.08.13', 'drwxr-xr-x  2 90 114688 Dec 16  2008 2003.08.21', 'drwxr-xr-x  2 90 124928 Dec 16  2008 2003.08.29', 'drwxr-xr-x  2 90 118784 Dec 16  2008 2003.09.06', 'drwxr-xr-x  2 90 106496 Dec 16  2008 2003.09.14', 'drwxr-xr-x  2 90 122880 Dec 16  2008 2003.09.22', 'drwxr-xr-x  2 90 114688 Dec 16  2008 2003.09.30', 'drwxr-xr-x  2 90 120832 Dec 16  2008 2003.10.08', 'drwxr-xr-x  2 90 114688 Dec 16  2008 2003.10.16', 'drwxr-xr-x  2 90 120832 Dec 16  2008 2003.10.24', 'drwxr-xr-x  2 90 114688 Dec 16  2008 2003.11.01', 'drwxr-xr-x  2 90 120832 Dec 16  2008 2003.11.09', 'drwxr-xr-x  2 90 116736 Dec 16  2008 2003.11.17', 'drwxr-xr-x  2 90 120832 Dec 16  2008 2003.11.25', 'drwxr-xr-x  2 90 112640 Dec 16  2008 2003.12.03', 'drwxr-xr-x  2 90 110592 Dec 16  2008 2003.12.11', 'drwxr-xr-x  2 90 110592 Dec 16  2008 2003.12.19', 'drwxr-xr-x  2 90 110592 Dec 16  2008 2003.12.27', 'drwxr-xr-x  2 90 114688 Dec 16  2008 2004.01.01', 'drwxr-xr-x  2 90 120832 Dec 16  2008 2004.01.09', 'drwxr-xr-x  2 90 120832 Dec 16  2008 2004.01.17', 'drwxr-xr-x  2 90 114688 Dec 16  2008 2004.01.25', 'drwxr-xr-x  2 90 114688 Dec 16  2008 2004.02.02', 'drwxr-xr-x  2 90 116736 Dec 16  2008 2004.02.10', 'drwxr-xr-x  2 90 126976 Dec 16  2008 2004.02.18', 'drwxr-xr-x  2 90 120832 Dec 16  2008 2004.02.26', 'drwxr-xr-x  2 90 116736 May 22  2008 2004.03.05', 'drwxr-xr-x  2 90 122880 May 22  2008 2004.03.13', 'drwxr-xr-x  2 90 116736 May 22  2008 2004.03.21', 'drwxr-xr-x  2 90 116736 May 22  2008 2004.03.29', 'drwxr-xr-x  2 90 118784 May 22  2008 2004.04.06', 'drwxr-xr-x  2 90 118784 May 22  2008 2004.04.14', 'drwxr-xr-x  2 90 118784 May 22  2008 2004.04.22', 'drwxr-xr-x  2 90 116736 May 22  2008 2004.04.30', 'drwxr-xr-x  2 90 116736 May 22  2008 2004.05.08', 'drwxr-xr-x  2 90 114688 May 22  2008 2004.05.16', 'drwxr-xr-x  2 90 120832 May 22  2008 2004.05.24', 'drwxr-xr-x  2 90 118784 May 22  2008 2004.06.01', 'drwxr-xr-x  2 90 126976 May 22  2008 2004.06.09', 'drwxr-xr-x  2 90 114688 May 22  2008 2004.06.17', 'drwxr-xr-x  2 90 112640 May 22  2008 2004.06.25', 'drwxr-xr-x  2 90 116736 May 22  2008 2004.07.03', 'drwxr-xr-x  2 90 120832 May 22  2008 2004.07.11', 'drwxr-xr-x  2 90 120832 May 22  2008 2004.07.19', 'drwxr-xr-x  2 90 120832 May 22  2008 2004.07.27', 'drwxr-xr-x  2 90 114688 May 22  2008 2004.08.04', 'drwxr-xr-x  2 90 116736 May 22  2008 2004.08.12', 'drwxr-xr-x  2 90 129024 May 22  2008 2004.08.20', 'drwxr-xr-x  2 90 110592 May 22  2008 2004.08.28', 'drwxr-xr-x  2 90 112640 May 22  2008 2004.09.05', 'drwxr-xr-x  2 90 116736 May 22  2008 2004.09.13', 'drwxr-xr-x  2 90 120832 May 22  2008 2004.09.21', 'drwxr-xr-x  2 90 116736 May 22  2008 2004.09.29', 'drwxr-xr-x  2 90 124928 May 22  2008 2004.10.07', 'drwxr-xr-x  2 90 116736 May 22  2008 2004.10.15', 'drwxr-xr-x  2 90 114688 May 22  2008 2004.10.23', 'drwxr-xr-x  2 90 118784 May 22  2008 2004.10.31', 'drwxr-xr-x  2 90 114688 May 22  2008 2004.11.08', 'drwxr-xr-x  2 90 120832 May 22  2008 2004.11.16', 'drwxr-xr-x  2 90 122880 May 22  2008 2004.11.24', 'drwxr-xr-x  2 90 112640 May 22  2008 2004.12.02', 'drwxr-xr-x  2 90 114688 May 22  2008 2004.12.10', 'drwxr-xr-x  2 90 114688 May 22  2008 2004.12.18', 'drwxr-xr-x  2 90 108544 May 22  2008 2004.12.26', 'drwxr-xr-x  2 90 116736 May 22  2008 2005.01.01', 'drwxr-xr-x  2 90 114688 May 22  2008 2005.01.09', 'drwxr-xr-x  2 90 114688 May 22  2008 2005.01.17', 'drwxr-xr-x  2 90 120832 May 22  2008 2005.01.25', 'drwxr-xr-x  2 90 116736 May 22  2008 2005.02.02', 'drwxr-xr-x  2 90 118784 Nov 30  2008 2005.02.10', 'drwxr-xr-x  2 90 114688 May 23  2008 2005.02.18', 'drwxr-xr-x  2 90 124928 May 23  2008 2005.02.26', 'drwxr-xr-x  2 90 116736 May 22  2008 2005.03.06', 'drwxr-xr-x  2 90 114688 May 22  2008 2005.03.14', 'drwxr-xr-x  2 90 118784 May 22  2008 2005.03.22', 'drwxr-xr-x  2 90 114688 May 22  2008 2005.03.30', 'drwxr-xr-x  2 90 120832 May 22  2008 2005.04.07', 'drwxr-xr-x  2 90 112640 May 22  2008 2005.04.15', 'drwxr-xr-x  2 90 114688 May 23  2008 2005.04.23', 'drwxr-xr-x  2 90 118784 May 22  2008 2005.05.01', 'drwxr-xr-x  2 90 122880 May 22  2008 2005.05.09', 'drwxr-xr-x  2 90 122880 May 22  2008 2005.05.17', 'drwxr-xr-x  2 90 118784 May 22  2008 2005.05.25', 'drwxr-xr-x  2 90 110592 May 22  2008 2005.06.02', 'drwxr-xr-x  2 90 116736 May 22  2008 2005.06.10', 'drwxr-xr-x  2 90 122880 May 22  2008 2005.06.18', 'drwxr-xr-x  2 90 126976 May 22  2008 2005.06.26', 'drwxr-xr-x  2 90 116736 May 23  2008 2005.07.04', 'drwxr-xr-x  2 90 116736 May 22  2008 2005.07.12', 'drwxr-xr-x  2 90 126976 May 23  2008 2005.07.20', 'drwxr-xr-x  2 90 116736 May 23  2008 2005.07.28', 'drwxr-xr-x  2 90 114688 May 22  2008 2005.08.05', 'drwxr-xr-x  2 90 114688 May 23  2008 2005.08.13', 'drwxr-xr-x  2 90 120832 May 23  2008 2005.08.21', 'drwxr-xr-x  2 90 118784 May 23  2008 2005.08.29', 'drwxr-xr-x  2 90 124928 Dec 16  2008 2005.09.06', 'drwxr-xr-x  2 90 110592 Dec 16  2008 2005.09.14', 'drwxr-xr-x  2 90 116736 Dec 16  2008 2005.09.22', 'drwxr-xr-x  2 90 122880 Dec 16  2008 2005.09.30', 'drwxr-xr-x  2 90 114688 Apr 30  2012 2005.10.08', 'drwxr-xr-x  2 90 120832 Dec 16  2008 2005.10.16', 'drwxr-xr-x  2 90 120832 Dec 16  2008 2005.10.24', 'drwxr-xr-x  2 90 112640 Dec 16  2008 2005.11.01', 'drwxr-xr-x  2 90 118784 Dec 16  2008 2005.11.09', 'drwxr-xr-x  2 90 112640 Dec 16  2008 2005.11.17', 'drwxr-xr-x  2 90 120832 Dec 16  2008 2005.11.25', 'drwxr-xr-x  2 90 112640 Dec 16  2008 2005.12.03', 'drwxr-xr-x  2 90 116736 Dec 16  2008 2005.12.11', 'drwxr-xr-x  2 90 110592 Nov 30  2008 2005.12.19', 'drwxr-xr-x  2 90 114688 Nov 30  2008 2005.12.27', 'drwxr-xr-x  2 90 106496 May 23  2008 2006.01.01', 'drwxr-xr-x  2 90 114688 Dec 16  2008 2006.01.09', 'drwxr-xr-x  2 90 118784 Dec 16  2008 2006.01.17', 'drwxr-xr-x  2 90 112640 Dec 16  2008 2006.01.25', 'drwxr-xr-x  2 90 122880 Dec 16  2008 2006.02.02', 'drwxr-xr-x  2 90 114688 Dec 16  2008 2006.02.10', 'drwxr-xr-x  2 90 116736 Nov 30  2008 2006.02.18', 'drwxr-xr-x  2 90 118784 May 24  2008 2006.02.26', 'drwxr-xr-x  2 90 122880 May 24  2008 2006.03.06', 'drwxr-xr-x  2 90 114688 May 24  2008 2006.03.14', 'drwxr-xr-x  2 90 116736 Sep  7  2011 2006.03.22', 'drwxr-xr-x  2 90 110592 Apr  8  2008 2006.03.30', 'drwxr-xr-x  2 90 112640 Apr  8  2008 2006.04.07', 'drwxr-xr-x  2 90 114688 Apr 11  2008 2006.04.15', 'drwxr-xr-x  2 90 114688 Apr 14  2008 2006.04.23', 'drwxr-xr-x  2 90 120832 Apr 20  2008 2006.05.01', 'drwxr-xr-x  2 90 124928 Apr 26  2008 2006.05.09', 'drwxr-xr-x  2 90 108544 Apr 27  2008 2006.05.17', 'drwxr-xr-x  2 90 116736 Apr 27  2008 2006.05.25', 'drwxr-xr-x  2 90 116736 Apr 29  2008 2006.06.02', 'drwxr-xr-x  2 90 116736 May  8  2008 2006.06.10', 'drwxr-xr-x  2 90 122880 May  8  2008 2006.06.18', 'drwxr-xr-x  2 90 114688 May  8  2008 2006.06.26', 'drwxr-xr-x  2 90 120832 May 12  2008 2006.07.04', 'drwxr-xr-x  2 90 110592 May 13  2008 2006.07.12', 'drwxr-xr-x  2 90 122880 May 17  2008 2006.07.20', 'drwxr-xr-x  2 90 114688 Mar 30  2009 2006.07.28', 'drwxr-xr-x  2 90 114688 Apr 10  2008 2006.08.05', 'drwxr-xr-x  2 90 116736 Apr 12  2008 2006.08.13', 'drwxr-xr-x  2 90 110592 Apr 14  2008 2006.08.21', 'drwxr-xr-x  2 90 120832 Apr 13  2008 2006.08.29', 'drwxr-xr-x  2 90 118784 Jul 11  2008 2006.09.06', 'drwxr-xr-x  2 90 116736 Apr 18  2008 2006.09.14', 'drwxr-xr-x  2 90 118784 Apr 25  2008 2006.09.22', 'drwxr-xr-x  2 90 122880 Apr 25  2008 2006.09.30', 'drwxr-xr-x  2 90 114688 Apr 26  2008 2006.10.08', 'drwxr-xr-x  2 90 118784 Apr 26  2008 2006.10.16', 'drwxr-xr-x  2 90 120832 Apr 28  2008 2006.10.24', 'drwxr-xr-x  2 90 116736 May  1  2008 2006.11.01', 'drwxr-xr-x  2 90 118784 May  1  2008 2006.11.09', 'drwxr-xr-x  2 90 118784 May  6  2008 2006.11.17', 'drwxr-xr-x  2 90 122880 May  6  2008 2006.11.25', 'drwxr-xr-x  2 90 110592 May  9  2008 2006.12.03', 'drwxr-xr-x  2 90 106496 May  9  2008 2006.12.11', 'drwxr-xr-x  2 90 108544 May 12  2008 2006.12.19', 'drwxr-xr-x  2 90 110592 May 13  2008 2006.12.27', 'drwxr-xr-x  2 90 110592 Jun 28  2008 2007.01.01', 'drwxr-xr-x  2 90 122880 Jun 28  2008 2007.01.09', 'drwxr-xr-x  2 90 112640 Jun 28  2008 2007.01.17', 'drwxr-xr-x  2 90 112640 Dec 16  2008 2007.01.25', 'drwxr-xr-x  2 90 122880 Dec 16  2008 2007.02.02', 'drwxr-xr-x  2 90 118784 Dec 16  2008 2007.02.10', 'drwxr-xr-x  2 90 122880 Jun 28  2008 2007.02.18', 'drwxr-xr-x  2 90 120832 Dec 16  2008 2007.02.26', 'drwxr-xr-x  2 90 122880 Dec 16  2008 2007.03.06', 'drwxr-xr-x  2 90 116736 Dec 16  2008 2007.03.14', 'drwxr-xr-x  2 90 122880 Dec 16  2008 2007.03.22', 'drwxr-xr-x  2 90 118784 Dec 16  2008 2007.03.30', 'drwxr-xr-x  2 90 122880 Dec 16  2008 2007.04.07', 'drwxr-xr-x  2 90 124928 Dec 16  2008 2007.04.15', 'drwxr-xr-x  2 90 118784 Dec 16  2008 2007.04.23', 'drwxr-xr-x  2 90 114688 Dec 16  2008 2007.05.01', 'drwxr-xr-x  2 90 120832 Dec 16  2008 2007.05.09', 'drwxr-xr-x  2 90 112640 Dec 16  2008 2007.05.17', 'drwxr-xr-x  2 90 110592 Dec 12  2008 2007.05.25', 'drwxr-xr-x  2 90 116736 Nov 30  2008 2007.06.02', 'drwxr-xr-x  2 90 120832 Nov 30  2008 2007.06.10', 'drwxr-xr-x  2 90 114688 Dec 12  2008 2007.06.18', 'drwxr-xr-x  2 90 118784 Dec 12  2008 2007.06.26', 'drwxr-xr-x  2 90 122880 Dec 12  2008 2007.07.04', 'drwxr-xr-x  2 90 114688 Nov 30  2008 2007.07.12', 'drwxr-xr-x  2 90 118784 Nov 30  2008 2007.07.20', 'drwxr-xr-x  2 90 118784 Nov 30  2008 2007.07.28', 'drwxr-xr-x  2 90 112640 Nov 30  2008 2007.08.05', 'drwxr-xr-x  2 90 118784 Nov 30  2008 2007.08.13', 'drwxr-xr-x  2 90 116736 Nov 30  2008 2007.08.21', 'drwxr-xr-x  2 90 116736 Nov 30  2008 2007.08.29', 'drwxr-xr-x  2 90 120832 Dec 16  2008 2007.09.06', 'drwxr-xr-x  2 90 118784 Nov 30  2008 2007.09.14', 'drwxr-xr-x  2 90 118784 Dec 16  2008 2007.09.22', 'drwxr-xr-x  2 90 114688 Jun 17  2008 2007.09.30', 'drwxr-xr-x  2 90 116736 Dec 16  2008 2007.10.08', 'drwxr-xr-x  2 90 120832 Jun 17  2008 2007.10.16', 'drwxr-xr-x  2 90 116736 Jun 17  2008 2007.10.24', 'drwxr-xr-x  2 90 122880 Nov 30  2008 2007.11.01', 'drwxr-xr-x  2 90 116736 Jun 17  2008 2007.11.09', 'drwxr-xr-x  2 90 114688 Nov 30  2008 2007.11.17', 'drwxr-xr-x  2 90 124928 Jun 17  2008 2007.11.25', 'drwxr-xr-x  2 90 114688 Jul 31  2008 2007.12.03', 'drwxr-xr-x  2 90 114688 Jun 17  2008 2007.12.11', 'drwxr-xr-x  2 90 120832 Jun 17  2008 2007.12.19', 'drwxr-xr-x  2 90 114688 Jun 17  2008 2007.12.27', 'drwxr-xr-x  2 90 110592 May 25  2008 2008.01.01', 'drwxr-xr-x  2 90 112640 May 25  2008 2008.01.09', 'drwxr-xr-x  2 90 118784 May 25  2008 2008.01.17', 'drwxr-xr-x  2 90 116736 Jul 31  2008 2008.01.25', 'drwxr-xr-x  2 90 116736 May 25  2008 2008.02.02', 'drwxr-xr-x  2 90 122880 May 25  2008 2008.02.10', 'drwxr-xr-x  2 90 120832 May 25  2008 2008.02.18', 'drwxr-xr-x  2 90 114688 May 25  2008 2008.02.26', 'drwxr-xr-x  2 90 118784 May 25  2008 2008.03.05', 'drwxr-xr-x  2 90 118784 May 24  2008 2008.03.13', 'drwxr-xr-x  2 90 126976 Apr  4  2008 2008.03.21', 'drwxr-xr-x  2 90 116736 Apr  9  2008 2008.03.29', 'drwxr-xr-x  2 90 122880 Apr 19  2008 2008.04.06', 'drwxr-xr-x  2 90 114688 Apr 26  2008 2008.04.14', 'drwxr-xr-x  2 90 114688 May  3  2008 2008.04.22', 'drwxr-xr-x  2 90 118784 May 12  2008 2008.04.30', 'drwxr-xr-x  2 90 116736 May 19  2008 2008.05.08', 'drwxr-xr-x  2 90 118784 May 26  2008 2008.05.16', 'drwxr-xr-x  2 90 116736 Jun  4  2008 2008.05.24', 'drwxr-xr-x  2 90 118784 Jun 10  2008 2008.06.01', 'drwxr-xr-x  2 90 122880 Jun 19  2008 2008.06.09', 'drwxr-xr-x  2 90 120832 Jun 28  2008 2008.06.17', 'drwxr-xr-x  2 90 116736 Jul  7  2008 2008.06.25', 'drwxr-xr-x  2 90 120832 Jul 13  2008 2008.07.03', 'drwxr-xr-x  2 90 120832 Jul 20  2008 2008.07.11', 'drwxr-xr-x  2 90 116736 Jul 29  2008 2008.07.19', 'drwxr-xr-x  2 90 126976 Aug  7  2008 2008.07.27', 'drwxr-xr-x  2 90 120833 Aug 14  2008 2008.08.04', 'drwxr-xr-x  2 90 116736 Aug 25  2008 2008.08.12', 'drwxr-xr-x  2 90 114688 Aug 30  2008 2008.08.20', 'drwxr-xr-x  2 90 118784 Sep  7  2008 2008.08.28', 'drwxr-xr-x  2 90 112640 Sep 16  2008 2008.09.05', 'drwxr-xr-x  2 90 116736 Sep 23  2008 2008.09.13', 'drwxr-xr-x  2 90 116736 Oct  1  2008 2008.09.21', 'drwxr-xr-x  2 90 120832 Oct 13  2008 2008.09.29', 'drwxr-xr-x  2 90 120832 Oct 26  2008 2008.10.07', 'drwxr-xr-x  2 90 112640 Nov  3  2008 2008.10.15', 'drwxr-xr-x  2 90 110592 Nov  3  2008 2008.10.23', 'drwxr-xr-x  2 90 116736 Nov 12  2008 2008.10.31', 'drwxr-xr-x  2 90 116736 Nov 24  2008 2008.11.08', 'drwxr-xr-x  2 90 122880 Nov 27  2008 2008.11.16', 'drwxr-xr-x  2 90 114688 Jun  1  2009 2008.11.24', 'drwxr-xr-x  2 90 112640 Dec 18  2008 2008.12.02', 'drwxr-xr-x  2 90 112640 Dec 20  2008 2008.12.10', 'drwxr-xr-x  2 90 118784 Jan  9  2009 2008.12.18', 'drwxr-xr-x  2 90 116736 Jan 14  2009 2008.12.26', 'drwxr-xr-x  2 90 110592 Oct 28  2009 2009.01.01', 'drwxr-xr-x  2 90 114688 Feb  5  2009 2009.01.09', 'drwxr-xr-x  2 90 114688 Feb  2  2009 2009.01.17', 'drwxr-xr-x  2 90 116736 Feb 11  2009 2009.01.25', 'drwxr-xr-x  2 90 114688 Feb 17  2009 2009.02.02', 'drwxr-xr-x  2 90 114688 Feb 27  2009 2009.02.10', 'drwxr-xr-x  2 90 129024 Mar  1  2009 2009.02.18', 'drwxr-xr-x  2 90 120832 Mar  9  2009 2009.02.26', 'drwxr-xr-x  2 90 116736 Mar 21  2009 2009.03.06', 'drwxr-xr-x  2 90 116736 Apr  1  2009 2009.03.14', 'drwxr-xr-x  2 90 116736 Apr  6  2009 2009.03.22', 'drwxr-xr-x  2 90 116736 Apr 11  2009 2009.03.30', 'drwxr-xr-x  2 90 112640 Apr 17  2009 2009.04.07', 'drwxr-xr-x  2 90 116736 May  4  2009 2009.04.15', 'drwxr-xr-x  2 90 112640 May  8  2009 2009.04.23', 'drwxr-xr-x  2 90 114688 May 10  2009 2009.05.01', 'drwxr-xr-x  2 90 118784 May 21  2009 2009.05.09', 'drwxr-xr-x  2 90 124928 Jun  1  2009 2009.05.17', 'drwxr-xr-x  2 90 116736 Jun  3  2009 2009.05.25', 'drwxr-xr-x  2 90 120832 Jun 15  2009 2009.06.02', 'drwxr-xr-x  2 90 120832 Jun 29  2009 2009.06.10', 'drwxr-xr-x  2 90 118784 Jun 29  2009 2009.06.18', 'drwxr-xr-x  2 90 112640 Jul 14  2009 2009.06.26', 'drwxr-xr-x  2 90 118784 Jul 17  2009 2009.07.04', 'drwxr-xr-x  2 90 114688 Jul 23  2009 2009.07.12', 'drwxr-xr-x  2 90 114688 Jul 29  2009 2009.07.20', 'drwxr-xr-x  2 90 122880 Aug  9  2009 2009.07.28', 'drwxr-xr-x  2 90 116736 Aug 16  2009 2009.08.05', 'drwxr-xr-x  2 90 118784 Aug 22  2009 2009.08.13', 'drwxr-xr-x  2 90 110592 Sep  5  2009 2009.08.21', 'drwxr-xr-x  2 90 116736 Sep  7  2009 2009.08.29', 'drwxr-xr-x  2 90 114688 Sep 15  2009 2009.09.06', 'drwxr-xr-x  2 90 120832 Sep 25  2009 2009.09.14', 'drwxr-xr-x  2 90 118784 Oct  3  2009 2009.09.22', 'drwxr-xr-x  2 90 120832 Oct 10  2009 2009.09.30', 'drwxr-xr-x  2 90 116736 Nov  3  2009 2009.10.08', 'drwxr-xr-x  2 90 118784 Nov  3  2009 2009.10.16', 'drwxr-xr-x  2 90 108544 Nov  6  2009 2009.10.24', 'drwxr-xr-x  2 90 116736 Nov 10  2009 2009.11.01', 'drwxr-xr-x  2 90 116736 Nov 18  2009 2009.11.09', 'drwxr-xr-x  2 90 124928 Dec  7  2009 2009.11.17', 'drwxr-xr-x  2 90 114688 Dec 20  2009 2009.11.25', 'drwxr-xr-x  2 90 110592 Dec 12  2009 2009.12.03', 'drwxr-xr-x  2 90 112640 Dec 22  2009 2009.12.11', 'drwxr-xr-x  2 90 118784 Dec 31  2009 2009.12.19', 'drwxr-xr-x  2 90 112640 Jan 13  2010 2009.12.27', 'drwxr-xr-x  2 90 114688 Jan 28  2010 2010.01.01', 'drwxr-xr-x  2 90 116736 Jan 27  2010 2010.01.09', 'drwxr-xr-x  2 90 120832 Jan 27  2010 2010.01.17', 'drwxr-xr-x  2 90 116736 Feb 16  2010 2010.01.25', 'drwxr-xr-x  2 90 116736 Feb 11  2010 2010.02.02', 'drwxr-xr-x  2 90 118784 Feb 20  2010 2010.02.10', 'drwxr-xr-x  2 90 120833 Mar  3  2010 2010.02.18', 'drwxr-xr-x  2 90 114688 Mar  9  2010 2010.02.26', 'drwxr-xr-x  2 90 112640 Mar 24  2010 2010.03.06', 'drwxr-xr-x  2 90 118784 Mar 23  2010 2010.03.14', 'drwxr-xr-x  2 90 116736 Apr 14  2010 2010.03.22', 'drwxr-xr-x  2 90 120832 Apr 11  2010 2010.03.30', 'drwxr-xr-x  2 90 116736 Apr 18  2010 2010.04.07', 'drwxr-xr-x  2 90 122880 Apr 25  2010 2010.04.15', 'drwxr-xr-x  2 90 118784 May 13  2010 2010.04.23', 'drwxr-xr-x  2 90 118784 May 13  2010 2010.05.01', 'drwxr-xr-x  2 90 120832 May 22  2010 2010.05.09', 'drwxr-xr-x  2 90 112640 May 27  2010 2010.05.17', 'drwxr-xr-x  2 90 118784 Jun 10  2010 2010.05.25', 'drwxr-xr-x  2 90 118784 Jun 14  2010 2010.06.02', 'drwxr-xr-x  2 90 122881 Jun 21  2010 2010.06.10', 'drwxr-xr-x  2 90 122880 Jun 27  2010 2010.06.18', 'drwxr-xr-x  2 90 112640 Jul 11  2010 2010.06.26', 'drwxr-xr-x  2 90 112640 Jul 17  2010 2010.07.04', 'drwxr-xr-x  2 90 122880 Jul 21  2010 2010.07.12', 'drwxr-xr-x  2 90 120832 Aug 20  2010 2010.07.20', 'drwxr-xr-x  2 90 120832 Aug 22  2010 2010.07.28', 'drwxr-xr-x  2 90 124928 Aug 31  2010 2010.08.05', 'drwxr-xr-x  2 90 112640 Sep  3  2010 2010.08.13', 'drwxr-xr-x  2 90 116736 Sep 13  2010 2010.08.21', 'drwxr-xr-x  2 90 112640 Sep 13  2010 2010.08.29', 'drwxr-xr-x  2 90 116736 Sep 21  2010 2010.09.06', 'drwxr-xr-x  2 90 116736 Sep 27  2010 2010.09.14', 'drwxr-xr-x  2 90 122880 Oct 12  2010 2010.09.22', 'drwxr-xr-x  2 90 116736 Oct 12  2010 2010.09.30', 'drwxr-xr-x  2 90 116736 Oct 17  2010 2010.10.08', 'drwxr-xr-x  2 90 122880 Oct 25  2010 2010.10.16', 'drwxr-xr-x  2 90 118784 Nov  4  2010 2010.10.24', 'drwxr-xr-x  2 90 116736 Nov 10  2010 2010.11.01', 'drwxr-xr-x  2 90 122880 Nov 19  2010 2010.11.09', 'drwxr-xr-x  2 90 112640 Nov 26  2010 2010.11.17', 'drwxr-xr-x  2 90 114688 Dec  4  2010 2010.11.25', 'drwxr-xr-x  2 90 114688 Dec 12  2010 2010.12.03', 'drwxr-xr-x  2 90 118784 Dec 23  2010 2010.12.11', 'drwxr-xr-x  2 90 106496 Mar 27  2011 2010.12.19', 'drwxr-xr-x  2 90 110592 Mar 27  2011 2010.12.27', 'drwxr-xr-x  2 90 110592 Jan 18  2011 2011.01.01', 'drwxr-xr-x  2 90 122880 Jan 20  2011 2011.01.09', 'drwxr-xr-x  2 90 116736 Feb  2  2011 2011.01.17', 'drwxr-xr-x  2 90 114688 Feb  6  2011 2011.01.25', 'drwxr-xr-x  2 90 122880 Feb 15  2011 2011.02.02', 'drwxr-xr-x  2 90 118784 Feb 25  2011 2011.02.10', 'drwxr-xr-x  2 90 118784 Feb 28  2011 2011.02.18', 'drwxr-xr-x  2 90 116736 Mar 13  2011 2011.02.26', 'drwxr-xr-x  2 90 118784 Mar 17  2011 2011.03.06', 'drwxr-xr-x  2 90 116736 Mar 24  2011 2011.03.14', 'drwxr-xr-x  2 90 118784 Apr  5  2011 2011.03.22', 'drwxr-xr-x  2 90 116736 Apr 12  2011 2011.03.30', 'drwxr-xr-x  2 90 118784 Apr 25  2011 2011.04.07', 'drwxr-xr-x  2 90 122880 May  2  2011 2011.04.15', 'drwxr-xr-x  2 90 118784 May  2  2011 2011.04.23', 'drwxr-xr-x  2 90 112640 May 11  2011 2011.05.01', 'drwxr-xr-x  2 90 120832 May 19  2011 2011.05.09', 'drwxr-xr-x  2 90 122880 May 31  2011 2011.05.17', 'drwxr-xr-x  2 90 120832 Jun  9  2011 2011.05.25', 'drwxr-xr-x  2 90 114688 Jun 23  2011 2011.06.02', 'drwxr-xr-x  2 90 116736 Jun 23  2011 2011.06.10', 'drwxr-xr-x  2 90 116736 Jun 29  2011 2011.06.18', 'drwxr-xr-x  2 90 118784 Jul  5  2011 2011.06.26', 'drwxr-xr-x  2 90 237568 Aug 22  2011 2011.07.04', 'drwxr-xr-x  2 90 114688 Jul 25  2011 2011.07.12', 'drwxr-xr-x  2 90 112640 Jul 29  2011 2011.07.20', 'drwxr-xr-x  2 90 122880 Aug  9  2011 2011.07.28', 'drwxr-xr-x  2 90 120832 Aug 16  2011 2011.08.05', 'drwxr-xr-x  2 90 116736 Aug 25  2011 2011.08.13', 'drwxr-xr-x  2 90 118784 Aug 30  2011 2011.08.21', 'drwxr-xr-x  2 90 120832 Sep  7  2011 2011.08.29', 'drwxr-xr-x  2 90 122880 Sep 15  2011 2011.09.06', 'drwxr-xr-x  2 90 118784 Sep 23  2011 2011.09.14', 'drwxr-xr-x  2 90 118784 Oct 27  2011 2011.09.22', 'drwxr-xr-x  2 90 116736 Oct 14  2011 2011.09.30', 'drwxr-xr-x  2 90 114688 Oct 20  2011 2011.10.08', 'drwxr-xr-x  2 90 116736 Oct 25  2011 2011.10.16', 'drwxr-xr-x  2 90 114688 Nov  3  2011 2011.10.24', 'drwxr-xr-x  2 90 120832 Nov 11  2011 2011.11.01', 'drwxr-xr-x  2 90 114688 Nov 18  2011 2011.11.09', 'drwxr-xr-x  2 90 110592 Nov 29  2011 2011.11.17', 'drwxr-xr-x  2 90 116736 Dec  9  2011 2011.11.25', 'drwxr-xr-x  2 90 114688 Dec 12  2011 2011.12.03', 'drwxr-xr-x  2 90 114688 Dec 21  2011 2011.12.11', 'drwxr-xr-x  2 90 108544 Dec 29  2011 2011.12.19', 'drwxr-xr-x  2 90 110592 Jan  6  2012 2011.12.27', 'drwxr-xr-x  2 90 108544 Jan 31  2012 2012.01.01', 'drwxr-xr-x  2 90 114688 Jan 19  2012 2012.01.09', 'drwxr-xr-x  2 90 118784 Jan 26  2012 2012.01.17', 'drwxr-xr-x  2 90 241664 Apr  2  2012 2012.01.25', 'drwxr-xr-x  2 90 110592 Feb 11  2012 2012.02.02', 'drwxr-xr-x  2 90 110592 Feb 19  2012 2012.02.10', 'drwxr-xr-x  2 90 126976 Mar 11  2012 2012.02.18', 'drwxr-xr-x  2 90 116736 Mar 11  2012 2012.02.26', 'drwxr-xr-x  2 90 118784 Mar 16  2012 2012.03.05', 'drwxr-xr-x  2 90 114688 Mar 22  2012 2012.03.13', 'drwxr-xr-x  2 90 118784 Mar 30  2012 2012.03.21', 'drwxr-xr-x  2 90 118784 Apr 16  2012 2012.03.29', 'drwxr-xr-x  2 90 112640 Apr 17  2012 2012.04.06', 'drwxr-xr-x  2 90 122880 Apr 25  2012 2012.04.14', 'drwxr-xr-x  2 90 120832 May  1 06:32 2012.04.22', 'drwxr-xr-x  2 90 120832 May 16 20:19 2012.04.30', 'drwxr-xr-x  2 90 235520 Jun  5 10:23 2012.05.08', 'drwxr-xr-x  2 90 116736 Jun  1 00:03 2012.05.16', 'drwxr-xr-x  2 90 114688 Jun  8 09:27 2012.05.24', 'drwxr-xr-x  2 90 114688 Jun 14 12:40 2012.06.01', 'drwxr-xr-x  2 90 122880 Jun 18 07:10 2012.06.09', 'drwxr-xr-x  2 90 120832 Jun 29 12:33 2012.06.17', 'drwxr-xr-x  2 90 122880 Jul  6 13:23 2012.06.25', 'drwxr-xr-x  2 90 233472 Sep 27 12:23 2012.07.03', 'drwxr-xr-x  2 90 116736 Jul 20 13:49 2012.07.11', 'drwxr-xr-x  2 90 120832 Aug  2 13:24 2012.07.19', 'drwxr-xr-x  2 90 116736 Aug  6 16:18 2012.07.27', 'drwxr-xr-x  2 90 114688 Aug 16 07:26 2012.08.04', 'drwxr-xr-x  2 90 124928 Aug 21 08:19 2012.08.12', 'drwxr-xr-x  2 90 116736 Aug 29 13:10 2012.08.20', 'drwxr-xr-x  2 90 120832 Sep  6 22:48 2012.08.28', 'drwxr-xr-x  2 90 114688 Sep 17 20:28 2012.09.05', 'drwxr-xr-x  2 90 118784 Sep 26 08:26 2012.09.13', 'drwxr-xr-x  2 90 114688 Oct  2 10:52 2012.09.21', 'drwxr-xr-x  2 90 235520 Oct 25 09:54 2012.09.29', 'drwxr-xr-x  2 90 118784 Oct 23 10:29 2012.10.07', 'drwxr-xr-x  2 90 120832 Oct 25 18:44 2012.10.15']


Parsing the directory structue
==============================

We want extract the information in the directory names so we can select
the ones we are interested in

We want to store the year, month and day as integers

Since each directory line is a string, we can use string methods to
**split** the bits we want

But we need a robust way of doing this, as there can be **rogue
directory names** popping up

In[4]:

.. code:: python

    all_dirs = [] # We shall store the directory dates here
    for this_line in data[1:]: # We can loop over the directory listing lines
                               # Note we are skipping the first element
        the_dir = this_line.split()[-1] # Split by whitespace and grab the last element, the directory name
        parsed_dir = [] # A temporary empty list
        if ( len(the_dir.split(".")) == 3 ): # If we have three elements after splitting by "."
            for k in the_dir.split("."): # Loop over the three elements
                if k.isdigit(): # Test whether we have a digit
                    parsed_dir.append ( int(k) ) # We, do, convert the string to digit and append to temporary list
                else: # We don't
                    parsed_dir.append ( 0 ) # Append a 0
        else:
            parsed_dir = [0,0,0]
        all_dirs.append ( parsed_dir ) # Append temporary list to final list


Catching errors: Exceptions
===========================

The above code is quite messy (the one in the notes is even worse!), and
not very robust. What if the line ::

    the_dir = this_line.split()[-1]

fails? In practice, there could be all sorts of other errors. We can use
**exceptions** to catch these. We have the following structure

::

    try:
        # Do something that might break
    except:
        # Alternative action in case something broke in the try block

We can even specify different *exception types* to react to different
errors.

In the previous case, we can make the code more succint using
exceptions.

**REMEMBER** cleaner and leaner code results in simpler debugging!

In[5]:

.. code:: python

    all_dirs = []
    for this_line in data:
        try:
            the_dir = this_line.split()[-1].split(".")
            parsed_dir = [ int(the_dir[0]), int(the_dir[1]), int(the_dir[2])]
        except:
            parsed_dir = [ 0, 0, 0 ]
        all_dirs.append ( parsed_dir ) 
    
    print all_dirs

.. parsed-literal::

    [[0, 0, 0], [2002, 7, 4], [2002, 7, 12], [2002, 7, 20], [2002, 7, 28], [2002, 8, 5], [2002, 8, 13], [2002, 8, 21], [2002, 8, 29], [2002, 9, 6], [2002, 9, 14], [2002, 9, 22], [2002, 9, 30], [2002, 10, 8], [2002, 10, 16], [2002, 10, 24], [2002, 11, 1], [2002, 11, 9], [2002, 11, 17], [2002, 11, 25], [2002, 12, 3], [2002, 12, 11], [2002, 12, 19], [2002, 12, 27], [2003, 1, 1], [2003, 1, 9], [2003, 1, 17], [2003, 1, 25], [2003, 2, 2], [2003, 2, 10], [2003, 2, 18], [2003, 2, 26], [2003, 3, 6], [2003, 3, 14], [2003, 3, 22], [2003, 3, 30], [2003, 4, 7], [2003, 4, 15], [2003, 4, 23], [2003, 5, 1], [2003, 5, 9], [2003, 5, 17], [2003, 5, 25], [2003, 6, 2], [2003, 6, 10], [2003, 6, 18], [2003, 6, 26], [2003, 7, 4], [2003, 7, 12], [2003, 7, 20], [2003, 7, 28], [2003, 8, 5], [2003, 8, 13], [2003, 8, 21], [2003, 8, 29], [2003, 9, 6], [2003, 9, 14], [2003, 9, 22], [2003, 9, 30], [2003, 10, 8], [2003, 10, 16], [2003, 10, 24], [2003, 11, 1], [2003, 11, 9], [2003, 11, 17], [2003, 11, 25], [2003, 12, 3], [2003, 12, 11], [2003, 12, 19], [2003, 12, 27], [2004, 1, 1], [2004, 1, 9], [2004, 1, 17], [2004, 1, 25], [2004, 2, 2], [2004, 2, 10], [2004, 2, 18], [2004, 2, 26], [2004, 3, 5], [2004, 3, 13], [2004, 3, 21], [2004, 3, 29], [2004, 4, 6], [2004, 4, 14], [2004, 4, 22], [2004, 4, 30], [2004, 5, 8], [2004, 5, 16], [2004, 5, 24], [2004, 6, 1], [2004, 6, 9], [2004, 6, 17], [2004, 6, 25], [2004, 7, 3], [2004, 7, 11], [2004, 7, 19], [2004, 7, 27], [2004, 8, 4], [2004, 8, 12], [2004, 8, 20], [2004, 8, 28], [2004, 9, 5], [2004, 9, 13], [2004, 9, 21], [2004, 9, 29], [2004, 10, 7], [2004, 10, 15], [2004, 10, 23], [2004, 10, 31], [2004, 11, 8], [2004, 11, 16], [2004, 11, 24], [2004, 12, 2], [2004, 12, 10], [2004, 12, 18], [2004, 12, 26], [2005, 1, 1], [2005, 1, 9], [2005, 1, 17], [2005, 1, 25], [2005, 2, 2], [2005, 2, 10], [2005, 2, 18], [2005, 2, 26], [2005, 3, 6], [2005, 3, 14], [2005, 3, 22], [2005, 3, 30], [2005, 4, 7], [2005, 4, 15], [2005, 4, 23], [2005, 5, 1], [2005, 5, 9], [2005, 5, 17], [2005, 5, 25], [2005, 6, 2], [2005, 6, 10], [2005, 6, 18], [2005, 6, 26], [2005, 7, 4], [2005, 7, 12], [2005, 7, 20], [2005, 7, 28], [2005, 8, 5], [2005, 8, 13], [2005, 8, 21], [2005, 8, 29], [2005, 9, 6], [2005, 9, 14], [2005, 9, 22], [2005, 9, 30], [2005, 10, 8], [2005, 10, 16], [2005, 10, 24], [2005, 11, 1], [2005, 11, 9], [2005, 11, 17], [2005, 11, 25], [2005, 12, 3], [2005, 12, 11], [2005, 12, 19], [2005, 12, 27], [2006, 1, 1], [2006, 1, 9], [2006, 1, 17], [2006, 1, 25], [2006, 2, 2], [2006, 2, 10], [2006, 2, 18], [2006, 2, 26], [2006, 3, 6], [2006, 3, 14], [2006, 3, 22], [2006, 3, 30], [2006, 4, 7], [2006, 4, 15], [2006, 4, 23], [2006, 5, 1], [2006, 5, 9], [2006, 5, 17], [2006, 5, 25], [2006, 6, 2], [2006, 6, 10], [2006, 6, 18], [2006, 6, 26], [2006, 7, 4], [2006, 7, 12], [2006, 7, 20], [2006, 7, 28], [2006, 8, 5], [2006, 8, 13], [2006, 8, 21], [2006, 8, 29], [2006, 9, 6], [2006, 9, 14], [2006, 9, 22], [2006, 9, 30], [2006, 10, 8], [2006, 10, 16], [2006, 10, 24], [2006, 11, 1], [2006, 11, 9], [2006, 11, 17], [2006, 11, 25], [2006, 12, 3], [2006, 12, 11], [2006, 12, 19], [2006, 12, 27], [2007, 1, 1], [2007, 1, 9], [2007, 1, 17], [2007, 1, 25], [2007, 2, 2], [2007, 2, 10], [2007, 2, 18], [2007, 2, 26], [2007, 3, 6], [2007, 3, 14], [2007, 3, 22], [2007, 3, 30], [2007, 4, 7], [2007, 4, 15], [2007, 4, 23], [2007, 5, 1], [2007, 5, 9], [2007, 5, 17], [2007, 5, 25], [2007, 6, 2], [2007, 6, 10], [2007, 6, 18], [2007, 6, 26], [2007, 7, 4], [2007, 7, 12], [2007, 7, 20], [2007, 7, 28], [2007, 8, 5], [2007, 8, 13], [2007, 8, 21], [2007, 8, 29], [2007, 9, 6], [2007, 9, 14], [2007, 9, 22], [2007, 9, 30], [2007, 10, 8], [2007, 10, 16], [2007, 10, 24], [2007, 11, 1], [2007, 11, 9], [2007, 11, 17], [2007, 11, 25], [2007, 12, 3], [2007, 12, 11], [2007, 12, 19], [2007, 12, 27], [2008, 1, 1], [2008, 1, 9], [2008, 1, 17], [2008, 1, 25], [2008, 2, 2], [2008, 2, 10], [2008, 2, 18], [2008, 2, 26], [2008, 3, 5], [2008, 3, 13], [2008, 3, 21], [2008, 3, 29], [2008, 4, 6], [2008, 4, 14], [2008, 4, 22], [2008, 4, 30], [2008, 5, 8], [2008, 5, 16], [2008, 5, 24], [2008, 6, 1], [2008, 6, 9], [2008, 6, 17], [2008, 6, 25], [2008, 7, 3], [2008, 7, 11], [2008, 7, 19], [2008, 7, 27], [2008, 8, 4], [2008, 8, 12], [2008, 8, 20], [2008, 8, 28], [2008, 9, 5], [2008, 9, 13], [2008, 9, 21], [2008, 9, 29], [2008, 10, 7], [2008, 10, 15], [2008, 10, 23], [2008, 10, 31], [2008, 11, 8], [2008, 11, 16], [2008, 11, 24], [2008, 12, 2], [2008, 12, 10], [2008, 12, 18], [2008, 12, 26], [2009, 1, 1], [2009, 1, 9], [2009, 1, 17], [2009, 1, 25], [2009, 2, 2], [2009, 2, 10], [2009, 2, 18], [2009, 2, 26], [2009, 3, 6], [2009, 3, 14], [2009, 3, 22], [2009, 3, 30], [2009, 4, 7], [2009, 4, 15], [2009, 4, 23], [2009, 5, 1], [2009, 5, 9], [2009, 5, 17], [2009, 5, 25], [2009, 6, 2], [2009, 6, 10], [2009, 6, 18], [2009, 6, 26], [2009, 7, 4], [2009, 7, 12], [2009, 7, 20], [2009, 7, 28], [2009, 8, 5], [2009, 8, 13], [2009, 8, 21], [2009, 8, 29], [2009, 9, 6], [2009, 9, 14], [2009, 9, 22], [2009, 9, 30], [2009, 10, 8], [2009, 10, 16], [2009, 10, 24], [2009, 11, 1], [2009, 11, 9], [2009, 11, 17], [2009, 11, 25], [2009, 12, 3], [2009, 12, 11], [2009, 12, 19], [2009, 12, 27], [2010, 1, 1], [2010, 1, 9], [2010, 1, 17], [2010, 1, 25], [2010, 2, 2], [2010, 2, 10], [2010, 2, 18], [2010, 2, 26], [2010, 3, 6], [2010, 3, 14], [2010, 3, 22], [2010, 3, 30], [2010, 4, 7], [2010, 4, 15], [2010, 4, 23], [2010, 5, 1], [2010, 5, 9], [2010, 5, 17], [2010, 5, 25], [2010, 6, 2], [2010, 6, 10], [2010, 6, 18], [2010, 6, 26], [2010, 7, 4], [2010, 7, 12], [2010, 7, 20], [2010, 7, 28], [2010, 8, 5], [2010, 8, 13], [2010, 8, 21], [2010, 8, 29], [2010, 9, 6], [2010, 9, 14], [2010, 9, 22], [2010, 9, 30], [2010, 10, 8], [2010, 10, 16], [2010, 10, 24], [2010, 11, 1], [2010, 11, 9], [2010, 11, 17], [2010, 11, 25], [2010, 12, 3], [2010, 12, 11], [2010, 12, 19], [2010, 12, 27], [2011, 1, 1], [2011, 1, 9], [2011, 1, 17], [2011, 1, 25], [2011, 2, 2], [2011, 2, 10], [2011, 2, 18], [2011, 2, 26], [2011, 3, 6], [2011, 3, 14], [2011, 3, 22], [2011, 3, 30], [2011, 4, 7], [2011, 4, 15], [2011, 4, 23], [2011, 5, 1], [2011, 5, 9], [2011, 5, 17], [2011, 5, 25], [2011, 6, 2], [2011, 6, 10], [2011, 6, 18], [2011, 6, 26], [2011, 7, 4], [2011, 7, 12], [2011, 7, 20], [2011, 7, 28], [2011, 8, 5], [2011, 8, 13], [2011, 8, 21], [2011, 8, 29], [2011, 9, 6], [2011, 9, 14], [2011, 9, 22], [2011, 9, 30], [2011, 10, 8], [2011, 10, 16], [2011, 10, 24], [2011, 11, 1], [2011, 11, 9], [2011, 11, 17], [2011, 11, 25], [2011, 12, 3], [2011, 12, 11], [2011, 12, 19], [2011, 12, 27], [2012, 1, 1], [2012, 1, 9], [2012, 1, 17], [2012, 1, 25], [2012, 2, 2], [2012, 2, 10], [2012, 2, 18], [2012, 2, 26], [2012, 3, 5], [2012, 3, 13], [2012, 3, 21], [2012, 3, 29], [2012, 4, 6], [2012, 4, 14], [2012, 4, 22], [2012, 4, 30], [2012, 5, 8], [2012, 5, 16], [2012, 5, 24], [2012, 6, 1], [2012, 6, 9], [2012, 6, 17], [2012, 6, 25], [2012, 7, 3], [2012, 7, 11], [2012, 7, 19], [2012, 7, 27], [2012, 8, 4], [2012, 8, 12], [2012, 8, 20], [2012, 8, 28], [2012, 9, 5], [2012, 9, 13], [2012, 9, 21], [2012, 9, 29], [2012, 10, 7], [2012, 10, 15]]


Selecting directories
=====================

Let's say you want to access data only for a given year and month... How
do we go about that?

The simplest way is by looping:

In[6]:

.. code:: python

    the_year = 2011
    the_month = 7
    for the_dir in all_dirs:
        if ( the_dir[0] == the_year ) and ( the_dir[1] == the_month ):
            print the_dir
            # Or actually do something interesting

.. parsed-literal::

    [2011, 7, 4]
    [2011, 7, 12]
    [2011, 7, 20]
    [2011, 7, 28]


We can also use the fact that ``all_dirs`` is a list, convert it into a
numpy array and use numpy to index it

In[7]:

.. code:: python

    all_dirs = np.array ( all_dirs ) # You make an array out of a list by using np.array( <list name> )
    print all_dirs.shape
    selected_dirs1 = np.logical_and ( all_dirs[:, 0] == the_year, all_dirs[:,1] == the_month )
    print all_dirs[selected_dirs1] # Question: what is selected_dirs1?
    # We can also use the np.where construct
    selected_dirs2 = np.where ( (all_dirs[:, 0] == the_year) * ( all_dirs[:,1] == the_month ) )[0]
    print all_dirs[selected_dirs2] # Question: what is selected_dirs?

.. parsed-literal::

    (475, 3)
    [[2011    7    4]
     [2011    7   12]
     [2011    7   20]
     [2011    7   28]]
    [[2011    7    4]
     [2011    7   12]
     [2011    7   20]
     [2011    7   28]]


In[8]:

.. code:: python

    print selected_dirs1
    print selected_dirs2
    print np.array( data )[selected_dirs2]

.. parsed-literal::

    [False False False False False False False False False False False False
     False False False False False False False False False False False False
     False False False False False False False False False False False False
     False False False False False False False False False False False False
     False False False False False False False False False False False False
     False False False False False False False False False False False False
     False False False False False False False False False False False False
     False False False False False False False False False False False False
     False False False False False False False False False False False False
     False False False False False False False False False False False False
     False False False False False False False False False False False False
     False False False False False False False False False False False False
     False False False False False False False False False False False False
     False False False False False False False False False False False False
     False False False False False False False False False False False False
     False False False False False False False False False False False False
     False False False False False False False False False False False False
     False False False False False False False False False False False False
     False False False False False False False False False False False False
     False False False False False False False False False False False False
     False False False False False False False False False False False False
     False False False False False False False False False False False False
     False False False False False False False False False False False False
     False False False False False False False False False False False False
     False False False False False False False False False False False False
     False False False False False False False False False False False False
     False False False False False False False False False False False False
     False False False False False False False False False False False False
     False False False False False False False False False False False False
     False False False False False False False False False False False False
     False False False False False False False False False False False False
     False False False False False False False False False False False False
     False False False False False False False False False False False False
     False False False False False False False False False False False False
     False False False False False False False  True  True  True  True False
     False False False False False False False False False False False False
     False False False False False False False False False False False False
     False False False False False False False False False False False False
     False False False False False False False False False False False False
     False False False False False False False]
    [415 416 417 418]
    ['drwxr-xr-x  2 90 237568 Aug 22  2011 2011.07.04'
     'drwxr-xr-x  2 90 114688 Jul 25  2011 2011.07.12'
     'drwxr-xr-x  2 90 112640 Jul 29  2011 2011.07.20'
     'drwxr-xr-x  2 90 122880 Aug  9  2011 2011.07.28']


Downloading stuff
=================

So, what do we need to do to download a file?

1. We need to change into the required directory
2. We need to download the file
3. Go back to #1 and repeat

In order to download a file from FTPLIB, we need to have a **handler
function**, that sends the data to an already opened file.

Also, we shall only download files from a single MODIS "tile", h09v05.
See where this tile lies

![MODIS tile map] (
http://nsidc.org/data/docs/daac/mod10\_modis\_snow/images/sinusoidal.gif
)

In[9]:

.. code:: python

    def write_chunk ( block ):
        """A file writer handler for FTPLIB. Writes `block`
        to an open file handler called `fp`"""
        fp.write ( block )
    # Need to select the actual directories...    
    the_dirs = np.array( data )[selected_dirs2]
    # We only want a small portion of the surface of the Earth
    tile = "h09v05"
    
    quick_looks = [] # There are also a number of JPG quicklooks. Let's track their filenames
    
    for curr_line in the_dirs: # Loop over the desired directories/folders in the remote FTP server
        curr_dir = curr_line.split()[-1] # Just the dirname
        ftp.cwd ( curr_dir ) # Change directory to curr_dir
        file_list = [] # Each folder has a file list
        ftp.dir( file_list.append ) # Now stored in file_list
        for fich in file_list: # Loop over the elements of the file list
            if fich.find ( tile ) >= 0: # If we find the name of the tile in the filename...
                the_fich = fich.split()[7] # Grab the actual filename
                
                if the_fich.find ( ".1.jpg" ) >= 0: # If the filename has a ".1.jpg" extension, it's a 
                    quick_looks.append ( the_fich ) # quicklook file
                    
                print "Downloading %s" % the_fich # let the user know what's happening
                
                fp = open ( the_fich, 'w' ) # Open the output file
                ftp.retrbinary ( "RETR %s" % the_fich, write_chunk ) # Do the downloading. Use the handler
                                                                     # defined above
                fp.close() # Close the file for writing
                print "\t>>> Done!"
        
        ftp.cwd ( ".." ) # Go back to parent directory in remote server
        

.. parsed-literal::

    Downloading BROWSE.MCD15A2.A2011185.h09v05.005.2011213154534.1.jpg
    	>>> Done!
    Downloading BROWSE.MCD15A2.A2011185.h09v05.005.2011213154534.2.jpg
    	>>> Done!
    Downloading MCD15A2.A2011185.h09v05.005.2011213154534.hdf
    	>>> Done!
    Downloading MCD15A2.A2011185.h09v05.005.2011213154534.hdf.xml
        >>> Done!
    Downloading BROWSE.MCD15A2.A2011193.h09v05.005.2011203175347.1.jpg
    	>>> Done!
    Downloading BROWSE.MCD15A2.A2011193.h09v05.005.2011203175347.2.jpg
    	>>> Done!
    Downloading MCD15A2.A2011193.h09v05.005.2011203175347.hdf
    	>>> Done!
    Downloading MCD15A2.A2011193.h09v05.005.2011203175347.hdf.xml
    	>>> Done!
    Downloading BROWSE.MCD15A2.A2011201.h09v05.005.2011210161955.1.jpg
    	>>> Done!
    Downloading BROWSE.MCD15A2.A2011201.h09v05.005.2011210161955.2.jpg
    	>>> Done!
    Downloading MCD15A2.A2011201.h09v05.005.2011210161955.hdf
    	>>> Done!
    Downloading MCD15A2.A2011201.h09v05.005.2011210161955.hdf.xml
    	>>> Done!
    Downloading BROWSE.MCD15A2.A2011209.h09v05.005.2011220122803.1.jpg
    	>>> Done!
    Downloading BROWSE.MCD15A2.A2011209.h09v05.005.2011220122803.2.jpg
    	>>> Done!
    Downloading MCD15A2.A2011209.h09v05.005.2011220122803.hdf
    	>>> Done!
    Downloading MCD15A2.A2011209.h09v05.005.2011220122803.hdf.xml
    	>>> Done!

    


Seeing the result of our exploit
================================

You'll notice we now have some JPG images. We can use the shell program
``display <filename>`` to view them interactively. We can also plot them
with matplotlib..

In[12]:

.. code:: python

    from IPython.core.display import Image 
    Image(filename='BROWSE.MCD15A2.A2011185.h09v05.005.2011213154534.1.jpg')

Out[12]:

.. parsed-literal::

    <IPython.core.display.Image at 0xaacf8cc>

Examining the MODIS HDF files in the shell
==========================================

The GDAL tools offer many command line utilitis to perform many
operations with raster and vector spatial datasets, see
`here <http://www.gdal.org/gdal_utilities.html%20%60http://www.gdal.org/gdal_utilities.html%60>`_.

Let's see what we can find out about the files from the shell, and we'll
then use the Python GDAL bindings to read data into Python and
manipulate it.

Open a shell and ``cd`` to the directory/folder where you can see the
HDF files you've just downloaded...

Then just use the gdalinfo program to examine the HDF dataset

::

    $ gdalinfo MCD15A2.A2011185.h09v05.005.2011213154534.hdf
    Driver: HDF4/Hierarchical Data Format Release 4
    Files: MCD15A2.A2011185.h09v05.005.2011213154534.hdf
    Size is 512, 512
    Coordinate System is `'
    Metadata:
    [...]
    VERTICALTILENUMBER=05
    WESTBOUNDINGCOORDINATE=-117.486656023174
    Subdatasets:
      SUBDATASET_1_NAME=HDF4_EOS:EOS_GRID:"MCD15A2.A2011185.h09v05.005.2011213154534.hdf":MOD_Grid_MOD15A2:Fpar_1km
      SUBDATASET_1_DESC=[1200x1200] Fpar_1km MOD_Grid_MOD15A2 (8-bit unsigned integer)
      SUBDATASET_2_NAME=HDF4_EOS:EOS_GRID:"MCD15A2.A2011185.h09v05.005.2011213154534.hdf":MOD_Grid_MOD15A2:Lai_1km
      SUBDATASET_2_DESC=[1200x1200] Lai_1km MOD_Grid_MOD15A2 (8-bit unsigned integer)
      SUBDATASET_3_NAME=HDF4_EOS:EOS_GRID:"MCD15A2.A2011185.h09v05.005.2011213154534.hdf":MOD_Grid_MOD15A2:FparLai_QC
      SUBDATASET_3_DESC=[1200x1200] FparLai_QC MOD_Grid_MOD15A2 (8-bit unsigned integer)
      SUBDATASET_4_NAME=HDF4_EOS:EOS_GRID:"MCD15A2.A2011185.h09v05.005.2011213154534.hdf":MOD_Grid_MOD15A2:FparExtra_QC
      SUBDATASET_4_DESC=[1200x1200] FparExtra_QC MOD_Grid_MOD15A2 (8-bit unsigned integer)
      SUBDATASET_5_NAME=HDF4_EOS:EOS_GRID:"MCD15A2.A2011185.h09v05.005.2011213154534.hdf":MOD_Grid_MOD15A2:FparStdDev_1km
      SUBDATASET_5_DESC=[1200x1200] FparStdDev_1km MOD_Grid_MOD15A2 (8-bit unsigned integer)
      SUBDATASET_6_NAME=HDF4_EOS:EOS_GRID:"MCD15A2.A2011185.h09v05.005.2011213154534.hdf":MOD_Grid_MOD15A2:LaiStdDev_1km
      SUBDATASET_6_DESC=[1200x1200] LaiStdDev_1km MOD_Grid_MOD15A2 (8-bit unsigned integer)
    Corner Coordinates:
    Upper Left  (    0.0,    0.0)
    Lower Left  (    0.0,  512.0)
    Upper Right (  512.0,    0.0)
    Lower Right (  512.0,  512.0)
    Center      (  256.0,  256.0)


We have **6 datasets**:

-  fAPAR @ 1km
-  LAI @ 1 km
-  fAPAR :math:`$\sigma$`
-  LAI :math:`$\sigma$`
-  Standard QA (quality assurance) flags
-  Extended QA flags

We can get more insight into each dataset by using its GDAL name (see
after the ``=`` symbol where it says ``SUBDATASET_1_NAME``,
``SUBDATASET_2_NAME``, etc). We need to use single quotes ``'`` around
the GDAL dataset:

::

    gdalinfo  'HDF4_EOS:EOS_GRID:"MCD15A2.A2011185.h09v05.005.2011213154534.hdf":MOD_Grid_MOD15A2:Fpar_1km'
    Driver: HDF4Image/HDF4 Dataset
    Files: MCD15A2.A2011185.h09v05.005.2011213154534.hdf
    Size is 1200, 1200
    Coordinate System is:
    PROJCS["unnamed",
        GEOGCS["Unknown datum based upon the custom spheroid",
            DATUM["Not specified (based on custom spheroid)",
                SPHEROID["Custom spheroid",6371007.181,0]],
            PRIMEM["Greenwich",0],
            UNIT["degree",0.0174532925199433]],
        PROJECTION["Sinusoidal"],
        PARAMETER["longitude_of_center",0],
        PARAMETER["false_easting",0],
        PARAMETER["false_northing",0],
        UNIT["Meter",1]]
    Origin = (-10007554.676999999210238,4447802.078666999936104)
    Pixel Size = (926.625433055833014,-926.625433055833355)
    Metadata:
    [...]
    Corner Coordinates:
    Upper Left  (-10007554.677, 4447802.079) (117d29'11.96"W, 40d 0' 0.00"N)
    Lower Left  (-10007554.677, 3335851.559) (103d55'22.97"W, 30d 0' 0.00"N)
    Upper Right (-8895604.157, 4447802.079) (104d25'57.30"W, 40d 0' 0.00"N)
    Lower Right (-8895604.157, 3335851.559) ( 92d22'33.76"W, 30d 0' 0.00"N)
    Center      (-9451579.417, 3891826.819) (103d45'57.02"W, 35d 0' 0.00"N)
    Band 1 Block=1200x100 Type=Byte, ColorInterp=Gray
          Description = MCD15A2 MODIS/Terra+Aqua Gridded 1KM FPAR (8-day composite)
          NoData Value=255
          Unit Type: Percent
          Offset: 0,   Scale:0.01

Note how this tells us

-  the size of the dataset
-  the projection used (in this case, the MODIS sinusoidal projection)
-  the pixel size
-  the origin of the dataset (upper left corner)
-  lots of "metadata"
-  the coordinates of the corners of the raster
-  the bands, as well as their datatype


Opening the dataset in python
=============================

Just to list the available datasets in the HDF file, we can open the
filename, and use the ``GetSubDatasets()`` method...

In[28]:

.. code:: python

    from osgeo import gdal
    g = gdal.Open ( "MCD15A2.A2011185.h09v05.005.2011213154534.hdf")
    sds = g.GetSubDatasets()
    print sds

.. parsed-literal::

    [('HDF4_EOS:EOS_GRID:"MCD15A2.A2011185.h09v05.005.2011213154534.hdf":MOD_Grid_MOD15A2:Fpar_1km', '[1200x1200] Fpar_1km MOD_Grid_MOD15A2 (8-bit unsigned integer)'), ('HDF4_EOS:EOS_GRID:"MCD15A2.A2011185.h09v05.005.2011213154534.hdf":MOD_Grid_MOD15A2:Lai_1km', '[1200x1200] Lai_1km MOD_Grid_MOD15A2 (8-bit unsigned integer)'), ('HDF4_EOS:EOS_GRID:"MCD15A2.A2011185.h09v05.005.2011213154534.hdf":MOD_Grid_MOD15A2:FparLai_QC', '[1200x1200] FparLai_QC MOD_Grid_MOD15A2 (8-bit unsigned integer)'), ('HDF4_EOS:EOS_GRID:"MCD15A2.A2011185.h09v05.005.2011213154534.hdf":MOD_Grid_MOD15A2:FparExtra_QC', '[1200x1200] FparExtra_QC MOD_Grid_MOD15A2 (8-bit unsigned integer)'), ('HDF4_EOS:EOS_GRID:"MCD15A2.A2011185.h09v05.005.2011213154534.hdf":MOD_Grid_MOD15A2:FparStdDev_1km', '[1200x1200] FparStdDev_1km MOD_Grid_MOD15A2 (8-bit unsigned integer)'), ('HDF4_EOS:EOS_GRID:"MCD15A2.A2011185.h09v05.005.2011213154534.hdf":MOD_Grid_MOD15A2:LaiStdDev_1km', '[1200x1200] LaiStdDev_1km MOD_Grid_MOD15A2 (8-bit unsigned integer)')]


If we use the actual GDAL name, we will actually open the raster
data....

In[20]:

.. code:: python

    g = gdal.Open ( 'HDF4_EOS:EOS_GRID:"MCD15A2.A2011185.h09v05.005.2011213154534.hdf":MOD_Grid_MOD15A2:Fpar_1km' )
    fapar = g.ReadAsArray()
    plt.imshow ( fapar, vmin=1, vmax=90, interpolation='nearest', cmap=plt.cm.spectral )
    plt.colorbar()
    print "The type of fapar is " , type ( fapar )
    print "The size of fapar is ", fapar.shape


.. parsed-literal::

    The type of fapar is  <type 'numpy.ndarray'>
    The size of fapar is  (1200, 1200)


.. image:: FTP_session_files/FTP_session_fig_00.png

So in the example above, ``fapar`` is a standard numpy array, so we can
use the numpy library to process it, and matplotlib to easily do plots,
as done above

In[22]:

.. code:: python

    import numpy as np
    import pylab as plt
    g = gdal.Open ( 'HDF4_EOS:EOS_GRID:"MCD15A2.A2011185.h09v05.005.2011213154534.hdf":MOD_Grid_MOD15A2:FparLai_QC' )
    qc = g.ReadAsArray()
    mask = (qc*0).astype(bool)
    okvalues = [0,2]
    for i in okvalues:
        mask[np.where(qc == i)] = True
    
    
    fig = plt.figure()
    ax = fig.add_subplot(111)
    cax = ax.imshow(mask, interpolation='nearest')
    cbar = fig.colorbar(cax, ticks=[0,1])
    ax.set_title('Data mask')
    plt.show()

.. image:: FTP_session_files/FTP_session_fig_01.png

Use this mask to mask the LAI value where we don't have assurance of
good quality...

In[24]:

.. code:: python

    g = gdal.Open ( 'HDF4_EOS:EOS_GRID:"MCD15A2.A2011185.h09v05.005.2011213154534.hdf":MOD_Grid_MOD15A2:Lai_1km' )
    lai = g.ReadAsArray()
    fig = plt.figure()
    ax = fig.add_subplot(111)
    nlai = np.where ( mask == 1, lai*.1, 0.0 )
    cax = ax.imshow(nlai, interpolation='nearest', cmap=plt.cm.spectral)
    cbar = fig.colorbar(cax)
    ax.set_title('LAI data')
    plt.show()

.. image:: FTP_session_files/FTP_session_fig_02.png

What about the uncertainty in the estimate of LAI? This is stored as the
standard deviation in another layer. We can easily access it, mask it
and plot it:

In[27]:

.. code:: python

    g = gdal.Open ( 'HDF4_EOS:EOS_GRID:"MCD15A2.A2011185.h09v05.005.2011213154534.hdf":MOD_Grid_MOD15A2:LaiStdDev_1km' )
    sigma_lai = g.ReadAsArray()
    fig = plt.figure()
    ax = fig.add_subplot(111)
    n_sigma_lai = np.where ( mask == 1, sigma_lai*0.1, 0.0 )
    cax = ax.imshow(n_sigma_lai, interpolation='nearest', cmap=plt.cm.spectral)
    cbar = fig.colorbar(cax)
    ax.set_title(r'LAI standard deviation data')
    plt.show()

.. image:: FTP_session_files/FTP_session_fig_03.png

More on GDAL
============

There's quite a bit of extra documentation on using GDAL on
`http://jgomezdans.github.com/gdal\_notes/ <http://jgomezdans.github.com/gdal_notes/>`_

Vector datasets
===============

Vector data are usually given in a format called ESRI Shapefile
(although other formats also exist). OGR (GDAL's vector sister library)
can deal with shapefiles and many other formats.

Getting some data
`````````````````

The file of interest is in the following url:
`http://txpub.usgs.gov/USACE/data/water\_resources/Hydrologic\_Units.zip <http://txpub.usgs.gov/USACE/data/water_resources/Hydrologic_Units.zip>`_.
We will use some shell tools to download this file, but remember that
you could use Python for this! However, it's just a one off, so might as
well use the shell for this:

::

    berlin% mkdir hucData
    berlin% cd hucData
    berlin% wget http://txpub.usgs.gov/USACE/data/water_resources/Hydrologic_Units.zip
    berlin% curl http://txpub.usgs.gov/USACE/data/water_resources/Hydrologic_Units.zip -o Hydrologic_Units.zip
    berlin% unzip Hydrologic_Units.zip
        Archive:  Hydrologic_Units.zip
        ...
        inflating: Hydrologic_Units/HUC_Polygons.shp

We can then use ``ogrinfo``, the equivalent of ``gdalinfo`` for vector
data, and point to the file with the ``.shp`` extension. Remember to put
the right path to the file, and then to specify the *layer*, which in
the case of a Shapefile, it's just the filename without the ``.shp``
extension. Also, maybe use ``less`` to page the output

::

    ogrinfo Hydrologic_Units/HUC_Polygons.shp HUC_Polygons | less
    INFO: Open of `Hydrologic_Units/HUC_Polygons.shp'
      using driver `ESRI Shapefile' successful.

    Layer name: HUC_Polygons
    Geometry: Polygon
    Feature Count: 71
    Extent: (-1207861.193700, -1295788.385400) - (-115932.919500, 152769.254400)
    Layer SRS WKT:
    PROJCS["USA_Contiguous_Albers_Equal_Area_Conic",
        GEOGCS["GCS_North_American_1983",
            DATUM["North_American_Datum_1983",
                SPHEROID["GRS_1980",6378137.0,298.257222101]],
            PRIMEM["Greenwich",0.0],
            UNIT["Degree",0.0174532925199433]],
        PROJECTION["Albers_Conic_Equal_Area"],
        PARAMETER["False_Easting",0.0],
        PARAMETER["False_Northing",0.0],
        PARAMETER["longitude_of_center",-96.0],
        PARAMETER["Standard_Parallel_1",29.5],
        PARAMETER["Standard_Parallel_2",45.5],
        PARAMETER["latitude_of_center",37.5],
        UNIT["Meter",1.0]]
    HUC: Integer (9.0)
    REG_NAME: String (50.0)
    SUB_NAME: String (51.0)
    ACC_NAME: String (36.0)
    CAT_NAME: String (60.0)
    HUC2: Integer (4.0)
    HUC4: Integer (4.0)
    HUC6: Integer (9.0)
    REG: Integer (4.0)
    SUB: Integer (4.0)
    ACC: Integer (9.0)
    CAT: Integer (9.0)
    CAT_NUM: String (8.0)
    Shape_Leng: Real (19.11)
    Shape_Area: Real (19.11)
    OGRFeature(HUC_Polygons):0
      HUC (Integer) = 13010003
      REG_NAME (String) = Rio Grande Region
      SUB_NAME (String) = Rio Grande Headwaters
      ACC_NAME (String) = Rio Grande Headwaters
      CAT_NAME (String) = San Luis. Colorado.
      HUC2 (Integer) = 13
      HUC4 (Integer) = 1301
      HUC6 (Integer) = 130100
      REG (Integer) = 13
      SUB (Integer) = 1301
      ACC (Integer) = 130100
      CAT (Integer) = 13010003
      CAT_NUM (String) = 13010003
      Shape_Leng (Real) =  382736.41359499999
      Shape_Area (Real) = 4133451308.51999998093
      POLYGON ((-828905.55460000038147 49985.936499999836087,-828498.212600000202656 49096.979100000113249,
      [...]




Selecting and transforming features
-----------------------------------

You can do this programmatically in Python, but for simplicity, we will
use the shell today in the session. The notes detail how you can do this
in Python, and **you are encouraged to read about this and try it out**

Briefly, the process we'll follow will be:

1. Select the feature of interest (our basin of interest)
2. Re-project the data to the MODIS sinusoida projection
3. Build a mask using the MODIS LAI/fAPAR dataset as a reference

Let's say we want to select a feature identified by the HUC code (see
output from ``ogrinfo``) 13010001 (Rio Grande Headwaters. Colorado). We
can use the ``ogr2ogr`` tool to extract this feature, and reproject.

In GDAL/OGR (and in many other places), projections are defined by WKT
(Well-known text) or Proj4. We can go to
`spatialreference.org <http://spatialreference.org>`_ and have a look
for WKT/Proj4 string that GDAL/OGR need for the projection. In our case,
we shall be using the MODIS projection, with a proj4 string given by

::

    "+proj=sinu +R=6371007.181 +nadgrids=@null +wktext"

``ogr2ogr`` requires two options:

1. An option to select features where the field ``HUC`` is 13010001. For
   this we'll use the ``-where`` option.
2. A target (or output) projection definition. This is achieved with the
   ``-t_srs`` option

We also need: an output directory (``HUC_Polygon_MODIS``, say), and the
input shapefile and the layer name (shapefile name minus ``.shp``
extension). We build the command line as follows. note that the order of
the output files/layers **IS** important!

::

    $ ogr2ogr \
              -where "HUC=13010001"\ # Select features where HUC = 13010001
               -t_srs "+proj=sinu +R=6371007.181 +nadgrids=@null +wktext" \ # The output projection
               HUC_Polygons_MODIS \ # The output directory/file
               Hydrologic_Units/HUC_Polygons.shp \ # The input shapefile
               HUC_Polygons # The input shapefile's layer

Now test the output in ``HUC_Polygons_MODIS/HUC_Polygons.shp`` with
``ogrinfo`` again:

::

    $ ogrinfo -al -so HUC_Polygons_MODIS/HUC_Polygons.shp # Note the extra options!
    INFO: Open of `/tmp/stuffo/HUC_Polygons.shp'
      using driver `ESRI Shapefile' successful.

    Layer name: HUC_Polygons
    Geometry: Polygon
    Feature Count: 1
    Extent: (-9464744.171953, 4160060.958514) - (-9351954.997604, 4221926.101067)
    Layer SRS WKT:
    PROJCS["Sinusoidal",
        GEOGCS["GCS_unnamed ellipse",
            DATUM["unknown",
                SPHEROID["Unknown",6371007.181,0]],
        PRIMEM["Greenwich",0],
            UNIT["Degree",0.017453292519943295]],
        PROJECTION["Sinusoidal"],
        PARAMETER["longitude_of_center",0],
        PARAMETER["false_easting",0],
        PARAMETER["false_northing",0],
        UNIT["Meter",1]]
    HUC: Integer (9.0)
    REG_NAME: String (50.0)
    SUB_NAME: String (51.0)
    ACC_NAME: String (36.0)
    CAT_NAME: String (60.0)
    HUC2: Integer (4.0)
    HUC4: Integer (4.0)
    HUC6: Integer (9.0)
    REG: Integer (4.0)
    SUB: Integer (4.0)
    ACC: Integer (9.0)
    CAT: Integer (9.0)
    CAT_NUM: String (8.0)
    Shape_Leng: Real (19.11)
    Shape_Area: Real (19.11)

Compare the projection reported now by ``ogrinfo`` with that reported
earlier by ``gdalinfo``. Also see how the reported extenst for both
datasets relate.

Create a KML and upload it to Google Maps...
''''''''''''''''''''''''''''''''''''''''''''

If you specify

-  KML as your output format
-  EPSG:4326 `latitude/longitude reference
   system <http://spatialreference.org/ref/epsg/4326/>`_

you can create a KML file suitable for viewing in Google Earth/Maps

::

    ogr2ogr -f "KML" \ # Output set to KML format
             -where "HUC=13010001" # Select feature
             -t_srs "EPSG:4326"  \ # Output projection
             Hydrologic_Units_MODIS.kml \ # Output filename
             Hydrologic_Units/HUC_Polygons.shp \ # As above
             HUC_Polygons # As above


Creating the mask
`````````````````

We shall use ``gdal_rasterize`` to create the mask. We'll create a
GeoTIFF file. What we need

-  The target projection
-  The output format
-  The extent of the output file
-  The number of rows & columns in the output file
-  The datatype

We can gleam this information from the MODIS HDF file using ``gdalinfo``
and the commentws above. This is the command to use:

::

    gdal_rasterize -burn 1 \
        -of GTiff \
        -a_srs "+proj=sinu +R=6371007.181 +nadgrids=@null +wktext" \
        -te -10007554.677 3335851.559 -8895604.157 4447802.079 \
        -ts 1200 1200 \
        -ot Byte \
        Hydrologic_Units_MODIS/HUC_Polygons.shp \
        HUC_mask.tif

Check that ``HUC_mask.tif`` is indeed GDAL-readable by using
``gdalinfo`` as before.

Using the mask
==============

Let's read the mask the some LAI data...

In[30]:

.. code:: python

    from osgeo import gdal
    import numpy as np
    import matplotlib.pyplot as plt
    
    g = gdal.Open( 'HDF4_EOS:EOS_GRID:"MCD15A2.A2011193.h09v05.005.2011203175347.hdf":MOD_Grid_MOD15A2:Lai_1km')
    lai = g.ReadAsArray()*0.1
    
    g = gdal.Open ( "HUC_mask.tif" )
    mask = g.ReadAsArray()
    
    plt.imshow ( mask, interpolation='nearest', cmap=plt.cm.gray )


Out[30]:

.. parsed-literal::

    <matplotlib.image.AxesImage at 0xae0042c>

.. image:: FTP_session_files/FTP_session_fig_04.png


In[38]:

.. code:: python

    # We can use the mask to select MODIS data from the raster
    lai_m = np.where ( mask==1, lai, 0 )
    plt.imshow ( lai_m, interpolation='nearest', cmap=plt.cm.spectral )
    plt.colorbar()
    plt.figure()
    # Why does it go up to 24?

Out[38]:

.. parsed-literal::

    <matplotlib.figure.Figure at 0xb728ccc>

.. image:: FTP_session_files/FTP_session_fig_05.png

In[39]:

.. code:: python

    # The mean value of LAI within the catchment...
    mean_lai = lai_m[lai_m > 0].mean()
    std_lai = lai_m[lai_m > 0].std()
    print mean_lai, std_lai

.. parsed-literal::

    1.33370674633 1.90879912294


