---
title: ICorDebugStepper::SetUnmappedStopMask – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetUnmappedStopMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetUnmappedStopMask
helpviewer_keywords:
- ICorDebugStepper::SetUnmappedStopMask method [.NET Framework debugging]
- SetUnmappedStopMask method [.NET Framework debugging]
ms.assetid: b1211981-e90c-4e05-8def-fa18d85ad9ab
topic_type:
- apiref
ms.openlocfilehash: ef458fda8e8b7e75f92a4b3c06eabec106180d23
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379250"
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a>ICorDebugStepper::SetUnmappedStopMask – metoda
Nastaví hodnotu, která určuje typ nemapovaného kódu, ve kterém se spuštění zastaví.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `mask`  
 pro Hodnota výčtu CorDebugUnmappedStop –, která určuje typ nemapovaného kódu, ve kterém ladicí program zastaví provádění.  
  
 Výchozí hodnota je STOP_OTHER_UNMAPPED. Hodnota STOP_UNMANAGED je platná pouze s laděním spolupráce.  
  
## <a name="remarks"></a>Poznámky  
 Když ladicí program najde kompilaci za běhu (JIT), která nemá žádné odpovídající mapování na jazyk MSIL (Microsoft Intermediate Language), zastaví provádění, pokud byl nastaven příznak určující tento typ nemapovaného kódu; v opačném případě pokračuje krokování transparentně.  
  
 Pokud ladicí program nepoužívá stepper k zadání metody, pak nebude nutně Krokovat s nemapovaným kódem.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
