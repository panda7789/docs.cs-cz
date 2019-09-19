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
# <a name="ienumrawinputdevicnext"></a><span data-ttu-id="a1fdb-102">IEnumRAWINPUTDEVIC:Next</span><span class="sxs-lookup"><span data-stu-id="a1fdb-102">IEnumRAWINPUTDEVIC:Next</span></span>
<span data-ttu-id="a1fdb-103">Vytvoří `celt` výčet dalších [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) struktur v seznamu enumerátoru `rgelt` a vrátí je spolu se skutečným počtem výčtových prvků v. `pceltFetched`</span><span class="sxs-lookup"><span data-stu-id="a1fdb-103">Enumerates the next `celt` [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) structures in the enumerator's list, returning them in `rgelt` along with the actual number of enumerated elements in `pceltFetched`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1fdb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1fdb-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
      [in] ULONG celt,  
      [out, size_is(celt), length_is(*pceltFetched)] RAWINPUTDEVICE *rgelt,  
      [out] ULONG *pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1fdb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a1fdb-105">Parameters</span></span>  
 `celt`  
  
 <span data-ttu-id="a1fdb-106">pro Počet [RAWINPUTDEVICEch](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) struktur vrácených `rgelt`v.</span><span class="sxs-lookup"><span data-stu-id="a1fdb-106">[in] Number of [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) structures returned in `rgelt`.</span></span>  
  
 `rgelt`  
  
 <span data-ttu-id="a1fdb-107">mimo Pole velikosti celt (nebo větší) pro příjem výčtu RAWINPUTDEVICE struktur.</span><span class="sxs-lookup"><span data-stu-id="a1fdb-107">[out] Array of size celt (or larger) to receive enumerated RAWINPUTDEVICE structures.</span></span>  
  
 `pceltFetched`  
  
 <span data-ttu-id="a1fdb-108">mimo Ukazatel na počet prvků, které jsou ve skutečnosti `rgelt`dodány v.</span><span class="sxs-lookup"><span data-stu-id="a1fdb-108">[out] Pointer to the number of elements actually supplied in `rgelt`.</span></span> <span data-ttu-id="a1fdb-109">Volající může předat, `NULL` Pokud `rgelt` je jeden.</span><span class="sxs-lookup"><span data-stu-id="a1fdb-109">Caller can pass in `NULL` if `rgelt` is one.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="a1fdb-110">Hodnota vlastnosti / návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a1fdb-110">Property Value/Return Value</span></span>  
 <span data-ttu-id="a1fdb-111">HRESULT S_OK, pokud je `celt`zadaný počet prvků; S_FALSE jinak.</span><span class="sxs-lookup"><span data-stu-id="a1fdb-111">HRESULT: S_OK if the number of elements supplied is `celt`; S_FALSE otherwise.</span></span>
