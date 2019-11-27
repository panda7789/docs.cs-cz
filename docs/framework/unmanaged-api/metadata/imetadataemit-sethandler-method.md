---
title: IMetaDataEmit::SetHandler – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetHandler
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetHandler
helpviewer_keywords:
- IMetaDataEmit::SetHandler method [.NET Framework metadata]
- SetHandler method [.NET Framework metadata]
ms.assetid: c6c1aaaf-e2cd-407c-b73e-fbe6ffd83bb3
topic_type:
- apiref
ms.openlocfilehash: 6737275fb77e6f177832eb1d96214c37942bcd22
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442151"
---
# <a name="imetadataemitsethandler-method"></a>IMetaDataEmit::SetHandler – metoda
Nastaví metodu, na kterou odkazuje zadaný `IUnknown` ukazatel jako zpětné volání oznámení pro přemapování tokenů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetHandler (   
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pUnk`  
 pro Obslužná rutina, která se má zaregistrovat  
  
## <a name="remarks"></a>Poznámky  
 Modul metadat odesílá oznámení pomocí metody, která je poskytována `SetHandler`, kompilátorům, které negenerují záznamy optimalizovaným způsobem a které by chtěli optimalizovat uložené záznamy.  
  
 Pokud metoda zpětného volání není k dispozici prostřednictvím `SetHandler`, nebude provedena žádná optimalizace s výjimkou případů, kdy byl pro každý obor sloučeno několik importovaných oborů pomocí `IMapToken` při sloučení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
