---
title: "IMetaDataEmit – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit
helpviewer_keywords: IMetaDataEmit interface [.NET Framework metadata]
ms.assetid: 3b48fd47-7397-4e2c-8bec-8157aa08978c
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b62e11f8237330122ccd2bd8775f8d113545dd95
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemit-interface"></a>IMetaDataEmit – rozhraní
Poskytuje metody pro vytváření, úpravě a uložit metadata o sestavení v aktuálně definován obor. Metadata dá uložené v paměti nebo uložit na disk.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Applyeditandcontinue – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md)|Aktualizuje aktuální obor sestavení se změny provedené v zadané `pImport`.|  
|[Definecustomattribute – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md)|Vytvoří definici pro vlastní atribut podpisem Zadaná metadata, připojí se k zadaný objekt a získá token tuto definici vlastních atributů.|  
|[Defineevent – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md)|Vytvoří definici pro události s podpisem Zadaná metadata a získá token tuto definici událostí.|  
|[Definefield – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definefield-method.md)|Vytvoří definici pole s podpisem Zadaná metadata a získá token tuto definici pole.|  
|[Defineimportmember – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md)|Vytvoří definici pro člena typu, který je definován v modulu mimo aktuální obor a získá token pro tuto referenční definice.|  
|[Defineimporttype – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)|Vytvoří definici pro odkaz na typ, který je definován v modulu mimo aktuální obor a získá token pro tuto referenční definice.|  
|[Definememberref – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md)|Vytvoří definici pro odkaz na člena modulu mimo aktuální obor a získá token pro tuto referenční definice.|  
|[DefineMethod – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md)|Vytvoří definici pro metodu podpisem zadané a vrátí token tuto definici metody.|  
|[Definemethodimpl – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethodimpl-method.md)|Vytvoří definici implementace metody zděděno z rozhraní a vrátí token tuto definici implementace metod.|  
|[Definemoduleref – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md)|Vytvoří metadata podpis pro modul se zadaným názvem.|  
|[Definenestedtype – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definenestedtype-method.md)|Vytvoří metadata podpis definice typu a vrátí `mdTypeDef` tokenu pro tento typ, kromě určení, že definovaný typ je člen typu odkazuje `tdEncloser`.|  
|[Defineparam – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md)|Vytvoří definici parametru podpisem zadaný pro metodu odkazuje zadaný token a získá token pro tuto definici parametru.|  
|[Definepermissionset – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md)|Vytvoří definici oprávnění nastavit podpisem Zadaná metadata a získá token pro tuto definici sady oprávnění.|  
|[Definepinvokemap – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md)|Nastaví funkce PInvoke podpis metody odkazuje zadaný token.|  
|[Defineproperty – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md)|Vytvoří definici vlastnosti pro zadaný typ se zadaným `get` a `set` metody přístupových objektů a získá token pro tuto definici vlastnosti.|  
|[Definesecurityattributeset – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definesecurityattributeset-method.md)|Vytvoří sadu oprávnění zabezpečení pro připojení k objektu, který odkazuje zadaný token.|  
|[Definetypedef – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)|Vytvoří definici typu pro běžné typ modulu runtime jazyka a získá token metadata pro tuto definici typu.|  
|[Definetyperefbyname – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md)|Získá token metadat pro typ, který je definován v jiném modulu mimo aktuální obor.|  
|[Defineuserstring – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md)|Získá token metadata pro zadanou řetězcového literálu.|  
|[Deleteclasslayout – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deleteclasslayout-method.md)|Zničí podpis třída rozložení metadata pro typ, který odkazuje zadaný token.|  
|[Deletefieldmarshal – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletefieldmarshal-method.md)|Zničí PInvoke zařazování podpis metadata pro objekt, který odkazuje zadaný token.|  
|[Deletepinvokemap – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletepinvokemap-method.md)|Zničí metadata PInvoke mapování pro objekt, který odkazuje zadaný token.|  
|[Deletetoken – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletetoken-method.md)|Odstraní zadaný token z aktuálního oboru metadat.|  
|[Getsavesize – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-getsavesize-method.md)|Získá odhadovanou velikost binární sestavení v aktuálním oboru.|  
|[Gettokenfromsig – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md)|Získá token pro podpis Zadaná metadata.|  
|[Gettokenfromtypespec – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md)|Získá token metadat pro typ s podpisem Zadaná metadata.|  
|[Merge – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)|Zadaný obor importované přidá do seznamu oborů, který se má sloučit.|  
|[Mergeend – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md)|Sloučení do aktuální obor všechny obory metadata určeného jeden nebo více předchozích volání `IMetaDataEmit::Merge`.|  
|[Save – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-save-method.md)|Uloží všechna metadata v aktuálním oboru do souboru na zadané adrese.|  
|[Savetomemory – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md)|Uloží všechna metadata v aktuálním oboru do určené oblasti paměti.|  
|[Savetostream – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md)|Uloží všechna metadata v aktuálním oboru do zadané `IStream`.|  
|[Setclasslayout – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md)|Nastaví nebo aktualizuje podpis rozložení – třída typu definované předchozí volání `IMetaDataEmit::DefineTypeDef`.|  
|[Setcustomattributevalue – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setcustomattributevalue-method.md)|Nastaví nebo aktualizuje hodnota vlastního atributu definované předchozí volání `IMetaDataEmit::DefineCustomAttribute`.|  
|[Seteventprops – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-seteventprops-method.md)|Nastaví nebo aktualizuje určenou funkci události definované předchozí volání `IMetaDataEmit::DefineEvent`.|  
|[Setfieldmarshal – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldmarshal-method.md)|Nastaví PInvoke zařazování informace pro parametr pole, metoda návratový nebo metoda odkazuje zadaný token.|  
|[Setfieldprops – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldprops-method.md)|Nastaví nebo aktualizuje výchozí hodnota pro pole odkazuje token zadané pole.|  
|[Setfieldrva – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldrva-method.md)|Nastaví hodnotu globální proměnné pro relativní virtuální adresu pole odkazuje zadaný token.|  
|[Sethandler – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)|Nastaví metodu, která odkazuje zadanou `IUnknown` ukazatel jako zpětné volání oznámení pro token přemapuje.|  
|[Setmethodimplflags – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md)|Nastaví nebo aktualizuje podpis metadata implementace zděděné metody odkazuje zadaný token.|  
|[Setmethodprops – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodprops-method.md)|Nastaví nebo aktualizuje funkce, které jsou uložené na zadaný relativní virtuální na adrese definované předchozí volání metody `IMetaDataEmit::DefineMethod`.|  
|[Setmoduleprops – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md)|Aktualizace odkazů na modul definované předchozí volání `IMetaDataEmit::DefineModuleRef`.|  
|[Setparamprops – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md)|Nastaví nebo změny funkcí parametru metody, která byla definována voláním předchozí `IMetaDataEmit::DefineParam`.|  
|[Setparent – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparent-method.md)|Zjistí, že zadaný člen, jak je definována předchozí volání `IMetaDataEmit::DefineMemberRef`, je členem skupiny zadaný typ podle definice předchozí volání `IMetaDataEmit::DefineTypeDef`.|  
|[Setpermissionsetprops – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpermissionsetprops-method.md)|Nastaví nebo aktualizuje funkce metadata podpis sadu oprávnění definovanou před voláním `IMetaDataEmit::DefinePermissionSet`.|  
|[Setpinvokemap – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpinvokemap-method.md)|Nastaví nebo změny funkcí metoda PInvoke podpis, podle definice předchozí volání `IMetaDataEmit::DefinePinvokeMap`.|  
|[Setpropertyprops – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpropertyprops-method.md)|Nastaví uložené v metadata pro vlastnost definovanou před voláním funkce `IMetaDataEmit::DefineProperty`.|  
|[Setrva – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md)|Nastaví relativní virtuální adresu zadanou metodu.|  
|[Settypedefprops – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-settypedefprops-method.md)|Nastaví funkce typu definované předchozí volání `IMetaDataEmit::DefineTypeDef`.|  
|[Translatesigwithscope – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-translatesigwithscope-method.md)|Importuje sestavení do aktuální obor a získá nové podpis metadata pro sloučené obor.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní metadat](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [Imetadataemit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
