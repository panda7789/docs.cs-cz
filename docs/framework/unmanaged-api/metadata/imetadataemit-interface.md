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
ms.openlocfilehash: a2c2512abc28f0140fc261c5136c7e1255db96de
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009207"
---
# <a name="imetadataemit-interface"></a>IMetaDataEmit – rozhraní
Poskytuje metody pro vytváření, úpravy a ukládání metadat sestavení v aktuálně definovaném oboru. Metadata se můžou ukládat do paměti nebo ukládat na disk.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[ApplyEditAndContinue – metoda](imetadataemit-applyeditandcontinue-method.md)|Aktualizuje aktuální obor sestavení o změny provedené v zadaném `pImport` .|  
|[DefineCustomAttribute – metoda](imetadataemit-definecustomattribute-method.md)|Vytvoří definici pro vlastní atribut se zadaným podpisem metadat, který se má připojit k zadanému objektu, a získá token do této definice vlastního atributu.|  
|[DefineEvent – metoda](imetadataemit-defineevent-method.md)|Vytvoří definici události se zadaným podpisem metadat a získá token této definice události.|  
|[DefineField – metoda](imetadataemit-definefield-method.md)|Vytvoří definici pro pole se zadaným podpisem metadat a získá token do této definice pole.|  
|[DefineImportMember – metoda](imetadataemit-defineimportmember-method.md)|Vytvoří definici pro člena typu, který je definován v modulu mimo aktuální rozsah, a získá token pro tuto definici odkazu.|  
|[DefineImportType – metoda](imetadataemit-defineimporttype-method.md)|Vytvoří definici pro odkaz na typ, který je definován v modulu mimo aktuální rozsah, a získá token do této referenční definice.|  
|[DefineMemberRef – metoda](imetadataemit-definememberref-method.md)|Vytvoří definici pro odkaz na člena modulu mimo aktuální rozsah a získá token do této referenční definice.|  
|[DefineMethod – metoda](imetadataemit-definemethod-method.md)|Vytvoří definici metody se zadaným podpisem a vrátí do této definice metody token.|  
|[DefineMethodImpl – metoda](imetadataemit-definemethodimpl-method.md)|Vytvoří definici pro implementaci metody zděděné z rozhraní a vrátí token této metody – definice implementace.|  
|[DefineModuleRef – metoda](imetadataemit-definemoduleref-method.md)|Vytvoří podpis metadat pro modul se zadaným názvem.|  
|[DefineNestedType – metoda](imetadataemit-definenestedtype-method.md)|Vytvoří podpis metadat definice typu a vrátí `mdTypeDef` token pro tento typ, navíc určení, že definovaný typ je členem typu, na který odkazuje `tdEncloser` .|  
|[DefineParam – metoda](imetadataemit-defineparam-method.md)|Vytvoří definici parametru se specifikovanou signaturou pro metodu, na kterou se odkazuje pomocí zadaného tokenu, a získá token pro tuto definici parametru.|  
|[DefinePermissionSet – metoda](imetadataemit-definepermissionset-method.md)|Vytvoří definici sady oprávnění se zadaným podpisem metadat a získá token do této definice sady oprávnění.|  
|[DefinePinvokeMap – metoda](imetadataemit-definepinvokemap-method.md)|Nastaví funkce signatury PInvoke metody, na kterou odkazuje zadaný token.|  
|[DefineProperty – metoda](imetadataemit-defineproperty-method.md)|Vytvoří definici vlastnosti pro zadaný typ se zadaným `get` a přístupovým objektem `set` metody a získá token do této definice vlastnosti.|  
|[DefineSecurityAttributeSet – metoda](imetadataemit-definesecurityattributeset-method.md)|Vytvoří sadu oprávnění zabezpečení pro připojení k objektu, na který odkazuje zadaný token.|  
|[DefineTypeDef – metoda](imetadataemit-definetypedef-method.md)|Vytvoří definici typu pro typ modulu CLR (Common Language Runtime) a získá token metadat do této definice typu.|  
|[DefineTypeRefByName – metoda](imetadataemit-definetyperefbyname-method.md)|Získá token metadat pro typ, který je definován v jiném modulu mimo aktuální obor.|  
|[DefineUserString – metoda](imetadataemit-defineuserstring-method.md)|Získá token metadat pro zadaný řetězcový literál.|  
|[DeleteClassLayout – metoda](imetadataemit-deleteclasslayout-method.md)|Odstraní signaturu metadat rozložení třídy pro typ, na který odkazuje zadaný token.|  
|[DeleteFieldMarshal – metoda](imetadataemit-deletefieldmarshal-method.md)|Odstraní signaturu zařazovacích metadat PInvoke pro objekt, na který odkazuje zadaný token.|  
|[DeletePinvokeMap – metoda](imetadataemit-deletepinvokemap-method.md)|Zničí metadata mapování PInvoke pro objekt, na který odkazuje zadaný token.|  
|[DeleteToken – metoda](imetadataemit-deletetoken-method.md)|Odstraní zadaný token z aktuálního oboru metadat.|  
|[GetSaveSize – metoda](imetadataemit-getsavesize-method.md)|Získá odhadovanou binární velikost sestavení v aktuálním oboru.|  
|[GetTokenFromSig – metoda](imetadataemit-gettokenfromsig-method.md)|Získá token pro zadaný podpis metadat.|  
|[GetTokenFromTypeSpec – metoda](imetadataemit-gettokenfromtypespec-method.md)|Získá token metadat pro typ se zadaným podpisem metadat.|  
|[Merge – metoda](imetadataemit-merge-method.md)|Přidá zadaný importovaný obor do seznamu rozsahů, které se mají sloučit.|  
|[MergeEnd – metoda](imetadataemit-mergeend-method.md)|Sloučí se do aktuálního oboru všech oborů metadat určených jedním nebo více předchozími voláními `IMetaDataEmit::Merge` .|  
|[Save – metoda](imetadataemit-save-method.md)|Uloží všechna metadata v aktuálním oboru do souboru na zadané adrese.|  
|[SaveToMemory – metoda](imetadataemit-savetomemory-method.md)|Uloží všechna metadata v aktuálním oboru do zadané oblasti paměti.|  
|[SaveToStream – metoda](imetadataemit-savetostream-method.md)|Uloží všechna metadata v aktuálním oboru do určeného `IStream` .|  
|[SetClassLayout – metoda](imetadataemit-setclasslayout-method.md)|Nastaví nebo aktualizuje podpis rozložení třídy typu definovaného předchozím voláním metody `IMetaDataEmit::DefineTypeDef` .|  
|[SetCustomAttributeValue – metoda](imetadataemit-setcustomattributevalue-method.md)|Nastaví nebo aktualizuje hodnotu vlastního atributu definovaného předchozím voláním metody `IMetaDataEmit::DefineCustomAttribute` .|  
|[SetEventProps – metoda](imetadataemit-seteventprops-method.md)|Nastaví nebo aktualizuje zadanou funkci události definované předchozím voláním metody `IMetaDataEmit::DefineEvent` .|  
|[SetFieldMarshal – metoda](imetadataemit-setfieldmarshal-method.md)|Nastaví informace o zařazování PInvoke pro pole, návrat metody nebo parametr metody, na který odkazuje zadaný token.|  
|[SetFieldProps – metoda](imetadataemit-setfieldprops-method.md)|Nastaví nebo aktualizuje výchozí hodnotu pro pole, na které se odkazuje pomocí zadaného tokenu pole.|  
|[SetFieldRVA – metoda](imetadataemit-setfieldrva-method.md)|Nastaví hodnotu globální proměnné pro relativní virtuální adresu pole, na které odkazuje zadaný token.|  
|[SetHandler – metoda](imetadataemit-sethandler-method.md)|Nastaví metodu, na kterou odkazuje zadaný `IUnknown` ukazatel jako zpětné volání oznámení pro přemapování tokenů.|  
|[SetMethodImplFlags – metoda](imetadataemit-setmethodimplflags-method.md)|Nastaví nebo aktualizuje podpis metadat zděděné implementace metody, na kterou odkazuje zadaný token.|  
|[SetMethodProps – metoda](imetadataemit-setmethodprops-method.md)|Nastaví nebo aktualizuje funkci, uloženou na zadané relativní virtuální adrese, metody definované předchozím voláním `IMetaDataEmit::DefineMethod` .|  
|[SetModuleProps – metoda](imetadataemit-setmoduleprops-method.md)|Aktualizuje odkazy na modul definovaný předchozím voláním metody `IMetaDataEmit::DefineModuleRef` .|  
|[SetParamProps – metoda](imetadataemit-setparamprops-method.md)|Nastaví nebo změní funkce parametru metody, které byly definovány předchozím voláním metody `IMetaDataEmit::DefineParam` .|  
|[SetParent – metoda](imetadataemit-setparent-method.md)|Stanoví, že zadaný člen, jak je definováno předchozím voláním `IMetaDataEmit::DefineMemberRef` , je členem zadaného typu, jak je definováno před voláním metody `IMetaDataEmit::DefineTypeDef` .|  
|[SetPermissionSetProps – metoda](imetadataemit-setpermissionsetprops-method.md)|Nastaví nebo aktualizuje funkce podpisu metadat sady oprávnění definované předchozím voláním metody `IMetaDataEmit::DefinePermissionSet` .|  
|[SetPinvokeMap – metoda](imetadataemit-setpinvokemap-method.md)|Nastaví nebo změní funkce signatury PInvoke metody, jak je definováno před voláním metody `IMetaDataEmit::DefinePinvokeMap` .|  
|[SetPropertyProps – metoda](imetadataemit-setpropertyprops-method.md)|Nastaví funkce uložené v metadatech pro vlastnost definovanou před voláním metody `IMetaDataEmit::DefineProperty` .|  
|[SetRVA – metoda](imetadataemit-setrva-method.md)|Nastaví relativní virtuální adresu zadané metody.|  
|[SetTypeDefProps – metoda](imetadataemit-settypedefprops-method.md)|Nastaví funkce typu definovaného předchozím voláním metody `IMetaDataEmit::DefineTypeDef` .|  
|[TranslateSigWithScope – metoda](imetadataemit-translatesigwithscope-method.md)|Importuje sestavení do aktuálního oboru a získá nový podpis metadat pro sloučený obor.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Rozhraní pro metadata](metadata-interfaces.md)
- [IMetaDataEmit2 – rozhraní](imetadataemit2-interface.md)
