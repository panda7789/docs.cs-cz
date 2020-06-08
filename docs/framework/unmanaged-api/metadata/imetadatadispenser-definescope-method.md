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
ms.openlocfilehash: 12a32b5d2f0647ea2d9b696d08d6644e30be0c65
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501349"
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
  
 Atributy můžete k oboru metadat připojit jako celek pomocí metody [IMetaDataEmit:: SetModuleProps –](imetadataemit-setmoduleprops-method.md) nebo [IMetaDataEmit::D efinecustomattribute](imetadataemit-definecustomattribute-method.md) , podle potřeby.  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataDispenser – rozhraní](imetadatadispenser-interface.md)
- [IMetaDataDispenserEx – rozhraní](imetadatadispenserex-interface.md)
- [IMetaDataAssemblyEmit – rozhraní](imetadataassemblyemit-interface.md)
- [IMetaDataEmit – rozhraní](imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](imetadataemit2-interface.md)
