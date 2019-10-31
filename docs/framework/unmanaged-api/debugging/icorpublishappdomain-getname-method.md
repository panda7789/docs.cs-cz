---
title: ICorPublishAppDomain::GetName – metoda
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomain.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomain::GetName
helpviewer_keywords:
- GetName method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetName method [.NET Framework debugging]
ms.assetid: 6ef8ac9b-9803-4b65-8b13-25f3e0b1bc6b
topic_type:
- apiref
ms.openlocfilehash: 2f91891164f1f80617cab10347eb4a7a08762c10
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140349"
---
# <a name="icorpublishappdomaingetname-method"></a>ICorPublishAppDomain::GetName – metoda
Získá název domény aplikace, která je reprezentovaná tímto [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32   cchName,   
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR       *szName  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cchName`  
 pro Velikost pole `szName`.  
  
 `pcchName`  
 mimo Ukazatel na počet velkých znaků, včetně znaku null, vrácený v poli `szName`.  
  
 `szName`  
 mimo Pole, do kterého se má uložit název  
  
## <a name="remarks"></a>Poznámky  
 Pokud `szName` není null, metoda `GetName` kopíruje až `cchName` znaky (včetně ukončovacího znaku null) do `szName`. Pokud je v `pcchName`vrácena hodnota, která není null, je v poli `szName` uložen skutečný počet znaků v názvu (včetně ukončovacího znaku null).  
  
 Metoda `GetName` vrátí hodnotu S_OK HRESULT bez ohledu na to, kolik znaků bylo kopírováno.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorPub. idl, CorPub. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorPublishAppDomain – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)
