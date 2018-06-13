---
title: IMetaDataEmit – rozhraní
ms.date: 03/30/2017
api_name:
- IMetaDataEmit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit
helpviewer_keywords:
- IMetaDataEmit interface [.NET Framework metadata]
ms.assetid: 3b48fd47-7397-4e2c-8bec-8157aa08978c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4c77edfff640f796dd3f345eaeb4728830c5f4c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449141"
---
# <a name="imetadataemit-interface"></a>IMetaDataEmit – rozhraní
Poskytuje metody pro vytváření, úpravě a uložit metadata o sestavení v aktuálně definován obor. Metadata dá uložené v paměti nebo uložit na disk.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ApplyEditAndContinue – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md)|Aktualizuje aktuální obor sestavení se změny provedené v zadané `pImport`.|  
|[DefineCustomAttribute – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md)|Vytvoří definici pro vlastní atribut podpisem Zadaná metadata, připojí se k zadaný objekt a získá token tuto definici vlastních atributů.|  
|[DefineEvent – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md)|Vytvoří definici pro události s podpisem Zadaná metadata a získá token tuto definici událostí.|  
|[DefineField – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definefield-method.md)|Vytvoří definici pole s podpisem Zadaná metadata a získá token tuto definici pole.|  
|[DefineImportMember – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md)|Vytvoří definici pro člena typu, který je definován v modulu mimo aktuální obor a získá token pro tuto referenční definice.|  
|[DefineImportType – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)|Vytvoří definici pro odkaz na typ, který je definován v modulu mimo aktuální obor a získá token pro tuto referenční definice.|  
|[DefineMemberRef – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md)|Vytvoří definici pro odkaz na člena modulu mimo aktuální obor a získá token pro tuto referenční definice.|  
|[DefineMethod – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md)|Vytvoří definici pro metodu podpisem zadané a vrátí token tuto definici metody.|  
|[DefineMethodImpl – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethodimpl-method.md)|Vytvoří definici implementace metody zděděno z rozhraní a vrátí token tuto definici implementace metod.|  
|[DefineModuleRef – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md)|Vytvoří metadata podpis pro modul se zadaným názvem.|  
|[DefineNestedType – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definenestedtype-method.md)|Vytvoří metadata podpis definice typu a vrátí `mdTypeDef` tokenu pro tento typ, kromě určení, že definovaný typ je člen typu odkazuje `tdEncloser`.|  
|[DefineParam – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md)|Vytvoří definici parametru podpisem zadaný pro metodu odkazuje zadaný token a získá token pro tuto definici parametru.|  
|[DefinePermissionSet – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md)|Vytvoří definici oprávnění nastavit podpisem Zadaná metadata a získá token pro tuto definici sady oprávnění.|  
|[DefinePinvokeMap – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md)|Nastaví funkce PInvoke podpis metody odkazuje zadaný token.|  
|[DefineProperty – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md)|Vytvoří definici vlastnosti pro zadaný typ se zadaným `get` a `set` metody přístupových objektů a získá token pro tuto definici vlastnosti.|  
|[DefineSecurityAttributeSet – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definesecurityattributeset-method.md)|Vytvoří sadu oprávnění zabezpečení pro připojení k objektu, který odkazuje zadaný token.|  
|[DefineTypeDef – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)|Vytvoří definici typu pro běžné typ modulu runtime jazyka a získá token metadata pro tuto definici typu.|  
|[DefineTypeRefByName – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md)|Získá token metadat pro typ, který je definován v jiném modulu mimo aktuální obor.|  
|[DefineUserString – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md)|Získá token metadata pro zadanou řetězcového literálu.|  
|[DeleteClassLayout – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deleteclasslayout-method.md)|Zničí podpis třída rozložení metadata pro typ, který odkazuje zadaný token.|  
|[DeleteFieldMarshal – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletefieldmarshal-method.md)|Zničí PInvoke zařazování podpis metadata pro objekt, který odkazuje zadaný token.|  
|[DeletePinvokeMap – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletepinvokemap-method.md)|Zničí metadata PInvoke mapování pro objekt, který odkazuje zadaný token.|  
|[DeleteToken – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletetoken-method.md)|Odstraní zadaný token z aktuálního oboru metadat.|  
|[GetSaveSize – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-getsavesize-method.md)|Získá odhadovanou velikost binární sestavení v aktuálním oboru.|  
|[GetTokenFromSig – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md)|Získá token pro podpis Zadaná metadata.|  
|[GetTokenFromTypeSpec – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md)|Získá token metadat pro typ s podpisem Zadaná metadata.|  
|[Merge – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)|Zadaný obor importované přidá do seznamu oborů, který se má sloučit.|  
|[MergeEnd – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md)|Sloučení do aktuální obor všechny obory metadata určeného jeden nebo více předchozích volání `IMetaDataEmit::Merge`.|  
|[Save – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-save-method.md)|Uloží všechna metadata v aktuálním oboru do souboru na zadané adrese.|  
|[SaveToMemory – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md)|Uloží všechna metadata v aktuálním oboru do určené oblasti paměti.|  
|[SaveToStream – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md)|Uloží všechna metadata v aktuálním oboru do zadané `IStream`.|  
|[SetClassLayout – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md)|Nastaví nebo aktualizuje podpis rozložení – třída typu definované předchozí volání `IMetaDataEmit::DefineTypeDef`.|  
|[SetCustomAttributeValue – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setcustomattributevalue-method.md)|Nastaví nebo aktualizuje hodnota vlastního atributu definované předchozí volání `IMetaDataEmit::DefineCustomAttribute`.|  
|[SetEventProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-seteventprops-method.md)|Nastaví nebo aktualizuje určenou funkci události definované předchozí volání `IMetaDataEmit::DefineEvent`.|  
|[SetFieldMarshal – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldmarshal-method.md)|Nastaví PInvoke zařazování informace pro parametr pole, metoda návratový nebo metoda odkazuje zadaný token.|  
|[SetFieldProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldprops-method.md)|Nastaví nebo aktualizuje výchozí hodnota pro pole odkazuje token zadané pole.|  
|[SetFieldRVA – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldrva-method.md)|Nastaví hodnotu globální proměnné pro relativní virtuální adresu pole odkazuje zadaný token.|  
|[SetHandler – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)|Nastaví metodu, která odkazuje zadanou `IUnknown` ukazatel jako zpětné volání oznámení pro token přemapuje.|  
|[SetMethodImplFlags – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md)|Nastaví nebo aktualizuje podpis metadata implementace zděděné metody odkazuje zadaný token.|  
|[SetMethodProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodprops-method.md)|Nastaví nebo aktualizuje funkce, které jsou uložené na zadaný relativní virtuální na adrese definované předchozí volání metody `IMetaDataEmit::DefineMethod`.|  
|[SetModuleProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md)|Aktualizace odkazů na modul definované předchozí volání `IMetaDataEmit::DefineModuleRef`.|  
|[SetParamProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md)|Nastaví nebo změny funkcí parametru metody, která byla definována voláním předchozí `IMetaDataEmit::DefineParam`.|  
|[SetParent – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparent-method.md)|Zjistí, že zadaný člen, jak je definována předchozí volání `IMetaDataEmit::DefineMemberRef`, je členem skupiny zadaný typ podle definice předchozí volání `IMetaDataEmit::DefineTypeDef`.|  
|[SetPermissionSetProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpermissionsetprops-method.md)|Nastaví nebo aktualizuje funkce metadata podpis sadu oprávnění definovanou před voláním `IMetaDataEmit::DefinePermissionSet`.|  
|[SetPinvokeMap – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpinvokemap-method.md)|Nastaví nebo změny funkcí metoda PInvoke podpis, podle definice předchozí volání `IMetaDataEmit::DefinePinvokeMap`.|  
|[SetPropertyProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpropertyprops-method.md)|Nastaví uložené v metadata pro vlastnost definovanou před voláním funkce `IMetaDataEmit::DefineProperty`.|  
|[SetRVA – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md)|Nastaví relativní virtuální adresu zadanou metodu.|  
|[SetTypeDefProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-settypedefprops-method.md)|Nastaví funkce typu definované předchozí volání `IMetaDataEmit::DefineTypeDef`.|  
|[TranslateSigWithScope – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-translatesigwithscope-method.md)|Importuje sestavení do aktuální obor a získá nové podpis metadata pro sloučené obor.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
