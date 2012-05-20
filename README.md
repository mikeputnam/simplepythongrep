
A simple python grep. Useful when Windows search isn't good enough.

--

    import os
    import sys

    if sys.argv[1] == '':
        print "Usage: python grep.py searchterm pathtosearch"
        sys.exit()
    searchterm = sys.argv[1] 
    pathtosearch = sys.argv[2]
    os.chdir(pathtosearch)
    for root,dir,files in os.walk(pathtosearch):
        for fi in files:
            path = os.path.join(root,fi)
            for num,line in enumerate(open(path)):
                if searchterm.upper() in line.upper():
                    print "[%s] found in [%s] , line number [%d]" %(searchterm.upper(),path,num+1)
     
