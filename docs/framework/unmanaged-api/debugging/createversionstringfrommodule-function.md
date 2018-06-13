---
title: CreateVersionStringFromModule – funkce
ms.date: 03/30/2017
api_name:
- CreateVersionStringFromModule
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- CreateVersionStringFromModule
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CreateVersionStringFromModule function
ms.assetid: 3d2fe9bd-75ef-4364-84a6-da1e1994ac1a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0988b2c4471cb5449f7c7fac82c6e94bcd537b7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33409277"
---
# <a name="createversionstringfrommodule-function"></a><span data-ttu-id="a4312-102">CreateVersionStringFromModule – funkce</span><span class="sxs-lookup"><span data-stu-id="a4312-102">CreateVersionStringFromModule Function</span></span>
<span data-ttu-id="a4312-103">Vytvoří řetězec verze z běžných language runtime (CLR) cestu Cílový proces.</span><span class="sxs-lookup"><span data-stu-id="a4312-103">Creates a version string from a common language runtime (CLR) path in a target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4312-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4312-104">Syntax</span></span>  
  
```  
HRESULT CreateVersionStringFromModule (  
    [in]  DWORD      pidDebuggee,  
    [in]  LPCWSTR    szModuleName,  
    [out, size_is(cchBuffer),  
          length_is(*pdwLength)] LPWSTR Buffer,  
    [in]  DWORD      cchBuffer,  
    [out] DWORD*     pdwLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a4312-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a4312-105">Parameters</span></span>  
 `pidDebuggee`  
 <span data-ttu-id="a4312-106">[v] Identifikátor procesu, ve kterém je načtena cíl CLR.</span><span class="sxs-lookup"><span data-stu-id="a4312-106">[in] Identifier of the process in which the target CLR is loaded.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="a4312-107">[v] Úplná nebo relativní cesta k cílovému CLR, který je načten do procesu.</span><span class="sxs-lookup"><span data-stu-id="a4312-107">[in] Full or relative path to the target CLR that is loaded in the process.</span></span>  
  
 `pBuffer`  
 <span data-ttu-id="a4312-108">[out] Vrátí velikost vyrovnávací paměti pro ukládání řetězec verze pro cíl CLR.</span><span class="sxs-lookup"><span data-stu-id="a4312-108">[out] Return buffer for storing the version string for the target CLR.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="a4312-109">[v] Velikost `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="a4312-109">[in] Size of `pBuffer`.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="a4312-110">[out] Délka řetězce verze vrácený `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="a4312-110">[out] Length of the version string returned by `pBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4312-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a4312-111">Return Value</span></span>  
 <span data-ttu-id="a4312-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="a4312-112">S_OK</span></span>  
 <span data-ttu-id="a4312-113">Řetězec verze pro cíl CLR byla úspěšně vrácena v `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="a4312-113">The version string for the target CLR was successfully returned in `pBuffer`.</span></span>  
  
 <span data-ttu-id="a4312-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a4312-114">E_INVALIDARG</span></span>  
 <span data-ttu-id="a4312-115">`szModuleName` je null, nebo zadejte `pBuffer` nebo `cchBuffer` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="a4312-115">`szModuleName` is null, or either `pBuffer` or `cchBuffer` is null.</span></span> <span data-ttu-id="a4312-116">`pBuffer` a `cchBuffer` musí být null ani nesmí být nulová.</span><span class="sxs-lookup"><span data-stu-id="a4312-116">`pBuffer` and `cchBuffer` must both be null or non-null.</span></span>  
  
 <span data-ttu-id="a4312-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="a4312-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>  
 <span data-ttu-id="a4312-118">`pdwLength` je větší než `cchBuffer`.</span><span class="sxs-lookup"><span data-stu-id="a4312-118">`pdwLength` is greater than `cchBuffer`.</span></span> <span data-ttu-id="a4312-119">Pokud jste pro obě uplynulo hodnotu null. to může být očekávaný výsledek `pBuffer` a `cchBuffer`a dotaz velikost vyrovnávací paměti nezbytné pomocí `pdwLength`.</span><span class="sxs-lookup"><span data-stu-id="a4312-119">This may be an expected result if you have passed null for both `pBuffer` and `cchBuffer`, and queried the necessary buffer size by using `pdwLength`.</span></span>  
  
 <span data-ttu-id="a4312-120">HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)</span><span class="sxs-lookup"><span data-stu-id="a4312-120">HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)</span></span>  
 <span data-ttu-id="a4312-121">`szModuleName` neobsahuje cestu k platný CLR v tento cílový proces.</span><span class="sxs-lookup"><span data-stu-id="a4312-121">`szModuleName` does not contain a path to a valid CLR in the target process.</span></span>  
  
 <span data-ttu-id="a4312-122">E_FAIL (nebo ostatní návratové kódy E_)</span><span class="sxs-lookup"><span data-stu-id="a4312-122">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="a4312-123">`pidDebuggee` neodkazuje na platný procesu nebo jiné chyby.</span><span class="sxs-lookup"><span data-stu-id="a4312-123">`pidDebuggee` does not refer to a valid process, or other failure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4312-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a4312-124">Remarks</span></span>  
 <span data-ttu-id="a4312-125">Tato funkce přijímá CLR proces, který je určený podle `pidDebuggee` a řetězec cesty, která je zadána `szModuleName`.</span><span class="sxs-lookup"><span data-stu-id="a4312-125">This function accepts a CLR process that is identified by `pidDebuggee` and a string path that is specified by `szModuleName`.</span></span> <span data-ttu-id="a4312-126">Řetězec verze se vrátí ve vyrovnávací paměti, `pBuffer` odkazuje na.</span><span class="sxs-lookup"><span data-stu-id="a4312-126">The version string is returned in the buffer that `pBuffer` points to.</span></span> <span data-ttu-id="a4312-127">Tento řetězec je plné krytí funkce uživateli; To znamená neexistuje žádný vnitřní význam v samotné řetězec verze.</span><span class="sxs-lookup"><span data-stu-id="a4312-127">This string is opaque to the function user; that is, there is no intrinsic meaning in the version string itself.</span></span> <span data-ttu-id="a4312-128">Se používá pouze v kontextu této funkce a [createdebugginginterfacefromversion – funkce](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md).</span><span class="sxs-lookup"><span data-stu-id="a4312-128">It is used solely in the context of this function and the [CreateDebuggingInterfaceFromVersion function](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md).</span></span>  
  
 <span data-ttu-id="a4312-129">Tato funkce by měla být volána dvakrát.</span><span class="sxs-lookup"><span data-stu-id="a4312-129">This function should be called twice.</span></span> <span data-ttu-id="a4312-130">Při volání ji poprvé, předat hodnotu null pro obě `pBuffer` a `cchBuffer`.</span><span class="sxs-lookup"><span data-stu-id="a4312-130">When you call it the first time, pass null for both `pBuffer` and `cchBuffer`.</span></span> <span data-ttu-id="a4312-131">Pokud jste to provést, velikost vyrovnávací paměti, která je potřebná pro `pBuffer` , vrátí se `pdwLength`.</span><span class="sxs-lookup"><span data-stu-id="a4312-131">When you do this, the size of the buffer necessary for `pBuffer` will be returned in `pdwLength`.</span></span> <span data-ttu-id="a4312-132">Můžete pak zavolejte funkci znovu a předávat vyrovnávací paměť v `pBuffer` a jeho velikost v `cchBuffer`.</span><span class="sxs-lookup"><span data-stu-id="a4312-132">You can then call the function a second time, and pass the buffer in `pBuffer` and its size in `cchBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4312-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a4312-133">Requirements</span></span>  
 <span data-ttu-id="a4312-134">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4312-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4312-135">**Záhlaví:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="a4312-135">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="a4312-136">**Knihovna:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="a4312-136">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="a4312-137">**Verze rozhraní .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="a4312-137">**.NET Framework Versions:** 3.5 SP1</span></span>
