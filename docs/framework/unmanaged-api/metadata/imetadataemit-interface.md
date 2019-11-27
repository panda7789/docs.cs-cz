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
ms.openlocfilehash: b4ae599a0e5cdb604fd9a610728671b39c67af31
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440897"
---
# <a name="imetadataemit-interface"></a>IMetaDataEmit – rozhraní
Poskytuje metody pro vytváření, úpravy a ukládání metadat sestavení v aktuálně definovaném oboru. Metadata se můžou ukládat do paměti nebo ukládat na disk.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ApplyEditAndContinue – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md)|Aktualizuje aktuální obor sestavení změnami provedenými v zadaném `pImport`.|  
|[DefineCustomAttribute – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md)|Vytvoří definici pro vlastní atribut se zadaným podpisem metadat, který se má připojit k zadanému objektu, a získá token do této definice vlastního atributu.|  
|[DefineEvent – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md)|Vytvoří definici události se zadaným podpisem metadat a získá token této definice události.|  
|[DefineField – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definefield-method.md)|Vytvoří definici pro pole se zadaným podpisem metadat a získá token do této definice pole.|  
|[DefineImportMember – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md)|Vytvoří definici pro člena typu, který je definován v modulu mimo aktuální rozsah, a získá token pro tuto definici odkazu.|  
|[DefineImportType – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)|Vytvoří definici pro odkaz na typ, který je definován v modulu mimo aktuální rozsah, a získá token do této referenční definice.|  
|[DefineMemberRef – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md)|Vytvoří definici pro odkaz na člena modulu mimo aktuální rozsah a získá token do této referenční definice.|  
|[DefineMethod – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md)|Vytvoří definici metody se zadaným podpisem a vrátí do této definice metody token.|  
|[DefineMethodImpl – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethodimpl-method.md)|Vytvoří definici pro implementaci metody zděděné z rozhraní a vrátí token této metody – definice implementace.|  
|[DefineModuleRef – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md)|Vytvoří podpis metadat pro modul se zadaným názvem.|  
|[DefineNestedType – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definenestedtype-method.md)|Vytvoří podpis metadat definice typu a vrátí `mdTypeDef` token pro daný typ. Kromě toho určuje, že definovaný typ je členem typu, na který odkazuje `tdEncloser`.|  
|[DefineParam – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md)|Vytvoří definici parametru se specifikovanou signaturou pro metodu, na kterou se odkazuje pomocí zadaného tokenu, a získá token pro tuto definici parametru.|  
|[DefinePermissionSet – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md)|Vytvoří definici sady oprávnění se zadaným podpisem metadat a získá token do této definice sady oprávnění.|  
|[DefinePinvokeMap – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md)|Nastaví funkce signatury PInvoke metody, na kterou odkazuje zadaný token.|  
|[DefineProperty – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md)|Vytvoří definici vlastnosti pro zadaný typ se zadanými přístupovými metodami metody `get` a `set` a získá token této definici vlastnosti.|  
|[DefineSecurityAttributeSet – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definesecurityattributeset-method.md)|Vytvoří sadu oprávnění zabezpečení pro připojení k objektu, na který odkazuje zadaný token.|  
|[DefineTypeDef – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)|Vytvoří definici typu pro typ modulu CLR (Common Language Runtime) a získá token metadat do této definice typu.|  
|[DefineTypeRefByName – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md)|Získá token metadat pro typ, který je definován v jiném modulu mimo aktuální obor.|  
|[DefineUserString – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md)|Získá token metadat pro zadaný řetězcový literál.|  
|[DeleteClassLayout – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deleteclasslayout-method.md)|Odstraní signaturu metadat rozložení třídy pro typ, na který odkazuje zadaný token.|  
|[DeleteFieldMarshal – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletefieldmarshal-method.md)|Odstraní signaturu zařazovacích metadat PInvoke pro objekt, na který odkazuje zadaný token.|  
|[DeletePinvokeMap – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletepinvokemap-method.md)|Zničí metadata mapování PInvoke pro objekt, na který odkazuje zadaný token.|  
|[DeleteToken – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletetoken-method.md)|Odstraní zadaný token z aktuálního oboru metadat.|  
|[GetSaveSize – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-getsavesize-method.md)|Získá odhadovanou binární velikost sestavení v aktuálním oboru.|  
|[GetTokenFromSig – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md)|Získá token pro zadaný podpis metadat.|  
|[GetTokenFromTypeSpec – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md)|Získá token metadat pro typ se zadaným podpisem metadat.|  
|[Merge – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)|Přidá zadaný importovaný obor do seznamu rozsahů, které se mají sloučit.|  
|[MergeEnd – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md)|Sloučí se do aktuálního oboru všech oborů metadat určených jedním nebo více předchozími voláními `IMetaDataEmit::Merge`.|  
|[Save – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-save-method.md)|Uloží všechna metadata v aktuálním oboru do souboru na zadané adrese.|  
|[SaveToMemory – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md)|Uloží všechna metadata v aktuálním oboru do zadané oblasti paměti.|  
|[SaveToStream – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md)|Uloží všechna metadata v aktuálním oboru do určeného `IStream`.|  
|[SetClassLayout – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md)|Nastaví nebo aktualizuje podpis rozložení třídy typu definovaného předchozím voláním `IMetaDataEmit::DefineTypeDef`.|  
|[SetCustomAttributeValue – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setcustomattributevalue-method.md)|Nastaví nebo aktualizuje hodnotu vlastního atributu definovaného předchozím voláním `IMetaDataEmit::DefineCustomAttribute`.|  
|[SetEventProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-seteventprops-method.md)|Nastaví nebo aktualizuje zadanou funkci události definované předchozím voláním `IMetaDataEmit::DefineEvent`.|  
|[SetFieldMarshal – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldmarshal-method.md)|Nastaví informace o zařazování PInvoke pro pole, návrat metody nebo parametr metody, na který odkazuje zadaný token.|  
|[SetFieldProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldprops-method.md)|Nastaví nebo aktualizuje výchozí hodnotu pro pole, na které se odkazuje pomocí zadaného tokenu pole.|  
|[SetFieldRVA – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldrva-method.md)|Nastaví hodnotu globální proměnné pro relativní virtuální adresu pole, na které odkazuje zadaný token.|  
|[SetHandler – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)|Nastaví metodu, na kterou odkazuje zadaný `IUnknown` ukazatel jako zpětné volání oznámení pro přemapování tokenů.|  
|[SetMethodImplFlags – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md)|Nastaví nebo aktualizuje podpis metadat zděděné implementace metody, na kterou odkazuje zadaný token.|  
|[SetMethodProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodprops-method.md)|Nastaví nebo aktualizuje funkci, uloženou na zadané relativní virtuální adrese, metody definované předchozím voláním `IMetaDataEmit::DefineMethod`.|  
|[SetModuleProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md)|Aktualizuje odkazy na modul definovaný předchozím voláním `IMetaDataEmit::DefineModuleRef`.|  
|[SetParamProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md)|Nastaví nebo změní funkce parametru metody, které byly definovány předchozím voláním `IMetaDataEmit::DefineParam`.|  
|[SetParent – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparent-method.md)|Určí, že zadaný člen, jak je definován předchozím voláním `IMetaDataEmit::DefineMemberRef`, je členem zadaného typu, jak je definováno předchozím voláním `IMetaDataEmit::DefineTypeDef`.|  
|[SetPermissionSetProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpermissionsetprops-method.md)|Nastaví nebo aktualizuje funkce podpisu metadat sady oprávnění definovaného předchozím voláním `IMetaDataEmit::DefinePermissionSet`.|  
|[SetPinvokeMap – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpinvokemap-method.md)|Nastaví nebo změní funkce signatury PInvoke metody definované předchozím voláním `IMetaDataEmit::DefinePinvokeMap`.|  
|[SetPropertyProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpropertyprops-method.md)|Nastaví funkce uložené v metadatech pro vlastnost definovanou předchozím voláním `IMetaDataEmit::DefineProperty`.|  
|[SetRVA – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md)|Nastaví relativní virtuální adresu zadané metody.|  
|[SetTypeDefProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-settypedefprops-method.md)|Nastaví funkce typu definovaného předchozím voláním `IMetaDataEmit::DefineTypeDef`.|  
|[TranslateSigWithScope – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-translatesigwithscope-method.md)|Importuje sestavení do aktuálního oboru a získá nový podpis metadat pro sloučený obor.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
