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
ms.openlocfilehash: 4fa227d18b8cb10936d93fda9bcaf413ce63ca3b
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003932"
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
 Modul metadat odesílá oznámení pomocí metody, která je poskytována `SetHandler` , na kompilátory, které negenerují záznamy optimalizovaným způsobem a které by chtěli optimalizovat uložené záznamy.  
  
 Pokud není metoda zpětného volání poskytována prostřednictvím `SetHandler` , nebude provedena žádná optimalizace při uložení, s výjimkou případů, kdy byl pro každý obor sloučeno několik importovaných oborů pomocí `IMapToken` sloučení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataEmit – rozhraní](imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](imetadataemit2-interface.md)
