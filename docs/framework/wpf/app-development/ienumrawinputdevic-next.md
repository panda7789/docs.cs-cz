---
title: IEnumRAWINPUTDEVIC:Next
ms.date: 03/30/2017
helpviewer_keywords:
- Next method [WPF]
ms.assetid: 3698b44d-510e-4d18-b32b-85f17188ee26
ms.openlocfilehash: a1f76bf42da9a311633de39e42dee2055fac4a27
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2019
ms.locfileid: "56745182"
---
# <a name="ienumrawinputdevicnext"></a><span data-ttu-id="65c6d-102">IEnumRAWINPUTDEVIC:Next</span><span class="sxs-lookup"><span data-stu-id="65c6d-102">IEnumRAWINPUTDEVIC:Next</span></span>
<span data-ttu-id="65c6d-103">Vytvoří výčet Další `celt` [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) struktury v seznamu čítače výčtu je vrácení `rgelt` spolu s skutečný počet prvků ve výčtu v `pceltFetched`.</span><span class="sxs-lookup"><span data-stu-id="65c6d-103">Enumerates the next `celt` [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) structures in the enumerator's list, returning them in `rgelt` along with the actual number of enumerated elements in `pceltFetched`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65c6d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65c6d-104">Syntax</span></span>  
  
```  
HRESULT Next(  
      [in] ULONG celt,  
      [out, size_is(celt), length_is(*pceltFetched)] RAWINPUTDEVICE *rgelt,  
      [out] ULONG *pceltFetched);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="65c6d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="65c6d-105">Parameters</span></span>  
 `celt`  
  
 <span data-ttu-id="65c6d-106">[in] Počet [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) struktury vrácené v `rgelt`.</span><span class="sxs-lookup"><span data-stu-id="65c6d-106">[in] Number of [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) structures returned in `rgelt`.</span></span>  
  
 `rgelt`  
  
 <span data-ttu-id="65c6d-107">[out] Pole celt velikost (a vyšší) pro příjem Výčtový RAWINPUTDEVICE struktury.</span><span class="sxs-lookup"><span data-stu-id="65c6d-107">[out] Array of size celt (or larger) to receive enumerated RAWINPUTDEVICE structures.</span></span>  
  
 `pceltFetched`  
  
 <span data-ttu-id="65c6d-108">[out] Ukazatel na počet prvků ve skutečnosti zadaný v `rgelt`.</span><span class="sxs-lookup"><span data-stu-id="65c6d-108">[out] Pointer to the number of elements actually supplied in `rgelt`.</span></span> <span data-ttu-id="65c6d-109">Můžete předat volající `NULL` Pokud `rgelt` je jedna.</span><span class="sxs-lookup"><span data-stu-id="65c6d-109">Caller can pass in `NULL` if `rgelt` is one.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="65c6d-110">Hodnota vlastnosti / návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="65c6d-110">Property Value/Return Value</span></span>  
 <span data-ttu-id="65c6d-111">HODNOTA HRESULT: S_OK, pokud je počet elementů zadaný `celt`; S_FALSE jinak.</span><span class="sxs-lookup"><span data-stu-id="65c6d-111">HRESULT: S_OK if the number of elements supplied is `celt`; S_FALSE otherwise.</span></span>
