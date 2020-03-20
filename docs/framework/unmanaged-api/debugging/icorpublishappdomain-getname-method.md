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
ms.openlocfilehash: 762c637696fdf79ccab6702918b5bf962ea55903
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178408"
---
# <a name="icorpublishappdomaingetname-method"></a>ICorPublishAppDomain::GetName – metoda
Získá název domény aplikace, která je reprezentována touto [ICorPublishAppDomain](icorpublishappdomain-interface.md).  
  
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
 [v] Velikost `szName` pole.  
  
 `pcchName`  
 [out] Ukazatel na počet širokých znaků, včetně znaku `szName` null, vráceného v poli.  
  
 `szName`  
 [out] Pole, do kterého chcete uložit název.  
  
## <a name="remarks"></a>Poznámky  
 Pokud `szName` je non-null, `GetName` metoda `cchName` zkopíruje až znaky (včetně zakončení null) do `szName`. Pokud je vrácena hodnota `pcchName`non-null , je v `szName` poli uložen skutečný počet znaků v názvu (včetně zakončení null).  
  
 Metoda `GetName` vrátí S_OK HRESULT bez ohledu na to, kolik znaků bylo zkopírováno.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorPub.idl, CorPub.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorPublishAppDomain – rozhraní](icorpublishappdomain-interface.md)
