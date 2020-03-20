---
title: ICorDebugAppDomain::GetName – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetName
helpviewer_keywords:
- ICorDebugAppDomain::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 02c596d7-00b0-4e2c-856b-5425158fcefd
topic_type:
- apiref
ms.openlocfilehash: 45d27fca888bdabedf197525c63dbd03af7ba1ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179093"
---
# <a name="icordebugappdomaingetname-method"></a>ICorDebugAppDomain::GetName – metoda
Získá název domény aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
         WCHAR              szName[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cchName`  
 [v] Velikost `szName` pole. Nastavte tuto hodnotu na nulu, aby tuto metodu v režimu dotazu.  
  
 `pcchName`  
 [out] Ukazatel na velikost názvu nebo počet znaků skutečně `szName`vrácených v . V režimu dotazu tato hodnota umožňuje volajícímu vědět, jak velké vyrovnávací paměti přidělit pro název.  
  
 `szName`  
 [out] Pole, které ukládá název domény aplikace.  
  
## <a name="remarks"></a>Poznámky  
 Ladicí program `GetName` volá metodu jednou získat velikost vyrovnávací paměti potřebné pro název. Ladicí program přidělí vyrovnávací paměť a potom volá metodu podruhé k vyplnění vyrovnávací paměti. První volání, chcete-li získat velikost názvu, se označuje jako *režim dotazu*.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
