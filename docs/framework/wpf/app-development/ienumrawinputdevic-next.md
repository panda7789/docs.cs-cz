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
ms.locfileid: "33546403"
---
# <a name="ienumrawinputdevicnext"></a><span data-ttu-id="f2b9c-102">IEnumRAWINPUTDEVIC:Next</span><span class="sxs-lookup"><span data-stu-id="f2b9c-102">IEnumRAWINPUTDEVIC:Next</span></span>
<span data-ttu-id="f2b9c-103">Vytvoří výčet Další `celt` [RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) struktury v seznamu je čítač je v vrácení `rgelt` společně s skutečný počet elementů výčtové v `pceltFetched`.</span><span class="sxs-lookup"><span data-stu-id="f2b9c-103">Enumerates the next `celt` [RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) structures in the enumerator's list, returning them in `rgelt` along with the actual number of enumerated elements in `pceltFetched`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2b9c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2b9c-104">Syntax</span></span>  
  
```  
HRESULT Next(  
      [in] ULONG celt,  
      [out, size_is(celt), length_is(*pceltFetched)] RAWINPUTDEVICE *rgelt,  
      [out] ULONG *pceltFetched);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f2b9c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f2b9c-105">Parameters</span></span>  
 `celt`  
  
 <span data-ttu-id="f2b9c-106">[v] Počet [RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) struktury, vrátí se v `rgelt`.</span><span class="sxs-lookup"><span data-stu-id="f2b9c-106">[in] Number of [RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) structures returned in `rgelt`.</span></span>  
  
 `rgelt`  
  
 <span data-ttu-id="f2b9c-107">[out] Pole celt velikost (nebo vyšší) pro příjem výčtové RAWINPUTDEVICE struktury.</span><span class="sxs-lookup"><span data-stu-id="f2b9c-107">[out] Array of size celt (or larger) to receive enumerated RAWINPUTDEVICE structures.</span></span>  
  
 `pceltFetched`  
  
 <span data-ttu-id="f2b9c-108">[out] Ukazatel na počet elementů ve skutečnosti zadaný v `rgelt`.</span><span class="sxs-lookup"><span data-stu-id="f2b9c-108">[out] Pointer to the number of elements actually supplied in `rgelt`.</span></span> <span data-ttu-id="f2b9c-109">Volající lze předat v `NULL` Pokud `rgelt` je jedna.</span><span class="sxs-lookup"><span data-stu-id="f2b9c-109">Caller can pass in `NULL` if `rgelt` is one.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="f2b9c-110">Hodnota vlastnosti / návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f2b9c-110">Property Value/Return Value</span></span>  
 <span data-ttu-id="f2b9c-111">HRESULT: S_OK Pokud je počet elementů zadaný `celt`; S_FALSE jinak.</span><span class="sxs-lookup"><span data-stu-id="f2b9c-111">HRESULT: S_OK if the number of elements supplied is `celt`; S_FALSE otherwise.</span></span>
