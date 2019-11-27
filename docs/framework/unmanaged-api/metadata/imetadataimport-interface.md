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
ms.openlocfilehash: 2d45a369def193b9c8d8f9a3aa954ede600a87dd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434734"
---
# <a name="imetadataimport-interface"></a>IMetaDataImport – rozhraní
Poskytuje metody pro import a manipulaci s existujícími metadaty ze souboru přenositelného spustitelného souboru (PE) nebo jiného zdroje, jako je například knihovna typů nebo samostatného binárního souboru metadat run-time.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CloseEnum – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-closeenum-method.md)|Uzavře enumerátor se zadaným popisovačem.|  
|[CountEnum – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-countenum-method.md)|Získá počet prvků v enumerátoru se zadaným popisovačem.|  
|[EnumCustomAttributes – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md)|Vytvoří seznam vlastních tokenů definice atributu přidružených k zadanému typu nebo členu.|  
|[EnumEvents – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumevents-method.md)|Vytvoří výčet tokenů definice události pro zadaný token TypeDef.|  
|[EnumFields – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md)|Vytvoří výčet tokenů FieldDef pro typ, na který odkazuje zadaný token TypeDef.|  
|[EnumFieldsWithName – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfieldswithname-method.md)|Vytvoří výčet tokenů FieldDef zadaného typu se zadaným názvem.|  
|[EnumInterfaceImpls – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enuminterfaceimpls-method.md)|Vytvoří výčet tokenů MethodDef představujících implementace rozhraní.|  
|[EnumMemberRefs – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummemberrefs-method.md)|Vytvoří výčet tokenů MemberRef představujících členy zadaného typu.|  
|[EnumMembers – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md)|Vytvoří výčet tokenů memberDef či představujících členy zadaného typu.|  
|[EnumMembersWithName – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummemberswithname-method.md)|Vytvoří výčet tokenů memberDef či představujících členy zadaného typu se zadaným názvem.|  
|[EnumMethodImpls – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodimpls-method.md)|Vytvoří výčet tokenů MethodBody a MethodDeclaration představujících metody zadaného typu.|  
|[EnumMethods – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md)|Vytvoří výčet tokenů MethodDef představujících metody zadaného typu.|  
|[EnumMethodSemantics – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodsemantics-method.md)|Vytvoří výčet vlastností a událostí změny vlastností, na které se vztahuje zadaná metoda.|  
|[EnumMethodsWithName – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodswithname-method.md)|Vytvoří výčet metod, které mají zadaný název a které jsou definovány typem, na který odkazuje zadaný token TypeDef.|  
|[EnumModuleRefs – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummodulerefs-method.md)|Vytvoří výčet tokenů Odkaz ModuleRef, které reprezentují importované moduly.|  
|[EnumParams – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumparams-method.md)|Vytvoří výčet tokenů ParamDef představujících parametry metody, na kterou odkazuje zadaný token MethodDef.|  
|[EnumPermissionSets – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumpermissionsets-method.md)|Vytvoří výčet oprávnění pro objekty v zadaném oboru metadat.|  
|[EnumProperties – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumproperties-method.md)|Vytvoří výčet tokenů PropertyDef představujících vlastnosti typu, na který odkazuje zadaný token TypeDef.|  
|[EnumSignatures – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumsignatures-method.md)|Vytvoří výčet tokenů podpisu představujících samostatné podpisy v aktuálním oboru.|  
|[EnumTypeDefs – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)|Vytvoří výčet tokenů TypeDef reprezentujících všechny typy v rámci aktuálního oboru.|  
|[EnumTypeRefs – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtyperefs-method.md)|Vytvoří výčet tokenů TypeRef definovaných v aktuálním oboru metadat.|  
|[EnumTypeSpecs – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypespecs-method.md)|Vytvoří výčet tokenů token TypeSpec definovaných v aktuálním oboru metadat.|  
|[EnumUnresolvedMethods – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumunresolvedmethods-method.md)|Vytvoří výčet tokenů memberDef či představujících nerozpoznané metody v aktuálním oboru metadat.|  
|[EnumUserStrings – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumuserstrings-method.md)|Vytvoří výčet řetězcových tokenů představujících pevně zakódované řetězce v aktuálním oboru metadat.|  
|[FindField – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md)|Získá token FieldDef pro pole, které je členem zadaného typu, a má zadaný název a signaturu metadat.|  
|[FindMember – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmember-method.md)|Získá ukazatel na token memberDef či pro člena definovaného zadaným typem se zadaným názvem a signaturou metadat.|  
|[FindMemberRef – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmemberref-method.md)|Získá ukazatel na token MemberRef pro člena definovaného zadaným typem se zadaným názvem a signaturou metadat.|  
|[FindMethod – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md)|Získá ukazatel na token MethodDef pro metodu definovanou zadaným typem se zadaným názvem a signaturou metadat.|  
|[FindTypeDefByName – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findtypedefbyname-method.md)|Získá ukazatel na token metadat TypeDef pro typ se zadaným názvem.|  
|[FindTypeRef – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findtyperef-method.md)|Získá ukazatel na token metadat TypeRef, který odkazuje na typ v zadaném oboru hledání se zadaným názvem.|  
|[GetClassLayout – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md)|Získá informace o rozložení pro třídu, na kterou odkazuje zadaný token TypeDef.|  
|[GetCustomAttributeByName – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getcustomattributebyname-method.md)|Získá hodnotu vlastního atributu, který je dán názvem.|  
|[GetCustomAttributeProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getcustomattributeprops-method.md)|Získá hodnotu vlastního atributu s ohledem na jeho token metadat.|  
|[GetEventProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-geteventprops-method.md)|Načte informace metadat (včetně deklarovaného typu, metod přidání a odebrání delegátů a všech příznaků a dalších přidružených dat) pro událost reprezentované zadaným tokenem události.|  
|[GetFieldMarshal – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getfieldmarshal-method.md)|Získá ukazatel na nativní nespravovaný typ pole reprezentovaného tokenem metadat zadaného pole.|  
|[GetFieldProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getfieldprops-method.md)|Načte metadata přidružená k poli, na které odkazuje zadaný FieldDef token.|  
|[GetInterfaceImplProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getinterfaceimplprops-method.md)|Získá ukazatel na tokeny metadat pro typ, který implementuje zadanou metodu a pro rozhraní, které deklaruje tuto metodu.|  
|[GetMemberProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmemberprops-method.md)|Načte informace o metadatech (včetně názvu, binárního podpisu a relativní virtuální adresy) typu členu, na který odkazuje zadaný token metadat.|  
|[GetMemberRefProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmemberrefprops-method.md)|Načte metadata přidružená k členu, na který odkazuje zadaný token.|  
|[GetMethodProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmethodprops-method.md)|Získá metadata přidružená k metodě, na kterou odkazuje zadaný token MethodDef.|  
|[GetMethodSemantics – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmethodsemantics-method.md)|Získá ukazatel na vztah mezi metodou, na kterou se odkazuje zadaný token MethodDef, a spárovanými vlastnostmi a událostmi, na které odkazuje zadaný EventProp token.|  
|[GetModuleFromScope – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmodulefromscope-method.md)|Získá ukazatel na token metadat pro modul, na který se odkazuje v aktuálním oboru metadat.|  
|[GetModuleRefProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmodulerefprops-method.md)|Získá název modulu, na který odkazuje zadaný token metadat.|  
|[GetNameFromToken – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnamefromtoken-method.md)|Získá název UTF-8 objektu, na který odkazuje zadaný token metadat.|  
|[GetNativeCallConvFromSig – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnativecallconvfromsig-method.md)|Získá nativní konvenci volání pro metodu, která je reprezentovaná zadaným ukazatelem podpisu.|  
|[GetNestedClassProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnestedclassprops-method.md)|Získá token TypeDef pro ohraničující nadřazený typ zadaného vnořeného typu.|  
|[GetParamForMethodIndex – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getparamformethodindex-method.md)|Získá ukazatel na token, který představuje parametr na zadaném pořadovém místě v pořadí parametrů metody pro metodu reprezentovanou zadaným tokenem MethodDef.|  
|[GetParamProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getparamprops-method.md)|Načte hodnoty metadat pro parametr, na který odkazuje zadaný ParamDef token.|  
|[GetPermissionSetProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpermissionsetprops-method.md)|Načte metadata přidružená k System. Security. PermissionSet reprezentovanému zadaným tokenem oprávnění.|  
|[GetPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpinvokemap-method.md)|Získá token Odkaz ModuleRef představující cílové sestavení volání PInvoke.|  
|[GetPropertyProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpropertyprops-method.md)|Načte metadata přidružená k vlastnosti reprezentované zadaným tokenem.|  
|[GetRVA – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getrva-method.md)|Získá posun relativní virtuální adresy objektu kódu reprezentovaného zadaným tokenem.|  
|[GetScopeProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md)|Získá název a volitelně identifikátor verze sestavení nebo modulu v aktuálním oboru metadat.|  
|[GetSigFromToken – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getsigfromtoken-method.md)|Získá binární podpis metadat přidružených k zadanému tokenu.|  
|[GetTypeDefProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettypedefprops-method.md)|Vrátí informace o metadatech pro typ reprezentovaný zadaným tokenem TypeDef.|  
|[GetTypeRefProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettyperefprops-method.md)|Získá metadata přidružená k typu, na který odkazuje zadaný token TypeRef.|  
|[GetTypeSpecFromToken – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettypespecfromtoken-method.md)|Získá binární podpis metadat specifikace typu reprezentované zadaným tokenem.|  
|[GetUserString – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getuserstring-method.md)|Získá řetězcový literál reprezentovaný zadaným tokenem metadat.|  
|[IsGlobal – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-isglobal-method.md)|Získá hodnotu, která označuje, zda pole, metoda nebo typ reprezentovaný zadaným tokenem metadat má globální rozsah.|  
|[IsValidToken – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-isvalidtoken-method.md)|Získá hodnotu, která označuje, zda zadaný token drží platný odkaz na objekt kódu.|  
|[ResetEnum – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-resetenum-method.md)|Obnoví zadaný enumerátor na určenou pozici.|  
|[ResolveTypeRef – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-resolvetyperef-method.md)|Načte informace o typu pro typ, na který odkazuje zadaný token TypeRef.|  
  
## <a name="remarks"></a>Poznámky  
 Návrh rozhraní `IMetaDataImport` je určen hlavně pro nástroje a služby, které budou importovat informace o typu (například vývojové nástroje) nebo spravovat nasazené komponenty (například služby pro rozpoznávání/aktivaci). Metody v `IMetaDataImport` spadají do následujících kategorií úkolů:  
  
- Vytváření výčtu kolekcí položek v oboru metadat.  
  
- Hledání položky, která má konkrétní sadu charakteristik.  
  
- Načítají se vlastnosti zadané položky.  
  
- Metody Get jsou určeny konkrétně k vrácení vlastností položky metadat s jedinou hodnotou. Pokud je vlastnost odkazem na jinou položku, vrátí se token pro tuto položku. Libovolný typ vstupu ukazatele může být NULL, aby označoval, že konkrétní hodnota není požadována. Chcete-li získat vlastnosti, které jsou v podstatě objekty kolekce (například kolekce rozhraní implementující třídu), použijte metody výčtu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
