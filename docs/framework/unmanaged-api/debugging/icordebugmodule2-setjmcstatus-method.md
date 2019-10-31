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
ms.openlocfilehash: a0b70078dee88b270d8361aa9bddcb7d80df1db1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129474"
---
# <a name="icordebugmodule2setjmcstatus-method"></a>ICorDebugModule2::SetJMCStatus – metoda
Nastaví Pouze můj kód (JMC) pro všechny metody všech tříd v této ICorDebugModule2 na zadanou hodnotu, s výjimkou těch v poli `pTokens`, která nastavuje na opačnou hodnotu.  
  
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
 pro Nastavte na `true`, pokud se má ladit kód. v opačném případě nastavte na `false`.  
  
 `cTokens`  
 pro Velikost pole `pTokens`.  
  
 `pTokens`  
 pro Pole hodnot `mdToken`, z nichž každá odkazuje na metodu, která bude mít stav JMC nastaven na hodnotu!`bIsJustMycode`.  
  
## <a name="remarks"></a>Poznámky  
 Stav JMC každé metody, která je určena v poli `pTokens`, je nastaven na opak hodnoty `bIsJustMycode`. Stav všech ostatních metod v tomto modulu je nastaven na hodnotu `bIsJustMycode`.  
  
 Metoda `SetJMCStatus` vymaže všechna předchozí nastavení JMC v tomto modulu.  
  
 Metoda `SetJMCStatus` vrací hodnotu S_OK HRESULT, pokud byly všechny funkce úspěšně nastaveny. Vrátí CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT, pokud některé funkce, které jsou označeny `true`, nelze ladit.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
