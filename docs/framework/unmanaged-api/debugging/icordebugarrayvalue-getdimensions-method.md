---
title: ICorDebugArrayValue::GetDimensions – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetDimensions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetDimensions
helpviewer_keywords:
- ICorDebugArrayValue::GetDimensions method [.NET Framework debugging]
- GetDimensions method [.NET Framework debugging]
ms.assetid: 6c116592-134b-4ef2-a319-680e92d013aa
topic_type:
- apiref
ms.openlocfilehash: fa2be894af6e44d09c25a736f45acba56052f9fa
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895044"
---
# <a name="icordebugarrayvaluegetdimensions-method"></a>ICorDebugArrayValue::GetDimensions – metoda
Získá počet prvků v každé dimenzi tohoto pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetDimensions (  
    [in] ULONG32         cdim,  
    [out, size_is(cdim), length_is(cdim)]
        ULONG32          dims[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cdim`  
 pro Počet dimenzí tohoto objektu ICorDebugArrayValue  
  
 Tato hodnota je také velikost `dims` pole, protože jeho velikost je rovna počtu rozměrů `ICorDebugArrayValue` objektu.  
  
 `dims`  
 mimo Pole celých čísel, z nichž každý Určuje počet prvků v dimenzi v tomto `ICorDebugArrayValue` objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
