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
ms.openlocfilehash: 02d1ea1ef12fa158ce7ec94aeca4356ac54d4e5f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503481"
---
# <a name="imetadataimport-interface"></a>IMetaDataImport – rozhraní
Poskytuje metody pro import a manipulaci s existujícími metadaty ze souboru přenositelného spustitelného souboru (PE) nebo jiného zdroje, jako je například knihovna typů nebo samostatného binárního souboru metadat run-time.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[CloseEnum – metoda](imetadataimport-closeenum-method.md)|Uzavře enumerátor se zadaným popisovačem.|  
|[CountEnum – metoda](imetadataimport-countenum-method.md)|Získá počet prvků v enumerátoru se zadaným popisovačem.|  
|[EnumCustomAttributes – metoda](imetadataimport-enumcustomattributes-method.md)|Vytvoří seznam vlastních tokenů definice atributu přidružených k zadanému typu nebo členu.|  
|[EnumEvents – metoda](imetadataimport-enumevents-method.md)|Vytvoří výčet tokenů definice události pro zadaný token TypeDef.|  
|[EnumFields – metoda](imetadataimport-enumfields-method.md)|Vytvoří výčet tokenů FieldDef pro typ, na který odkazuje zadaný token TypeDef.|  
|[EnumFieldsWithName – metoda](imetadataimport-enumfieldswithname-method.md)|Vytvoří výčet tokenů FieldDef zadaného typu se zadaným názvem.|  
|[EnumInterfaceImpls – metoda](imetadataimport-enuminterfaceimpls-method.md)|Vytvoří výčet tokenů MethodDef představujících implementace rozhraní.|  
|[EnumMemberRefs – metoda](imetadataimport-enummemberrefs-method.md)|Vytvoří výčet tokenů MemberRef představujících členy zadaného typu.|  
|[EnumMembers – metoda](imetadataimport-enummembers-method.md)|Vytvoří výčet tokenů memberDef či představujících členy zadaného typu.|  
|[EnumMembersWithName – metoda](imetadataimport-enummemberswithname-method.md)|Vytvoří výčet tokenů memberDef či představujících členy zadaného typu se zadaným názvem.|  
|[EnumMethodImpls – metoda](imetadataimport-enummethodimpls-method.md)|Vytvoří výčet tokenů MethodBody a MethodDeclaration představujících metody zadaného typu.|  
|[EnumMethods – metoda](imetadataimport-enummethods-method.md)|Vytvoří výčet tokenů MethodDef představujících metody zadaného typu.|  
|[EnumMethodSemantics – metoda](imetadataimport-enummethodsemantics-method.md)|Vytvoří výčet vlastností a událostí změny vlastností, na které se vztahuje zadaná metoda.|  
|[EnumMethodsWithName – metoda](imetadataimport-enummethodswithname-method.md)|Vytvoří výčet metod, které mají zadaný název a které jsou definovány typem, na který odkazuje zadaný token TypeDef.|  
|[EnumModuleRefs – metoda](imetadataimport-enummodulerefs-method.md)|Vytvoří výčet tokenů Odkaz ModuleRef, které reprezentují importované moduly.|  
|[EnumParams – metoda](imetadataimport-enumparams-method.md)|Vytvoří výčet tokenů ParamDef představujících parametry metody, na kterou odkazuje zadaný token MethodDef.|  
|[EnumPermissionSets – metoda](imetadataimport-enumpermissionsets-method.md)|Vytvoří výčet oprávnění pro objekty v zadaném oboru metadat.|  
|[EnumProperties – metoda](imetadataimport-enumproperties-method.md)|Vytvoří výčet tokenů PropertyDef představujících vlastnosti typu, na který odkazuje zadaný token TypeDef.|  
|[EnumSignatures – metoda](imetadataimport-enumsignatures-method.md)|Vytvoří výčet tokenů podpisu představujících samostatné podpisy v aktuálním oboru.|  
|[EnumTypeDefs – metoda](imetadataimport-enumtypedefs-method.md)|Vytvoří výčet tokenů TypeDef reprezentujících všechny typy v rámci aktuálního oboru.|  
|[EnumTypeRefs – metoda](imetadataimport-enumtyperefs-method.md)|Vytvoří výčet tokenů TypeRef definovaných v aktuálním oboru metadat.|  
|[EnumTypeSpecs – metoda](imetadataimport-enumtypespecs-method.md)|Vytvoří výčet tokenů token TypeSpec definovaných v aktuálním oboru metadat.|  
|[EnumUnresolvedMethods – metoda](imetadataimport-enumunresolvedmethods-method.md)|Vytvoří výčet tokenů memberDef či představujících nerozpoznané metody v aktuálním oboru metadat.|  
|[EnumUserStrings – metoda](imetadataimport-enumuserstrings-method.md)|Vytvoří výčet řetězcových tokenů představujících pevně zakódované řetězce v aktuálním oboru metadat.|  
|[FindField – metoda](imetadataimport-findfield-method.md)|Získá token FieldDef pro pole, které je členem zadaného typu, a má zadaný název a signaturu metadat.|  
|[FindMember – metoda](imetadataimport-findmember-method.md)|Získá ukazatel na token memberDef či pro člena definovaného zadaným typem se zadaným názvem a signaturou metadat.|  
|[FindMemberRef – metoda](imetadataimport-findmemberref-method.md)|Získá ukazatel na token MemberRef pro člena definovaného zadaným typem se zadaným názvem a signaturou metadat.|  
|[FindMethod – metoda](imetadataimport-findmethod-method.md)|Získá ukazatel na token MethodDef pro metodu definovanou zadaným typem se zadaným názvem a signaturou metadat.|  
|[FindTypeDefByName – metoda](imetadataimport-findtypedefbyname-method.md)|Získá ukazatel na token metadat TypeDef pro typ se zadaným názvem.|  
|[FindTypeRef – metoda](imetadataimport-findtyperef-method.md)|Získá ukazatel na token metadat TypeRef, který odkazuje na typ v zadaném oboru hledání se zadaným názvem.|  
|[GetClassLayout – metoda](imetadataimport-getclasslayout-method.md)|Získá informace o rozložení pro třídu, na kterou odkazuje zadaný token TypeDef.|  
|[GetCustomAttributeByName – metoda](imetadataimport-getcustomattributebyname-method.md)|Získá hodnotu vlastního atributu, který je dán názvem.|  
|[GetCustomAttributeProps – metoda](imetadataimport-getcustomattributeprops-method.md)|Získá hodnotu vlastního atributu s ohledem na jeho token metadat.|  
|[GetEventProps – metoda](imetadataimport-geteventprops-method.md)|Načte informace metadat (včetně deklarovaného typu, metod přidání a odebrání delegátů a všech příznaků a dalších přidružených dat) pro událost reprezentované zadaným tokenem události.|  
|[GetFieldMarshal – metoda](imetadataimport-getfieldmarshal-method.md)|Získá ukazatel na nativní nespravovaný typ pole reprezentovaného tokenem metadat zadaného pole.|  
|[GetFieldProps – metoda](imetadataimport-getfieldprops-method.md)|Načte metadata přidružená k poli, na které odkazuje zadaný FieldDef token.|  
|[GetInterfaceImplProps – metoda](imetadataimport-getinterfaceimplprops-method.md)|Získá ukazatel na tokeny metadat pro typ, který implementuje zadanou metodu a pro rozhraní, které deklaruje tuto metodu.|  
|[GetMemberProps – metoda](imetadataimport-getmemberprops-method.md)|Načte informace o metadatech (včetně názvu, binárního podpisu a relativní virtuální adresy) typu členu, na který odkazuje zadaný token metadat.|  
|[GetMemberRefProps – metoda](imetadataimport-getmemberrefprops-method.md)|Načte metadata přidružená k členu, na který odkazuje zadaný token.|  
|[GetMethodProps – metoda](imetadataimport-getmethodprops-method.md)|Získá metadata přidružená k metodě, na kterou odkazuje zadaný token MethodDef.|  
|[GetMethodSemantics – metoda](imetadataimport-getmethodsemantics-method.md)|Získá ukazatel na vztah mezi metodou, na kterou se odkazuje zadaný token MethodDef, a spárovanými vlastnostmi a událostmi, na které odkazuje zadaný EventProp token.|  
|[GetModuleFromScope – metoda](imetadataimport-getmodulefromscope-method.md)|Získá ukazatel na token metadat pro modul, na který se odkazuje v aktuálním oboru metadat.|  
|[GetModuleRefProps – metoda](imetadataimport-getmodulerefprops-method.md)|Získá název modulu, na který odkazuje zadaný token metadat.|  
|[GetNameFromToken – metoda](imetadataimport-getnamefromtoken-method.md)|Získá název UTF-8 objektu, na který odkazuje zadaný token metadat.|  
|[GetNativeCallConvFromSig – metoda](imetadataimport-getnativecallconvfromsig-method.md)|Získá nativní konvenci volání pro metodu, která je reprezentovaná zadaným ukazatelem podpisu.|  
|[GetNestedClassProps – metoda](imetadataimport-getnestedclassprops-method.md)|Získá token TypeDef pro ohraničující nadřazený typ zadaného vnořeného typu.|  
|[GetParamForMethodIndex – metoda](imetadataimport-getparamformethodindex-method.md)|Získá ukazatel na token, který představuje parametr na zadaném pořadovém místě v pořadí parametrů metody pro metodu reprezentovanou zadaným tokenem MethodDef.|  
|[GetParamProps – metoda](imetadataimport-getparamprops-method.md)|Načte hodnoty metadat pro parametr, na který odkazuje zadaný ParamDef token.|  
|[GetPermissionSetProps – metoda](imetadataimport-getpermissionsetprops-method.md)|Načte metadata přidružená k System. Security. PermissionSet reprezentovanému zadaným tokenem oprávnění.|  
|[GetPinvokeMap](imetadataimport-getpinvokemap-method.md)|Získá token Odkaz ModuleRef představující cílové sestavení volání PInvoke.|  
|[GetPropertyProps – metoda](imetadataimport-getpropertyprops-method.md)|Načte metadata přidružená k vlastnosti reprezentované zadaným tokenem.|  
|[GetRVA – metoda](imetadataimport-getrva-method.md)|Získá posun relativní virtuální adresy objektu kódu reprezentovaného zadaným tokenem.|  
|[GetScopeProps – metoda](imetadataimport-getscopeprops-method.md)|Získá název a volitelně identifikátor verze sestavení nebo modulu v aktuálním oboru metadat.|  
|[GetSigFromToken – metoda](imetadataimport-getsigfromtoken-method.md)|Získá binární podpis metadat přidružených k zadanému tokenu.|  
|[GetTypeDefProps – metoda](imetadataimport-gettypedefprops-method.md)|Vrátí informace o metadatech pro typ reprezentovaný zadaným tokenem TypeDef.|  
|[GetTypeRefProps – metoda](imetadataimport-gettyperefprops-method.md)|Získá metadata přidružená k typu, na který odkazuje zadaný token TypeRef.|  
|[GetTypeSpecFromToken – metoda](imetadataimport-gettypespecfromtoken-method.md)|Získá binární podpis metadat specifikace typu reprezentované zadaným tokenem.|  
|[GetUserString – metoda](imetadataimport-getuserstring-method.md)|Získá řetězcový literál reprezentovaný zadaným tokenem metadat.|  
|[IsGlobal – metoda](imetadataimport-isglobal-method.md)|Získá hodnotu, která označuje, zda pole, metoda nebo typ reprezentovaný zadaným tokenem metadat má globální rozsah.|  
|[IsValidToken – metoda](imetadataimport-isvalidtoken-method.md)|Získá hodnotu, která označuje, zda zadaný token drží platný odkaz na objekt kódu.|  
|[ResetEnum – metoda](imetadataimport-resetenum-method.md)|Obnoví zadaný enumerátor na určenou pozici.|  
|[ResolveTypeRef – metoda](imetadataimport-resolvetyperef-method.md)|Načte informace o typu pro typ, na který odkazuje zadaný token TypeRef.|  
  
## <a name="remarks"></a>Poznámky  
 Návrh `IMetaDataImport` rozhraní je určen primárně pro nástroje a služby, které budou importovat informace o typu (například vývojové nástroje) nebo spravovat nasazené komponenty (například služby pro rozpoznávání/aktivaci). Metody v `IMetaDataImport` spadají do následujících kategorií úkolů:  
  
- Vytváření výčtu kolekcí položek v oboru metadat.  
  
- Hledání položky, která má konkrétní sadu charakteristik.  
  
- Načítají se vlastnosti zadané položky.  
  
- Metody Get jsou určeny konkrétně k vrácení vlastností položky metadat s jedinou hodnotou. Pokud je vlastnost odkazem na jinou položku, vrátí se token pro tuto položku. Libovolný typ vstupu ukazatele může být NULL, aby označoval, že konkrétní hodnota není požadována. Chcete-li získat vlastnosti, které jsou v podstatě objekty kolekce (například kolekce rozhraní implementující třídu), použijte metody výčtu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro metadata](metadata-interfaces.md)
- [IMetaDataImport2 – rozhraní](imetadataimport2-interface.md)
