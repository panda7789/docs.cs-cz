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
ms.openlocfilehash: 021ef8de602d6dd928f49e69e36f8d4a61425745
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008362"
---
# <a name="imetadatadispenserdefinescope-method"></a>IMetaDataDispenser::DefineScope – metoda
Vytvoří novou oblast v paměti, ve které můžete vytvořit nová metadata.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineScope (  
    [in]  REFCLSID    rclsid,  
    [in]  DWORD       dwCreateFlags,  
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `rclsid`  
 pro Identifikátor CLSID verze struktur metadat, které se mají vytvořit. Tato hodnota musí být CLSID_CorMetaDataRuntime pro .NET Framework verze 2,0.  
  
 `dwCreateFlags`  
 pro Příznaky, které určují možnosti. Tato hodnota musí být nula pro .NET Framework 2,0.  
  
 `riid`  
 pro Identifikátor IID požadovaného rozhraní metadat, které má být vráceno; Volající použije rozhraní k vytvoření nových metadat.  
  
 Hodnota `riid` musí určovat jedno z rozhraní Emit. Platné hodnoty jsou IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit nebo IID_IMetaDataEmit2.  
  
 `ppIUnk`  
 mimo Ukazatel na vrácené rozhraní.  
  
## <a name="remarks"></a>Poznámky  
 `DefineScope`Vytvoří sadu tabulek metadat v paměti, vygeneruje jedinečný identifikátor GUID (identifikátor verze modulu nebo identifikátor MVID) pro metadata a vytvoří položku v tabulce modulů pro vygenerování kompilační jednotky.  
  
 Atributy můžete k oboru metadat připojit jako celek pomocí metody [IMetaDataEmit:: SetModuleProps –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) nebo [IMetaDataEmit::D efinecustomattribute](imetadataemit-definecustomattribute-method.md) , podle potřeby.  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataDispenser – rozhraní](imetadatadispenser-interface.md)
- [IMetaDataDispenserEx – rozhraní](imetadatadispenserex-interface.md)
- [IMetaDataAssemblyEmit – rozhraní](imetadataassemblyemit-interface.md)
- [IMetaDataEmit – rozhraní](imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](imetadataemit2-interface.md)
