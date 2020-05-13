---
title: ICorDebugModule2::SetJMCStatus – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::SetJMCStatus
helpviewer_keywords:
- SetJMCStatus method, ICorDebugModule2 interface [.NET Framework debugging]
- ICorDebugModule2::SetJMCStatus method [.NET Framework debugging]
ms.assetid: 8c6d2089-4dbb-4715-b9e9-2a4491c8c9ce
topic_type:
- apiref
ms.openlocfilehash: d5109043a8601d7997f52e88ea472644f1b9ca03
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208769"
---
# <a name="icordebugmodule2setjmcstatus-method"></a>ICorDebugModule2::SetJMCStatus – metoda
Nastaví Pouze můj kód (JMC) pro všechny metody všech tříd v této ICorDebugModule2 na zadanou hodnotu, s výjimkou těch v `pTokens` poli, které nastaví na opačnou hodnotu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `bIsJustMycode`  
 pro Nastavte na, `true` Pokud má být kód laděn. jinak nastavte na `false` .  
  
 `cTokens`  
 pro Velikost `pTokens` pole.  
  
 `pTokens`  
 pro Pole `mdToken` hodnot, z nichž každá odkazuje na metodu, která bude mít stav JMC nastaven na! `bIsJustMycode` .  
  
## <a name="remarks"></a>Poznámky  
 Stav JMC jednotlivých metod, které jsou zadány v `pTokens` poli, je nastaven na opak `bIsJustMycode` hodnoty. Stav všech ostatních metod v tomto modulu je nastaven na `bIsJustMycode` hodnotu.  
  
 `SetJMCStatus`Metoda vymaže všechna předchozí nastavení JMC v tomto modulu.  
  
 `SetJMCStatus`Metoda vrátí S_OK HRESULT, pokud byly všechny funkce nastaveny úspěšně. Vrátí CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT, pokud některé funkce, které jsou označeny, `true` nelze ladit.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
