---
title: ICorDebugClass2::SetJMCStatus – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugClass2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2::SetJMCStatus
helpviewer_keywords:
- ICorDebugClass2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 077e6c7f-f857-480c-bebb-76ee1de4e8fc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d234e01e3d47a64b9a001591ee2b61074eea8afb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugclass2setjmcstatus-method"></a>ICorDebugClass2::SetJMCStatus – metoda
Pro každou metodu třídy nastaví hodnotu, která určuje, zda je metoda kód definovaný uživatelem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bIsJustMyCode`  
 [v] Nastavte na `true` označuje, že metoda uživatelem definované kód; jinak hodnota nastavena na `false`.  
  
## <a name="remarks"></a>Poznámky  
 Krokovač právě my kódu (dále jen SVK) přeskočí bez uživatelem definované kódu. Uživatelem definované kód musí být podmnožinou debuggable kódu.  
  
 `SetJMCStatus` Vrátí hodnotu HRESULT S_FALSE, pokud se nepodaří nastavit hodnotu pro libovolnou metodu, i když úspěšně nastaví hodnotu pro všechny ostatní metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
