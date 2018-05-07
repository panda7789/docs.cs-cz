---
title: IEnumRAWINPUTDEVIC:Next
ms.date: 03/30/2017
helpviewer_keywords:
- Next method [WPF]
ms.assetid: 3698b44d-510e-4d18-b32b-85f17188ee26
ms.openlocfilehash: 3cf3231bd48290c5b6b0ce8eeb6534de564c0c85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ienumrawinputdevicnext"></a>IEnumRAWINPUTDEVIC:Next
Vytvoří výčet Další `celt` [RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) struktury v seznamu je čítač je v vrácení `rgelt` společně s skutečný počet elementů výčtové v `pceltFetched`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Next(  
      [in] ULONG celt,  
      [out, size_is(celt), length_is(*pceltFetched)] RAWINPUTDEVICE *rgelt,  
      [out] ULONG *pceltFetched);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
  
 [v] Počet [RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) struktury, vrátí se v `rgelt`.  
  
 `rgelt`  
  
 [out] Pole celt velikost (nebo vyšší) pro příjem výčtové RAWINPUTDEVICE struktury.  
  
 `pceltFetched`  
  
 [out] Ukazatel na počet elementů ve skutečnosti zadaný v `rgelt`. Volající lze předat v `NULL` Pokud `rgelt` je jedna.  
  
## <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota  
 HRESULT: S_OK Pokud je počet elementů zadaný `celt`; S_FALSE jinak.
