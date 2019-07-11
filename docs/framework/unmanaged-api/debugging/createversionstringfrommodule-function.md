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
ms.openlocfilehash: b68624b962ed610dbeecd3e4cead769ab1400f4a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739211"
---
# <a name="createversionstringfrommodule-function"></a><span data-ttu-id="a04c0-102">CreateVersionStringFromModule – funkce</span><span class="sxs-lookup"><span data-stu-id="a04c0-102">CreateVersionStringFromModule Function</span></span>
<span data-ttu-id="a04c0-103">Vytvoří řetězec verze z společná cesta modulu runtime (CLR) jazyka v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="a04c0-103">Creates a version string from a common language runtime (CLR) path in a target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a04c0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a04c0-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateVersionStringFromModule (  
    [in]  DWORD      pidDebuggee,  
    [in]  LPCWSTR    szModuleName,  
    [out, size_is(cchBuffer),  
          length_is(*pdwLength)] LPWSTR Buffer,  
    [in]  DWORD      cchBuffer,  
    [out] DWORD*     pdwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a04c0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a04c0-105">Parameters</span></span>  
 `pidDebuggee`  
 <span data-ttu-id="a04c0-106">[in] Identifikátor procesu, ve které je cílem CLR načten.</span><span class="sxs-lookup"><span data-stu-id="a04c0-106">[in] Identifier of the process in which the target CLR is loaded.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="a04c0-107">[in] Úplná nebo relativní cesta k cíli CLR, který je načten do procesu.</span><span class="sxs-lookup"><span data-stu-id="a04c0-107">[in] Full or relative path to the target CLR that is loaded in the process.</span></span>  
  
 `pBuffer`  
 <span data-ttu-id="a04c0-108">[out] Vrátí vyrovnávací paměť pro ukládání řetězce verze pro cíl CLR.</span><span class="sxs-lookup"><span data-stu-id="a04c0-108">[out] Return buffer for storing the version string for the target CLR.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="a04c0-109">[in] Velikost `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="a04c0-109">[in] Size of `pBuffer`.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="a04c0-110">[out] Délka řetězce verze vrácené `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="a04c0-110">[out] Length of the version string returned by `pBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a04c0-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a04c0-111">Return Value</span></span>  
 <span data-ttu-id="a04c0-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="a04c0-112">S_OK</span></span>  
 <span data-ttu-id="a04c0-113">Řetězec verze pro cíl modulu CLR byla úspěšně vrácena v `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="a04c0-113">The version string for the target CLR was successfully returned in `pBuffer`.</span></span>  
  
 <span data-ttu-id="a04c0-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a04c0-114">E_INVALIDARG</span></span>  
 <span data-ttu-id="a04c0-115">`szModuleName` je null nebo buď `pBuffer` nebo `cchBuffer` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="a04c0-115">`szModuleName` is null, or either `pBuffer` or `cchBuffer` is null.</span></span> <span data-ttu-id="a04c0-116">`pBuffer` a `cchBuffer` musí být null nebo jinou hodnotu než null.</span><span class="sxs-lookup"><span data-stu-id="a04c0-116">`pBuffer` and `cchBuffer` must both be null or non-null.</span></span>  
  
 <span data-ttu-id="a04c0-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="a04c0-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>  
 <span data-ttu-id="a04c0-118">`pdwLength` je větší než `cchBuffer`.</span><span class="sxs-lookup"><span data-stu-id="a04c0-118">`pdwLength` is greater than `cchBuffer`.</span></span> <span data-ttu-id="a04c0-119">Pokud jste u obou prošly hodnotu null, může dojít očekávaný výsledek `pBuffer` a `cchBuffer`, Power pivotu a dotazované nezbytné vyrovnávací paměť s použitím `pdwLength`.</span><span class="sxs-lookup"><span data-stu-id="a04c0-119">This may be an expected result if you have passed null for both `pBuffer` and `cchBuffer`, and queried the necessary buffer size by using `pdwLength`.</span></span>  
  
 <span data-ttu-id="a04c0-120">HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)</span><span class="sxs-lookup"><span data-stu-id="a04c0-120">HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)</span></span>  
 <span data-ttu-id="a04c0-121">`szModuleName` neobsahuje cestu k platné CLR v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="a04c0-121">`szModuleName` does not contain a path to a valid CLR in the target process.</span></span>  
  
 <span data-ttu-id="a04c0-122">E_FAIL (nebo jiné E_ návratové kódy)</span><span class="sxs-lookup"><span data-stu-id="a04c0-122">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="a04c0-123">`pidDebuggee` neodkazuje na platný proces nebo jiné chyby.</span><span class="sxs-lookup"><span data-stu-id="a04c0-123">`pidDebuggee` does not refer to a valid process, or other failure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a04c0-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a04c0-124">Remarks</span></span>  
 <span data-ttu-id="a04c0-125">Tato funkce přijme procesu CLR, který je identifikován `pidDebuggee` a řetězec cesty, která je zadána `szModuleName`.</span><span class="sxs-lookup"><span data-stu-id="a04c0-125">This function accepts a CLR process that is identified by `pidDebuggee` and a string path that is specified by `szModuleName`.</span></span> <span data-ttu-id="a04c0-126">Řetězec verze je vrácen ve vyrovnávací paměti, která `pBuffer` odkazuje na.</span><span class="sxs-lookup"><span data-stu-id="a04c0-126">The version string is returned in the buffer that `pBuffer` points to.</span></span> <span data-ttu-id="a04c0-127">Tento řetězec je neprůhledný funkce uživatele. To znamená, že neexistuje žádný vnitřní význam v samotný řetězec verze.</span><span class="sxs-lookup"><span data-stu-id="a04c0-127">This string is opaque to the function user; that is, there is no intrinsic meaning in the version string itself.</span></span> <span data-ttu-id="a04c0-128">Používá se pouze v rámci této funkce a [createdebugginginterfacefromversion – funkce](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md).</span><span class="sxs-lookup"><span data-stu-id="a04c0-128">It is used solely in the context of this function and the [CreateDebuggingInterfaceFromVersion function](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md).</span></span>  
  
 <span data-ttu-id="a04c0-129">Tato funkce by měla být volána dvakrát.</span><span class="sxs-lookup"><span data-stu-id="a04c0-129">This function should be called twice.</span></span> <span data-ttu-id="a04c0-130">Při volání ji první, předat hodnotu null pro obě `pBuffer` a `cchBuffer`.</span><span class="sxs-lookup"><span data-stu-id="a04c0-130">When you call it the first time, pass null for both `pBuffer` and `cchBuffer`.</span></span> <span data-ttu-id="a04c0-131">Pokud to provedete, velikost vyrovnávací paměti pro `pBuffer` , vrátí se `pdwLength`.</span><span class="sxs-lookup"><span data-stu-id="a04c0-131">When you do this, the size of the buffer necessary for `pBuffer` will be returned in `pdwLength`.</span></span> <span data-ttu-id="a04c0-132">Můžete pak zavolejte funkci znovu a předejte vyrovnávací paměti v `pBuffer` a jeho velikost v `cchBuffer`.</span><span class="sxs-lookup"><span data-stu-id="a04c0-132">You can then call the function a second time, and pass the buffer in `pBuffer` and its size in `cchBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a04c0-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a04c0-133">Requirements</span></span>  
 <span data-ttu-id="a04c0-134">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a04c0-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a04c0-135">**Záhlaví:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="a04c0-135">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="a04c0-136">**Knihovna:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="a04c0-136">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="a04c0-137">**Verze rozhraní .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="a04c0-137">**.NET Framework Versions:** 3.5 SP1</span></span>
