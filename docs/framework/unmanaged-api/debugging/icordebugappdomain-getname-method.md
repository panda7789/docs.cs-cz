---
title: "ICorDebugAppDomain::GetName – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 62defcb4b7a2f143269c7f617b762e3419d55426
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomaingetname-method"></a>ICorDebugAppDomain::GetName – metoda
Získá název domény aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
         WCHAR              szName[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cchName`  
 [v] Velikost `szName` pole. Tuto hodnotu nastavte na nulu, tato metoda uvést do režimu dotazu.  
  
 `pcchName`  
 [out] Ukazatel na velikost název nebo počet znaků, které jsou ve skutečnosti, vrátí se v `szName`. V režimu dotazu, tato hodnota umožňuje volající vědět, jak velké vyrovnávací paměti k přidělení pro název.  
  
 `szName`  
 [out] Pole, které ukládá název domény aplikace.  
  
## <a name="remarks"></a>Poznámky  
 Ladicí program volá `GetName` metoda jednou se získat velikost vyrovnávací paměti potřebné pro název. Ladicí program přiděluje vyrovnávací paměť a pak zavolá metodu podruhé k vyplnění vyrovnávací paměti. První volání se získat velikost názvu, se označuje jako *režim dotazu*.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
