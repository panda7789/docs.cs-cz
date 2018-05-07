---
title: IMetaDataDispenser::DefineScope – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.DefineScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::DefineScope
helpviewer_keywords:
- DefineScope method [.NET Framework metadata]
- IMetaDataDispenser::DefineScope method [.NET Framework metadata]
ms.assetid: af28db02-29af-45ac-aec6-8d6c6123c2ff
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 11382f00839917185ba3c85b8fbae5c32d0b0d4a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="imetadatadispenserdefinescope-method"></a>IMetaDataDispenser::DefineScope – metoda
Vytvoří novou oblast v paměti, ve kterém můžete vytvořit nová metadata.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DefineScope (  
    [in]  REFCLSID    rclsid,  
    [in]  DWORD       dwCreateFlags,  
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `rclsid`  
 [v] CLSID verzi struktury metadat, který se má vytvořit. Tato hodnota musí být CLSID_CorMetaDataRuntime pro rozhraní .NET Framework verze 2.0.  
  
 `dwCreateFlags`  
 [v] Příznaky, které určují možnosti. Tato hodnota musí být nula pro rozhraní .NET Framework 2.0.  
  
 `riid`  
 [v] Identifikátory IID rozhraní požadované metadata má být vrácen. volající použije k vytvoření nové metadat rozhraní.  
  
 Hodnota `riid` musíte zadat jednu z rozhraní "emitování". Platné hodnoty jsou IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit nebo IID_IMetaDataEmit2.  
  
 `ppIUnk`  
 [out] Ukazatel rozhraní vrácená.  
  
## <a name="remarks"></a>Poznámky  
 `DefineScope` Vytvoří sadu tabulek v paměti metadata, generuje jedinečný identifikátor GUID (identifikátor verze modulu nebo identifikátoru MVID) pro metadata a vytvoří záznam v tabulce modulu pro jednotku kompilace se vygenerované.  
  
 Atributy můžete připojit k oboru metadat jako celek s použitím [imetadataemit::setmoduleprops –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) nebo [imetadataemit::definecustomattribute –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md) metoda, podle potřeby.  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataDispenser – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [IMetaDataDispenserEx – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
