---
title: IEnumRAWINPUTDEVIC:Next
ms.date: 03/30/2017
helpviewer_keywords:
- Next method [WPF]
ms.assetid: 3698b44d-510e-4d18-b32b-85f17188ee26
ms.openlocfilehash: c7450a9ababa9cf3cb02d572f5ed84f0791d74e4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053402"
---
# <a name="ienumrawinputdevicnext"></a>IEnumRAWINPUTDEVIC:Next
Vytvoří `celt` výčet dalších [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) struktur v seznamu enumerátoru `rgelt` a vrátí je spolu se skutečným počtem výčtových prvků v. `pceltFetched`  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Next(  
      [in] ULONG celt,  
      [out, size_is(celt), length_is(*pceltFetched)] RAWINPUTDEVICE *rgelt,  
      [out] ULONG *pceltFetched);  
```  
  
## <a name="parameters"></a>Parametry  
 `celt`  
  
 pro Počet [RAWINPUTDEVICEch](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) struktur vrácených `rgelt`v.  
  
 `rgelt`  
  
 mimo Pole velikosti celt (nebo větší) pro příjem výčtu RAWINPUTDEVICE struktur.  
  
 `pceltFetched`  
  
 mimo Ukazatel na počet prvků, které jsou ve skutečnosti `rgelt`dodány v. Volající může předat, `NULL` Pokud `rgelt` je jeden.  
  
## <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota  
 HRESULT S_OK, pokud je `celt`zadaný počet prvků; S_FALSE jinak.
