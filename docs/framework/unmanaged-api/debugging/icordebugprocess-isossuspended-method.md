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
ms.openlocfilehash: 9452f238bd84c9c185ca8e007acac563474d29df
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212058"
---
# <a name="icordebugprocessisossuspended-method"></a>ICorDebugProcess::IsOSSuspended – metoda
Získá hodnotu, která označuje, zda bylo zadané vlákno pozastaveno v důsledku zastavení tohoto procesu v rámci ladicího programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
## <a name="parameters"></a>Parametry  
 `threadID`  
 pro ID daného vlákna.  
  
 `pbSuspended`  
 mimo Ukazatel na logickou hodnotu, která je `true` v případě pozastavení zadaného vlákna; v opačném případě * `pbSuspended` je `false` .  
  
## <a name="remarks"></a>Poznámky  
 Pokud bylo zadané vlákno pozastaveno v důsledku zastavení tohoto procesu ladicím programem, je počet pozastavených vláken v systému Win32 zvýšen o jednu. Uživatelské rozhraní (UI) ladicího programu může chtít tyto informace vzít v úvahu, pokud zobrazuje počet pozastavených vláken v operačním systému na uživatele.  
  
 `IsOSSuspended`Metoda dává smysl pouze v kontextu nespravovaného ladění. Během spravovaného ladění jsou vlákna v pozastaveném operačním systému spíše pozastavena.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
