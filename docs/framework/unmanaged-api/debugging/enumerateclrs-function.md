---
title: EnumerateCLRs – funkce
ms.date: 03/30/2017
api_name:
- EnumerateCLRs
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- EnumerateCLRs
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- EnumerateCLRs function
ms.assetid: f8d50cb3-ec4f-4529-8fe3-bd61fd28e13c
topic_type:
- apiref
ms.openlocfilehash: 69288e995ec789091bf089368cd9a60f003df86e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122978"
---
# <a name="enumerateclrs-function"></a><span data-ttu-id="b5e19-102">EnumerateCLRs – funkce</span><span class="sxs-lookup"><span data-stu-id="b5e19-102">EnumerateCLRs Function</span></span>
<span data-ttu-id="b5e19-103">Poskytuje mechanismus pro vytváření výčtu CLRs v procesu.</span><span class="sxs-lookup"><span data-stu-id="b5e19-103">Provides a mechanism for enumerating the CLRs in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5e19-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5e19-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateCLRs (  
    [in]  DWORD      debuggeePID,  
    [out] HANDLE**   ppHandleArrayOut,  
    [out] LPWSTR**   ppStringArrayOut,  
    [out] DWORD*     pdwArrayLengthOut  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5e19-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b5e19-105">Parameters</span></span>  
 `debuggeePID`  
 <span data-ttu-id="b5e19-106">pro Identifikátor procesu, ze kterého se má vyčíslit načtené CLRs</span><span class="sxs-lookup"><span data-stu-id="b5e19-106">[in] Process identifier of the process from which loaded CLRs will be enumerated.</span></span>  
  
 `ppHandleArrayOut`  
 <span data-ttu-id="b5e19-107">mimo Ukazatel na pole obsahující obslužné rutiny událostí, které se používají k pokračování spuštění modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="b5e19-107">[out] Pointer to an array containing event handles that are used to continue a CLR startup.</span></span> <span data-ttu-id="b5e19-108">Není zaručeno, že každý popisovač v poli je platný.</span><span class="sxs-lookup"><span data-stu-id="b5e19-108">Each handle in the array is not guaranteed to be valid.</span></span> <span data-ttu-id="b5e19-109">Je-li tento postup platný, je třeba použít popisovač jako událost pokračování po spuštění pro odpovídající modul runtime umístěný ve stejném indexu `ppStringArrayOut`.</span><span class="sxs-lookup"><span data-stu-id="b5e19-109">If valid, the handle is to be used as the continue-startup event for the corresponding runtime located in the same index of `ppStringArrayOut`.</span></span>  
  
 `ppStringArrayOut`  
 <span data-ttu-id="b5e19-110">mimo Ukazatel na pole řetězců, které určují úplné cesty pro CLRs načtené v procesu.</span><span class="sxs-lookup"><span data-stu-id="b5e19-110">[out] Pointer to an array of strings that specify full paths to CLRs loaded in the process.</span></span>  
  
 `pdwArrayLengthOut`  
 <span data-ttu-id="b5e19-111">mimo Ukazatel na DWORD, který obsahuje délku rovnoměrné velikosti `ppHandleArrayOut` a `pdwArrayLengthOut`.</span><span class="sxs-lookup"><span data-stu-id="b5e19-111">[out] Pointer to a DWORD that contains the length of the equally sized `ppHandleArrayOut` and `pdwArrayLengthOut`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b5e19-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b5e19-112">Return Value</span></span>  
 <span data-ttu-id="b5e19-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="b5e19-113">S_OK</span></span>  
 <span data-ttu-id="b5e19-114">Počet CLRs v procesu byl úspěšně zjištěn a odpovídající pole popisovače a cesty byly správně vyplněny.</span><span class="sxs-lookup"><span data-stu-id="b5e19-114">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="b5e19-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b5e19-115">E_INVALIDARG</span></span>  
 <span data-ttu-id="b5e19-116">Buď je `ppHandleArrayOut` nebo `ppStringArrayOut` null, nebo je `pdwArrayLengthOut` null.</span><span class="sxs-lookup"><span data-stu-id="b5e19-116">Either `ppHandleArrayOut` or `ppStringArrayOut` is null, or `pdwArrayLengthOut` is null.</span></span>  
  
 <span data-ttu-id="b5e19-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="b5e19-117">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="b5e19-118">Funkce nemůže přidělit dostatek paměti pro pole popisovač a cesta.</span><span class="sxs-lookup"><span data-stu-id="b5e19-118">The function is unable to allocate enough memory for the handle and path arrays.</span></span>  
  
 <span data-ttu-id="b5e19-119">E_FAIL (nebo jiné návratové kódy E_)</span><span class="sxs-lookup"><span data-stu-id="b5e19-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="b5e19-120">Nelze vytvořit výčet načtených CLRs.</span><span class="sxs-lookup"><span data-stu-id="b5e19-120">Unable to enumerate loaded CLRs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5e19-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b5e19-121">Remarks</span></span>  
 <span data-ttu-id="b5e19-122">Pro cílový proces, který je identifikován `debuggeePID`, funkce vrátí pole cest, `ppStringArrayOut`, na CLRs načtený v procesu; pole obslužných rutin událostí, `ppHandleArrayOut`, které mohou obsahovat událost pokračování-spuštění pro modul CLR ve stejném indexu; a velikost polí `pdwArrayLengthOut`, které určují počet načtených CLRs.</span><span class="sxs-lookup"><span data-stu-id="b5e19-122">For a target process that is identified by `debuggeePID`, the function returns an array of paths, `ppStringArrayOut`, to CLRs loaded in the process; an array of event handles, `ppHandleArrayOut`, which may contain a continue-startup event for the CLR at the same index; and the size of the arrays, `pdwArrayLengthOut`, which specifies the number of CLRs that are loaded.</span></span>  
  
 <span data-ttu-id="b5e19-123">V operačním systému Windows `debuggeePID` mapuje identifikátor procesu operačního systému.</span><span class="sxs-lookup"><span data-stu-id="b5e19-123">On the Windows operating system, `debuggeePID` maps to an OS process identifier.</span></span>  
  
 <span data-ttu-id="b5e19-124">Tato funkce přiděluje paměť pro `ppHandleArrayOut` a `ppStringArrayOut`.</span><span class="sxs-lookup"><span data-stu-id="b5e19-124">The memory for `ppHandleArrayOut` and `ppStringArrayOut` are allocated by this function.</span></span> <span data-ttu-id="b5e19-125">Chcete-li uvolnit přidělenou paměť, je nutné volat [funkci CloseCLREnumeration –](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md).</span><span class="sxs-lookup"><span data-stu-id="b5e19-125">To free the memory allocated, you must call [CloseCLREnumeration Function](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md).</span></span>  
  
 <span data-ttu-id="b5e19-126">Tuto funkci lze volat s parametrem pole nastaveným na hodnotu null, aby bylo možné vrátit počet CLRs v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="b5e19-126">This function can be called with both array parameters set to null in order to return the count of CLRs in the target process.</span></span> <span data-ttu-id="b5e19-127">Od tohoto počtu může volající odvodit velikost vyrovnávací paměti, která se vytvoří: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.</span><span class="sxs-lookup"><span data-stu-id="b5e19-127">From this count, a caller can infer the size of the buffer that will be created: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5e19-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b5e19-128">Requirements</span></span>  
 <span data-ttu-id="b5e19-129">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5e19-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5e19-130">**Záhlaví:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="b5e19-130">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="b5e19-131">**Knihovna:** dbgshim. dll</span><span class="sxs-lookup"><span data-stu-id="b5e19-131">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="b5e19-132">**Verze .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="b5e19-132">**.NET Framework Versions:** 3.5 SP1</span></span>
