c-image-scale
=============
### Reference
- https://github.com/ainouna/neutrino2/search?q=scaleImage
  - ```c
    /*
    int p_w = 0;
    int p_h = 0;

    ::scaleImage(cover, &p_w, &p_h);
    */

    //
    void scaleImage(const std::string &tname, int *p_w, int *p_h)
    {
      int nbpp = 0;

      if(!access(tname.c_str(), F_OK) )
      {
        CFrameBuffer::getInstance()->getSize(tname, p_w, p_h, &nbpp);

        // scale
        if(*p_w <= PIC_W && *p_h <= PIC_H)
        {
          // do not thing
        }
        else
        {
          float aspect = (float)(*p_w) / (float)(*p_h);

          if (((float)(*p_w) / (float)PIC_W) > ((float)(*p_h) / (float)PIC_H)) 
          {
            *p_w = PIC_W;
            *p_h = (int)(PIC_W / aspect);
          }
          else
          {
            *p_h = PIC_H;
            *p_w = (int)(PIC_H * aspect);
          }
        }
      }
      else
      {
        *p_w = 0;
        *p_h = 0;
      }
    }
    ```
