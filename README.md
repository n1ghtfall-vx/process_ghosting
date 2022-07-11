# process_ghosting
C++ demo code for the Process Ghosting code injection technique, simplified from original demo by hasherezade. [Note: Currently under development, this notice will be removed once the demo code is complete.]

[Write explanation of what Process Ghosting is]

The attack flow of this process injection technique is as follows:
1. Create a file
2. Put the file into a delete-pending state using NtSetInformationFile(FileDispositionInformation).
3. Write the payload executable to the file. The content isn’t persisted because the file is already delete-pending. The delete-pending state also blocks external file-open attempts.
4. Create an image section for the file.
5. Close the delete-pending handle, deleting the file.
6. Create a process using the image section.
7. Assign process arguments and environment variables.
8. Create a thread to execute in the process.

References:

hasherezade's process ghosting C++ demo code: https://github.com/hasherezade/process_ghosting 

Simplified process ghosting C++ demo code, but it writes to dummy file before making it delete-pending, my code is intended to be simplified demo code that fixes this flaw in implementation: https://github.com/aaaddress1/PR0CESS/tree/main/miniGhosting 

Blog post by Gabriel Landau at Elastic describing the Process Ghosting technique for the first time: https://www.elastic.co/blog/process-ghosting-a-new-executable-image-tampering-attack 
