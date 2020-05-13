---
title: ICorDebugProcess::GetID – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetID
helpviewer_keywords:
- GetID method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetID method [.NET Framework debugging]
ms.assetid: b0ba8453-fa7e-4c14-93e5-335409cd4a47
topic_type:
- apiref
ms.openlocfilehash: 8cd40ffb60bf837a9aa3b0db34892350a05964d7
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213280"
---
# <a name="icordebugprocessgetid-method"></a>ICorDebugProcess::GetID – metoda
Získá ID operačního systému (OS) procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetID([out] DWORD *pdwProcessId);  
```  
  
## <a name="parameters"></a>Parametry  
 `pdwProcessId`  
 mimo Jedinečné ID procesu  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
