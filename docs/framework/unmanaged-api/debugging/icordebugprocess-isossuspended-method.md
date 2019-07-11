---
title: ICorDebugProcess::IsOSSuspended – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsOSSuspended
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsOSSuspended
helpviewer_keywords:
- IsOSSuspended method [.NET Framework debugging]
- ICorDebugProcess::IsOSSuspended method [.NET Framework debugging]
ms.assetid: 83406cb2-5797-4402-872d-89c9516aefec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 275f62c8211f71f067d310dd4b3af2ddb11e93d7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755456"
---
# <a name="icordebugprocessisossuspended-method"></a>ICorDebugProcess::IsOSSuspended – metoda
Získá hodnotu určující, zda zadaná vlákna se pozastavilo, v důsledku ukončení tohoto procesu ladicího programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
## <a name="parameters"></a>Parametry  
 `threadID`  
 [in] ID vlákna nejistá.  
  
 `pbSuspended`  
 [out] Ukazatel na logickou hodnotu, která je `true` Pokud vlákna zadaného byl pozastavený, jinak *`pbSuspended` je `false`.  
  
## <a name="remarks"></a>Poznámky  
 Když zadaného vlákna se pozastavilo, v důsledku ukončení tohoto procesu ladicího programu, zadané vlákno Win32 pozastavit počet se zvýší o jedna. Uživatelské rozhraní (UI) ladicí program může být vhodné vzít v úvahu tyto informace pokud zobrazí operační systém (OS) pozastavit počet vláken pro uživatele.  
  
 `IsOSSuspended` Metoda má smysl pouze v kontextu ladění nespravovaného kódu. Při ladění spravovaných vláken jsou spolupráce při pozastavené, spíše než pozastaveno operačního systému.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
