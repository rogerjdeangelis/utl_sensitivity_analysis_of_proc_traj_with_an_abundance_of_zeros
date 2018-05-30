# -utl_sensitivity_analysis_of_proc_traj_with_an_abundance_of_zeros-
Sensitivity_analysis_of_proc_traj_with_an_abundance_of_zeros.  Keywords: sas sql join merge big data analytics macros oracle teradata mysql sas communities stackoverflow statistics artificial inteligence AI Python R Java Javascript WPS Matlab SPSS Scala Perl C C# Excel MS Access JSON graphics maps NLP natural language processing machine learning igraph DOSUBL DOW loop stackoverflow SAS community.

     Sensitivity analysis of proc traj with an abundance of zeros

     *******************************************************************************************************************;
     *                                                                                                                 *;
     *  PROJECT TOKEN = taj                                                                                            *;
     *                                                                                                                 *;
     *; %let purpose=Sensitivity SAS Proc Traj Trajectory of Food and Leisure Costs;                                   *;
     *                                                                                                                 *;
     *                                                                                                                 *;
     *  Windows Local workstation SAS 9.4M2(64bit) Win 7(64bit) Dell T7400 64gb ram, dual SSD raid 0 arrays, 8 core    *;
     *                                                                                                                 *;
     *; %let pgm=taj_200pay;     * program name                                                                        *;
     *                                                                                                                 *;
     *; %let pgmloc = c:/utl;    * program location;                                                                   *;
     *; %let pgmver = d:/ver;    * program versioning;                                                                 *;
     *; libname taj "d:/taj";    * data input and output location                                                      *;
     *                                                                                                                 *;
     *  INPUTS                                                                                                         *;
     *  =======                                                                                                        *;
     *                                                                                                                 *;
     *; Simulation data generated within program                                                                       *;
     *                                                                                                                 *;
     *  Used with slides                                                                                               *;
     *                                                                                                                 *;
     *; %let z=%str(                    );                                                                             *;
     *; %let b=%str(font_weight=bold);                                                                                 *;
     *; %let c=%str(font_face="Courier New");                                                                          *;
     *; %let f=%str(font_face="Arial");                                                                                *;
     *; %let w=%str(cellwidth=100pct);                                                                                 *;
     *; %let t=^S={font_size=20pt just=l cellwidth=100pct};                                                            *;
     *; %let u=^S={font_size=16pt font_face="Courier New" just=l cellwidth=100pct font_weight=bold};                   *;
     *; %let v=^S={font_size=14pt font_face="Courier New" just=l cellwidth=100pct font_weight=bold};                   *;
     *; %let x=^S={font_size=11pt font_face="Courier New" just=l cellwidth=100pct font_weight=bold};                   *;
     *                                                                                                                 *;
     *    Use   For in slides                                                                                          *;
     *    ===   =============                                                                                          *;
     *      |   ,                                                                                                      *;
     *                                                                                                                 *;
     *      ~   ;                                                                                                      *;
     *                                                                                                                 *;
     *      #   %                                                                                                      *;
     *                                                                                                                 *;
     *      @   &                                                                                                      *;
     *                                                                                                                 *;
     *  OUTPUTS                                                                                                        *;
     *  =======                                                                                                        *;
     *    Individual PDF to be                                                                                         *;
     *    You can esily combine the individiual PDFs into word or use Adobe or fre tools to combine all the pdfs.     ;*;
     *;                                                                                                               ;*;
     *                                                                                                                 *;
     *******************************************************************************************************************;

     *
      _ __ ___   __ _  ___ _ __ ___  ___
     | '_ ` _ \ / _` |/ __| '__/ _ \/ __|
     | | | | | | (_| | (__| | | (_) \__ \
     |_| |_| |_|\__,_|\___|_|  \___/|___/
     ;
     %Macro utl_pdflan100
         (
           style=utl_pdflan100
           ,frame=void
           ,TitleFont=16pt
           ,docfont=15pt
           ,fixedfont=15pt
           ,rules=none
           ,bottommargin=.25in
           ,topmargin= .25in
           ,rightmargin=.25in
           ,leftmargin=.25in
           ,cellheight=13pt
           ,cellpadding = .2pt
           ,cellspacing = .2pt
           ,borderwidth = .2pt
         ) /  Des="SAS PDF Template for PDF";

     ods path work.templat(update) sasuser.templat(update) sashelp.tmplmst(read);

     proc template ;
     source styles.printer;
     run;quit;

     Proc Template;

        define style &Style;
        parent=styles.rtf;

             class body from Document /

                    protectspecialchars=off
                    asis=on
                    bottommargin=&bottommargin
                    topmargin   =&topmargin
                    rightmargin =&rightmargin
                    leftmargin  =&leftmargin
                    ;

             class color_list /
                   'link' = blue
                    'bgH'  = _undef_
                    'fg'  = black
                    'bg'   = _undef_;

             class fonts /
                    'TitleFont2'           = ("Arial, Helvetica, Helv",&titlefont,Bold)
                    'TitleFont'            = ("Arial, Helvetica, Helv",&titlefont,Bold)

                    'HeadingFont'          = ("Arial, Helvetica, Helv",&titlefont)
                    'HeadingEmphasisFont'  = ("Arial, Helvetica, Helv",&titlefont,Italic)

                    'StrongFont'           = ("Arial, Helvetica, Helv",&titlefont,Bold)
                    'EmphasisFont'         = ("Arial, Helvetica, Helv",&titlefont,Italic)

                    'FixedFont'            = ("Courier New, Courier",&fixedfont)
                    'FixedEmphasisFont'    = ("Courier New, Courier",&fixedfont,Italic)
                    'FixedStrongFont'      = ("Courier New, Courier",&fixedfont,Bold)
                    'FixedHeadingFont'     = ("Courier New, Courier",&fixedfont,Bold)
                    'BatchFixedFont'       = ("Courier New, Courier",&fixedfont)

                    'docFont'              = ("Arial, Helvetica, Helv",&docfont)

                    'FootFont'             = ("Arial, Helvetica, Helv", 9pt)
                    'StrongFootFont'       = ("Arial, Helvetica, Helv",8pt,Bold)
                    'EmphasisFootFont'     = ("Arial, Helvetica, Helv",8pt,Italic)
                    'FixedFootFont'        = ("Courier New, Courier",8pt)
                    'FixedEmphasisFootFont'= ("Courier New, Courier",8pt,Italic)
                    'FixedStrongFootFont'  = ("Courier New, Courier",7pt,Bold);

             class GraphFonts /
                    'GraphDataFont'        = ("Arial, Helvetica, Helv",&fixedfont)
                    'GraphValueFont'       = ("Arial, Helvetica, Helv",&fixedfont)
                    'GraphLabelFont'       = ("Arial, Helvetica, Helv",&fixedfont,Bold)
                    'GraphFootnoteFont'    = ("Arial, Helvetica, Helv",8pt)
                    'GraphTitleFont'       = ("Arial, Helvetica, Helv",&titlefont,Bold)
                    'GraphAnnoFont'        = ("Arial, Helvetica, Helv",&fixedfont)
                    'GraphUnicodeFont'     = ("Arial, Helvetica, Helv",&fixedfont)
                    'GraphLabel2Font'      = ("Arial, Helvetica, Helv",&fixedfont)
                    'GraphTitle1Font'      = ("Arial, Helvetica, Helv",&fixedfont)
                    'NodeDetailFont'       = ("Arial, Helvetica, Helv",&fixedfont)
                    'NodeInputLabelFont'   = ("Arial, Helvetica, Helv",&fixedfont)
                    'NodeLabelFont'        = ("Arial, Helvetica, Helv",&fixedfont)
                    'NodeTitleFont'        = ("Arial, Helvetica, Helv",&fixedfont);


             style Graph from Output/
                     outputwidth = 100% ;

             style table from table /
                     outputwidth=100%
                     protectspecialchars=off
                     asis=on
                     background = colors('tablebg')
                     frame=&frame
                     rules=&rules
                     cellheight  = &cellheight
                     cellpadding = &cellpadding
                     cellspacing = &cellspacing
                     bordercolor = colors('tableborder')
                     borderwidth = &borderwidth;

              class Footer from HeadersAndFooters

                     / font = fonts('FootFont')  just=left asis=on protectspecialchars=off ;

                     class FooterFixed from Footer
                     / font = fonts('FixedFootFont')  just=left asis=on protectspecialchars=off;

                     class FooterEmpty from Footer
                     / font = fonts('FootFont')  just=left asis=on protectspecialchars=off;

                     class FooterEmphasis from Footer
                     / font = fonts('EmphasisFootFont')  just=left asis=on protectspecialchars=off;

                     class FooterEmphasisFixed from FooterEmphasis
                     / font = fonts('FixedEmphasisFootFont')  just=left asis=on protectspecialchars=off;

                     class FooterStrong from Footer
                     / font = fonts('StrongFootFont')  just=left asis=on protectspecialchars=off;

                     class FooterStrongFixed from FooterStrong
                     / font = fonts('FixedStrongFootFont')  just=left asis=on protectspecialchars=off;

                     class RowFooter from Footer
                     / font = fonts('FootFont')  asis=on protectspecialchars=off just=left;

                     class RowFooterFixed from RowFooter
                     / font = fonts('FixedFootFont')  just=left asis=on protectspecialchars=off;

                     class RowFooterEmpty from RowFooter
                     / font = fonts('FootFont')  just=left asis=on protectspecialchars=off;

                     class RowFooterEmphasis from RowFooter
                     / font = fonts('EmphasisFootFont')  just=left asis=on protectspecialchars=off;

                     class RowFooterEmphasisFixed from RowFooterEmphasis
                     / font = fonts('FixedEmphasisFootFont')  just=left asis=on protectspecialchars=off;

                     class RowFooterStrong from RowFooter
                     / font = fonts('StrongFootFont')  just=left asis=on protectspecialchars=off;

                     class RowFooterStrongFixed from RowFooterStrong
                     / font = fonts('FixedStrongFootFont')  just=left asis=on protectspecialchars=off;

                     class SystemFooter from TitlesAndFooters / asis=on
                             protectspecialchars=off just=left;
         end;
     run;
     quit;

     %Mend utl_pdflan100;

     %utl_pdflan100;


     %Macro Tut_Sly
     (
      stop=52,
      L1=' ',  L2=' ', L3=' ', L4=' ', L5=' ', L6=' ', L7=' ', L8=' ', L9=' ',
      L10=' ', L11=' ',
      L12=' ', L13=' ', L14=' ', L15=' ', L16=' ', L17=' ', L18=' ', L19=' ',
      L20=' ', L21=' ',
      L22=' ', L23=' ', L24=' ', L25=' ', L26=' ', L27=' ', L28=' ', L29=' ', L30=' ', L31=' ', L32=' ',
      L33=' ', L34=' ', L35=' ', L36=' ', L37=' ', L38=' ', L39=' ', L40=' ', L41=' ', L42=' ', L43=' ',
      L44=' ', L45=' ', L46=' ', L47=' ', L48=' ', L49=' ', L50=' ', L51=' ', L52=' '
      )/ des="SAS Slides all argument values need to be single quoted";

     /* creating slides for a presentation */
     /* up to 32 lines */
     /* backtic ` is converted to a single quote  */
     /* | is converted to a , */

     Data _OneLyn1st(rename=t=title);

     Length t $255;
      t=resolve(translate(&L1,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
      t=resolve(translate(&L2,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
      t=resolve(translate(&L3,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
      t=resolve(translate(&L4,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
      t=resolve(translate(&L5,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
      t=resolve(translate(&L6,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
      t=resolve(translate(&L7,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
      t=resolve(translate(&L8,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
      t=resolve(translate(&L9,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L10,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L11,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L12,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L13,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L14,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L15,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L16,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L17,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L18,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L19,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L20,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L21,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L22,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L23,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L24,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L25,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L26,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L27,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L28,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L29,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L30,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L31,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L32,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L33,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L34,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L35,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L36,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L37,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L38,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L39,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L41,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L42,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L43,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L44,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L45,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L46,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L47,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L48,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L50,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L51,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;
     t=resolve(translate(&L52,"'","`"));t=translate(t,",","|");t=translate(t,";","~");t=translate(t,'%',"#");t=translate(t,'&',"@");Output;

     run;quit;

     /*  %let l7='^S={font_size=25pt just=c cellwidth=100pct}Premium Dollars';  */

     options label;
     %if &stop=7 %then %do;
        data _null_;
           tyt=scan(&l7,2,'}');
           call symputx("tyt",tyt);
        run;
        ods pdf bookmarkgen=on bookmarklist=show;
        ods proclabel="&tyt";run;quit;
     %end;
     %else %do;
        ods proclabel="Title";run;quit;
     %end;


     data _onelyn;
       set _onelyn1st(obs=%eval(&stop + 1));
       if not (left(title) =:  '^') then do;
          pre=upcase(scan(left(title),1,' '));
          idx=index(left(title),' ');
          title=substr(title,idx+1);
       end;
       put title;
     run;

     * display the slide ;
     title;
     footnote;

     proc report data=_OneLyn nowd  style=utl_ymrlan100;
     col title;
     define title / display ' ';
     run;
     quit;

     %Mend Tut_Sly;

     %macro utlfkil
         (
         utlfkil
         ) / des="delete an external file";


         /*-------------------------------------------------*\
         |                                                   |
         |  Delete an external file                          |
         |   From SAS macro guide                                                |
         |  Sample invocations                               |
         |                                                   |
         |  WIN95                                            |
         |  %utlfkil(c:\dat\utlfkil.sas);                    |
         |                                                   |
         |                                                   |
         |  Solaris 2.5                                      |
         |  %utlfkil(/home/deangel/delete.dat);              |
         |                                                   |
         |                                                   |
         |  Roger DeAngelis                                  |
         |                                                   |
         \*-------------------------------------------------*/

         %local urc;

         /*-------------------------------------------------*\
         | Open file   -- assign file reference              |
         \*-------------------------------------------------*/

         %let urc = %sysfunc(filename(fname,%quote(&utlfkil)));

         /*-------------------------------------------------*\
         | Delete file if it exits                           |
         \*-------------------------------------------------*/

         %if &urc = 0 and %sysfunc(fexist(&fname)) %then
             %let urc = %sysfunc(fdelete(&fname));

         /*-------------------------------------------------*\
         | Close file  -- deassign file reference            |
         \*-------------------------------------------------*/

         %let urc = %sysfunc(filename(fname,''));

       run;

     %mend utlfkil;


     %macro utl_boxpdf2ppt(inp=&outpdf001,out=&outppt001)/des="www.boxoft.con pdf to ppt";
       data _null_;
         cmd=catt("&pdf2ppt",' "',"&inp", '"',' "',"&out",'"');
         put cmd;
         call system(cmd);
       run;
     %mend utl_boxpdf2ppt;

     %MACRO greenbar ;
        DEFINE _row / order COMPUTED NOPRINT ;
        COMPUTE _row;
           nobs+1;
           _row = nobs;
           IF (MOD( _row,2 )=0) THEN
              CALL DEFINE( _ROW_,'STYLE',"STYLE={BACKGROUND=graydd}" );
        ENDCOMP;
     %MEND greenbar;

     %macro pdfbeg(rules=all,frame=box,pdf=);
         %*utlnopts;
         title;
         footnote;
         options orientation=landscape validvarname=v7;
         ods listing close;
         ods pdf close;
         ods path work.templat(update) sasuser.templat(update) sashelp.tmplmst(read);
         %utlfkil(&pdf);
         ods noptitle;
         ods escapechar='^';
         ods listing close;
         ods graphics on / width=10in  height=7in ;
         ods pdf file="&pdf" style=utl_pdflan100 notoc ;
         run;quit;
     %mend pdfbeg;

     %macro codebegin;
       options orientation=landscape lrecl=384;
       data _null_;
       length lyn $384;
        input;
        lyn=strip(_infile_);
        file print;
        put lyn "^{newline}" @;
        *call execute(_infile_);
     %mend codebegin;


     %macro pdfend;
        ods graphics off;
        ods pdf close;
        ods listing;
        options ls=171 ps=66;
        %*utlopts;
        run;quit;
     %mend pdfend;

     *_                _
     | |__   ___  __ _(_)_ __
     | '_ \ / _ \/ _` | | '_ \
     | |_) |  __/ (_| | | | | |
     |_.__/ \___|\__, |_|_| |_|
                 |___/
     ;

     * the input looks like this;


     /*
     TAJ.TAJ_SIMULATE total obs=500 12 Months
                                                                  PAY
      ID  AGE  SMOKER  CARBS  GENDER  T1  T2  T3 ..T12     _1   _2   _3 .. _12
       1   34     1     -10      0     1   2   3 .. 12    783  808  796 .. 795
       2   29     1     -11      0     1   2   3 .. 12    817  816  833 .. 747
       3   40     0      -9      0     1   2   3 .. 12    820  813  793 .. 837
       4   38     0     -11      0     1   2   3 .. 12    786  738  706 .. 796
       5   27     1     -12      1     1   2   3 .. 12    709  796  819 .. 817
     ...
     500   37     1     -9       0     1   2   3 .. 12    719  795  829 .. 818
     */


     data taj.taj_simulatex;
      retain id 0 ;
      array und[12] _1-_12;
      array ts[12] t1-t12 (1,2,3,4,5,6,7,8,9,10,11,12);
      call streaminit(1234);
      do j=1 to 1500;
      do i=1 to 12;
            /* f(month)=76 + 2 * month +0.1 * month**2 + normal(0,15) */
            und[i]= abs(10 +  2*i    + .1*(i*i) + rand('normal',0,20)) +66;
            idx= int(12*rand('uniform')) +1;
            if rand('uniform') < .15 then und[idx]=.;
      end;
      fro=1;id=id+1;output;
      do i=1 to 12;
            /* f(month)=116 +4 * month +0.3 * month**2 + normal(0,20) */
            und[i]= abs(50 +  4*(i) + .3*(i*i)  + rand('normal',0,40))  +66;
            idx= int(12*rand('uniform')) +1;
            if rand('uniform') < .15 then und[idx]=.;
      end;
      fro=2;id=id+1;output;
      do i=1 to 12;
            /* f(month)=146 + 6 * month + 1.0 * month**2 + normal(0,15) */
            und[i]= abs(80 +  6*(i) +  (i*i)  + rand('normal',0,40))  +66;
            idx= int(12*rand('uniform')) +1;
            if rand('uniform') < .15 then und[idx]=.;
      end;
      fro=3;id=id+1;output;
      end;
      drop i j;
      run;quit;

     data taj.taj_simulate;
      retain id 0 ;
      array und[12] _1-_12;
      array ts[12] t1-t12 (1,2,3,4,5,6,7,8,9,10,11,12);
      call streaminit(1234);
      do j=1 to 1500;
      do i=1 to 12;
            und[i]= abs(10 +  2*i    + .1*(i*i) + rand('normal',0,20)) +66;
            idx= int(12*rand('uniform')) +1;
            if rand('uniform') < .15 then und[idx]=0;
      end;
      fro=1;id=id+1;output;
      do i=1 to 12;
            und[i]= abs(50 +  4*(i) + .3*(i*i)  + rand('normal',0,40))  +66;
            idx= int(12*rand('uniform')) +1;
            if rand('uniform') < .15 then und[idx]=0;
      end;
      fro=2;id=id+1;output;
      do i=1 to 12;
            und[i]= abs(80 +  6*(i) +  (i*i)  + rand('normal',0,40))  +66;
            idx= int(12*rand('uniform')) +1;
            if rand('uniform') < .15 then und[idx]=0;
      end;
      fro=3;id=id+1;output;
      end;
      drop i j;
      run;quit;
            /* f(month)= 76 + 2 * month +0.1 * month**2 + normal(0,15)   */
            /* f(month)=116 + 4 * month +0.3 * month**2 + normal(0,40)   */
            /* f(month)=146 + 6 * month +1.0 * month**2 + normal(0,45) */

     * lets normalize;

     proc transpose data=taj.taj_simulate out=&pgm._simNrm(rename=(_name_=mthc col1=pay));
     by id;
     var _1-_12;
     run;quit;

     data taj.taj_simNrm(label="Normalized version of original input dataset created by &pgmloc./&pgm..sas");
        set &pgm._simNrm;
        mth=input(substr(mthc,2),3.);
        drop mthc;
     run;quit;

     proc transpose data=taj.taj_simulatex out=&pgm._simNrmx(rename=(_name_=mthc col1=pay));
     by id;
     var _1-_12;
     run;quit;

     data taj.taj_simNrmx(label="Normalized version of original input dataset created by &pgmloc./&pgm..sas");
        set &pgm._simNrmx;
        mth=input(substr(mthc,2),3.);
        drop mthc;
     run;quit;

     *    _ _     _
      ___| (_) __| | ___  ___
     / __| | |/ _` |/ _ \/ __|
     \__ \ | | (_| |  __/\__ \
     |___/_|_|\__,_|\___||___/
     ;

     %pdfbeg(pdf=d:/taj/pdf/&pgm._tbl0000.pdf);
     %Tut_Sly
        (
         stop=14
         ,L6 ='^S={font_size=25pt just=c &w}Sensitivity Analysis on Trajectory with an Abundance of Zeros'
         ,L8 ='^S={font_size=25pt just=c &w}Comparing Missings with Weighted Payments and zero payments'
         ,L9 ='^S={font_size=25pt just=c &w}Problematic Residuals and Inferential Statistics with Zeros'
         ,L11 ='^S={font_size=25pt just=c &w}Monthly Food and Leisure Costs'
         ,L12='^S={font_size=25pt just=c &w}January through December Fake Data'
         ,L13 ='^S={font_size=25pt just=c &w}SAS Proc Traj by Dr Jones'
         ,L14 ='^S={font_size=25pt just=c &w}https://www.andrew.cmu.edu/user/bjones/'
        );
     %pdfend;

     %pdfbeg(pdf=d:/taj/pdf/&pgm._tbl0050.pdf);
     %Tut_Sly
        (
         stop=15
         ,L7 ='^S={font_size=30pt just=c &w}Trajectories are very robust with respect to zeros.'
         ,L9 ='^S={font_size=25pt just=c &w}However statisticians should be cautious about inference.'
         ,L11='^S={font_size=25pt just=c &w}With zeros standard errors and confidence intervals are very wide. '
         ,L13 ='^S={font_size=25pt just=c &w}Individual Residuals are not symetric or normal'
         ,L14 ='^S={font_size=25pt just=c &w}Substituting missings for zeros and using weighted payments helps?'
         ,L15 ='^S={font_size=25pt just=c &w}For large sample sizes distributions around means is better.'
        );
     %pdfend;

     %pdfbeg(pdf=d:/taj/pdf/&pgm._tbl1050.pdf);
     %Tut_Sly
        (
         stop=15
         ,L7 ='^S={font_size=30pt just=c &w}Sensitivity Analysis: Parameters and Standard Errors'
         ,L9 ='^S={font_size=25pt just=c &w}Generate a three trajectory dataset with known trends'
         ,L11='^S={font_size=25pt just=c &w}Three with 15# zeros and second set with 15# missing'
         ,L13 ='^S={font_size=25pt just=c &w}f(month)= 76 + 2 * month +0.1 * month**2 + normal(0,15)'
         ,L14 ='^S={font_size=25pt just=c &w}f(month)=116 + 4 * month +0.3 * month**2 + normal(0,40)'
         ,L15 ='^S={font_size=25pt just=c &w}f(month)=146 + 6 * month +1.0 * month**2 + normal(0,40)'
        );
     %pdfend;


     %pdfbeg(pdf=d:/taj/pdf/&pgm._tbl1200.pdf);
     proc sgplot data=taj.taj_simNrm;
     title "Slide 1200  Problematic Overall 12 Month Histogram of Payments" ;
     label pay="Payments Food and Leisure";
     histogram pay/binwidth=5;
     yaxis grid offsetmax=.05;
     xaxis grid;
     run;quit;
     %pdfend;

     %pdfbeg(pdf=d:/taj/pdf/&pgm._tbl1300.pdf);
     proc sgplot data=taj.taj_simNrmx;
     title "Slide 1300 Better Histogram Proc Traj ignores missing";
     label pay="Payments Food and Leisure";
     histogram pay/binwidth=5;
     yaxis grid offsetmax=.05;
     xaxis grid;
     run;quit;
     %pdfend;
     %utl_pdflan100;

    *
     * percent of total pay in the top 5% by month;
     * since we have exactly 500 in each month the top 10% will at 450 and above;
     proc sort data=taj.taj_simNrmx out=taj_simNrmSrtx;
      by mth pay;
     run;quit;

     data taj_simNrmSumx;
       retain cnt paySum payTot 0;
       set taj_simNrmSrtx(keep=mth pay);
       by mth;
       cnt=cnt+1;
       payTot=sum(payTot,pay);
       if cnt>950 then paySum=sum(paySum,pay);
       if last.mth then do;
          payPct=100*paySum/payTot;
          cnt5Pct=25;
          payPerResident=payTot/1000;
          output;
          cnt=0;
          paySum=0;
          payTot=0;
       end;
     run;quit;

     %utl_pdflan100(frame=box,rules=all);
     %pdfbeg(pdf=d:/taj/pdf/&pgm._tbl1500.pdf);
     ods escapechar='^';
     proc report data=taj_simNrmSumx missing nowd list split="#";
        cols ("Figure 1500 With Missings: Percent of Monthly Payments in the Top 5 Percent by Month^{newline}
        Same result using Zeros because we ignore the zeros but divide by sample size"
     mth ("All Data" cnt payTot) ( "Top 5%" cnt5pct paySum payPct PayPerResident)) _row;
     DEFINE  MTH     / display     center "Month" ;
     DEFINE  cnt     / display     center "Count" ;
     DEFINE  payTot  / display FORMAT= dollar12.   center "Total" ;
     DEFINE  cnt5pct / display                    center "Count" ;
     DEFINE  paySum  / display FORMAT= dollar9.   center "Dollars" ;
     DEFINE  payPct  / display FORMAT= 5.1        center "Percent of#Total" ;
     DEFINE  payPerResident  / display FORMAT= dollar9.  center "Payment#Per Resident" ;
     %greenbar;
     run;quit;
     %pdfend;
     %utl_pdflan100;
    */
        *                    _      _
         _ __ ___   ___   __| | ___| |
        | '_ ` _ \ / _ \ / _` |/ _ \ |
        | | | | | | (_) | (_| |  __/ |
        |_| |_| |_|\___/ \__,_|\___|_|
        ;

    title;
    footnote;
    %utl_pdflan100(fixedfont=11pt);
    %pdfbeg(pdf=d:/taj/pdf/&pgm._tbl1600.pdf);
    %codebegin;
    cards4;

    *;
    * PROC TRAJ MULTIPLE MODELS;
    *;

    %let cmpMdl=%sysfunc(compress(&mdl));

    %macro cmmi_mdlchk(mdl,x=);

    %let cmpMdl=%sysfunc(compress(&mdl));
    %pdfbeg(pdf=d:/taj/pdf/&pgm._tbl1510&x.pdf);
    proc traj data = taj.taj_simulate&x
           outplot =   taj.taj_mdlPlot12_&cmpMdl&x
           outest  =    taj.taj_mdlEst12_&cmpMdl&x
           outstat =   taj.taj_mdlStat12_&cmpMdl&x
               out = taj.taj_mdlDetail12_&cmpMdl&x ci95M;
      model order&cmpmdl;
      id id;
      var _1-_12 ;
      indep t1-t12;
      order &mdl;
      min 0;
      max 500;
      model cnorm;
    run;quit;
    %pdfend;

    %mend cmmi_mdlchk;

    %*cmmi_mdlchk(2 2 2);
    %*cmmi_mdlchk(2 2 2,x=X);
    ,
    ;;;;
    run;quit;
    %pdfend;

    */

    %macro cmmi_mdlchk(mdl,x=,sli=);

    /* %let x=X;   taj.taj_mdlplot12_222  */

    %utlfkil(d:/txt/&pgm._&sli..txt);

    %let cmpMdl=%sysfunc(compress(&mdl));
    proc printto print="d:/txt/&pgm._&sli..txt";
    proc traj data = taj.taj_simulate&x
           outplot =   taj.taj_mdlPlot12_&cmpMdl&x
           outest  =    taj.taj_mdlEst12_&cmpMdl&x
           outstat =   taj.taj_mdlStat12_&cmpMdl&x
               out = taj.taj_mdlDetail12_&cmpMdl&x ci95M;
      model order&cmpmdl;
      id id;
      var _1-_12 ;
      indep t1-t12;
      order &mdl;
      min 0;
      max 500;
      model cnorm;
    run;quit;
    proc printto;


    %utl_pdflan100(fixedfont=11pt);
    %pdfbeg(pdf=d:/taj/pdf/&pgm._tbl&sli..pdf);
    options ls=96;
    data load;
      label lyn=' ';
      infile "d:/txt/&pgm._&sli..txt" missover;
      *infile "d:/txt/taj_200pay_1700.txt";
      input;
      if _infile_ ne ' ';
      lyn=' '!!put(_infile_,$char96.);
      put lyn;
      output;
    run;quit;

    title;footnote;
    proc report data=load missing nowd;
    format lyn $char96.;
    col ("%sysfunc(ifc(X=&x,Model (222) Three Quadratics With Missings,Model (222) Three Quadratics With Zeros))" lyn);
    define lyn / display style={font_face=Courier font_size=11pt};
    run;quit;

    %pdfend;

    %mend cmmi_mdlchk;

    %cmmi_mdlchk(2 2 2,sli=1700);
    %cmmi_mdlchk(2 2 2,x=X,sli=1800);


    options validvarname=v7;
    data &pgm._parms;
     length Parameter $10.;
     input Parameter Theory  Missing  Zeros;
    cards4;
    Intercept 76 83.74 67.52
    Linear 2.0 0.80 1.78
    Quadratic 0.1 0.15 0.19
    . . . .
    Intercept 116 121.20 24.08
    Linear 4.0 2.83 5.26
    Quadratic 0.3 0.36 1.21
    . . . .
    Intercept 146 146.09 99.73
    Linear 6.0 5.93 4.42
    Quadratic 1.0 1.01 0.39
    . . . .
    ;;;;
    run;quit;

    options missing=" ";
    %utl_pdflan100(frame=box,rules=all);
    %pdfbeg(pdf=d:/taj/pdf/&pgm._tbl1900.pdf);
    ods escapechar='^';
    proc report data=&pgm._parms nowd missing style(column)={just=center};
    cols ( "Figure 1900 Sensitivity Analysis on Model Parameters^{newline}Using 15% Zero or Missing" _all_) _row;
    define Parameter / display  style(column)={just=l};
    %greenbar;
    run;quit;
    %pdfend;


    data &pgm._stdErr;
     length Standard_Error $10.;
     input Standard_Error Missing Zeros;
    cards4;
    Intercept 0.95 1.53
    Linear 0.33 0.54
    Quadratic 0.02 0.04
    . . . .
    Intercept 0.96 1.58
    Linear 0.33 0.56
    Quadratic 0.02 0.04
    . . . .
    Intercept 0.95 1.61
    Linear 0.33 0.57
    Quadratic 0.02 0.04
    .  . . .
    ;;;;
    run;quit;

    options missing=" ";
    %utl_pdflan100(frame=box,rules=all);
    %pdfbeg(pdf=d:/taj/pdf/&pgm._tbl2000.pdf);
    ods escapechar='^';
    proc report data=&pgm._stdErr nowd missing style(column)={just=center};
    cols ( "Figure 2000 Sensitivity Analysis on Model Standard Errors^{newline}Using 15% Zero or Missing" _all_) _row;
    define standard_Error / display "Standard Error" style(column)={just=l};
    %greenbar;
    run;quit;
    %pdfend;


    *              _     _             _
     _ __ ___  ___(_) __| |_   _  __ _| |___
    | '__/ _ \/ __| |/ _` | | | |/ _` | / __|
    | | |  __/\__ \ | (_| | |_| | (_| | \__ \
    |_|  \___||___/_|\__,_|\__,_|\__,_|_|___/
    ;

    /* inputs
    taj.taj_mdlDetail12_211
    taj.taj_mdlPlot12_211;
    */

    proc sort data=taj.taj_mdlDetail12_222x(where=(uniform(1234)<.05)) out=&pgm._detSrt noequals;
      by group id;
    run;quit;

    proc transpose data=&pgm._detSrt out=&pgm._detXpo;
      by group id;
      var _1-_12;
    run;quit;

    proc transpose data=taj.taj_mdlPlot12_222 out=&pgm._pltXpo;
      by t;
      var pred:;
    run;quit;

    proc sql;
      create
        table &pgm._res as
      select
        l.group
       ,r.t + normal(1234)/8 as t
       ,l.col1 as raw
       ,r.col1 as est
       ,r.col1 - l.col1 as resid
      from
        &pgm._detXpo as l left join &pgm._pltXpo as r
      on
       input(substr(l._name_,2),3.) = r.t and
       l.group                      = input(substr(r._name_,5),3.)
    ;quit;

    %pdfbeg(pdf=d:/taj/pdf/&pgm._tbl2100.pdf);
    proc sgplot data=&pgm._res;
    title "Figure 2100 Missings Time jittered Residual Plot Three Quadratics(222)";
    label resid="Residual";
    label t="Jittered Month";
    scatter x=t y=resid;
    xaxis grid values=(1 to 12 by 1) offsetmin=.1 offsetmax=.1;
    yaxis grid  values=(-300 to 300 by 50);
    run;quit;
    %pdfend;

    proc standard data=&pgm._res mean=0 std=1 out=&pgm._std;
      var resid;
    run;

    %pdfbeg(pdf=d:/taj/pdf/&pgm._tbl2200.pdf);
    proc sgplot data=&pgm._std;
    title "Figure 2200 Missings Time jittered Standardized Residual Plot Three Quadratics(222)";
    label resid="Residual";
    label t="Jittered Month";
    scatter x=t y=resid;
    xaxis grid values=(1 to 12 by 1) offsetmin=.1 offsetmax=.1;
    yaxis grid values=(-4 to + 4 by 1 );
    run;quit;
    %pdfend;


    proc sort data=taj.taj_mdlDetail12_222(where=(uniform(1234)<.05)) out=&pgm._detSrt noequals;
      by group id;
    run;quit;

    proc transpose data=&pgm._detSrt out=&pgm._detXpo;
      by group id;
      var _1-_12;
    run;quit;

    proc transpose data=taj.taj_mdlPlot12_222 out=&pgm._pltXpo;
      by t;
      var pred:;
    run;quit;

    proc sql;
      create
        table &pgm._res as
      select
        l.group
       ,r.t + normal(1234)/8 as t
       ,l.col1 as raw
       ,r.col1 as est
       ,r.col1 - l.col1 as resid
      from
        &pgm._detXpo as l left join &pgm._pltXpo as r
      on
       input(substr(l._name_,2),3.) = r.t and
       l.group                      = input(substr(r._name_,5),3.)
    ;quit;

    %pdfbeg(pdf=d:/taj/pdf/&pgm._tbl2300.pdf);
    proc sgplot data=&pgm._res;
    title "Figure 2400 With Zeros: Time jittered Residual Plot Three QuadraticsModel";
    label resid="Residual";
    label t="Jittered Month";
    scatter x=t y=resid;
    xaxis grid values=(1 to 12 by 1) offsetmin=.1 offsetmax=.1;
    yaxis grid  values=(-200 to 450 by 50);
    run;quit;
    %pdfend;

    proc standard data=&pgm._res mean=0 std=1 out=&pgm._std;
      var resid;
    run;

    %pdfbeg(pdf=d:/taj/pdf/&pgm._tbl2400.pdf);
    proc sgplot data=&pgm._std;
    title "Figure 2400 With Zeros: Time jittered Standardized Residual Plot Three QuadraticsModel";
    label resid="Residual";
    label t="Jittered Month";
    scatter x=t y=resid;
    xaxis grid values=(1 to 12 by 1) offsetmin=.1 offsetmax=.1;
    yaxis grid values=(-2.5 to 7.5 by 1.5 );
    run;quit;
    %pdfend;


    * __ _ _                   _                                 _
     / _(_) |_  __   __   ___ | |__  ___  ___ _ ____   _____  __| |
    | |_| | __| \ \ / /  / _ \| '_ \/ __|/ _ \ '__\ \ / / _ \/ _` |
    |  _| | |_   \ V /  | (_) | |_) \__ \  __/ |   \ V /  __/ (_| |
    |_| |_|\__|   \_/    \___/|_.__/|___/\___|_|    \_/ \___|\__,_|
    ;

    %pdfbeg(pdf=d:/taj/pdf/&pgm._tbl2450.pdf);
    %Tut_Sly
       (
        stop=5
        ,L3 ='^S={font_size=20pt just=c &w}Figure 2450 Fit Analysis and Residuals'
        ,L5 ='^S={font_size=20pt just=c &w}Model 131 Linear Cubic Linear '
       );
    %pdfend;

    %pdfbeg(pdf=d:/taj/pdf/&pgm._tbl2500.pdf);
    %Tut_Sly
       (
        stop=5
        ,L3 ='^S={font_size=20pt just=c &w}Figure 2500 With Zeros: Fit Analysis and Residuals'
        ,L5 ='^S={font_size=20pt just=c &w}Model 222 Three Quadratics '
       );
    %pdfend;

    data &pgm._dif0;
      retain sd1-sd3;
      set taj.taj_mdlplot12_222;
      sd1=-1* (L95M1  -   U95M1)*31.6/4;
      sd2=-1* (L95M2  -   U95M2)*31.6/4;
      sd3=-1* (L95M3  -   U95M3)*31.6/4;

      L95M1  =  pred1  - 1.96*sd1;
      L95M2  =  pred2  - 1.96*sd2;
      L95M3  =  pred3  - 1.96*sd3;
      U95M1  =  pred1  + 1.96*sd1;
      U95M2  =  pred2  + 1.96*sd2;
      U95M3  =  pred3  + 1.96*sd3;
    run;quit;

    * model 222;
    proc transpose data=&pgm._dif0 out=&pgm._mdlPlot12_222(rename=(_name_=grp col1=pay));
    by t;
    var pred1 pred2 pred3 avg1 avg2 avg3  l95m1 u95m1 l95m2 u95m2 l95m3 u95m3;
    run;quit;

    proc sort data=&pgm._mdlPlot12_222  out=taj.&pgm._mdlPlot12_222pltz;
    by t;
    run;quit;

     data &pgm._difx;
       set taj.taj_mdlplot12_222x;
       sd1=-1* (L95M1  -   U95M1)*31.6/4;
       sd2=-1* (L95M2  -   U95M2)*31.6/4;
       sd3=-1* (L95M3  -   U95M3)*31.6/4;

       L95M1  =  pred1  - 1.96*sd1;
       L95M2  =  pred2  - 1.96*sd2;
       L95M3  =  pred3  - 1.96*sd3;
       U95M1  =  pred1  + 1.96*sd1;
       U95M2  =  pred2  + 1.96*sd2;
       U95M3  =  pred3  + 1.96*sd3;
     run;quit;

    * model 222;
    proc transpose data=&pgm._difx out=&pgm._mdlPlot12_222x(rename=(_name_=grp col1=pay));
    by t;
    var pred1 pred2 pred3 avg1 avg2 avg3 l95m1 u95m1 l95m2 u95m2 l95m3 u95m3;
    run;quit;

    proc sort data=&pgm._mdlPlot12_222x  out=taj.&pgm._mdlPlot12_222pltx;
    by t;
    run;quit;

    %pdfbeg(pdf=d:/taj/pdf/&pgm._tbl2600.pdf);
    proc sgplot data=taj.&pgm._mdlPlot12_222pltz  noautolegend;
    title1 "Figure 2600 Model 222 With Zeros Best Fit Trajectories Payments";
    title2 "Individual Obsevations 95% CI";
    format pay dollar12.;
    label t="Month";
    Label grp="Group";
    Label Pay="Pay";
    series x=t y=pay / group=grp lineattrs=(pattern=solid thickness=.5pt)
     /* datalabel=pay datalabelattrs=(size=10) */;
    xaxis  values=(1 to 12 by 1) valueattrs=(size=10) grid offsetmin=.05 offsetmax=.05;
    yaxis  grid  offsetmin=.05 offsetmax=.05  values=(0 to 400 by 50)
    valueattrs=(size=12);
    run;quit;
    %pdfend;


    %pdfbeg(pdf=d:/taj/pdf/&pgm._tbl2700.pdf);
    proc sgplot data=taj.&pgm._mdlPlot12_222pltx/*(where=(not (grp =: "Aver")))*/ noautolegend;
    title1 "Figure 2700 Model 222  With Missing Best Fit Trajectories Three Quadratic";
    title2 "Individual Obsevations 95% CI";
    format pay dollar12.;
    label t="Month";
    Label grp="Group";
    Label Pay="Pay";
    series x=t y=pay / group=grp lineattrs=(pattern=solid thickness=.5pt)
    /* datalabel=pay datalabelattrs=(size=10) */;
    xaxis  values=(1 to 12 by 1) valueattrs=(size=10) grid offsetmin=.05 offsetmax=.05;
    yaxis  grid  offsetmin=.05 offsetmax=.05
    valueattrs=(size=12) values=(0 to 400 by 50);
    run;quit;
    %pdfend;

    *          _                _               _  __
     _ __ ___ (_)___ ___    ___| | __ _ ___ ___(_)/ _|_   _
    | '_ ` _ \| / __/ __|  / __| |/ _` / __/ __| | |_| | | |
    | | | | | | \__ \__ \ | (__| | (_| \__ \__ \ |  _| |_| |
    |_| |_| |_|_|___/___/  \___|_|\__,_|___/___/_|_|  \__, |
                                                      |___/
    ;

    * probabilites of each of the four trajectories;
    data taj.&pgm._prbmy;
       set
        taj.taj_mdlDetail12_222x(keep=id grp1prb grp2prb grp3prb group in=N)
        taj.taj_mdlDetail12_222(keep=id grp1prb grp2prb grp3prb group in=Y);
        if not n then do;
           savgrp=group;
           if group=2 then group=3;
           if savgrp=3 then group=2;
        end;
        if n then fro="Missings";
        else fro="Zeros";
        select ;
          when (group=1)  do; typ="1. Low     ";val=GRP1PRB;output;end;
          when (group=2)  do; typ="2. Moderate";val=GRP2PRB;output;end;
          when (group=3)  do; typ="3. High    ";val=GRP3PRB;output;end;
        end;
        keep id fro group typ val;
    run;quit;

    proc sql;
      create
         table taj.&pgm._prbmz as
      select
         l.*
        ,r.*
      from
         taj.taj_simulate(keep=id fro rename=fro=theory) as l, taj.&pgm._prbmy as r
      where
         l.id = r.id
    ;quit;

    ods exclude all;
    ods output summary=taj.&pgm._prbsum(drop=_: variable);;
    proc means data=taj.&pgm._prbmz missing stackodsoutput mean;
    class fro typ theory;
    var val;
    run;quit;
    ods select all;

    data &pgm._two;
      retain fro typ classified theory;
      set taj.&pgm._prbsum(rename=theory=thery);
      cntPrb=catx(' ',put(mean,8.2),cats('(',put(nobs,comma8.),')'));
      select (thery);
         when (2) theory='2. Moderate';
         when (1) theory='1. Low';
         when (3) theory='3. High';
      end;
      if typ=theory then classified="Correct              ";
      else classified="Miss Classified";
      drop thery;
      mean=nobs/1500;
    run;quit;

    proc sort data=&pgm._two(where=(classified ne 'Correct')) out=taj.&pgm._twoxposrt;
       by  fro typ classified theory ;
    run;quit;

    %utl_pdflan100(frame=box,rules=all);
    options orientation=landscape;
    ods escapechah='^';
    %pdfbeg(pdf=d:/taj/pdf/&pgm._tbl2800.pdf);
     proc report data=taj.&pgm._twoxposrt(drop=_:) nowd missing split='#' style(header)={font_weight=bold};  ;
     COLUMN  (
    "^S={ just=l font_size=15pt font_face=arial} Figure 2800 Classification a little more Accurate for the missing model^{newline}^{newline}"
         fro  ("Miss Classification Probabilities" classified typ theory nobs mean));
     DEFINE  fro / order    left "^S={just=left} Models" ;
     DEFINE  classified / order    left "^S={just=left} Classified" ;
     DEFINE  typ / display    left "^S={just=left}Trajectory" ;
     DEFINE  theory / display    left "^S={just=left}Theoretical#Trajectory" ;
     DEFINE  Nobs / "^S={just=center}Frequency"  format=comma8.    center ;
     DEFINE  Mean / display FORMAT= 6.4      center "^S={just=center}Probability" ;
     break after fro / skip;
     compute after fro;
       lyn="  ";
       line lyn $2.;
     endcomp;
    run;quit;
    %pdfend;

    *               _
      ___ _ __   __| |
     / _ \ '_ \ / _` |
    |  __/ | | | (_| |
     \___|_| |_|\__,_|

    ;

