---
title: IMetaDataImport – rozhraní
ms.date: 03/30/2017
api_name:
- IMetaDataImport
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport
helpviewer_keywords:
- IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 0adbbd35-5e8d-4fec-8268-dc70a07c5975
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fdea4c456f04911c37acd69ced65ba841f7959ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449348"
---
# <a name="imetadataimport-interface"></a>IMetaDataImport – rozhraní
Poskytuje metody pro import a manipulace s existující metadat ze souboru přenosné spustitelný soubor (PE) nebo jiný zdroj, například knihovny typů nebo binární samostatnou, běhu metadat.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CloseEnum – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-closeenum-method.md)|Zavře čítač s Zadaný popisovač.|  
|[CountEnum – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-countenum-method.md)|Získá počet elementů v enumerátor s Zadaný popisovač.|  
|[EnumCustomAttributes – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md)|Zobrazí seznam vlastní definice atributu tokeny spojených s zadaný typ nebo člen.|  
|[EnumEvents – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumevents-method.md)|Vytvoří výčet událostí definice tokeny pro zadaný token TypeDef.|  
|[EnumFields – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md)|Vytvoří výčet FieldDef tokeny pro typ, který odkazuje zadaný token TypeDef.|  
|[EnumFieldsWithName – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfieldswithname-method.md)|Vytvoří výčet FieldDef tokeny zadaného typu se zadaným názvem.|  
|[EnumInterfaceImpls – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enuminterfaceimpls-method.md)|Vytvoří výčet MethodDef tokeny představující implementace rozhraní.|  
|[EnumMemberRefs – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummemberrefs-method.md)|Vytvoří výčet MemberRef tokeny představující členů zadaného typu.|  
|[EnumMembers – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md)|Vytvoří výčet MemberDef tokeny představující členů zadaného typu.|  
|[EnumMembersWithName – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummemberswithname-method.md)|Vytvoří výčet MemberDef tokeny představující členů zadaného typu se zadaným názvem.|  
|[EnumMethodImpls – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodimpls-method.md)|Vytvoří výčet MethodBody a MethodDeclaration tokenů představující metody zadaného typu.|  
|[EnumMethods – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md)|Vytvoří výčet MethodDef tokeny představující metody zadaného typu.|  
|[EnumMethodSemantics – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodsemantics-method.md)|Vytvoří výčet vlastností a změnu vlastnosti události, ke kterým je související zadanou metodu.|  
|[EnumMethodsWithName – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodswithname-method.md)|Vytvoří výčet metod, které jsou definovány podle typu, který odkazuje zadaný token TypeDef, které mají zadaný název.|  
|[EnumModuleRefs – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummodulerefs-method.md)|Vytvoří výčet Odkaz ModuleRef tokeny, které představují importovaných modulů.|  
|[EnumParams – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumparams-method.md)|Vytvoří výčet představující parametry metody odkazuje zadaný token MethodDef tokeny ParamDef.|  
|[EnumPermissionSets – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumpermissionsets-method.md)|Vytvoří výčet oprávnění pro objekty v oboru Zadaná metadata.|  
|[EnumProperties – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumproperties-method.md)|Vytvoří výčet představující vlastnosti typu odkazuje zadaný token TypeDef tokeny vlastnosti.|  
|[EnumSignatures – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumsignatures-method.md)|Vytvoří výčet podpis tokeny představující samostatné podpisy v aktuálním oboru.|  
|[EnumTypeDefs – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)|Vytvoří výčet TypeDef tokeny představující všechny typy v aktuálním oboru.|  
|[EnumTypeRefs – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtyperefs-method.md)|Vytvoří výčet Odkaz TypeRef tokeny definované v aktuálním oboru metadat.|  
|[EnumTypeSpecs – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypespecs-method.md)|Zobrazí typ TypeSpec tokeny definované v aktuálním oboru metadat.|  
|[EnumUnresolvedMethods – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumunresolvedmethods-method.md)|Vytvoří výčet MemberDef tokeny představující nerozpoznané metody v aktuálním oboru metadat.|  
|[EnumUserStrings – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumuserstrings-method.md)|Vytvoří výčet tokeny řetězec představující pevně řetězce v aktuálním oboru metadat.|  
|[FindField – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md)|Získá token FieldDef pole, která je členem zadaný typ a má zadaný název a podpis metadat.|  
|[FindMember – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmember-method.md)|Získá ukazatel na MemberDef token pro člena definované zadaný typ se zadaným názvem a podpis metadat.|  
|[FindMemberRef – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmemberref-method.md)|Získá ukazatel na MemberRef token pro člena definované zadaný typ se zadaným názvem a podpis metadat.|  
|[FindMethod – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md)|Získá ukazatel na MethodDef token pro metodu definované zadaný typ se zadaným názvem a podpis metadat.|  
|[FindTypeDefByName – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findtypedefbyname-method.md)|Získá ukazatel k metadatům TypeDef token pro typ se zadaným názvem.|  
|[FindTypeRef – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findtyperef-method.md)|Získá ukazatel na odkaz TypeRef metadata token, který odkazuje na typ v oboru zadaný hledaný se zadaným názvem.|  
|[GetClassLayout – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md)|Získá informace o třídě odkazuje zadaný TypeDef rozložení token.|  
|[GetCustomAttributeByName – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getcustomattributebyname-method.md)|Získá hodnotu vlastních atributů, jeho název.|  
|[GetCustomAttributeProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getcustomattributeprops-method.md)|Získá hodnotu atributu vlastní zadaný token jeho metadata.|  
|[GetEventProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-geteventprops-method.md)|Získá informace o metadatech (včetně deklarující typ přidat a odebrat metody pro Delegáti a všechny příznaky a další související data) pro událost reprezentována token zadané události.|  
|[GetFieldMarshal – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getfieldmarshal-method.md)|Získá ukazatel na nativní, nespravovaný typ pole reprezentována zadaný token metadata pole.|  
|[GetFieldProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getfieldprops-method.md)|Získá metadata spojená s polem odkazuje zadaný FieldDef token.|  
|[GetInterfaceImplProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getinterfaceimplprops-method.md)|Získá ukazatel na tokeny metadata pro typ, který implementuje zadanou metodu a rozhraní, který deklaruje, že metoda.|  
|[GetMemberProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmemberprops-method.md)|Získá informace metadat (včetně názvu, binární podpisu a relativní virtuální adresy) člena typu odkazuje token Zadaná metadata.|  
|[GetMemberRefProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmemberrefprops-method.md)|Získá metadata spojených se členem odkazuje zadaný token.|  
|[GetMethodProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmethodprops-method.md)|Získá metadata přidružená metoda odkazuje zadaný MethodDef token.|  
|[GetMethodSemantics – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmethodsemantics-method.md)|Získá ukazatel na vztah mezi metoda odkazuje zadaný token MethodDef a spárované vlastnosti a události odkazuje zadaný EventProp token.|  
|[GetModuleFromScope – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmodulefromscope-method.md)|Získá ukazatel k metadatům token pro modul odkazuje v aktuálním oboru metadat.|  
|[GetModuleRefProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmodulerefprops-method.md)|Získá název modulu odkazuje token Zadaná metadata.|  
|[GetNameFromToken – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnamefromtoken-method.md)|Získá název znakové sady UTF-8 objektu odkazuje token Zadaná metadata.|  
|[GetNativeCallConvFromSig – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnativecallconvfromsig-method.md)|Získá nativního konvence volání pro metodu, která je reprezentována Zadaný podpis ukazatele.|  
|[GetNestedClassProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnestedclassprops-method.md)|Získá token TypeDef pro nadřazených nadřazený typ vnořené zadaného typu.|  
|[GetParamForMethodIndex – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getparamformethodindex-method.md)|Získá ukazatel na token, který představuje parametr v zadané pořadové číslo pozice v pořadí parametrů metody pro metodu reprezentovanou zadaný token MethodDef.|  
|[GetParamProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getparamprops-method.md)|Získá metadata hodnoty pro parametr odkazuje zadaný ParamDef token.|  
|[GetPermissionSetProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpermissionsetprops-method.md)|Získá metadata přidružená System.Security.PermissionSet reprezentována zadaný token oprávnění.|  
|[GetPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpinvokemap-method.md)|Získá odkaz ModuleRef token představující cíl sestavení volání PInvoke.|  
|[GetPropertyProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpropertyprops-method.md)|Získá metadata přidružená vlastnost reprezentována zadaný token.|  
|[GetRVA – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getrva-method.md)|Získá posun relativní virtuální adresy kód objekt reprezentovaný rozhraním zadaný token.|  
|[GetScopeProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md)|Získá název a volitelně identifikátor verze sestavení nebo modul v aktuálním oboru metadat.|  
|[GetSigFromToken – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getsigfromtoken-method.md)|Získá podpis binární metadata související s zadaný token.|  
|[GetTypeDefProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettypedefprops-method.md)|Vrátí informace metadat pro typu představovaný typem zadaný token TypeDef.|  
|[GetTypeRefProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettyperefprops-method.md)|Získá metadata spojená s typem odkazuje zadaný odkaz TypeRef token.|  
|[GetTypeSpecFromToken – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettypespecfromtoken-method.md)|Získá podpis binární metadat specifikace typu reprezentována zadaný token.|  
|[GetUserString – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getuserstring-method.md)|Získá reprezentována Zadaná metadata token řetězcového literálu.|  
|[IsGlobal – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-isglobal-method.md)|Získá hodnotu označující, zda pole, metoda nebo typu představovaný typem Zadaná metadata token má globální obor.|  
|[IsValidToken – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-isvalidtoken-method.md)|Získá hodnotu označující, zda zadaný token obsahuje neplatný odkaz na objekt kódu.|  
|[ResetEnum – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-resetenum-method.md)|Zadaný čítač obnoví na zadané pozici.|  
|[ResolveTypeRef – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-resolvetyperef-method.md)|Získá typ informace pro typ, který odkazuje zadaný odkaz TypeRef token.|  
  
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
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
