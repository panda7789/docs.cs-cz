---
title: "IMetaDataImport – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport
helpviewer_keywords: IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 0adbbd35-5e8d-4fec-8268-dc70a07c5975
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6c7f1c7e99df61cc0cd33e1697de52a039d412df
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimport-interface"></a>IMetaDataImport – rozhraní
Poskytuje metody pro import a manipulace s existující metadat ze souboru přenosné spustitelný soubor (PE) nebo jiný zdroj, například knihovny typů nebo binární samostatnou, běhu metadat.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Closeenum – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-closeenum-method.md)|Zavře čítač s Zadaný popisovač.|  
|[Countenum – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-countenum-method.md)|Získá počet elementů v enumerátor s Zadaný popisovač.|  
|[Enumcustomattributes – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md)|Zobrazí seznam vlastní definice atributu tokeny spojených s zadaný typ nebo člen.|  
|[Enumevents – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumevents-method.md)|Vytvoří výčet událostí definice tokeny pro zadaný token TypeDef.|  
|[Enumfields – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md)|Vytvoří výčet FieldDef tokeny pro typ, který odkazuje zadaný token TypeDef.|  
|[Enumfieldswithname – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfieldswithname-method.md)|Vytvoří výčet FieldDef tokeny zadaného typu se zadaným názvem.|  
|[Enuminterfaceimpls – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enuminterfaceimpls-method.md)|Vytvoří výčet MethodDef tokeny představující implementace rozhraní.|  
|[Enummemberrefs – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummemberrefs-method.md)|Vytvoří výčet MemberRef tokeny představující členů zadaného typu.|  
|[Enummembers – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md)|Vytvoří výčet MemberDef tokeny představující členů zadaného typu.|  
|[Enummemberswithname – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummemberswithname-method.md)|Vytvoří výčet MemberDef tokeny představující členů zadaného typu se zadaným názvem.|  
|[Enummethodimpls – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodimpls-method.md)|Vytvoří výčet MethodBody a MethodDeclaration tokenů představující metody zadaného typu.|  
|[Enummethods – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md)|Vytvoří výčet MethodDef tokeny představující metody zadaného typu.|  
|[Enummethodsemantics – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodsemantics-method.md)|Vytvoří výčet vlastností a změnu vlastnosti události, ke kterým je související zadanou metodu.|  
|[Enummethodswithname – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodswithname-method.md)|Vytvoří výčet metod, které jsou definovány podle typu, který odkazuje zadaný token TypeDef, které mají zadaný název.|  
|[Enummodulerefs – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummodulerefs-method.md)|Vytvoří výčet Odkaz ModuleRef tokeny, které představují importovaných modulů.|  
|[Enumparams – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumparams-method.md)|Vytvoří výčet představující parametry metody odkazuje zadaný token MethodDef tokeny ParamDef.|  
|[Enumpermissionsets – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumpermissionsets-method.md)|Vytvoří výčet oprávnění pro objekty v oboru Zadaná metadata.|  
|[Enumproperties – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumproperties-method.md)|Vytvoří výčet představující vlastnosti typu odkazuje zadaný token TypeDef tokeny vlastnosti.|  
|[Enumsignatures – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumsignatures-method.md)|Vytvoří výčet podpis tokeny představující samostatné podpisy v aktuálním oboru.|  
|[Enumtypedefs – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)|Vytvoří výčet TypeDef tokeny představující všechny typy v aktuálním oboru.|  
|[Enumtyperefs – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtyperefs-method.md)|Vytvoří výčet Odkaz TypeRef tokeny definované v aktuálním oboru metadat.|  
|[Enumtypespecs – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypespecs-method.md)|Zobrazí typ TypeSpec tokeny definované v aktuálním oboru metadat.|  
|[Enumunresolvedmethods – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumunresolvedmethods-method.md)|Vytvoří výčet MemberDef tokeny představující nerozpoznané metody v aktuálním oboru metadat.|  
|[Enumuserstrings – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumuserstrings-method.md)|Vytvoří výčet tokeny řetězec představující pevně řetězce v aktuálním oboru metadat.|  
|[Findfield – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md)|Získá token FieldDef pole, která je členem zadaný typ a má zadaný název a podpis metadat.|  
|[Findmember – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmember-method.md)|Získá ukazatel na MemberDef token pro člena definované zadaný typ se zadaným názvem a podpis metadat.|  
|[Findmemberref – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmemberref-method.md)|Získá ukazatel na MemberRef token pro člena definované zadaný typ se zadaným názvem a podpis metadat.|  
|[Findmethod – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md)|Získá ukazatel na MethodDef token pro metodu definované zadaný typ se zadaným názvem a podpis metadat.|  
|[Findtypedefbyname – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findtypedefbyname-method.md)|Získá ukazatel k metadatům TypeDef token pro typ se zadaným názvem.|  
|[Findtyperef – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findtyperef-method.md)|Získá ukazatel na odkaz TypeRef metadata token, který odkazuje na typ v oboru zadaný hledaný se zadaným názvem.|  
|[Getclasslayout – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md)|Získá informace o třídě odkazuje zadaný TypeDef rozložení token.|  
|[Getcustomattributebyname – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getcustomattributebyname-method.md)|Získá hodnotu vlastních atributů, jeho název.|  
|[Getcustomattributeprops – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getcustomattributeprops-method.md)|Získá hodnotu atributu vlastní zadaný token jeho metadata.|  
|[Geteventprops – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-geteventprops-method.md)|Získá informace o metadatech (včetně deklarující typ přidat a odebrat metody pro Delegáti a všechny příznaky a další související data) pro událost reprezentována token zadané události.|  
|[Getfieldmarshal – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getfieldmarshal-method.md)|Získá ukazatel na nativní, nespravovaný typ pole reprezentována zadaný token metadata pole.|  
|[Getfieldprops – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getfieldprops-method.md)|Získá metadata spojená s polem odkazuje zadaný FieldDef token.|  
|[Getinterfaceimplprops – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getinterfaceimplprops-method.md)|Získá ukazatel na tokeny metadata pro typ, který implementuje zadanou metodu a rozhraní, který deklaruje, že metoda.|  
|[Getmemberprops – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmemberprops-method.md)|Získá informace metadat (včetně názvu, binární podpisu a relativní virtuální adresy) člena typu odkazuje token Zadaná metadata.|  
|[Getmemberrefprops – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmemberrefprops-method.md)|Získá metadata spojených se členem odkazuje zadaný token.|  
|[Getmethodprops – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmethodprops-method.md)|Získá metadata přidružená metoda odkazuje zadaný MethodDef token.|  
|[Getmethodsemantics – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmethodsemantics-method.md)|Získá ukazatel na vztah mezi metoda odkazuje zadaný token MethodDef a spárované vlastnosti a události odkazuje zadaný EventProp token.|  
|[Getmodulefromscope – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmodulefromscope-method.md)|Získá ukazatel k metadatům token pro modul odkazuje v aktuálním oboru metadat.|  
|[Getmodulerefprops – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmodulerefprops-method.md)|Získá název modulu odkazuje token Zadaná metadata.|  
|[Getnamefromtoken – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnamefromtoken-method.md)|Získá název znakové sady UTF-8 objektu odkazuje token Zadaná metadata.|  
|[Getnativecallconvfromsig – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnativecallconvfromsig-method.md)|Získá nativního konvence volání pro metodu, která je reprezentována Zadaný podpis ukazatele.|  
|[Getnestedclassprops – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnestedclassprops-method.md)|Získá token TypeDef pro nadřazených nadřazený typ vnořené zadaného typu.|  
|[Getparamformethodindex – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getparamformethodindex-method.md)|Získá ukazatel na token, který představuje parametr v zadané pořadové číslo pozice v pořadí parametrů metody pro metodu reprezentovanou zadaný token MethodDef.|  
|[Getparamprops – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getparamprops-method.md)|Získá metadata hodnoty pro parametr odkazuje zadaný ParamDef token.|  
|[Getpermissionsetprops – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpermissionsetprops-method.md)|Získá metadata přidružená System.Security.PermissionSet reprezentována zadaný token oprávnění.|  
|[Getpinvokemap –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpinvokemap-method.md)|Získá odkaz ModuleRef token představující cíl sestavení volání PInvoke.|  
|[Getpropertyprops – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpropertyprops-method.md)|Získá metadata přidružená vlastnost reprezentována zadaný token.|  
|[Getrva – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getrva-method.md)|Získá posun relativní virtuální adresy kód objekt reprezentovaný rozhraním zadaný token.|  
|[Getscopeprops – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md)|Získá název a volitelně identifikátor verze sestavení nebo modul v aktuálním oboru metadat.|  
|[Getsigfromtoken – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getsigfromtoken-method.md)|Získá podpis binární metadata související s zadaný token.|  
|[Gettypedefprops – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettypedefprops-method.md)|Vrátí informace metadat pro typu představovaný typem zadaný token TypeDef.|  
|[Gettyperefprops – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettyperefprops-method.md)|Získá metadata spojená s typem odkazuje zadaný odkaz TypeRef token.|  
|[Gettypespecfromtoken – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettypespecfromtoken-method.md)|Získá podpis binární metadat specifikace typu reprezentována zadaný token.|  
|[Getuserstring – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getuserstring-method.md)|Získá reprezentována Zadaná metadata token řetězcového literálu.|  
|[Isglobal – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-isglobal-method.md)|Získá hodnotu označující, zda pole, metoda nebo typu představovaný typem Zadaná metadata token má globální obor.|  
|[Isvalidtoken – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-isvalidtoken-method.md)|Získá hodnotu označující, zda zadaný token obsahuje neplatný odkaz na objekt kódu.|  
|[Resetenum – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-resetenum-method.md)|Zadaný čítač obnoví na zadané pozici.|  
|[Resolvetyperef – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-resolvetyperef-method.md)|Získá typ informace pro typ, který odkazuje zadaný odkaz TypeRef token.|  
  
## <a name="remarks"></a>Poznámky  
 Návrh `IMetaDataImport` rozhraní je určena především pro použití pomocí nástroje a služby, které bude import informací o typu (například nástroje pro vývoj) nebo Správa nasazení součásti (například řešení nebo aktivace služby). Metody v `IMetaDataImport` spadají do následujících kategorií úloh:  
  
-   Vytváření výčtů kolekcí položek v oboru metadat.  
  
-   Hledání položku, která obsahuje konkrétní sadu vlastností.  
  
-   Získávání vlastnosti zadané položky.  
  
-   Metody Get jsou navrženy speciálně vrátit jednou hodnotou vlastnosti položky metadat. Když vlastnost je odkaz na další položku, se vrátí token pro danou položku. Všechny vstupní typ ukazatele může mít hodnotu NULL k označení, že není požadováno pro dané hodnoty. K získání vlastností, které jsou v podstatě kolekci objektů (například kolekce rozhraní, která implementuje třídu), použijte metodu výčtu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní metadat](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [Imetadataimport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
