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
ms.openlocfilehash: 9fb2f960098e970b4d3d9f0be499f4d9fda6558e
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893899"
---
# <a name="icordebugclass2setjmcstatus-method"></a>ICorDebugClass2::SetJMCStatus – metoda
Pro každou metodu třídy nastaví hodnotu, která označuje, zda je metoda uživatelem definovaný kód.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `bIsJustMyCode`  
 pro Nastavte na `true` k označení toho, že metoda je uživatelsky definovaný kód; v opačném případě `false`nastavte na.  
  
## <a name="remarks"></a>Poznámky  
 JMC (Just-The-Code) stepper přeskočí neuživatelsky definovaný kód. Uživatelsky definovaný kód musí být podmnožinou laděného kódu.  
  
 `SetJMCStatus`Vrátí hodnotu HRESULT S_FALSE, pokud se nepodaří nastavit hodnotu pro jakoukoliv metodu, i když úspěšně nastaví hodnotu pro všechny ostatní metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
