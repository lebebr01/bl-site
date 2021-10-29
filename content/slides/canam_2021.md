---
title: "Tidy Meta-Analytic Data"
author: "Brandon LeBeau & Ariel M. Aloe"
date: "2021-10-29"
slug: "canam2021"
tags: [slides, software, analysis]
---

<h1>Tidy Meta-Analytic Data</h1>
<h2>Brandon LeBeau & Ariel M. Aloe</h2>
<h3>University of Iowa</h3>




# Rationale

- Data entry is an important component for quantitative studies
    + Often neglected in courses
- Messy data can make data manipulation much more difficult
    + Substantial time could be lost due to poor data entry procedures
- Strong data entry procedures are particularly important in evidence synthesis




# Rationale 2

- Data Organization in Spreadsheets - Broman and Woo (2018), *The American Statistician*, https://doi.org/10.1080/00031305.2017.1375989
- Tidy Data - Wickham (2014), *Journal of Statistical Software*, https://www.jstatsoft.org/index.php/jss/article/view/v059i10
- Nine simple ways to make it easier to (re)use your data - White et al., (2013), https://ojs.library.queensu.ca/index.php/IEE/article/view/4608




# Tidy Meta Analytic Data

- A series of data entry rules
- Promotes more consistent evidence synthesis data
- Promotes reproducible analyses (See Reproducible Analyses in Education Research by LeBeau, Ellison, Aloe (2021) in Review of Research in Education). 
- Promotes reusable analyses across evidence synthesis projects
- Facilitates a split-apply-combine data analysis framework (Wickham, 2011; https://www.jstatsoft.org/v40/i01/)




# Data Entry Rules

- These rules are mostly agnostic to data storage mode/program
    + Text based (csv, tsv, etc.)
    + SQL databases of all types
    + Excel (but please avoid)
- Rows should be the unit of analysis
- Columns are attributes/characteristics about a unit of analysis
- Data should be rectangular





# Column Rules

1. Avoid placing attributes/characteristics in column names
2. Do not use spaces in names
3. Columns should contain one attribute/characteristic
4. Use one row for column names
5. Ensure appropriate ID columns




# Column Example(s)

<div id="htmlwidget-9cdb944ea49dddb3b582" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-9cdb944ea49dddb3b582">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40","41","42","43","44","45","46","47","48","49","50","51","52","53","54","55","56","57","58","59","60","61","62","63","64","65","66","67","68","69","70","71","72","73","74","75","76","77","78","79","80","81","82","83","84","85","86","87","88","89","90","91","92","93","94","95","96","97","98","99","100","101","102","103","104","105","106","107","108","109","110","111","112","113","114","115","116","117","118","119","120","121","122","123","124","125","126","127","128","129","130","131","132","133","134","135","136","137","138","139","140","141","142","143","144","145","146","147","148","149","150","151","152","153","154","155","156","157","158","159","160","161","162","163","164","165","166","167","168","169","170","171","172","173","174","175","176","177","178","179","180","181","182","183","184","185","186","187","188","189","190","191","192","193","194","195","196","197","198","199","200","201","202","203","204","205","206","207","208","209","210","211","212","213","214","215","216","217","218","219","220","221","222","223","224","225","226","227","228","229","230","231","232","233","234","235","236","237","238","239","240","241","242","243","244","245","246","247","248","249","250","251","252","253","254","255","256","257","258","259","260","261","262","263","264","265","266","267","268","269","270","271","272","273","274","275","276","277","278","279","280","281","282","283","284","285","286","287","288","289","290","291","292","293","294","295","296","297","298","299","300","301","302","303","304","305","306","307","308","309","310","311","312","313","314","315","316","317","318","319","320","321","322","323","324","325","326","327","328","329","330","331","332","333","334","335","336","337","338","339","340","341","342","343","344","345","346","347","348","349","350","351","352","353","354","355","356","357","358","359","360","361","362","363","364","365","366","367","368","369","370","371","372","373","374","375","376","377","378","379","380","381","382","383","384","385","386","387","388","389","390","391","392","393","394","395","396","397","398","399","400","401","402","403","404","405","406","407","408","409","410","411","412","413","414","415","416","417","418","419","420","421","422","423","424","425","426","427","428","429","430","431","432","433","434","435","436","437","438","439","440","441","442","443","444","445","446","447","448","449","450","451","452","453","454","455","456","457","458","459","460","461","462","463","464","465","466","467","468","469","470","471","472","473","474","475","476","477","478","479","480","481","482","483","484","485","486","487","488","489","490","491","492","493","494","495","496","497","498","499","500","501","502","503","504","505","506","507","508","509","510","511","512","513","514","515","516","517","518","519","520","521","522","523","524","525","526","527","528","529","530","531","532","533","534","535","536","537","538","539","540","541","542","543","544","545","546","547","548","549","550","551","552","553","554","555","556","557","558","559","560","561","562","563","564","565","566","567","568","569","570","571","572","573","574","575","576","577","578","579","580","581","582","583","584","585","586","587","588","589","590","591","592","593","594","595","596","597","598","599","600","601","602","603","604","605","606","607","608","609","610","611","612","613","614","615","616","617","618","619","620","621","622","623","624","625","626","627","628","629","630","631","632","633","634","635","636","637","638","639","640","641","642","643","644","645","646","647","648","649","650","651","652","653","654","655","656","657","658","659","660","661","662","663","664","665","666","667","668","669","670","671","672","673","674","675","676","677","678","679","680","681","682","683","684","685","686","687","688","689","690","691","692","693","694","695","696","697","698","699","700","701","702","703","704","705","706","707","708","709","710","711","712","713","714","715","716"],["Abadi_MV_2008","Aberson_1996","Aberson_1996_p2","Abikoff_GRBFK_1988","Abikoff_GRBFK_1988_p2","Abikoff_GWMHLP_2013","Abikoff_GWMHLP_2013","Abikoff_G_1984","Abikoff_G_1985","Abikoff_G_1985_p2","Abikoff_G_1985_p3","Abikoff_HKGFECGMP_2004_social","Abikoff_HKWFECGMP_2004_symptom","Abikoff_TLLFMKRHS_2015","Abramowitz_EOD_1992","Abramowitz_EOD_1992","Abramowitz_OF_1988","Abramowitz_OR_1987_study1","Abramowitz_OR_1987_Study2","Abramowitz_O_1990","Acker_O_1988","Ajibola_C_1995","Ajibola_C_1995","Ajibola_C_1995_p2","Al-Ansari_H_1998","Al-Ansari_H_1998","Alaniz_2010","Alkahtani_2013","Almeida_1985","Almeraisi_2008","Altszuler_ETAL_2016","Amonn_FBBD_2013","Anastopoulos_SDG_1993","Andrews_1994","Anhalt_MB_1998","Antshel_FG_2012","Antshel_FG_2012_p2","Antshel_R_2003","Arnold_CDACEGHHHJKLMNPSSVWW_2004","Asher_1989","Asher_1989","Askins_1994","Atkins_1981","Atkins_PW_1989","Au_LWLLLL_2014","Ayllon_LK_1975","Azevedo_SGH_2013","Azevedo_SGH_2015","Azevedo_SGH_2015","Azevedo_SGH_2015_p2","Azrin_EB_2006","Babinski_SRP_2013","Babinski_SRP_2013","Bai_WYN_2015","Bakhshayesh_HWRE_2011","Banda_S_2012","Barkley_CS_1980","Barkley_CS_1980_p2","Barkley_ELFM_2001","Barkley_ELFM_2001_p2","Barkley_GAF_1992","Barkley_GAF_1992_p2","Barkley_SCMFBJM_2000","Barkley_SCMFBJM_2000_p2","Barkley_SCMFBJM_2000_p3","Barry_M_2003","Basu_D_1996","Basu_D_1996_p2","Beauchaine_NGRCBOSW_2015","Beck_HPBB_2010","Beyer_1994","Bidder_GN_1978","Bigorra_GGH_2015","Bigorra_GGH_2015_p2","Binder_DG_2000","Bjornebekk_KO_2015","Blakemore_SC_1993","Bloomquist_AO_1991","Bolich_KMQU_1995","Bolich_KMQU_1995","Bor_SM_2002","Bowers_CFS_1985","Bowers_CFS_1985","Bowers_CFS_1985_p2","Boyd_HH_1978","Boyer_GPV_2015","Boyer_GPV_2015_p2","Boyer_GPV_2016","Boyer_GPV_2016","Brady_K_2010","Brown_1995","Brown_BWSC_1986","Brown_BWSC_1986","Brown_WBCGS_1986","Brown_WM_1985","Bugental_CSC_1978","Bugental_WH_1977","Burley_ W_2005","Burrows_2000","Cabiya_PMP_2003","Cabiya_PMP_2003_p2","Cameron_R_1980","Cameron_R_1980","Campbell_A_2011","Canu_B_2011","Carboni_RF_2013","Carlson_PMD_1992","Carlson_PMD_1992_p2","Carpenter_FMDS_2004","Chacko_BMFUCRCAZR_2014","Chacko_BMFUCRCAZR_2014","Chacko_BMGFUCHCAZR_2016","Chacko_S_2018","Chacko_WCWP_2012","Chacko_WCWP_2012_p2","Chacko_WFPWAVSGPH_2008","Chacko_WWPSGPHGPO_2009","Channell_1997","Chavez_MP_2015","Choi_L_2015","Choi_L_2015","Christie_HL_1984","Chronis-Tuscano_OJJCRRDPS_2011","Chronis_FGOPLCWCS_2004","Chronis_GRP_2006","Clarfield_S_2005","Cocciarella_WL_1995","Coelho_BRMBM_2015","Cohen_1999","Cohen_1999","Cohen_SMNH_1981","Cohen_SMNK_1983","Coles_PGBFCWTWR_2005","Coles_PG_2010","Coles_PG_2010_p2","Colton_S_1998","Connell_SM_1997","Connell_SM_1997_p2","Conte_BS_1994","Cook_JB-J_2015","Corkum_CP_2010","Corkum_MM_2005","Cormier_2004","Cormier_2004","Corrin_2003","Creel_FBB_2006","Cruz_2009","Cruz_2009_p2","Curtis_2010","Curtis_2010","Curtis_CDM_2013","Dahlin_2013","DAHL_PW_1991","Daley_O_2013","Danforth_1999","Danforth_1999_p2","Danforth_2000","Danforth_2000_p2","Danforth_HUM_2006","Danforth_HUM_2006","Danforth_HUM_2006_p2","Davies_W_2000","Depry_2008","Docking_MCE_2013","Docking_MCE_2013","Doherty_1991","Dooney_P_1989","Dopfner_BSMRL_2004","Dopfner_IMSRB_2015","Dopfner_IMSRB_2015","Douglas_PMG_1976","Dovis_VWP_2015","Dovis_VWP_2015_p2","Drechsler_SDHSB_2007","Drechsler_SDHSB_2007","Driskill_1999","Dubey_OK_1983","Dubey_O_1975","Dubey_O_1975","Ducharme_H_2005","Duckham-Shoor_1980","Dunlap_dPCWWWG_1994","DuPaul_EHM_1998","DuPaul_GB_1992","DuPaul_H_1993","DuPaul_JVTLVCFM_2006","DuPaul_KVCSAVP_2013","Eastman_R_1981","Edwards_ME_2002","Eisenstadt_EMNF_1993","Epstein_WCJ_2001","Epstein_WCJ_2001","Ercan_AKD_2012","Ercan_AKD_2012","Ercan_VD_2005","Ercan_VD_2005","Ernhardt_B_1990","Ervin_DKF_1998","Ervin_KCDDF_2000","Evans_AL_2004","Evans_FFG_1995","Evans_LRVB_2005","Evans_LSVAMZ_2016","Evans_PG_1994_Study 1","Evans_PG_1994_Study 2","Evans_SSDD_2011","Everett_AAAE_2011","Fabiano_CPRWWSFKVSHP_2009","Fabiano_HLNPGLPWWGGB_2011","Fabiano_HLNPGLPWWGGB_2011","Fabiano_HLNPGLPWWGGB_2011_p2","Fabiano_PCYGBLGG_2012","Fabiano_PGBCCWWAGKOHMR_2007","Fabiano_PGBCCWWAGKOHMR_2007_p2","Fabiano_PGBCCWWAGKOHMR_2007_p3","Fabiano_PMGCOLBCMCS_2004","Fabiano_P_2003","Fabiano_SMWVHRHHLHW_2016","Fabiano_VPWMYPNRCGV_2010","Falcomata_NDSVE_2008","Falissard_CRL_2010","Fallone_1998","Fehlings_RHD_1991","Fehlings_RHD_1991","Fenstermacher_OS_2006","Ferrari_2005_Study2","Ferreri_2005_Study1","Field_QHK_1998","Field_QHK_1998","Firestone_CGM_1986","Firestone_KGD_1981","Flood_WFM_2002","Flood_W_2002","Frankel_MCF_1997","Frankel_MCF_1997","Frankel_MCF_1997b","Friars_M_2007","Friedling_O_1979_study1","Friedling_O_1979_study2","Friedman_1992","Froelich_DL_2002","Gannon_HW_1997","Gardner_GW_2015","Gerdes_HS_2012","Germer_KGMFOL_2011","Germer_KGMFOL_2011","Gevensleben_HAVSKSRMH_2009","Ghanizadeh_S_2005","Gittelman_KAKPM_1980","Goldhaber_1991","Goldhaber_1991_p2","Gol_J_2005","Gonzalez_ 2002","Goodwin_M_1975","Gordon_TCI_1991","Gordon_TCI_1991_p2","Gormley_D_2015","Grauvogel-MacAleese_W_2010","Gray_CMGGKT_2012","Guderjahn_GSG_2013","Guevremont_TH_1985","Guevremont_TH_1985","Gulley_NHSLR_2003","Gumpel_2007","Gumpel_2007","Gureasko-Moore_DW_2006","Gureasko-Moore_DW_2006","Gureasko-Moore_DW_2007","Gureasko-Moore_DW_2007_p2","Gurney_2008","Haas_WPKAC_2011","Habboushe_DKLCGEP_2001","Haffner_RGPR_2006","Hahn-Markowitz_MM_2011","Hall_2002","Hall_2002_p2","Halperin_MBCCYH_2013","Hantson_WG-VT-SHJG_2012","Harbeitner_1996","Harbeitner_1996_p2","Harper_1996","Harris_FSFG_2005","Harris_FSFG_2005_p2","Harvey_DMUF_2003","Hauch_2005","Hauch_2005_p2","Hawkins_A_2008","Haydicky_SWD_2015","Haydicky_SWD_2015_p2","Heath_CFM_2015","Heath_CFM_2015","Hechtman_AKGECFWP_2004","Hechtman_AKWRKBGEFP_2004","Helseth_WGOBFCCWWWGMRHWNP_2015","Helseth_WGOBFCCWWWGMRHWNP_2015","Helseth_WGOBFCCWWWGMRHWNP_2015_p2","Henry_1987","Henry_1987_p2","Herbert_HRWL_2013","Hernandez-Reif_FT_2001","Hernandez-Reif_FT_2001","HInshaw_HW_1984a","Hinshaw_HW_1984b_Study1","Hinshaw_HW_1984b_Study2","Hinshaw_OWKAACEGHHJMNPSVW_2000","Hoat_S_2002","Hoat_S_2002_p2","Hoff_EF_2005","Hogg_CC_1986","Hook_1997","Hook_D_1999","Horn_CC_1983","Horn_CC_1983","Horn_CC_1983_p2","Horn_CC_1983_p2","Horn_IGPS_1990","Horn_IPGPLWP_1991","Horn_IPGPLWP_1991_p2","Horn_IPP_1987","Horn_IPP_1987_p2","Hoza_GMHBGAACEGHJKMNSSVWW_2005","Hoza_MPGG_2003","Hoza_MPGG_2003","Hoza_PSC_1992","Huang_CTY_2003","Hupp_RNOCL_2002","Hupp_R_1999","Hupp_R_1999","Hutchinson_MWC_2000","Ialongo_HPGPLWP_1993","Ialongo_HPGPLWP_1993_p2","Iseman_N_2011","Iseman_N_2011","Iskander_R_2013","Jacobson_R_2010","Jacob_OR_1978","Jans_JWZGMBHHRRVHSAPHCGJKBHFGIP_2015","Jarrett_O_2012","Jarrett_O_2012","Jensen_ASVAGHHPWCEEHMMNSWGH_2007","Jensen_GGCFSHVAEHNPSW_2005","Jensen_K_2004","Jensen_K_2004_p2","Jitendra_DVT_2007","Johnson_1994_Study1","Johnson_1994_Study2","Johnson_YS_1989","Johnstone_RBJLMB_2012","Johnston_MR_2010","Jones_BFB_2008","Jones_DHBE_2007","Jones_DHBE_2007","Jones_DHBE_2008","Jurbergs_PK_2007","Jurbergs_PK_2007_p2","Jurbergs_PK_2010","Kaduson_F_1995","Kapalka_2002","Kapalka_2004","Kapalka_2004","Kapalka_2006","Kapalka_B_2007","Kayser_WDAGS_1997","Kelley_M_1995","Kendall_B_1982","Kendall_F_1978","Kendall_Z_1981","Kendall_Z_1981","Kercood_G_2010","Kercood_G_2010_Study2","Kern_CDCF_1994","Kern_DVSLAPV_2007","Kimonis_A_2012","Kirby_1984","Kirby_H_1982","Kirby_H_1982","Kirby_S_1972","Klein_A_1997","Klein_A_1997_p2","Klein_A_1997_p3","Klein_A_1997_p4","Klingberg_FOJGDGFW_2005","Klingberg_FOJGDGFW_2005","Kobler_1982","Kolko_BB_1999","Konstantareas_H_1983","Konstantareas_H_1983","Kotkin_1998","Kotwal_BM_1996","Kratter_H_1982","Kubany_WS_1971","Laezer_2015","Langberg_AFEAHSKSMJ_2010","Langberg_AFEAHSKSMJ_2010","Langberg_EBGV_2012","Langberg_EUSG_2008","Lastra_2015","Lees_R_2008","Lee_A_2004","Lehner-Dua_2003","Leisman_MTROTC_2010","Leppanen_2013","Lequia_ML_2013","Lerew_2004","Lerew_2004_p2","Lerner_MM_2011","Lienemann_R_2008","Locke_Fuchs_1995","Loffredo_OH_1984","Loffredo_OH_1984","Long_RA_1993","Long_RA_1993","Loren_VLCPSTE_2015","Luiselli_P_1999","Lyons_2000","Majeika_WHSFOL_2011","Malekpour_AH_2014","Malekpour_AH_2014","Malik_T_2014","Mathes_B_1997","Matos_BB_2009","Mautone_DJTVV_2009","Mautone_DJTVV_2009","Mautone_DJ_2005","Mautone_MSEJP_2012","Mazius_1990","McCain_K_1994","McCleary_R_1999","McGoey_DEVB_2005","McGoey_DEVB_2005_p2","McGoey_D_2000","McGrath_LTMCWWSBSC_2011","McKee_HDUF_2004","McKinnon_2001","McNeil_EENF_1991","McNeil_EENF_1991","McTate_BHB_2013","McTate_BHB_2013","McTate_BHB_2013_p2","Meftagh_NMGRA_2014","Menezes_DTCS_2015","Merrill_MAMGGCRCP_2016","Merrill_MAMGGCRCP_2016","Merrill_MAMGGCRCP_2016_p2","Merriman_C_2008","Meyer_K_2007","Mikami_GLERJA_2013","Mikami_LGMC_2010","Miller_K_1994","Miranda_JR_2006","Miranda_PSJ_2013","Miranda_PS_2002","Miranda_PS_2002_p2","Miranda_P_2000","Molina_FBGBKE_2008","Molina_FHGASHJVHPEWAGMCEGMNSW_2007","Molina_HSAVJEHHAEGNWWGHH_2009","Molina_HSAVJEHHAEGNWWGHH_2009_p2","Morrison_MBK_2014","Moser_FKH_2012","MTACooperativeGroup_1999","MTACooperativeGroup_2004","Murray_RSN_2008","Neef_L_2001","Newman_1999","Nixon_2001","Noell_GWWFLGN_1998","Noell_GWWFLGN_1998_p2","Nolan_F_2012","Northup_FSHBFGE_1999","Northup_FSHBFGE_1999","Northup_JBDHFH_1997","Northup_JBDHFH_1997","OCallaghan_RNHM_2003","OConnor_FWBGPGR_2014","Odom_1996","Ogg_C_2009","OLeary_KKD_1970","OLeary_KKD_1970_p2","OLeary_PRP_1976","OLeary_P_1978","Ostberg_R_2012","Ota_D_2002","Owens_HMP_2016","Owens_HZEHGM_2012","Owens_RBCMV_2005","Owens_RBCMV_2005_p2","Ozcan_OTF_2013","Ozdemir_2011","Ozdemir_2011","Palcic_JK_2009","Palkes_SK_1968","Pang_Z_2011","Paniagua_1987","Paniagua_1987","Paniagua_1992_Study1","Paniagua_1992_Study2","Paniagua_1992_Study3","Paniagua_B_1990","Paniagua_B_1990_p2","Paniagua_B_1990_p3","Paniagua_B_1990_p4","Paniagua_B_1993","Paniagua_MB_1990","Paniagua_PB_1988","Paoni_2000","Pariseau_FMHP_2010","Parrish_E_1981","Parrish_E_1981","Pekarsky_2012","Pekarsky_2012","Pelham_B-MGFCTCWWWH_2005","Pelham_B-MGFCTCWWWH_2005_p2","Pelham_B-MGFCWCWWGHWW_2014","Pelham_B-MGFCWCWWGHWW_2014_p2","Pelham_CSVDH_1993","Pelham_CSVDH_1993_p2","Pelham_FWGGPCVBHKKTHM_2016","Pelham_F_2001","Pelham_GFCWCWAGROB-MHWWM_InPreparation","Pelham_GFCWCWAGROB-MHWWM_InPreparation_p2","Pelham_GGHHSSSBBM_2000","Pelham_H_1996","Pelham_SBC_1980","Pelham_SBC_1980_p2","Pelham_SBNMBRPM_1988","Perry_1999","Perry_1999_p2","Pfiffner_HOZKVM_2014","Pfiffner_MHEZM_2007","Pfiffner_MHEZM_2007","Pfiffner_M_1997","Pfiffner_ORS_1985","Pfiffner_O_1987","Pfiffner_RO_1985","Pfiffner_RO_1985","Pfiffner_VKRM_2013","Pfiffner_VKRM_2013","Piscalkiene_2009","Piscalkiene_2009_p2","Pisterman_FMGWMG_1992","Pisterman_FMGWMG_1992a","Pisterman_MFGWM_1989","Plumer_S_2005","Poley_1995","Pollard_WB_1983","Posavac_SP_1999","Powell_N_1997","Power_MSCMSBGEJ_2012","Pratt_F_1975","Price_MMC_2002","Raggi_2008","Raggi_2008_p2","Raggi_2008_p3","Rapport_MB_1980_exp1","Rapport_MB_1980_exp2","Rapport_MB_1982","Raymer_P_1985","Reddy_BSBHHB_2002","Reddy_BSBHHB_2002_p2","Reese_SSS_2012","Reid_B_1987","Reid_L_2006","Reitman_HOGN_2001","Resnick_2012","Re_C_2015","Rickman_M_1996","Rieppi_GFCWDAACEHHHJKMNPSSVWW_2002","Ringeisen_1999","RiveraFlores_2015","Robert_1994","Robert_1994_p2","Robinson_NG_1981","Rogers_CCLL_2003","Rosen_OJCP_1984_Study 1","Rosen_OJCP_1984_Study2","Rosen_OJCP_1984_Study3","Rosen_OJCP_1984_Study4","Rudolph_2005","Satterfield_SS_1987","Schanding_TS_2009","SchmelzerBenisz_2002","SchmelzerBenisz_2002_p2","Schmitt_2009","Schofield_HW_1974","Scholte_BP_2007","Schottelkorb_R_2009","Schuhmann_FEBA_1998","Schultz_ELS_2017","Schultz_ELS_2017","Semrud-Clikeman_NCSPC_1999","Shalev_TM_2007","Shapiro_DB_1998","Shelton_BCMFBJM_2000","Shepp_J_1983","Sheridan_DMMW_1996","Shimabukuro_PJE_1999","Shipley_2013","Shipley_2013_p2","Shipley_2013_p3","Sibley_ARSPG_2014","Sibley_ARSPG_2014_p2","Sibley_GKCPRSDHW_2016","Sibley_PDKSG_2013","Sibley_PDKSG_2013_p2","Sibley_PMGRK_2012","Silverstein_HWFSPCC_2015","Singh_SLSWA_2010","Siwek_2005","Slattery_CL_2016","Smitheman-Brown_LC_1996","Smitheman-Brown_LC_1996","Smith_2000_Study1","Smith_2000_Study2","Smith_B_2000","Smith_B_2002","Sonuga-Barke_DTLW_2001","Sonuga-Barke_TDL_2004","Sotnikova_SWGSPGS_2012","Sotnikova_SWGSPGS_2012","So_LH_2008","So_LH_2008","Sprich_BLS_2015","Stableford_BHLP_1976","Stableford_BHLP_1976_p2","Stahr_CLF_2006","Stattin_EOG_2015","Steeger_GBR_2016","Stewart_M_1993","Storebo_GWS_2012","Sullivan_1989","Sullivan_O_1990","Swenson_LWM_2000","Szymula_1990","Szymula_1990_p2","Tamm_EPNH_2013","Tamm_EPNH_2013_p2","Tamm_EPNH_2013_p3","Tamm_HAPSSCRMFBHNE_2010","Tamm_HAPSSCRMFBHNE_2010_p2","Thompson_LALMDPBDWMATS_2009","Thompson_LALMDPBDWMATS_2009","Thompson_T_1998","Thorell_2009","Thurston_1979","Trahant_2004","Treacy_TB_2005","Treacy_TB_2005","Treacy_TB_2005_p2","Treacy_TB_2005_p2","Trillingsgaard__W-B_2014","Trillingsgaard__W-B_2014","Turner_1996","Turner_1996_p2","Tutty_GW_2003","Tymms_M_2006","Tynan_SL_2000","Umbreit_1995_Study1","Umbreit_1995_Study2","Umbreit_1995_Study3","Van Den Hoofdakker_LV-MSEMN_2007","VanderOord_BP_2012","Van der Oord_POE_2007","vanderOord_POE_2012","VandeWeijer-Bergsma_FDB_2012","VandeWeijer-Bergsma_FDB_2012_p2","VanHasselt_GKEU_1984","vanLeir_MVC_2004","Varni_H_1979","Verduin_AK_2008","Vilardo_DKH_2013","Vilardo_DKH_2013","Volpe_DJT_2009","Vujnovic_2010","Walker_1980","Walker_B_1968","Watemberg_WZL_2007","Waxmonsky_PGCOCMVHMB-MFWCAWGR_2008","Waxmonsky_PGCOCMVHMB-MFWCAWGR_2008","Waxmonsky_WPBWBFAHP_2012","Webb_M_2003","Webster-Stratton_RB_2011","Webster-Stratton_RB_2011_p2","Webster-Stratton_RB_2011_p3","Webster-Stratton_RB_2013","Weinberg_1999","Weinberg_1999","Wells_CHEPNOAACEGHHJMNPSSVW_2006","Wells_CHEPNOAACEGHHJMNPSSVW_2006","Wells_EHCKAAEEGHHJMPPSSVW_2000","White_2004","White_2004","White_2004_p2","White_2004_p2","Whitford_LUF_2013","Wilkes-Gillan_BCL_2014","Wilkes_CBDM_2011","Williams_1990","Wills_M_2014","Woeppel","Woltersdorf_1992","Woods_1994","Workman_D_1979","Wulbert_D_1977","Yamashita_MAHKKTEKNNM_2011","Yamashita_MHAKKMSONNGGPM_2010","Yelling_KG_1981","Yeo_WGA_2005","Yeo_WGA_2005_p2","Yi_2011","Young_Pelton_B_2015","Zentall_J_2007","Zentall_J_2007_p2","Zentall_L_1985","Zentall_L_2012","Ziereis_J_2015"],[0,1,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,1,0,0,0,0,0,0,1,0,0,0,0,0,0,1,0,0,0,0,0,0,0,1,1,0,0,0,0,0,0,1,0,0,0,0,1,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,1,0,0,0,1,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,1,0,0,0,1,0,0,0,0,0,1,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,1,1,0,0,0,0,0,0,1,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,1,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,1,0,0,1,0,0,0,0,0,0,0,0,0,0,0,1,1,0,0,0,0,1,1,0,0,0,1,0,0,0,1,0,0,0,0,0,0,1,0,0,1,0,0,0,0,1,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,1,1,1,0,0,0,0,0,0,0,0,0,0,0,1,0,1,1,0,1,0,0,0,0,1,1,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,1,0,0,1,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,1,1,0,0,0,0,0,1,0,1,0,0,0,1,0,0,0,1,0,0,1,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,1,1,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,1,0,0,0,0,0,1,0,0,0,1,1,0,1,1,1,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,1,0,0,0,0,0,0,1,1,0,0,0,0,0,0,0,0,1,0,1,1,1,0,1,1,1,0,0,1,1,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,1,1,1,1,0,0,0,0,0,1,0,1,0,0,0,0,0,0,0,1,0,1,0,0,0,0,0,0,0,0,1,0,1,1,1,1,0,1,1,0,1,0,0,0,0,0,0,0,1,0,1,0,0,1,0,0,0,1,1,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,1,0,0,0,0,1,1,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,1,0,0,0,0,0,0,1,1,0,0,0,0,0],[1,0,0,1,0,1,0,0,0,0,0,1,0,1,0,0,0,0,0,1,0,0,0,0,1,0,1,0,0,1,1,1,1,1,0,1,0,1,1,1,0,1,0,0,1,0,0,1,0,0,0,0,0,1,1,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,1,0,0,0,0,0,1,1,0,0,0,0,0,0,0,1,0,1,0,0,0,1,0,0,1,1,0,0,1,0,0,0,0,0,1,0,1,0,0,1,0,1,1,0,0,1,0,1,1,1,0,0,1,0,0,0,1,1,1,0,1,0,0,1,0,0,0,0,0,0,0,1,0,0,1,0,0,0,1,0,0,1,0,1,0,0,0,0,0,0,0,0,0,1,0,0,0,0,1,0,1,0,0,1,0,0,0,0,0,0,0,0,0,0,0,1,0,1,0,1,0,0,1,0,0,0,0,0,0,1,0,0,1,0,0,1,0,1,1,0,0,0,1,0,0,1,0,0,1,0,1,1,1,0,0,0,0,0,0,0,1,0,0,1,0,0,1,1,0,1,1,0,0,0,0,0,0,1,1,0,0,1,0,0,0,0,0,0,1,1,0,0,0,0,0,0,0,0,0,0,0,0,1,0,1,0,1,1,1,0,0,0,0,0,1,0,0,1,0,1,0,1,0,1,0,0,0,0,0,1,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,1,0,0,0,0,0,1,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,1,0,0,0,0,0,0,1,0,1,0,0,1,1,1,1,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,1,0,0,1,0,0,0,1,0,0,1,1,0,0,0,1,0,0,1,0,1,1,0,0,0,1,1,0,0,0,0,0,0,0,1,0,1,0,1,0,1,0,1,0,0,0,0,0,0,0,0,0,0,1,1,0,0,1,0,1,1,0,1,0,0,1,1,0,0,0,0,1,0,1,0,1,0,0,0,0,0,0,1,0,0,0,1,1,1,0,1,1,0,0,0,0,0,0,0,1,1,0,0,0,0,1,1,0,0,1,1,0,0,1,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,1,0,0,0,1,0,0,0,1,0,0,0,1,0,0,0,0,0,1,0,0,1,1,0,1,0,1,0,0,1,0,0,0,0,1,1,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,1,0,1,0,0,0,0,1,0,0,0,0,1,0,1,1,1,1,1,1,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,1,0,1,0,0,0,0,0,0,1,1,0,0,1,0,1,0,0,0,0,0,0,1,1,1,0,0,1,0,0,0,0,0,0,1,0,0,1,0,0,1,0,1,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,1,0,0,0,1,0,0,0,0,0,0,0,1,1,0,0,1,0,0,1,0,0,0,0,0,0,0,1,0,1,0,0,0,0,0,1,0,1,0,0,0,1,0,0,1,1,0,1,0,1,0,0,0,1,0,0],[0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,1,0,0,0,0,0,0,0,1,0,0,1,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,1,0,0,1,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,1,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,1,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,1,1,0,0,0,1,0,0,0,0,0,0,0,0,1,1,0,0,1,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,1,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,1,0,0,0,0,0,0],[0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,1,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0],[0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0],[1,1,null,1,null,1,null,null,null,null,null,1,null,1,1,null,null,null,null,1,9,null,null,null,1,null,1,1,null,1,1,1,1,1,1,1,null,1,1,1,null,1,1,1,1,null,null,1,null,null,1,null,null,1,1,1,null,null,null,null,null,null,1,null,null,1,null,null,null,null,1,null,null,null,null,null,1,1,1,null,null,null,null,null,null,1,null,1,null,1,null,1,null,null,1,1,null,1,1,null,null,1,null,null,1,1,1,null,null,1,null,1,1,null,null,9,null,1,1,1,null,null,1,null,null,1,1,1,1,null,1,null,null,1,null,1,null,null,1,1,null,1,null,null,1,1,null,null,1,null,null,1,1,1,null,null,null,null,1,null,null,null,null,1,null,null,null,null,1,null,1,null,null,1,null,null,null,1,1,null,null,null,1,1,null,1,1,1,null,1,9,null,1,null,null,null,1,null,null,1,null,null,1,null,null,1,null,1,1,null,null,1,1,null,null,1,1,null,1,1,1,1,1,null,null,null,null,null,null,null,1,null,1,1,null,null,1,1,null,1,1,1,null,null,1,null,null,1,1,null,null,1,null,null,null,null,1,1,1,1,null,null,1,1,null,null,null,1,null,null,null,1,1,null,1,null,1,1,1,null,null,1,null,null,1,null,1,1,null,1,null,1,null,1,null,null,1,null,null,1,null,1,null,null,null,null,null,null,null,1,1,1,null,null,null,1,null,null,1,null,null,null,null,1,1,1,1,null,1,null,null,null,null,1,1,null,null,null,null,null,null,1,null,1,null,null,1,null,null,null,1,null,1,1,null,1,1,1,1,null,null,null,1,null,null,null,1,null,null,null,null,null,null,null,1,null,1,1,null,null,null,1,null,null,1,1,null,1,null,1,1,null,1,null,1,1,null,null,1,1,1,null,null,null,null,1,1,1,1,null,1,null,1,1,1,1,1,null,null,1,null,null,null,1,null,null,1,1,1,null,1,1,null,1,1,null,1,null,null,1,1,null,null,null,1,1,null,1,null,1,null,null,null,null,null,null,1,null,1,1,1,1,1,1,1,1,null,null,null,null,null,null,null,1,1,1,null,null,null,1,1,null,1,1,1,null,null,1,1,null,1,null,1,1,null,1,1,1,null,null,null,null,null,null,null,null,1,1,null,1,null,1,null,null,null,1,null,null,1,1,null,null,null,null,null,1,1,null,1,1,null,1,null,1,9,null,1,null,null,null,null,1,1,1,null,1,1,1,1,1,1,1,null,null,1,1,null,1,1,null,1,null,null,null,null,1,null,null,null,null,1,null,1,1,1,1,1,1,1,null,null,null,null,null,1,null,1,null,1,null,null,null,null,1,1,1,1,null,null,null,null,null,1,1,null,1,1,1,1,1,1,null,1,9,null,1,1,1,null,null,1,null,null,1,null,1,null,1,1,null,1,null,1,1,null,1,null,null,null,null,1,null,null,null,null,1,null,null,null,null,null,null,1,null,null,null,1,1,1,null,1,null,null,null,1,null,null,null,1,null,null,null,1,1,null,null,1,null,null,1,null,null,null,null,null,1,null,1,null,1,null,null,null,null,null,1,null,1,null,null,1,1,1,null,1,1,null,1,null,1,1,1,null,1,null,null],[20,1,null,11,null,72,null,null,null,null,null,34,null,67,1,null,null,null,null,4,4,null,null,null,8,null,21,1,null,27,17,30,19,27,1,68,null,40,135,15,null,8,3,1,8,null,null,28,null,null,1,null,null,44,18,1,null,null,null,null,null,null,42,null,null,1,null,null,null,null,31,null,null,null,null,null,8,20,1,null,null,null,null,null,null,83,null,83,null,1,null,10,null,null,10,null,null,1,null,null,null,1,null,null,16,1,24,null,null,44,null,44,80,null,null,12,null,7,6,23,null,null,70,null,null,1,7,null,9,null,6,null,null,96,null,1,null,null,null,null,null,13,null,null,24,1,null,null,21,null,null,42,1,24,null,null,null,null,null,null,null,null,null,14,null,null,null,null,21,null,18,null,null,17,null,null,null,2,2,null,null,null,18,1,null,80,71,6,null,13,1,null,83,null,null,null,1,null,null,7,null,null,112,null,null,31,null,38,7,null,null,28,46,null,null,71,1,null,33,1,282,16,13,null,null,null,null,null,null,null,13,null,1,36,null,null,5,4,null,14,18,1,null,null,1,null,null,9,21,null,null,27,null,null,null,null,1,1,36,35,null,null,1,1,null,null,null,1,null,null,null,5,8,null,10,null,28,33,9,null,null,1,null,null,10,null,1,17,null,43,null,34,null,26,null,null,1,null,null,11,null,24,null,null,null,null,null,null,null,1,1,1,null,null,null,12,null,null,6,null,null,null,null,1,14,1,3,null,1,null,null,null,null,1,1,null,null,null,null,null,null,11,null,86,null,null,1,null,null,null,50,null,50,8,null,16,null,21,27,null,null,null,1,null,null,null,10,null,null,null,null,null,null,null,8,null,1,25,null,null,null,24,null,null,16,5,null,1,null,null,1,null,139,null,23,24,null,null,1,23,122,null,null,null,null,27,1,null,16,null,17,null,241,1,15,1,15,null,null,1,null,null,null,1,null,null,1,20,27,null,1,38,null,8,10,null,13,null,null,15,8,null,null,null,1,14,null,32,null,17,null,null,null,null,null,null,117,null,1,1,115,113,15,1,7,17,null,null,null,null,null,null,null,4,50,13,null,null,null,9,1,null,1,74,48,null,null,33,1,null,14,null,1,1,null,1,1,1,null,null,null,null,null,null,null,null,33,6,null,1,null,21,null,null,null,31,null,null,1,null,null,null,null,null,null,5,1,null,74,36,null,9,null,8,8,null,57,null,null,null,null,46,23,1,null,1,null,1,92,1,1,1,null,null,1,1,null,1,18,null,8,null,null,null,null,13,null,null,null,null,27,null,18,83,8,8,8,7,1,null,null,null,null,null,1,null,1,null,112,null,null,null,null,63,1,5,1,null,null,null,null,null,67,18,null,1,77,1,5,1,8,null,1,1,null,3,30,59,null,null,41,null,null,1,null,1,null,26,1,null,17,null,1,8,null,54,null,null,null,null,17,null,null,null,null,1,null,null,null,null,null,null,1,null,null,null,72,1,1,null,48,null,null,null,10,null,null,null,1,null,null,null,null,30,null,null,14,null,null,7,null,null,null,null,null,34,null,137,null,94,null,null,null,null,null,14,null,12,null,null,1,16,1,null,137,36,null,13,null,20,1,13,null,8,null,null],[20,1,null,11,null,64,null,null,null,null,null,34,null,57,1,null,null,null,null,4,4,null,null,null,8,null,21,1,null,27,17,29,19,27,1,68,null,40,143,15,null,8,3,null,7,null,null,28,null,null,1,null,null,44,18,1,null,null,null,null,null,null,42,null,null,1,null,null,null,null,31,null,null,null,null,null,8,11,1,null,null,null,null,null,null,79,null,79,null,null,null,10,null,null,10,null,null,1,null,null,null,1,null,null,16,1,null,null,null,null,null,null,80,null,null,10,null,7,6,23,null,null,70,null,null,1,7,null,9,null,6,null,null,96,null,1,null,null,null,null,null,13,null,null,22,1,null,null,21,null,null,42,1,24,null,null,null,null,null,null,null,null,null,14,null,null,null,null,21,null,18,null,null,17,null,null,null,2,2,null,null,null,18,1,null,80,71,6,null,13,1,null,83,null,null,null,1,null,null,7,null,null,112,null,null,31,null,null,7,null,null,28,null,null,null,71,1,null,33,1,185,16,13,null,null,null,null,null,null,null,13,null,1,36,null,null,5,4,null,14,18,1,null,null,1,null,null,9,21,null,null,9,null,null,null,null,1,1,32,35,null,null,1,1,null,null,null,1,null,null,null,5,8,null,10,null,28,33,9,null,null,1,null,null,10,null,1,17,null,43,null,34,null,26,null,null,1,null,null,11,null,11,null,null,null,null,null,null,null,1,1,1,null,null,null,12,null,null,6,null,null,null,null,1,14,1,3,null,1,null,null,null,null,1,1,null,null,null,null,null,null,11,null,86,null,null,1,null,null,null,44,null,44,4,null,16,null,21,27,null,null,null,1,null,null,null,10,null,null,null,null,null,null,null,8,null,1,25,null,null,null,20,null,null,16,5,null,1,null,null,1,null,105,null,23,24,null,null,1,23,null,null,null,null,null,27,1,null,16,null,13,null,165,1,15,1,15,null,null,1,null,null,null,1,null,null,1,20,27,null,1,36,null,8,10,null,13,null,null,15,8,null,null,null,1,14,null,25,null,null,null,null,null,null,null,null,99,null,1,1,102,108,15,1,7,17,null,null,null,null,null,null,null,4,49,10,null,null,null,9,1,null,1,73,48,null,null,33,1,null,14,null,1,1,null,1,1,1,null,null,null,null,null,null,null,null,null,6,null,1,null,21,null,null,null,null,null,null,1,null,null,null,null,null,null,5,1,null,73,36,null,9,null,8,8,null,57,null,null,null,null,46,23,1,null,1,null,1,88,1,1,1,null,null,1,1,null,1,18,null,8,null,null,null,null,13,null,null,null,null,24,null,18,83,8,8,8,7,1,null,null,null,null,null,1,null,1,null,112,null,null,null,null,null,1,5,1,null,null,null,null,null,59,18,null,1,74,1,5,1,8,null,1,1,null,3,30,59,null,null,31,null,null,1,null,1,null,22,1,null,17,null,1,8,null,45,null,null,null,null,17,null,null,null,null,1,null,null,null,null,null,null,1,null,null,null,55,1,1,null,47,null,null,null,10,null,null,null,1,null,null,null,null,26,null,null,14,null,null,7,null,null,null,null,null,34,null,132,null,null,null,null,null,null,null,5,null,12,null,null,1,14,1,null,137,36,null,13,null,20,1,11,null,8,null,null],[null,1,null,11,null,64,null,null,null,null,null,34,null,55,1,null,null,null,null,null,4,null,null,null,null,null,null,1,null,null,null,29,19,null,1,null,null,40,118,15,null,8,null,null,6,null,null,null,null,null,1,null,null,44,null,1,null,null,null,null,null,null,null,null,null,1,null,null,null,null,null,null,null,null,null,null,8,null,1,null,null,null,null,null,null,77,null,77,null,null,null,null,null,null,10,null,null,null,null,null,null,1,null,null,null,1,null,null,null,null,null,44,80,null,null,null,null,7,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,96,null,1,null,null,null,null,null,null,null,null,null,1,null,null,null,null,null,42,1,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,21,null,18,null,null,null,null,null,null,null,null,null,null,null,18,1,null,80,71,6,null,13,1,null,83,null,null,null,1,null,null,null,null,null,null,null,null,31,null,38,null,null,null,23,null,null,null,71,null,null,null,1,155,null,13,null,null,null,null,null,null,null,null,null,null,52,null,null,5,4,null,null,18,1,null,null,1,null,null,null,null,null,null,null,null,null,null,null,1,1,null,35,null,null,1,1,null,null,null,1,null,null,null,5,8,null,10,null,28,null,null,null,null,1,null,null,10,null,1,16,null,null,null,34,null,26,null,null,1,null,null,11,null,10,null,null,null,null,null,null,null,1,1,1,null,null,null,12,null,null,6,null,null,null,null,1,14,1,3,null,1,null,null,null,null,1,1,null,null,null,null,null,null,null,null,86,null,null,1,null,null,null,44,null,44,6,null,null,null,null,null,null,null,null,1,null,null,null,10,null,null,null,null,null,null,null,null,null,1,null,null,null,null,18,null,null,16,null,null,1,null,null,1,null,120,null,23,null,null,null,null,null,null,null,null,null,null,27,1,null,16,null,null,null,null,1,null,1,null,null,null,1,null,null,null,null,null,null,1,null,27,null,1,36,null,null,null,null,null,null,null,15,null,null,null,null,1,14,null,29,null,null,null,null,null,null,null,null,null,null,1,1,null,138,15,1,null,17,null,null,null,null,null,null,null,4,null,null,null,null,null,null,1,null,null,null,48,null,null,null,1,null,null,null,1,1,null,1,1,1,null,null,null,null,null,null,null,null,null,6,null,1,null,21,null,null,null,null,null,null,null,null,null,null,null,null,null,null,1,null,69,29,null,9,null,8,8,null,null,null,null,null,null,46,23,1,null,1,null,1,88,1,1,1,null,null,1,1,null,1,18,null,null,null,null,null,null,null,null,null,null,null,null,null,18,null,8,8,8,7,null,null,null,null,null,null,null,null,1,null,112,null,null,null,null,null,1,5,1,null,null,null,null,null,55,18,null,1,72,1,5,1,null,null,1,1,null,3,30,59,null,null,24,null,null,1,null,1,null,null,1,null,17,null,null,null,null,null,null,null,null,null,17,null,null,null,null,null,null,null,null,null,null,null,1,null,null,null,null,1,1,null,46,null,null,null,10,null,null,null,1,null,null,null,null,null,null,null,null,null,null,7,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,12,null,null,1,11,1,null,137,null,null,13,null,null,1,null,null,null,null,null],[20,1,null,10,null,72,null,null,null,null,null,34,null,63,1,null,null,null,null,4,null,null,null,null,null,null,null,null,null,null,18,null,15,19,null,null,null,40,135,15,null,null,null,1,9,null,null,16,null,null,null,null,null,45,17,null,null,null,null,null,null,null,39,null,null,1,null,null,null,null,null,null,null,null,null,null,8,16,1,null,null,null,null,null,null,76,null,76,null,1,null,8,null,null,10,null,null,null,null,null,null,1,null,null,null,1,24,null,null,41,null,41,81,null,null,null,null,7,null,25,null,null,null,null,null,1,null,null,5,null,8,null,null,null,null,1,null,null,null,null,null,11,null,null,15,1,null,null,null,null,null,14,null,19,null,null,null,null,null,null,null,null,null,null,null,null,null,null,23,null,11,null,null,13,null,null,null,null,null,null,null,null,null,1,null,88,64,5,null,11,null,null,37,null,null,null,1,null,null,null,null,null,110,null,null,18,null,37,null,null,null,27,46,null,null,null,null,null,30,1,364,14,12,null,null,null,null,null,null,null,18,null,1,null,null,null,6,4,null,14,null,null,null,null,null,null,null,null,21,null,null,24,null,null,null,null,1,1,24,22,null,null,1,1,null,null,null,1,null,null,null,null,11,null,9,null,null,15,9,null,null,1,null,null,9,null,1,null,null,null,null,34,null,125,null,null,1,null,null,null,null,24,null,null,null,null,null,null,null,1,1,null,null,null,null,12,null,null,6,null,null,null,null,1,null,1,null,null,null,null,null,null,null,1,1,null,null,null,null,null,null,8,null,81,null,null,null,null,null,null,null,null,29,8,null,13,null,23,26,null,null,null,null,null,null,null,10,null,null,null,null,null,null,null,7,null,null,25,null,null,null,26,null,null,16,5,null,1,null,null,null,null,139,null,24,13,null,null,1,25,null,null,null,null,null,null,1,null,16,null,15,null,null,null,null,null,15,null,null,1,null,null,null,1,null,null,1,null,21,null,1,34,null,8,9,null,35,null,null,15,10,null,null,null,1,14,null,30,null,17,null,null,null,null,null,null,113,null,1,1,117,117,9,1,7,17,null,null,null,null,null,null,null,null,38,12,null,null,null,8,1,null,1,74,5,null,null,null,1,null,13,null,1,1,null,1,null,1,null,null,null,null,null,null,null,null,33,6,null,1,null,null,null,null,null,31,null,null,null,null,null,null,null,null,null,6,1,null,74,33,null,9,null,null,null,null,null,null,null,null,null,45,23,1,null,1,null,null,96,null,null,1,null,null,null,null,null,1,14,null,null,null,null,null,null,13,null,null,null,null,null,null,null,null,null,null,null,null,1,null,null,null,null,null,1,null,1,null,104,null,null,null,null,65,null,null,1,null,null,null,null,null,61,18,null,null,78,1,null,1,4,null,1,null,null,null,28,30,null,null,45,null,null,null,null,null,null,26,null,null,15,null,null,null,null,51,null,null,null,null,13,null,null,null,null,1,null,null,null,null,null,null,1,null,null,null,null,null,null,null,48,null,null,null,null,null,null,null,1,null,null,null,null,33,null,null,14,null,null,null,null,null,null,null,null,null,null,141,null,106,null,null,null,null,null,null,null,12,null,null,1,16,null,null,null,null,null,null,null,null,1,15,null,7,null,null],[20,1,null,10,null,61,null,null,null,null,null,34,null,59,1,null,null,null,null,4,null,null,null,null,null,null,null,null,null,null,18,null,15,19,null,null,null,40,142,15,null,null,null,null,9,null,null,16,null,null,null,null,null,45,17,null,null,null,null,null,null,null,39,null,null,1,null,null,null,null,null,null,null,null,null,null,8,12,1,null,null,null,null,null,null,67,null,67,null,null,null,8,null,null,10,null,null,null,null,null,null,1,null,null,null,1,null,null,null,null,null,null,81,null,null,null,null,7,null,25,null,null,null,null,null,1,null,null,5,null,8,null,null,null,null,1,null,null,null,null,null,11,null,null,14,1,null,null,null,null,null,14,null,19,null,null,null,null,null,null,null,null,null,null,null,null,null,null,23,null,11,null,null,13,null,null,null,null,null,null,null,null,null,1,null,88,64,5,null,11,null,null,37,null,null,null,1,null,null,null,null,null,110,null,null,18,null,null,null,null,null,27,null,null,null,null,null,null,27,1,388,14,12,null,null,null,null,null,null,null,18,null,1,null,null,null,6,4,null,14,null,null,null,null,null,null,null,null,21,null,null,null,null,null,null,null,1,1,20,22,null,null,1,1,null,null,null,1,null,null,null,null,11,null,9,null,null,15,9,null,null,1,null,null,9,null,1,null,null,null,null,34,null,125,null,null,1,null,null,null,null,12,null,null,null,null,null,null,null,1,1,null,null,null,null,12,null,null,6,null,null,null,null,1,null,1,null,null,null,null,null,null,null,1,1,null,null,null,null,null,null,8,null,81,null,null,null,null,null,null,null,null,27,4,null,13,null,23,26,null,null,null,null,null,null,null,10,null,null,null,null,null,null,null,7,null,null,25,null,null,null,24,null,null,16,5,null,1,null,null,null,null,110,null,24,13,null,null,1,25,null,null,null,null,null,null,1,null,16,null,9,null,null,null,null,null,15,null,null,1,null,null,null,1,null,null,1,null,21,null,1,33,null,8,9,null,35,null,null,15,10,null,null,null,1,14,null,26,null,null,null,null,null,null,null,null,108,null,1,1,99,99,12,1,7,17,null,null,null,null,null,null,null,null,39,10,null,null,null,8,1,null,1,74,5,null,null,null,1,null,13,null,1,1,null,1,null,1,null,null,null,null,null,null,null,null,null,6,null,1,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,6,1,null,74,30,null,9,null,null,null,null,null,null,null,null,null,45,23,1,null,1,null,null,94,null,null,1,null,null,null,null,null,1,14,null,null,null,null,null,null,13,null,null,null,null,null,null,null,null,null,null,null,null,1,null,null,null,null,null,1,null,1,null,104,null,null,null,null,null,null,null,1,null,null,null,null,null,55,18,null,null,77,1,null,1,4,null,1,null,null,null,28,30,null,null,45,null,null,null,null,null,null,23,null,null,15,null,null,null,null,46,null,null,null,null,13,null,null,null,null,1,null,null,null,null,null,null,1,null,null,null,null,null,null,null,47,null,null,null,null,null,null,null,1,null,null,null,null,31,null,null,14,null,null,null,null,null,null,null,null,null,null,120,null,null,null,null,null,null,null,null,null,12,null,null,1,13,null,null,null,null,null,null,null,null,1,10,null,7,null,null],[null,1,null,10,null,61,null,null,null,null,null,34,null,49,1,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,40,109,15,null,null,null,null,null,null,null,null,null,null,null,null,null,45,null,null,null,null,null,null,null,null,null,null,null,1,null,null,null,null,null,null,null,null,null,null,8,null,1,null,null,null,null,null,null,59,null,59,null,null,null,null,null,null,10,null,null,null,null,null,null,1,null,null,null,1,null,null,null,null,null,41,81,null,null,null,null,7,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,1,null,null,null,null,null,null,null,null,null,1,null,null,null,null,null,14,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,23,null,11,null,null,null,null,null,null,null,null,null,null,null,null,1,null,88,64,5,null,11,null,null,37,null,null,null,1,null,null,null,null,null,null,null,null,18,null,37,null,null,null,23,null,null,null,null,null,null,null,1,438,null,12,null,null,null,null,null,null,null,null,null,null,null,null,null,6,4,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,1,null,null,22,null,null,null,1,null,null,null,1,null,null,null,null,11,null,9,null,null,null,null,null,null,1,null,null,9,null,1,null,null,null,null,34,null,125,null,null,1,null,null,null,null,12,null,null,null,null,null,null,null,1,1,null,null,null,null,12,null,null,6,null,null,null,null,1,null,1,null,null,null,null,null,null,null,1,1,null,null,null,null,null,null,null,null,81,null,null,null,null,null,null,null,null,null,5,null,null,null,null,null,null,null,null,null,null,null,null,10,null,null,null,null,null,null,null,null,null,null,null,null,null,null,24,null,null,16,null,null,1,null,null,null,null,125,null,null,null,null,null,null,null,null,null,null,null,null,null,1,null,16,null,null,null,null,null,null,null,null,null,null,1,null,null,null,null,null,null,1,null,21,null,1,33,null,null,null,null,null,null,null,15,null,null,null,null,1,14,null,null,null,null,null,null,null,null,null,null,null,null,1,1,null,128,null,1,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,1,null,null,null,5,null,null,null,1,null,null,null,1,1,null,1,null,1,null,null,null,null,null,null,null,null,null,6,null,1,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,1,null,73,25,null,9,null,null,null,null,null,null,null,null,null,45,23,1,null,1,null,null,92,null,null,1,null,null,null,null,null,1,14,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,1,null,104,null,null,null,null,null,null,null,1,null,null,null,null,null,46,18,null,null,76,1,null,1,null,null,1,null,null,null,28,30,null,null,44,null,null,null,null,null,null,null,null,null,15,null,null,null,null,null,null,null,null,null,13,null,null,null,null,null,null,null,null,null,null,null,1,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,1,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,12,null,null,1,11,null,null,null,null,null,null,null,null,1,null,null,null,null,null],[0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0],[0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>paper_id<\/th>\n      <th>scs_uoa_1<\/th>\n      <th>scs_uoa_2<\/th>\n      <th>scs_uoa_3<\/th>\n      <th>scs_uoa_4<\/th>\n      <th>scs_uoa_5<\/th>\n      <th>scs_uoa_design<\/th>\n      <th>group_1n_phase_1<\/th>\n      <th>group_1n_phase_2<\/th>\n      <th>group_1n_phase_3<\/th>\n      <th>group_2n_phase_1<\/th>\n      <th>group_2n_phase_2<\/th>\n      <th>group_2n_phase_3<\/th>\n      <th>scs_rgr_dv1_type_1<\/th>\n      <th>scs_rgr_dv1_type_2<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"scrollX":true,"columnDefs":[{"className":"dt-right","targets":[2,3,4,5,6,7,8,9,10,11,12,13,14,15]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false}},"evals":[],"jsHooks":[]}</script>






# Row Rules

1. Have deliberate missing data codes:
    + Using -99, 99, -9999, N/A are problematic
    + NA is a good option
2. No calculations in the data file
3. Use ISO 8601 standard for dates YYYY-MM-DD (https://xkcd.com/1179/)
    + Particularly needed when using Excel
4. Don't use highlighting as data
    + TRUE/FALSE attributes can be helpful here





# Date Conversion Excel

![](/figs/date-convert.gif)




# Highlighting Cells

![](/figs/data-highlighting.gif)




# Split-Apply-Combine

- Process of splitting a hard task into smaller manageable tasks
- This framework is particularly powerful in functional programming languages, like R, Python, Julia, Scala, Mathematica, Javascript, etc.
- Split-Apply-Combine in Data Analysis
    + Split observations into similar type
    + Apply a function (ie, often a computation)
    + Combine function results across observations




# Synthesis of Correlation Matrices

- One particular way to implement of tidy meta analytic data is the synthesis of correlation matrices.
- See *Meta-Analysis of Correlations, Correlation Matrices, and Their Functions* by Becker, Aloe, Cheung (2020) in Handbook of Meta-Analysis
- We will use an R package developed in tandem with this chapter, `metaRmat`.




# Install `metaRmat`
```r
remotes::install_github("lebebr01/metaRmat")
```

```r
library(metaRmat)
```




# Correlation Data Example

```r
becker09[, 1:6]
```

```
##    ID   N Team Cognitive_Performance Somatic_Performance
## 1   1 142    I                 -0.55               -0.48
## 2   3  37    I                  0.53               -0.12
## 3   6  16    T                  0.44                0.46
## 4  10  14    I                 -0.39               -0.17
## 5  17  45    I                  0.10                0.31
## 6  22 100    I                  0.23                0.08
## 7  26  51    T                 -0.52               -0.43
## 8  28 128    T                  0.14                0.02
## 9  36  70    T                 -0.01               -0.16
## 10 38  30    I                 -0.27               -0.13
##    Selfconfidence_Performance
## 1                        0.66
## 2                        0.03
## 3                          NA
## 4                        0.19
## 5                       -0.17
## 6                        0.51
## 7                        0.16
## 8                        0.13
## 9                        0.42
## 10                       0.15
```




# Split Correlation Matrices


```r
becker09_list <- df_to_corr(becker09, 
                           variables = 
                             c('Cognitive_Performance',
                               'Somatic_Performance',
                               'Selfconfidence_Performance', 
                               'Somatic_Cognitive',
                               'Selfconfidence_Cognitive',
                               'Selfconfidence_Somatic'),
                           ID = 'ID')
```




# View Split Correlation Matrices

```r
becker09_list[1:3]
```

```
## $`1`
##                Performance Cognitive Somatic Selfconfidence
## Performance           1.00     -0.55   -0.48           0.66
## Cognitive            -0.55      1.00    0.47          -0.38
## Somatic              -0.48      0.47    1.00          -0.46
## Selfconfidence        0.66     -0.38   -0.46           1.00
## 
## $`3`
##                Performance Cognitive Somatic Selfconfidence
## Performance           1.00      0.53   -0.12           0.03
## Cognitive             0.53      1.00    0.52          -0.48
## Somatic              -0.12      0.52    1.00          -0.40
## Selfconfidence        0.03     -0.48   -0.40           1.00
## 
## $`6`
##                Performance Cognitive Somatic Selfconfidence
## Performance           1.00      0.44    0.46             NA
## Cognitive             0.44      1.00    0.67             NA
## Somatic               0.46      0.67    1.00             NA
## Selfconfidence          NA        NA      NA              1
```




# Correlations as Tidy Meta Analytic Data

```r
input_metafor <- prep_data(becker09, 
                           becker09$N, 
                           type = 'weighted', missing = FALSE, 
                           variable_names =
                             c('Cognitive_Performance',
                               'Somatic_Performance',
                               'Selfconfidence_Performance', 
                               'Somatic_Cognitive',
                               'Selfconfidence_Cognitive',
                               'Selfconfidence_Somatic'),
                           ID = 'ID')
```




# View Tidy Meta Analytic Correlations


```r
head(input_metafor$data, n = 15)
```

```
##      Variable1      Variable2    yi outcome study
## 1  Performance      Cognitive -0.55       1     1
## 2  Performance        Somatic -0.48       2     1
## 3  Performance Selfconfidence  0.66       3     1
## 4    Cognitive        Somatic  0.47       4     1
## 5    Cognitive Selfconfidence -0.38       5     1
## 6      Somatic Selfconfidence -0.46       6     1
## 7  Performance      Cognitive  0.53       1     2
## 8  Performance        Somatic -0.12       2     2
## 9  Performance Selfconfidence  0.03       3     2
## 10   Cognitive        Somatic  0.52       4     2
## 11   Cognitive Selfconfidence -0.48       5     2
## 12     Somatic Selfconfidence -0.40       6     2
## 13 Performance      Cognitive  0.44       1     3
## 14 Performance        Somatic  0.46       2     3
## 15 Performance Selfconfidence    NA       3     3
```




# Fit a random effects meta analytic model


```r
random_model <- fit_model(data = input_metafor, effect_size = 'yi', 
                          var_cor = 'V', moderators = ~ -1 + factor(outcome), 
                          random_params = ~ factor(outcome) | factor(study))
```

```
## Warning: Rows with NAs omitted from model fitting.
```

```r
round(random_model$tau2, 3) # between studies variance 
```

```
## [1] 0.126 0.060 0.062 0.002 0.011 0.006
```

```r
round(random_model$b, 3) # random effect estimate
```

```
##                    [,1]
## factor(outcome)1 -0.034
## factor(outcome)2 -0.071
## factor(outcome)3  0.233
## factor(outcome)4  0.544
## factor(outcome)5 -0.453
## factor(outcome)6 -0.397
```




# Average correlation matrix


```r
model_out_random <- extract_model(random_model, 
                                  variable_names = c('Cognitive_Performance',
                                                     'Somatic_Performance',
                                                     'Selfconfidence_Performance', 
                                                     'Somatic_Cognitive',
                                                     'Selfconfidence_Cognitive',
                                                     'Selfconfidence_Somatic'))
round(model_out_random$beta_matrix, 3)
```

```
##                Performance Cognitive Somatic Selfconfidence
## Performance          1.000    -0.034  -0.071          0.233
## Cognitive           -0.034     1.000   0.544         -0.453
## Somatic             -0.071     0.544   1.000         -0.397
## Selfconfidence       0.233    -0.453  -0.397          1.000
```




# Fit path model

```r
model <- "## Regression paths
Performance ~ Cognitive + Somatic + Selfconfidence
Selfconfidence ~ Cognitive + Somatic
"
path_output <- path_model(data = model_out_random, model = model, 
                          num_obs = sum(becker09$N))
```




# Extract some results

```r
path_output$parameter_estimates
```

```
## [[1]]
##                                    predictor     outcome    estimate
## Cognitive -> Performance           Cognitive Performance  0.09757045
## Somatic -> Performance               Somatic Performance -0.01663048
## Selfconfidence -> Performance Selfconfidence Performance  0.27041818
## 
## [[2]]
##                             predictor        outcome   estimate
## Cognitive -> Selfconfidence Cognitive Selfconfidence -0.3359884
## Somatic -> Selfconfidence     Somatic Selfconfidence -0.2146362
```




# Summary

- Be mindful and plan for data entry - this is hard!
- Do not assume that data entry will "take care of itself"
- Think "long" instead of wide
- Ensure attributes contain one piece of information
- Ensure attributes are named well, but do not contain information directly
- Use text based or database systems rather than Excel




# Connect
- slides: https://brandonlebeau.org/slides/canam2021/
- twitter: blebeau11
