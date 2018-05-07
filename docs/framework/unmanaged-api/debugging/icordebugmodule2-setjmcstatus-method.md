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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a56b5c31c26dbe5c5371fdb7a10c13ad11847117
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmodule2setjmcstatus-method"></a>ICorDebugModule2::SetJMCStatus – metoda
Nastaví stav pouze můj kód (SVK) ze všech metod všechny třídy v této ICorDebugModule2 se zadanou hodnotou, s výjimkou těch, `pTokens` pole, které se nastaví na opačné hodnoty.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bIsJustMycode`  
 [v] Nastavte na `true` Pokud kód je být vyladěnou jinak, nastavit `false`.  
  
 `cTokens`  
 [v] Velikost `pTokens` pole.  
  
 `pTokens`  
 [v] Pole `mdToken` hodnoty, každý z nich odkazuje na metodu, která bude mít SVK stav nastavit na!`bIsJustMycode`.  
  
## <a name="remarks"></a>Poznámky  
 Stav SVK každá metoda, která je zadána v `pTokens` pole je nastaven na opakem `bIsJustMycode` hodnotu. Stav všech metod v tomto modulu nastaven na `bIsJustMycode` hodnotu.  
  
 `SetJMCStatus` Metoda vymaže všechna předchozí nastavení SVK v tomto modulu.  
  
 `SetJMCStatus` Metoda vrátí hodnotu S_OK HRESULT všechny funkce byla úspěšně nastavena. Vrátí CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT, pokud se některé funkce, které jsou označeny `true` nejsou debuggable.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
