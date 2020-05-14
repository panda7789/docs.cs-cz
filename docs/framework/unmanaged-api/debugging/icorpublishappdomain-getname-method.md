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
ms.openlocfilehash: e95f96847c6e069758362fb6febc28dc31911bc9
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396301"
---
# <a name="icorpublishappdomaingetname-method"></a>ICorPublishAppDomain::GetName – metoda
Získá název domény aplikace, která je reprezentovaná tímto [ICorPublishAppDomain](icorpublishappdomain-interface.md).  
  
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
 pro Velikost `szName` pole.  
  
 `pcchName`  
 mimo Ukazatel na počet velkých znaků, včetně znaku null, vrácený v `szName` poli.  
  
 `szName`  
 mimo Pole, do kterého se má uložit název  
  
## <a name="remarks"></a>Poznámky  
 Pokud `szName` je hodnota null, `GetName` Metoda zkopíruje až `cchName` znaků (včetně ukončovacího znaku null) do `szName` . Pokud je vrácena jiná hodnota než null `pcchName` , je v poli uložen skutečný počet znaků v názvu (včetně ukončovacího znaku null) `szName` .  
  
 `GetName`Metoda vrátí S_OK HRESULT bez ohledu na to, kolik znaků bylo kopírováno.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorPub. idl, CorPub. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorPublishAppDomain – rozhraní](icorpublishappdomain-interface.md)
