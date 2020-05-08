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
ms.openlocfilehash: 3db37576f5da7b26e7bd9d3343f8bb8b97f2ba82
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895232"
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
 pro Velikost `szName` pole. Nastavte tuto hodnotu na nula pro vložení této metody do režimu dotazu.  
  
 `pcchName`  
 mimo Ukazatel na velikost názvu nebo počet skutečně vrácených znaků `szName`. V režimu dotazu tato hodnota umožňuje volajícímu zjistit, jak velký má vyrovnávací paměť přidělit pro název.  
  
 `szName`  
 mimo Pole, ve kterém je uložen název domény aplikace.  
  
## <a name="remarks"></a>Poznámky  
 Ladicí program volá `GetName` metodu jednou, aby získala velikost vyrovnávací paměti potřebné pro název. Ladicí program přidělí vyrovnávací paměť a poté zavolá metodu za sekundu, aby vyplnila vyrovnávací paměť. První volání, pro získání velikosti názvu, je označováno jako *režim dotazu*.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
