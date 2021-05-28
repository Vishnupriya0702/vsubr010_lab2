# vsubr010_lab2

package edu.ucr.cs.cs167.vsubr010;

import java.lang.*;
import java.io.IOException;
import org.apache.hadoop.conf.Configuration;
import org.apache.hadoop.fs.Path;
import org.apache.hadoop.fs.FileSystem;
import org.apache.hadoop.fs.FSDataInputStream;
import org.apache.hadoop.fs.FSDataOutputStream;
/*import org.apache.hadoop.fs.IOUtils;*/


public class App
{
    public static void main(String[] args) throws Exception{

    /*check the total number of arguments*/
      if(args.length!=2)
      {
          System.err.println("the number of arugments are incorrect");
      }
     /*storing the filepath*/
       Path infile = new Path(args[0]);
        Path outfile =new Path(args[1]);
        /*Path appendfile = new Path(args[2]);*/

      Configuration conf = new Configuration();
      FileSystem fs = FileSystem.get(conf);

     /* check whether the Inputfile & Outputfile exists or not*/
       if(!fs.exists(infile)) {
            System.out.println("Inputfile not found");
        }

        if(fs.exists(outfile)) {
            System.out.println("Outputfile already exists");
        }
        /*open and creating the Infile & outfile*/
       FSDataInputStream in = fs.open(infile);
        FSDataOutputStream out =fs.create(outfile);
        /*/*Appends the file
        FSDataOutputStream append =fs.append(appendfile );
        */
        /*truncate the file*/
        long newlength = 100;
        FSDataOutputStream truncate =fs.truncate(filename, 150 );
        /*DeleteOnExit*/
        FSDataOutputStream DeleteExit = fs.deleteOnExit(filename);
        /*To check whether it is a file or Not*/
        FSDataOutputStream DeleteExit = fs.getFileStatus(Path);
        /*To know the locations of teh Block*/
        FSDataOutputStream ListLocatedStatus = fs.listLocatedStatus(Path);
        /*How we use in the Unix, we can copyfilefrom local, movefile from local*/
        using copyFromLocal , moveFromLocal
        /*Blocklocations*/
        Blocklocations using getdefaultBlockSize, getDefaultReplication.
        /*checksum for dataload*/
        /*When a file is copied from one location to another location, we are in need of this checksum.*/
         /*set storagepolicy for a given directory*/
       /* Path for storage policy of the datachange*/


        /*write the data and calculate the time*/
        int len;
        byte[] b =new byte[1024];

        long  startTime =System.nanoTime();
        while((len = in.read(b))>0)

        {
          out.write(b,0,len);
        }

       in.close();
        out.close();

        long estimatedTime = System.nanoTime() - startTime;
        int totalbytes = out.size();

        System.out.println("Copied" + "\t" + totalbytes + "\t" + "bytes from" + "\t" +infile + "\t" +"to" + "\t" +outfile + "\t" +"in" + "\t" + estimatedTime + "\t"+  "seconds");
           }
}
