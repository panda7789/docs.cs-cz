---
title: IEnumRAWINPUTDEVIC:Skip
ms.date: 03/30/2017
helpviewer_keywords:
- Skip method [WPF]
ms.assetid: c967b0f8-1c6a-459c-8c16-d4f08918ab65
ms.openlocfilehash: a74f71345a22f6d766c2d5966ca5d2cb33ab756e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053379"
---
# <a name="ienumrawinputdevicskip"></a><span data-ttu-id="79e7e-102">IEnumRAWINPUTDEVIC:Skip</span><span class="sxs-lookup"><span data-stu-id="79e7e-102">IEnumRAWINPUTDEVIC:Skip</span></span>
<span data-ttu-id="79e7e-103">Instruuje enumerátor pro přeskočení dalších `celt` prvků výčtu, aby další volání [IEnumRAWINPUTDEVIC: Next](ienumrawinputdevic-next.md) nevrátí tyto prvky.</span><span class="sxs-lookup"><span data-stu-id="79e7e-103">Instructs the enumerator to skip the next `celt` elements in the enumeration so that the next call to [IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md) will not return those elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79e7e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79e7e-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip( [in] ULONG celt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79e7e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="79e7e-105">Parameters</span></span>  
 `celt`  
  
 <span data-ttu-id="79e7e-106">pro Počet prvků, které mají být přeskočeny.</span><span class="sxs-lookup"><span data-stu-id="79e7e-106">[in] Number of elements to be skipped.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="79e7e-107">Hodnota vlastnosti / návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="79e7e-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="79e7e-108">HRESULT S_OK, pokud je `celt`zadaný počet prvků; S_FALSE jinak.</span><span class="sxs-lookup"><span data-stu-id="79e7e-108">HRESULT: S_OK if the number of elements supplied is `celt`; S_FALSE otherwise.</span></span>
