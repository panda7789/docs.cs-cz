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
ms.openlocfilehash: d438123dcefb901098954845596c210e5b76cea6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764103"
---
# <a name="icordebugmodule2setjmcstatus-method"></a>ICorDebugModule2::SetJMCStatus – metoda
Nastaví stav pouze můj kód (JMC) všech metod všechny třídy v tomto icordebugmodule2 – se zadanou hodnotou, s výjimkou těch, `pTokens` pole, které se nastaví na opačnou hodnotu.  
  
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
 [in] Nastavte na `true` Pokud bude ladění; v opačném případě je kód, nastavte na `false`.  
  
 `cTokens`  
 [in] Velikost `pTokens` pole.  
  
 `pTokens`  
 [in] Pole `mdToken` hodnot, z nichž každý odkazuje na metodu, která budou mít stav JMC nastavena na!`bIsJustMycode`.  
  
## <a name="remarks"></a>Poznámky  
 JMC stav každé metody, ve stanoveném `pTokens` pole nastavena na opak `bIsJustMycode` hodnotu. Je nastaven stav všech metod v tomto modulu `bIsJustMycode` hodnotu.  
  
 `SetJMCStatus` Metoda vymaže všechna předchozí nastavení JMC v tomto modulu.  
  
 `SetJMCStatus` Metoda vrátí hodnotu S_OK HRESULT, pokud všechny funkce byly úspěšně nastavené. Vrátí hodnotu HRESULT CORDBG_E_FUNCTION_NOT_DEBUGGABLE Pokud některé funkce, které jsou označeny `true` nejsou laditelný.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
