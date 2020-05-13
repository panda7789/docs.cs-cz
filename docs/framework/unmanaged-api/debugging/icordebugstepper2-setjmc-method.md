---
title: ICorDebugStepper2::SetJMC – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStepper2.SetJMC
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper2::SetJMC
helpviewer_keywords:
- ICorDebugStepper2::SetJMC method [.NET Framework debugging]
- SetJMC method [.NET Framework debugging]
ms.assetid: f5cdc135-6db4-4b32-9dd1-260ec58b774f
topic_type:
- apiref
ms.openlocfilehash: ab1351af042aba5042cc7a04614bc3cf14f7d7ae
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379465"
---
# <a name="icordebugstepper2setjmc-method"></a>ICorDebugStepper2::SetJMC – metoda
Nastaví hodnotu, která určuje, zda jsou tyto ICorDebugStepper kroky pouze prostřednictvím kódu, který je vytvořen vývojářem aplikace. Tento proces je také známý jako ladění pouze můj kód (JMC).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetJMC (  
    [in] BOOL    fIsJMCStepper  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `fIsJMCStepper`  
 pro Nastavte na `true` krok pouze pomocí kódu, který je vytvořen vývojářem aplikace. v opačném případě nastavte na `false` .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
