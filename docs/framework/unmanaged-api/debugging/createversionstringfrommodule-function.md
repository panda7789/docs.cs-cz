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
ms.openlocfilehash: 60b7d77542a5065fb1e09a98e659cac17fb093e9
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860855"
---
# <a name="createversionstringfrommodule-function"></a><span data-ttu-id="30aa2-102">CreateVersionStringFromModule – funkce</span><span class="sxs-lookup"><span data-stu-id="30aa2-102">CreateVersionStringFromModule Function</span></span>
<span data-ttu-id="30aa2-103">Vytvoří řetězec verze z cesty modulu CLR (Common Language Runtime) v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="30aa2-103">Creates a version string from a common language runtime (CLR) path in a target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30aa2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30aa2-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="30aa2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="30aa2-105">Parameters</span></span>  
 `pidDebuggee`  
 <span data-ttu-id="30aa2-106">pro Identifikátor procesu, ve kterém je načten cílový modul CLR.</span><span class="sxs-lookup"><span data-stu-id="30aa2-106">[in] Identifier of the process in which the target CLR is loaded.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="30aa2-107">pro Úplná nebo relativní cesta k cílovému modulu CLR, který je načten do procesu.</span><span class="sxs-lookup"><span data-stu-id="30aa2-107">[in] Full or relative path to the target CLR that is loaded in the process.</span></span>  
  
 `pBuffer`  
 <span data-ttu-id="30aa2-108">mimo Návratová vyrovnávací paměť pro uložení řetězce verze pro cílový CLR.</span><span class="sxs-lookup"><span data-stu-id="30aa2-108">[out] Return buffer for storing the version string for the target CLR.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="30aa2-109">pro Velikost `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="30aa2-109">[in] Size of `pBuffer`.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="30aa2-110">mimo Délka řetězce verze, kterou `pBuffer`vrátil.</span><span class="sxs-lookup"><span data-stu-id="30aa2-110">[out] Length of the version string returned by `pBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="30aa2-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="30aa2-111">Return Value</span></span>  
 <span data-ttu-id="30aa2-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="30aa2-112">S_OK</span></span>  
 <span data-ttu-id="30aa2-113">Řetězec verze pro cílový modul CLR byl úspěšně vrácen v `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="30aa2-113">The version string for the target CLR was successfully returned in `pBuffer`.</span></span>  
  
 <span data-ttu-id="30aa2-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="30aa2-114">E_INVALIDARG</span></span>  
 <span data-ttu-id="30aa2-115">`szModuleName`je null nebo buď `pBuffer` nebo `cchBuffer` je null.</span><span class="sxs-lookup"><span data-stu-id="30aa2-115">`szModuleName` is null, or either `pBuffer` or `cchBuffer` is null.</span></span> <span data-ttu-id="30aa2-116">`pBuffer`a `cchBuffer` musí mít hodnotu null nebo být null.</span><span class="sxs-lookup"><span data-stu-id="30aa2-116">`pBuffer` and `cchBuffer` must both be null or non-null.</span></span>  
  
 <span data-ttu-id="30aa2-117">HRESULT_FROM_WIN32 (ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="30aa2-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>  
 <span data-ttu-id="30aa2-118">`pdwLength`je větší než `cchBuffer`.</span><span class="sxs-lookup"><span data-stu-id="30aa2-118">`pdwLength` is greater than `cchBuffer`.</span></span> <span data-ttu-id="30aa2-119">To může být očekávaný výsledek, pokud jste předali hodnotu null pro `pBuffer` a `cchBuffer`a dotazováni jste na potřebnou velikost vyrovnávací paměti `pdwLength`pomocí.</span><span class="sxs-lookup"><span data-stu-id="30aa2-119">This may be an expected result if you have passed null for both `pBuffer` and `cchBuffer`, and queried the necessary buffer size by using `pdwLength`.</span></span>  
  
 <span data-ttu-id="30aa2-120">HRESULT_FROM_WIN32 (ERROR_MOD_NOT_FOUND)</span><span class="sxs-lookup"><span data-stu-id="30aa2-120">HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)</span></span>  
 <span data-ttu-id="30aa2-121">`szModuleName`neobsahuje cestu k platnému modulu CLR v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="30aa2-121">`szModuleName` does not contain a path to a valid CLR in the target process.</span></span>  
  
 <span data-ttu-id="30aa2-122">E_FAIL (nebo jiné návratové kódy E_)</span><span class="sxs-lookup"><span data-stu-id="30aa2-122">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="30aa2-123">`pidDebuggee`neodkazuje na platný proces nebo jiné selhání.</span><span class="sxs-lookup"><span data-stu-id="30aa2-123">`pidDebuggee` does not refer to a valid process, or other failure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30aa2-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="30aa2-124">Remarks</span></span>  
 <span data-ttu-id="30aa2-125">Tato funkce přijímá proces CLR, který je identifikován pomocí `pidDebuggee` , a cestu k řetězci, která je `szModuleName`určena parametrem.</span><span class="sxs-lookup"><span data-stu-id="30aa2-125">This function accepts a CLR process that is identified by `pidDebuggee` and a string path that is specified by `szModuleName`.</span></span> <span data-ttu-id="30aa2-126">Řetězec verze je vrácen do vyrovnávací paměti, která `pBuffer` odkazuje na.</span><span class="sxs-lookup"><span data-stu-id="30aa2-126">The version string is returned in the buffer that `pBuffer` points to.</span></span> <span data-ttu-id="30aa2-127">Tento řetězec je neprůhledný pro uživatele funkce. To znamená, že v samotném řetězci verze není žádný vnitřní význam.</span><span class="sxs-lookup"><span data-stu-id="30aa2-127">This string is opaque to the function user; that is, there is no intrinsic meaning in the version string itself.</span></span> <span data-ttu-id="30aa2-128">Používá se výhradně v kontextu této funkce a [funkci CreateDebuggingInterfaceFromVersion –](createdebugginginterfacefromversion-function-for-silverlight.md).</span><span class="sxs-lookup"><span data-stu-id="30aa2-128">It is used solely in the context of this function and the [CreateDebuggingInterfaceFromVersion function](createdebugginginterfacefromversion-function-for-silverlight.md).</span></span>  
  
 <span data-ttu-id="30aa2-129">Tato funkce by měla být volána dvakrát.</span><span class="sxs-lookup"><span data-stu-id="30aa2-129">This function should be called twice.</span></span> <span data-ttu-id="30aa2-130">Při prvním volání metody, předejte hodnotu null pro i `pBuffer` `cchBuffer`.</span><span class="sxs-lookup"><span data-stu-id="30aa2-130">When you call it the first time, pass null for both `pBuffer` and `cchBuffer`.</span></span> <span data-ttu-id="30aa2-131">Když to uděláte, bude vrácena velikost vyrovnávací paměti, která je `pBuffer` nezbytná pro `pdwLength`.</span><span class="sxs-lookup"><span data-stu-id="30aa2-131">When you do this, the size of the buffer necessary for `pBuffer` will be returned in `pdwLength`.</span></span> <span data-ttu-id="30aa2-132">Potom můžete zavolat funkci podruhé a předat vyrovnávací paměť v `pBuffer` a její velikosti v. `cchBuffer`</span><span class="sxs-lookup"><span data-stu-id="30aa2-132">You can then call the function a second time, and pass the buffer in `pBuffer` and its size in `cchBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30aa2-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="30aa2-133">Requirements</span></span>  
 <span data-ttu-id="30aa2-134">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30aa2-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30aa2-135">**Záhlaví:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="30aa2-135">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="30aa2-136">**Knihovna:** dbgshim. dll</span><span class="sxs-lookup"><span data-stu-id="30aa2-136">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="30aa2-137">**Verze .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="30aa2-137">**.NET Framework Versions:** 3.5 SP1</span></span>
