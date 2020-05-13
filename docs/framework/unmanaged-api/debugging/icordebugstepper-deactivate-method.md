---
title: ICorDebugStepper::Deactivate – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.Deactivate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::Deactivate
helpviewer_keywords:
- Deactivate method [.NET Framework debugging]
- ICorDebugStepper::Deactivate method [.NET Framework debugging]
ms.assetid: 855f4199-b62d-40ce-998e-1eb4a1772142
topic_type:
- apiref
ms.openlocfilehash: 760f69baf311cf320e9c358ba1c45c942934f1a5
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379399"
---
# <a name="icordebugstepperdeactivate-method"></a>ICorDebugStepper::Deactivate – metoda
Způsobí, že tato ICorDebugStepper zruší příkaz posledního kroku, který přijal.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Deactivate ();  
```  
  
## <a name="remarks"></a>Poznámky  
 Nový příkaz pro krokování může být vydán po zrušení příkazu poslední přijatý krok.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
