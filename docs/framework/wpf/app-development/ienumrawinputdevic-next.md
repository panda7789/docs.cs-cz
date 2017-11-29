---
title: IEnumRAWINPUTDEVIC:Next
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Next method [WPF]
ms.assetid: 3698b44d-510e-4d18-b32b-85f17188ee26
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 644a8e724a280a8b23048a381a099acd6e655d2c
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="ienumrawinputdevicnext"></a><span data-ttu-id="94cff-102">IEnumRAWINPUTDEVIC:Next</span><span class="sxs-lookup"><span data-stu-id="94cff-102">IEnumRAWINPUTDEVIC:Next</span></span>
<span data-ttu-id="94cff-103">Vytvoří výčet Další `celt` [RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) struktury v seznamu je čítač je v vrácení `rgelt` společně s skutečný počet elementů výčtové v `pceltFetched`.</span><span class="sxs-lookup"><span data-stu-id="94cff-103">Enumerates the next `celt` [RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) structures in the enumerator's list, returning them in `rgelt` along with the actual number of enumerated elements in `pceltFetched`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94cff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94cff-104">Syntax</span></span>  
  
```  
HRESULT Next(  
      [in] ULONG celt,  
      [out, size_is(celt), length_is(*pceltFetched)] RAWINPUTDEVICE *rgelt,  
      [out] ULONG *pceltFetched);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="94cff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="94cff-105">Parameters</span></span>  
 `celt`  
  
 <span data-ttu-id="94cff-106">[v] Počet [RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) struktury, vrátí se v `rgelt`.</span><span class="sxs-lookup"><span data-stu-id="94cff-106">[in] Number of [RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) structures returned in `rgelt`.</span></span>  
  
 `rgelt`  
  
 <span data-ttu-id="94cff-107">[out] Pole celt velikost (nebo vyšší) pro příjem výčtové RAWINPUTDEVICE struktury.</span><span class="sxs-lookup"><span data-stu-id="94cff-107">[out] Array of size celt (or larger) to receive enumerated RAWINPUTDEVICE structures.</span></span>  
  
 `pceltFetched`  
  
 <span data-ttu-id="94cff-108">[out] Ukazatel na počet elementů ve skutečnosti zadaný v `rgelt`.</span><span class="sxs-lookup"><span data-stu-id="94cff-108">[out] Pointer to the number of elements actually supplied in `rgelt`.</span></span> <span data-ttu-id="94cff-109">Volající lze předat v `NULL` Pokud `rgelt` je jedna.</span><span class="sxs-lookup"><span data-stu-id="94cff-109">Caller can pass in `NULL` if `rgelt` is one.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="94cff-110">Hodnota vlastnosti / návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="94cff-110">Property Value/Return Value</span></span>  
 <span data-ttu-id="94cff-111">HRESULT: S_OK Pokud je počet elementů zadaný `celt`; S_FALSE jinak.</span><span class="sxs-lookup"><span data-stu-id="94cff-111">HRESULT: S_OK if the number of elements supplied is `celt`; S_FALSE otherwise.</span></span>
