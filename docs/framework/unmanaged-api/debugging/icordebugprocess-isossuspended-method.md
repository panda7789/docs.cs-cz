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
ms.openlocfilehash: 21da69d4bff0f17eb607dda45fb7dbafea8c59f7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128773"
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
 mimo Ukazatel na logickou hodnotu, která je `true`, pokud je zadané vlákno pozastaveno. v opačném případě *`pbSuspended` `false`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud bylo zadané vlákno pozastaveno v důsledku zastavení tohoto procesu ladicím programem, je počet pozastavených vláken v systému Win32 zvýšen o jednu. Uživatelské rozhraní (UI) ladicího programu může chtít tyto informace vzít v úvahu, pokud zobrazuje počet pozastavených vláken v operačním systému na uživatele.  
  
 Metoda `IsOSSuspended` dává smysl pouze v kontextu nespravovaného ladění. Během spravovaného ladění jsou vlákna v pozastaveném operačním systému spíše pozastavena.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
