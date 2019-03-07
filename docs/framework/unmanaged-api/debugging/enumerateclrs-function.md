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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e7532218728aead72186b5156da87db6d3bc0a8c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469327"
---
# <a name="enumerateclrs-function"></a><span data-ttu-id="927e2-102">EnumerateCLRs – funkce</span><span class="sxs-lookup"><span data-stu-id="927e2-102">EnumerateCLRs Function</span></span>
<span data-ttu-id="927e2-103">Poskytuje mechanismus pro vytvoření výčtu CLRs v procesu.</span><span class="sxs-lookup"><span data-stu-id="927e2-103">Provides a mechanism for enumerating the CLRs in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="927e2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="927e2-104">Syntax</span></span>  
  
```  
HRESULT EnumerateCLRs (  
    [in]  DWORD      debuggeePID,  
    [out] HANDLE**   ppHandleArrayOut,  
    [out] LPWSTR**   ppStringArrayOut,  
    [out] DWORD*     pdwArrayLengthOut  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="927e2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="927e2-105">Parameters</span></span>  
 `debuggeePID`  
 <span data-ttu-id="927e2-106">[in] Zpracovat identifikátor procesu, ze kterého bude načten CLRs výčtu.</span><span class="sxs-lookup"><span data-stu-id="927e2-106">[in] Process identifier of the process from which loaded CLRs will be enumerated.</span></span>  
  
 `ppHandleArrayOut`  
 <span data-ttu-id="927e2-107">[out] Ukazatel na pole obsahující obslužné rutiny událostí, které se používají k pokračování spouštění modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="927e2-107">[out] Pointer to an array containing event handles that are used to continue a CLR startup.</span></span> <span data-ttu-id="927e2-108">Každý popisovač pole nemusí být platný.</span><span class="sxs-lookup"><span data-stu-id="927e2-108">Each handle in the array is not guaranteed to be valid.</span></span> <span data-ttu-id="927e2-109">Pokud platné, popisovač je má být použit jako událost pokračovat spuštění pro odpovídající modul runtime umístěný ve stejné index `ppStringArrayOut`.</span><span class="sxs-lookup"><span data-stu-id="927e2-109">If valid, the handle is to be used as the continue-startup event for the corresponding runtime located in the same index of `ppStringArrayOut`.</span></span>  
  
 `ppStringArrayOut`  
 <span data-ttu-id="927e2-110">[out] Ukazatel na pole řetězců, které určují úplné cesty k CLRs načtené v procesu.</span><span class="sxs-lookup"><span data-stu-id="927e2-110">[out] Pointer to an array of strings that specify full paths to CLRs loaded in the process.</span></span>  
  
 `pdwArrayLengthOut`  
 <span data-ttu-id="927e2-111">[out] Ukazatel na DWORD, který obsahuje délku stejně velké `ppHandleArrayOut` a `pdwArrayLengthOut`.</span><span class="sxs-lookup"><span data-stu-id="927e2-111">[out] Pointer to a DWORD that contains the length of the equally sized `ppHandleArrayOut` and `pdwArrayLengthOut`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="927e2-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="927e2-112">Return Value</span></span>  
 <span data-ttu-id="927e2-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="927e2-113">S_OK</span></span>  
 <span data-ttu-id="927e2-114">Úspěšně bylo zjištěno číslo CLRs v procesu a odpovídající popisovač a pole cesty byly správně vyplněné.</span><span class="sxs-lookup"><span data-stu-id="927e2-114">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="927e2-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="927e2-115">E_INVALIDARG</span></span>  
 <span data-ttu-id="927e2-116">Buď `ppHandleArrayOut` nebo `ppStringArrayOut` má hodnotu null, nebo `pdwArrayLengthOut` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="927e2-116">Either `ppHandleArrayOut` or `ppStringArrayOut` is null, or `pdwArrayLengthOut` is null.</span></span>  
  
 <span data-ttu-id="927e2-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="927e2-117">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="927e2-118">Funkce se nemůže přidělit dostatek paměti pro popisovač a cesta pole.</span><span class="sxs-lookup"><span data-stu-id="927e2-118">The function is unable to allocate enough memory for the handle and path arrays.</span></span>  
  
 <span data-ttu-id="927e2-119">E_FAIL (nebo jiné E_ návratové kódy)</span><span class="sxs-lookup"><span data-stu-id="927e2-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="927e2-120">Nepovedlo se vytvořit výčet načíst CLRs.</span><span class="sxs-lookup"><span data-stu-id="927e2-120">Unable to enumerate loaded CLRs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="927e2-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="927e2-121">Remarks</span></span>  
 <span data-ttu-id="927e2-122">Pro cílový proces, který je identifikován podle `debuggeePID`, funkce vrátí pole cest, `ppStringArrayOut`do CLRs načtené v procesu; pole obslužné rutiny událostí, `ppHandleArrayOut`, který může obsahovat pokračovat spouštěcí událost pro modul CLR ve stejném indexu; a Velikost pole, `pdwArrayLengthOut`, která určuje počet CLRs, které jsou načteny.</span><span class="sxs-lookup"><span data-stu-id="927e2-122">For a target process that is identified by `debuggeePID`, the function returns an array of paths, `ppStringArrayOut`, to CLRs loaded in the process; an array of event handles, `ppHandleArrayOut`, which may contain a continue-startup event for the CLR at the same index; and the size of the arrays, `pdwArrayLengthOut`, which specifies the number of CLRs that are loaded.</span></span>  
  
 <span data-ttu-id="927e2-123">V operačním systému Windows `debuggeePID` mapuje na operační systém zpracovávat identifikátor.</span><span class="sxs-lookup"><span data-stu-id="927e2-123">On the Windows operating system, `debuggeePID` maps to an OS process identifier.</span></span>  
  
 <span data-ttu-id="927e2-124">Paměť pro `ppHandleArrayOut` a `ppStringArrayOut` přidělují touto funkcí.</span><span class="sxs-lookup"><span data-stu-id="927e2-124">The memory for `ppHandleArrayOut` and `ppStringArrayOut` are allocated by this function.</span></span> <span data-ttu-id="927e2-125">K uvolnění paměti přidělené, musí volat [closeclrenumeration – funkce](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md).</span><span class="sxs-lookup"><span data-stu-id="927e2-125">To free the memory allocated, you must call [CloseCLREnumeration Function](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md).</span></span>  
  
 <span data-ttu-id="927e2-126">Tuto funkci lze volat s oba parametry pole nastavena na hodnotu null, aby mohla vrátit počet CLRs v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="927e2-126">This function can be called with both array parameters set to null in order to return the count of CLRs in the target process.</span></span> <span data-ttu-id="927e2-127">Z tohoto počtu může volající odvodit velikost vyrovnávací paměti, která bude vytvořena: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.</span><span class="sxs-lookup"><span data-stu-id="927e2-127">From this count, a caller can infer the size of the buffer that will be created: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="927e2-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="927e2-128">Requirements</span></span>  
 <span data-ttu-id="927e2-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="927e2-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="927e2-130">**Záhlaví:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="927e2-130">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="927e2-131">**Knihovna:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="927e2-131">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="927e2-132">**Verze rozhraní .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="927e2-132">**.NET Framework Versions:** 3.5 SP1</span></span>
