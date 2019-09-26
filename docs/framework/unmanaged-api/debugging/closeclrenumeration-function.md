---
title: CloseCLREnumeration – funkce
ms.date: 03/30/2017
api_name:
- CloseCLREnumeration
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- CloseCLREnumeration
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CloseCLR Enumeration function
ms.assetid: 5e3c3958-80bb-43b1-a96b-dd3e6dbd9cd7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a05a779d4a56eb8f881da1824d5ffaa363b5a01
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274284"
---
# <a name="closeclrenumeration-function"></a><span data-ttu-id="9d370-102">CloseCLREnumeration – funkce</span><span class="sxs-lookup"><span data-stu-id="9d370-102">CloseCLREnumeration Function</span></span>
<span data-ttu-id="9d370-103">Uzavře všechny platné události průběžného modulu CLR (Common Language Runtime), které se nacházejí v poli popisovačů vrácených [funkcí EnumerateCLRs –](enumerateclrs-function.md), a uvolní paměť pro pole popisovačů a cest řetězců.</span><span class="sxs-lookup"><span data-stu-id="9d370-103">Closes any valid common language runtime (CLR) continue-startup events located in an array of handles returned by the [EnumerateCLRs function](enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d370-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d370-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d370-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d370-105">Parameters</span></span>  
 `pHandleArray`  
 <span data-ttu-id="9d370-106">pro Ukazatel na pole obslužných rutin událostí vrácených [funkcí EnumerateCLRs –](enumerateclrs-function.md).</span><span class="sxs-lookup"><span data-stu-id="9d370-106">[in] Pointer to the array of event handles returned from the [EnumerateCLRs function](enumerateclrs-function.md).</span></span>  
  
 `pStringArray`  
 <span data-ttu-id="9d370-107">pro Ukazatel na pole cest řetězců CLR vrácených [funkcí EnumerateCLRs –](enumerateclrs-function.md).</span><span class="sxs-lookup"><span data-stu-id="9d370-107">[in] Pointer to the array of CLR string paths returned from the [EnumerateCLRs function](enumerateclrs-function.md).</span></span>  
  
 `dwArrayLength`  
 <span data-ttu-id="9d370-108">pro Hodnota DWORD, která obsahuje velikost (length) buď `pHandleArray` nebo `pStringArray` (jsou stejné).</span><span class="sxs-lookup"><span data-stu-id="9d370-108">[in] DWORD that contains the size (length) of either `pHandleArray` or `pStringArray` (they are the same).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d370-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9d370-109">Return Value</span></span>  
 <span data-ttu-id="9d370-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9d370-110">S_OK</span></span>  
 <span data-ttu-id="9d370-111">Obslužné rutiny otevřené [funkcí EnumerateCLRs –](enumerateclrs-function.md) jsou uzavřeny a přidělená paměť pro popisovač a pole řetězců jsou uvolněny.</span><span class="sxs-lookup"><span data-stu-id="9d370-111">Handles opened by the [EnumerateCLRs function](enumerateclrs-function.md) are closed, and memory allocated for the handle and string arrays is freed.</span></span>  
  
 <span data-ttu-id="9d370-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="9d370-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="9d370-113">Délka `pHandleArray` se neshoduje s délkou, která je `dwArrayLength`předána.</span><span class="sxs-lookup"><span data-stu-id="9d370-113">The length of `pHandleArray` does not match the length that is passed in `dwArrayLength`.</span></span>  
  
 <span data-ttu-id="9d370-114">E_FAIL (nebo jiné návratové kódy E_)</span><span class="sxs-lookup"><span data-stu-id="9d370-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="9d370-115">Funkce nemůže uvolnit paměť pro `pHandleArray` a. `pStringArray`</span><span class="sxs-lookup"><span data-stu-id="9d370-115">The function is unable to free the memory for `pHandleArray` and `pStringArray`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d370-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9d370-116">Requirements</span></span>  
 <span data-ttu-id="9d370-117">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d370-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d370-118">**Záhlaví:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="9d370-118">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="9d370-119">**Knihovna:** dbgshim. dll</span><span class="sxs-lookup"><span data-stu-id="9d370-119">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="9d370-120">**Verze .NET Framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="9d370-120">**.NET Framework Versions:** 3.5 SP1</span></span>
