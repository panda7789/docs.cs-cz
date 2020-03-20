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
ms.openlocfilehash: 375c4b2cece0bdfd763ae383c5412c9e25614baf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177546"
---
# <a name="imetadataemitsethandler-method"></a>IMetaDataEmit::SetHandler – metoda
Nastaví metodu, na `IUnknown` kterou zadaný ukazatel odkazuje jako zpětné volání oznámení pro přemapování tokenů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetHandler (
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pUnk`  
 [v] Obslužná rutina k registraci.  
  
## <a name="remarks"></a>Poznámky  
 Modul metadat odešle oznámení pomocí metody, která `SetHandler`je poskytována aplikace , kompilátorům, které negenerují záznamy optimalizovaným způsobem a které by chtěly optimalizovat uložené záznamy.  
  
 Pokud metoda zpětného volání není `SetHandler`k dispozici prostřednictvím , žádná optimalizace bude provedena `IMapToken` na uložit s výjimkou případů, kdy několik oborů importu byly sloučeny pomocí sloučení pro každý obor.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
