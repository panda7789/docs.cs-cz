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
ms.openlocfilehash: a0f4eb244e02e13e418a55351dbc1eb1f5b5d16d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64617745"
---
# <a name="imetadataimport-interface"></a>IMetaDataImport – rozhraní
Poskytuje metody pro import a manipulace s existující metadata ze souboru (PE portable executable) nebo jiné zdroje, například knihovny typů nebo binární soubor metadat samostatné, za běhu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CloseEnum – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-closeenum-method.md)|Zavře čítač s určený.|  
|[CountEnum – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-countenum-method.md)|Získá počet elementů v enumerátor určený.|  
|[EnumCustomAttributes – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md)|Zobrazí seznam tokenů vlastní definice atributu přidružené zadaný typ nebo člen.|  
|[EnumEvents – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumevents-method.md)|Vytvoří výčet tokeny definice události pro konkrétní token TypeDef.|  
|[EnumFields – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md)|Vytvoří výčet FieldDef tokenů pro typ odkazuje zadaný token TypeDef.|  
|[EnumFieldsWithName – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfieldswithname-method.md)|Vytvoří výčet FieldDef tokeny zadaného typu se zadaným názvem.|  
|[EnumInterfaceImpls – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enuminterfaceimpls-method.md)|Vytvoří výčet MethodDef tokeny představující implementace rozhraní.|  
|[EnumMemberRefs – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummemberrefs-method.md)|Vytvoří výčet MemberRef tokeny představující členů zadaného typu.|  
|[EnumMembers – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md)|Vytvoří výčet MemberDef tokeny představující členů zadaného typu.|  
|[EnumMembersWithName – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummemberswithname-method.md)|Vytvoří výčet MemberDef tokeny představující členů zadaného typu se zadaným názvem.|  
|[EnumMethodImpls – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodimpls-method.md)|Vytvoří výčet MethodBody a MethodDeclaration tokeny představující metody zadaného typu.|  
|[EnumMethods – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md)|Vytvoří výčet MethodDef tokeny představující metody zadaného typu.|  
|[EnumMethodSemantics – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodsemantics-method.md)|Vytvoří výčet vlastností a změnu vlastnosti události, ke kterým se vztahuje zadanou metodu.|  
|[EnumMethodsWithName – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodswithname-method.md)|Podává výčet metod, které mají se zadaným názvem a typem odkazuje zadaný token TypeDef, která jsou definována.|  
|[EnumModuleRefs – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummodulerefs-method.md)|Vytvoří výčet Odkaz ModuleRef tokeny, které představují importované moduly.|  
|[EnumParams – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumparams-method.md)|Vytvoří výčet ParamDef tokeny představující parametry metody odkazuje zadaný token MethodDef.|  
|[EnumPermissionSets – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumpermissionsets-method.md)|Vytvoří výčet oprávnění pro objekty v oboru Zadaná metadata.|  
|[EnumProperties – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumproperties-method.md)|Vytvoří výčet vlastnosti tokeny představující vlastnosti typu odkazuje zadaný token TypeDef.|  
|[EnumSignatures – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumsignatures-method.md)|Vytvoří výčet tokenů podpisu představující samostatné podpisy v aktuálním oboru.|  
|[EnumTypeDefs – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)|Vytvoří výčet TypeDef tokeny představující všechny typy v aktuálním oboru.|  
|[EnumTypeRefs – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtyperefs-method.md)|Vytvoří výčet TypeRef tokeny definované v aktuálním oboru metadat.|  
|[EnumTypeSpecs – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypespecs-method.md)|Vytvoří výčet token TypeSpec tokeny definované v aktuálním oboru metadat.|  
|[EnumUnresolvedMethods – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumunresolvedmethods-method.md)|Vytvoří výčet MemberDef tokeny představující nevyřešené metody v aktuálním oboru metadat.|  
|[EnumUserStrings – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumuserstrings-method.md)|Vytvoří výčet řetězec tokeny představující pevně zakódované řetězce v aktuálním oboru metadat.|  
|[FindField – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md)|Získá token FieldDef pro pole, která je členem zadaného typu a má zadaný název a podpis metadat.|  
|[FindMember – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmember-method.md)|Získá ukazatel MemberDef token pro člena definovaného podle zadaného typu pomocí zadaného názvu a podpisu metadat.|  
|[FindMemberRef – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmemberref-method.md)|Získá ukazatel Odkaz MemberRef token pro člena definovaného podle zadaného typu pomocí zadaného názvu a podpisu metadat.|  
|[FindMethod – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md)|Získá ukazatel MethodDef token metody definovány pomocí zadaného typu pomocí zadaného názvu a podpisu metadat.|  
|[FindTypeDefByName – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findtypedefbyname-method.md)|Získá ukazatel na TypeDef metadata token pro typ se zadaným názvem.|  
|[FindTypeRef – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findtyperef-method.md)|Získá ukazatel na token TypeRef metadata, která odkazuje na typ v rámci zadané hledání se zadaným názvem.|  
|[GetClassLayout – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md)|Získá informace o rozložení třídy odkazuje zadaný TypeDef token.|  
|[GetCustomAttributeByName – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getcustomattributebyname-method.md)|Získá hodnotu vlastního atributu, jeho název.|  
|[GetCustomAttributeProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getcustomattributeprops-method.md)|Získá hodnotu vlastní atribut zadaný svůj token metadat.|  
|[GetEventProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-geteventprops-method.md)|Získá informace o metadatech (včetně deklarovaného typu, přidání a odebrání metody pro delegáty a všechny příznaky a další související data) pro událost reprezentována token zadané události.|  
|[GetFieldMarshal – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getfieldmarshal-method.md)|Získá ukazatel na nativní, nespravovaným typem pole reprezentována zadaný token metadat pole.|  
|[GetFieldProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getfieldprops-method.md)|Získá metadata spojená s polem odkazuje zadaný FieldDef token.|  
|[GetInterfaceImplProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getinterfaceimplprops-method.md)|Získá ukazatel na tokeny metadat pro typ, který implementuje zadanou metodu a rozhraní, které deklaruje dané metody.|  
|[GetMemberProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmemberprops-method.md)|Získá metadata informace (včetně názvu, binární podpis a relativní virtuální adresa), odkazuje token metadat zadaného člena typu.|  
|[GetMemberRefProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmemberrefprops-method.md)|Získá metadata přidružená k členu odkazuje zadaný token.|  
|[GetMethodProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmethodprops-method.md)|Získá token budou metadata spojená s metodou odkazuje zadaný MethodDef.|  
|[GetMethodSemantics – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmethodsemantics-method.md)|Získá ukazatel na vztah mezi metodou odkazuje zadaný token MethodDef a spárované vlastnosti a události odkazuje zadaný EventProp token.|  
|[GetModuleFromScope – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmodulefromscope-method.md)|Získá ukazatel k metadatům token pro modul odkazovat v aktuálním oboru metadat.|  
|[GetModuleRefProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmodulerefprops-method.md)|Získá název odkazuje token metadat zadaného modulu.|  
|[GetNameFromToken – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnamefromtoken-method.md)|Získá název kódování UTF-8 odkazuje token metadat zadaného objektu.|  
|[GetNativeCallConvFromSig – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnativecallconvfromsig-method.md)|Získá nativní konvence volání pro metodu, která je reprezentována zadaným podpisem ukazatele.|  
|[GetNestedClassProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnestedclassprops-method.md)|Získá token TypeDef pro zadaný typ vnořeného typu nadřazeného nadřazeného typu.|  
|[GetParamForMethodIndex – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getparamformethodindex-method.md)|Získá ukazatel na token, který představuje parametr na zadané pořadové číslo pozice v pořadí parametrů metody k metodě reprezentované zadaný token MethodDef.|  
|[GetParamProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getparamprops-method.md)|Získá metadata hodnot pro parametr odkazuje zadaný ParamDef token.|  
|[GetPermissionSetProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpermissionsetprops-method.md)|Získá metadata přidružená k System.Security.PermissionSet reprezentována zadaný token oprávnění.|  
|[GetPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpinvokemap-method.md)|Získá token představující cílové sestavení volání PInvoke Odkaz ModuleRef.|  
|[GetPropertyProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpropertyprops-method.md)|Získá metadata přidružená vlastnost reprezentována zadaného tokenu.|  
|[GetRVA – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getrva-method.md)|Získá posun relativní virtuální adresu kód objektu reprezentovaného parametrem zadaného tokenu.|  
|[GetScopeProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md)|Získá název a volitelně identifikátor verze sestavení nebo modulu v aktuálním oboru metadat.|  
|[GetSigFromToken – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getsigfromtoken-method.md)|Získá metadata binární podpis přidružené k zadaným tokenu.|  
|[GetTypeDefProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettypedefprops-method.md)|Vrátí informace metadat pro typ zastoupený zadaný token TypeDef.|  
|[GetTypeRefProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettyperefprops-method.md)|Získá token budou metadata spojená s typem odkazuje zadaný odkaz TypeRef.|  
|[GetTypeSpecFromToken – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettypespecfromtoken-method.md)|Získá metadata binární podpis specifikace typu, který je reprezentován zadaného tokenu.|  
|[GetUserString – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getuserstring-method.md)|Získá reprezentována token metadat zadaného řetězcového literálu.|  
|[IsGlobal – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-isglobal-method.md)|Získá hodnotu označující, zda pole, metodu nebo typ zastoupený token metadat zadaného má globální obor.|  
|[IsValidToken – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-isvalidtoken-method.md)|Získá hodnotu označující, zda zadaný token obsahuje neplatný odkaz na objekt kódu.|  
|[ResetEnum – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-resetenum-method.md)|Zadaný čítač resetuje na určenou pozici.|  
|[ResolveTypeRef – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-resolvetyperef-method.md)|Získá typ informací pro typ odkazuje zadaný token TypeRef.|  
  
## <a name="remarks"></a>Poznámky  
 Návrh `IMetaDataImport` rozhraní je určený hlavně kvůli používat nástroje a služby, které bude import informací o typu (například nástroje pro vývoj) nebo správu nasazení součásti (například řešení/aktivace služby). Metody v `IMetaDataImport` spadají do následujících kategorií úloh:  
  
- Vytváření výčtů kolekcí položek v rámci metadat.  
  
- Hledání položky, která má specifickou sadu vlastností.  
  
- Získání vlastnosti zadané položky.  
  
- Metody Get jsou vytvořené speciálně k vrácení jednou hodnotou vlastnosti položky metadat. Vlastnost je odkazem na jinou položku, bude vrácen token pro danou položku. Žádné vstupní typ ukazatele může mít hodnotu NULL k označení, že není žádá konkrétní hodnotu. Získat vlastnosti, které jsou v podstatě kolekci objektů (například kolekce rozhraní, která implementuje třídu), použijte metody výčtu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
