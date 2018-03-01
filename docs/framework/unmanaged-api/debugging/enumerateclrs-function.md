---
title: "EnumerateCLRs – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6539b471d6a3075bb4cec69b382cf7702a439d5a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="enumerateclrs-function"></a><span data-ttu-id="eaf8e-102">EnumerateCLRs – funkce</span><span class="sxs-lookup"><span data-stu-id="eaf8e-102">EnumerateCLRs Function</span></span>
<span data-ttu-id="eaf8e-103">Poskytuje mechanismus pro vytvoření výčtu CLRs v procesu.</span><span class="sxs-lookup"><span data-stu-id="eaf8e-103">Provides a mechanism for enumerating the CLRs in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eaf8e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eaf8e-104">Syntax</span></span>  
  
```  
HRESULT EnumerateCLRs (  
    [in]  DWORD      debuggeePID,  
    [out] HANDLE**   ppHandleArrayOut,  
    [out] LPWSTR**   ppStringArrayOut,  
    [out] DWORD*     pdwArrayLengthOut  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eaf8e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eaf8e-105">Parameters</span></span>  
 `debuggeePID`  
 <span data-ttu-id="eaf8e-106">[v] Proces identifikátor procesu, ve kterém bude možné provést výčet načíst CLRs.</span><span class="sxs-lookup"><span data-stu-id="eaf8e-106">[in] Process identifier of the process from which loaded CLRs will be enumerated.</span></span>  
  
 `ppHandleArrayOut`  
 <span data-ttu-id="eaf8e-107">[out] Ukazatel na pole obsahující obslužné rutiny události, které se používají ke spuštění CLR pokračovat.</span><span class="sxs-lookup"><span data-stu-id="eaf8e-107">[out] Pointer to an array containing event handles that are used to continue a CLR startup.</span></span> <span data-ttu-id="eaf8e-108">Každý popisovač v poli, nemusí být platný.</span><span class="sxs-lookup"><span data-stu-id="eaf8e-108">Each handle in the array is not guaranteed to be valid.</span></span> <span data-ttu-id="eaf8e-109">Pokud se platný, popisovač má být použita jako událost pokračovat spuštění pro odpovídající runtime umístěný ve stejné index `ppStringArrayOut`.</span><span class="sxs-lookup"><span data-stu-id="eaf8e-109">If valid, the handle is to be used as the continue-startup event for the corresponding runtime located in the same index of `ppStringArrayOut`.</span></span>  
  
 `ppStringArrayOut`  
 <span data-ttu-id="eaf8e-110">[out] Ukazatel na pole řetězců, které určují úplné cesty k CLRs načíst v procesu.</span><span class="sxs-lookup"><span data-stu-id="eaf8e-110">[out] Pointer to an array of strings that specify full paths to CLRs loaded in the process.</span></span>  
  
 `pdwArrayLengthOut`  
 <span data-ttu-id="eaf8e-111">[out] Ukazatel na DWORD, který obsahuje délku stejně velké `ppHandleArrayOut` a `pdwArrayLengthOut`.</span><span class="sxs-lookup"><span data-stu-id="eaf8e-111">[out] Pointer to a DWORD that contains the length of the equally sized `ppHandleArrayOut` and `pdwArrayLengthOut`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eaf8e-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="eaf8e-112">Return Value</span></span>  
 <span data-ttu-id="eaf8e-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="eaf8e-113">S_OK</span></span>  
 <span data-ttu-id="eaf8e-114">Počet CLRs v procesu byla úspěšně zjistit a byly správně zadat odpovídající popisovač a cesta pole.</span><span class="sxs-lookup"><span data-stu-id="eaf8e-114">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="eaf8e-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="eaf8e-115">E_INVALIDARG</span></span>  
 <span data-ttu-id="eaf8e-116">Buď `ppHandleArrayOut` nebo `ppStringArrayOut` má hodnotu null, nebo `pdwArrayLengthOut` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="eaf8e-116">Either `ppHandleArrayOut` or `ppStringArrayOut` is null, or `pdwArrayLengthOut` is null.</span></span>  
  
 <span data-ttu-id="eaf8e-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="eaf8e-117">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="eaf8e-118">Funkce se nepodařilo přidělit dostatek paměti pro pole popisovač a cestu.</span><span class="sxs-lookup"><span data-stu-id="eaf8e-118">The function is unable to allocate enough memory for the handle and path arrays.</span></span>  
  
 <span data-ttu-id="eaf8e-119">E_FAIL (nebo ostatní návratové kódy E_)</span><span class="sxs-lookup"><span data-stu-id="eaf8e-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="eaf8e-120">Nelze vytvořit výčet načíst CLRs.</span><span class="sxs-lookup"><span data-stu-id="eaf8e-120">Unable to enumerate loaded CLRs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eaf8e-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eaf8e-121">Remarks</span></span>  
 <span data-ttu-id="eaf8e-122">Pro cílový proces, která je identifikovaná `debuggeePID`, funkce vrátí hodnotu pole cesty, `ppStringArrayOut`do CLRs načíst v procesu; pole obslužné rutiny události, `ppHandleArrayOut`, který může obsahovat pokračovat spouštění událostí pro CLR ve stejném indexu; a Velikost pole, `pdwArrayLengthOut`, která určuje počet CLRs, které jsou načteny.</span><span class="sxs-lookup"><span data-stu-id="eaf8e-122">For a target process that is identified by `debuggeePID`, the function returns an array of paths, `ppStringArrayOut`, to CLRs loaded in the process; an array of event handles, `ppHandleArrayOut`, which may contain a continue-startup event for the CLR at the same index; and the size of the arrays, `pdwArrayLengthOut`, which specifies the number of CLRs that are loaded.</span></span>  
  
 <span data-ttu-id="eaf8e-123">V operačním systému Windows `debuggeePID` mapuje operační systém zpracovat identifikátor.</span><span class="sxs-lookup"><span data-stu-id="eaf8e-123">On the Windows operating system, `debuggeePID` maps to an OS process identifier.</span></span>  
  
 <span data-ttu-id="eaf8e-124">Paměť pro `ppHandleArrayOut` a `ppStringArrayOut` jsou přiděleny pomocí této funkce.</span><span class="sxs-lookup"><span data-stu-id="eaf8e-124">The memory for `ppHandleArrayOut` and `ppStringArrayOut` are allocated by this function.</span></span> <span data-ttu-id="eaf8e-125">Chcete-li uvolnit je paměť přidělená, musí volat [closeclrenumeration – funkce](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md).</span><span class="sxs-lookup"><span data-stu-id="eaf8e-125">To free the memory allocated, you must call [CloseCLREnumeration Function](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md).</span></span>  
  
 <span data-ttu-id="eaf8e-126">Tuto funkci nelze volat s oba parametry pole nastavena na hodnotu null, aby bylo možné vrátí počet CLRs v tento cílový proces.</span><span class="sxs-lookup"><span data-stu-id="eaf8e-126">This function can be called with both array parameters set to null in order to return the count of CLRs in the target process.</span></span> <span data-ttu-id="eaf8e-127">Z tento počet můžete volající odvození velikost vyrovnávací paměti, která bude vytvořena: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.</span><span class="sxs-lookup"><span data-stu-id="eaf8e-127">From this count, a caller can infer the size of the buffer that will be created: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eaf8e-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eaf8e-128">Requirements</span></span>  
 <span data-ttu-id="eaf8e-129">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eaf8e-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eaf8e-130">**Záhlaví:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="eaf8e-130">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="eaf8e-131">**Knihovna:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="eaf8e-131">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="eaf8e-132">**Verze rozhraní .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="eaf8e-132">**.NET Framework Versions:** 3.5 SP1</span></span>
