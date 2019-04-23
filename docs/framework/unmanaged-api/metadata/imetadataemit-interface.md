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
ms.openlocfilehash: 10942541b781d367820301588656b2f1fc2fd006
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59184415"
---
# <a name="imetadataemit-interface"></a>IMetaDataEmit – rozhraní
Poskytuje metody pro vytváření, úpravě a uložit metadata o sestavení v současné době definovaného oboru. Metadata dá uložené v paměti nebo uložit na disk.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ApplyEditAndContinue – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md)|Aktualizuje aktuální obor sestavení změny provedené v zadaném `pImport`.|  
|[DefineCustomAttribute – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md)|Vytvoří definici vlastního atributu podpisem Zadaná metadata, připojí se k zadaný objekt a získá token pro tuto definici vlastního atributu.|  
|[DefineEvent – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md)|Vytvoří definici pro události s podpisem Zadaná metadata a získá token pro tuto definici událostí.|  
|[DefineField – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definefield-method.md)|Vytvoří definici pro pole s podpisem Zadaná metadata a získá token pro tuto definici pole.|  
|[DefineImportMember – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md)|Vytvoří definici pro člena typu, který je definovaný v modulu mimo aktuální obor a získá token pro tento odkaz na definici.|  
|[DefineImportType – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)|Vytvoří definici odkazu na typ, který je definovaný v modulu mimo aktuální obor a získá token pro tuto definici odkazu.|  
|[DefineMemberRef – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md)|Vytvoří definici pro odkaz na člena modulu mimo aktuální obor a získá token pro tuto definici odkazu.|  
|[DefineMethod – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md)|Vytvoří definici metody se zadaným podpisem a vrátí token k definici této metody.|  
|[DefineMethodImpl – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethodimpl-method.md)|Vytvoří definici pro implementaci metody zděděné z rozhraní a vrátí token k definici této implementace metody.|  
|[DefineModuleRef – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md)|Vytvoří podpis metadat pro modul se zadaným názvem.|  
|[DefineNestedType – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definenestedtype-method.md)|Vytvoří metadata podpis definici typu a vrátí `mdTypeDef` token daného typu, kromě určení, že definovaný typ je členem typu odkazuje `tdEncloser`.|  
|[DefineParam – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md)|Vytvoří definici parametru se zadaným podpisem pro metodu odkazuje zadaný token a získá token pro tuto definici parametru.|  
|[DefinePermissionSet – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md)|Vytvoří definici sada oprávnění s podpisem Zadaná metadata a získá token pro tuto definici sady oprávnění.|  
|[DefinePinvokeMap – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md)|Nastaví funkce PInvoke podpis metody odkazuje zadaný token.|  
|[DefineProperty – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md)|Vytvoří definici vlastností pro zadaný typ se zadaným `get` a `set` metoda přístupové objekty a získá token pro tuto definici vlastnosti.|  
|[DefineSecurityAttributeSet – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definesecurityattributeset-method.md)|Vytvoří sadu oprávnění zabezpečení k připojení k objekt odkazovaný zadaným parametrem zadaného tokenu.|  
|[DefineTypeDef – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)|Vytvoří definici typu pro společný typ modulu runtime jazyka a získá token metadat pro tuto definici typu.|  
|[DefineTypeRefByName – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md)|Získá token metadat pro typ, který je definován v jiném modulu mimo aktuální rozsah.|  
|[DefineUserString – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md)|Získá token metadat zadaného řetězcového literálu.|  
|[DeleteClassLayout – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deleteclasslayout-method.md)|Zničí podpis metadat rozložení třídy pro typ odkázal: Zadaný token.|  
|[DeleteFieldMarshal – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletefieldmarshal-method.md)|Zničí PInvoke zařazování podpis metadat pro objekt odkazovaný zadaným parametrem zadaného tokenu.|  
|[DeletePinvokeMap – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletepinvokemap-method.md)|Zničí metadat PInvoke mapování pro objekt odkazovaný zadaným parametrem zadaného tokenu.|  
|[DeleteToken – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletetoken-method.md)|Odstraní zadaný token z aktuálního rozsahu metadat.|  
|[GetSaveSize – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-getsavesize-method.md)|Získá odhadovaná velikost binárního sestavení v aktuálním oboru.|  
|[GetTokenFromSig – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md)|Získá token pro Zadaná metadata podpis.|  
|[GetTokenFromTypeSpec – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md)|Získá token metadat pro typ s podpisem Zadaná metadata.|  
|[Merge – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)|Přidá do seznamu oborů, která se má sloučit zadané importované oboru.|  
|[MergeEnd – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md)|Sloučení do aktuální obor oborů metadat zadán jeden nebo více předchozích volání `IMetaDataEmit::Merge`.|  
|[Save – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-save-method.md)|Uloží všechna metadata v aktuálním oboru k souboru na zadané adrese.|  
|[SaveToMemory – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md)|Uloží všechna metadata v aktuálním oboru k zadané oblasti paměti.|  
|[SaveToStream – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md)|Uloží všechna metadata v aktuálním oboru na zadaný `IStream`.|  
|[SetClassLayout – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md)|Nastaví nebo aktualizuje podpis rozložení třídy z typu definované v předchozím volání `IMetaDataEmit::DefineTypeDef`.|  
|[SetCustomAttributeValue – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setcustomattributevalue-method.md)|Nastaví nebo aktualizuje hodnotu vlastního atributu určené předchozím volání `IMetaDataEmit::DefineCustomAttribute`.|  
|[SetEventProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-seteventprops-method.md)|Nastaví nebo aktualizuje zadanou funkci události definované v předchozím volání `IMetaDataEmit::DefineEvent`.|  
|[SetFieldMarshal – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldmarshal-method.md)|Nastaví PInvoke zařazovací informace pro parametr pole, metoda návratový nebo metoda odkazuje zadaný token.|  
|[SetFieldProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldprops-method.md)|Nastaví nebo aktualizuje výchozí hodnota pro pole odkazuje token zadaného pole.|  
|[SetFieldRVA – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldrva-method.md)|Nastaví hodnotu globální proměnné pro relativní virtuální adresu pole odkazuje zadaný token.|  
|[SetHandler – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)|Nastaví metodu odkazuje zadaný `IUnknown` ukazatele jako zpětné volání oznámení pro token přemapování.|  
|[SetMethodImplFlags – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md)|Nastaví nebo aktualizuje podpis implementace zděděné metody odkazuje zadaný token metadat.|  
|[SetMethodProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodprops-method.md)|Nastaví nebo aktualizuje funkci uložen na zadané relativní virtuální adrese, určené předchozí volání metody `IMetaDataEmit::DefineMethod`.|  
|[SetModuleProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md)|Aktualizace odkazů na definované předchozím volání modulu `IMetaDataEmit::DefineModuleRef`.|  
|[SetParamProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md)|Nastavuje nebo mění parametru metody, která byla definována v předchozím volání funkce `IMetaDataEmit::DefineParam`.|  
|[SetParent – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparent-method.md)|Zjistí, že zadaný člen podle předchozího volání `IMetaDataEmit::DefineMemberRef`, je členem zadaného typu definované předchozím volání `IMetaDataEmit::DefineTypeDef`.|  
|[SetPermissionSetProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpermissionsetprops-method.md)|Nastaví nebo aktualizuje podpis metadat sady oprávnění určené předchozím volání funkce `IMetaDataEmit::DefinePermissionSet`.|  
|[SetPinvokeMap – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpinvokemap-method.md)|Nastavuje nebo mění určené předchozím volání funkce PInvoke signatury metody, `IMetaDataEmit::DefinePinvokeMap`.|  
|[SetPropertyProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpropertyprops-method.md)|Nastaví uložená v metadatech pro vlastnosti určené předchozím volání funkce `IMetaDataEmit::DefineProperty`.|  
|[SetRVA – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md)|Nastaví relativní virtuální adresu určenou metodu.|  
|[SetTypeDefProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-settypedefprops-method.md)|Nastaví funkce typu definované v předchozím volání `IMetaDataEmit::DefineTypeDef`.|  
|[TranslateSigWithScope – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-translatesigwithscope-method.md)|Importuje sestavení do aktuální obor a získá nový podpis metadat pro sloučený obor.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
