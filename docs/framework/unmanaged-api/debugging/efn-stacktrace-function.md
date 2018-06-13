---
title: _EFN_StackTrace – funkce
ms.date: 03/30/2017
api_name:
- _EFN_StackTrace
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_StackTrace
helpviewer_keywords:
- _EFN_StackTrace function [.NET Framework debugging]
ms.assetid: caea7754-867c-4360-a65c-5ced4408fd9d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 39a249108d10e5dc382775378e2d6b84bba87356
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408083"
---
# <a name="efnstacktrace-function"></a><span data-ttu-id="15601-102">_EFN_StackTrace – funkce</span><span class="sxs-lookup"><span data-stu-id="15601-102">_EFN_StackTrace Function</span></span>
<span data-ttu-id="15601-103">Poskytuje textové reprezentace trasování spravované zásobníku a pole `CONTEXT` zaznamenává, jednu pro každý přechod mezi nespravované a spravované kódu.</span><span class="sxs-lookup"><span data-stu-id="15601-103">Provides a text representation of a managed stack trace and an array of `CONTEXT` records, one for each transition between unmanaged and managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15601-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15601-104">Syntax</span></span>  
  
```  
HRESULT CALLBACK _EFN_StackTrace(  
    [in]  PDEBUG_CLIENT  Client,  
    [out] WCHAR          wszTextOut[],  
    [out] size_t         *puiTextLength,  
    [out] LPVOID         pTransitionContexts,  
    [out] size_t         *puiTransitionContextCount,  
    [in]  size_t         uiSizeOfContext,  
    [in]  DWORD          Flags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="15601-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="15601-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="15601-106">[v] Klient laděné.</span><span class="sxs-lookup"><span data-stu-id="15601-106">[in] The client being debugged.</span></span>  
  
 `wszTextOut`  
 <span data-ttu-id="15601-107">[out] Reprezentace textu trasování zásobníku.</span><span class="sxs-lookup"><span data-stu-id="15601-107">[out] The text representation of the stack trace.</span></span>  
  
 `puiTextLength`  
 <span data-ttu-id="15601-108">[out] Ukazatel na počet znaků v `wszTextOut`.</span><span class="sxs-lookup"><span data-stu-id="15601-108">[out] A pointer to the number of characters in `wszTextOut`.</span></span>  
  
 `pTransitionContexts`  
 <span data-ttu-id="15601-109">[out] Pole kontexty přechodu.</span><span class="sxs-lookup"><span data-stu-id="15601-109">[out] The array of transition contexts.</span></span>  
  
 `puiTransitionContextCount`  
 <span data-ttu-id="15601-110">[out] Ukazatel na počet přechod kontexty v poli.</span><span class="sxs-lookup"><span data-stu-id="15601-110">[out] A pointer to the number of transition contexts in the array.</span></span>  
  
 `uiSizeOfContext`  
 <span data-ttu-id="15601-111">[v] Velikost strukturu kontextu.</span><span class="sxs-lookup"><span data-stu-id="15601-111">[in] The size of the context structure.</span></span>  
  
 `Flags`  
 <span data-ttu-id="15601-112">[v] Nastavte na hodnotu 0 nebo SOS_STACKTRACE_SHOWADDRESSES (0x01) pro zobrazení EBP registrace a ukazatel zásobníku enter (ESP) před každou `module!functionname` řádku.</span><span class="sxs-lookup"><span data-stu-id="15601-112">[in] Set to either 0 or SOS_STACKTRACE_SHOWADDRESSES (0x01) to show the EBP register and the enter stack pointer (ESP) in front of each `module!functionname` line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15601-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="15601-113">Remarks</span></span>  
 <span data-ttu-id="15601-114">`_EFN_StackTrace` Struktura lze volat z WinDbg programovací rozhraní.</span><span class="sxs-lookup"><span data-stu-id="15601-114">The `_EFN_StackTrace` structure can be called from a WinDbg programmatic interface.</span></span> <span data-ttu-id="15601-115">Parametry se používají následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="15601-115">Parameters are used as follows:</span></span>  
  
-   <span data-ttu-id="15601-116">Pokud `wszTextOut` má hodnotu null a `puiTextLength` je hodnotou not null, funkce vrátí hodnotu délka řetězce v `puiTextLength`.</span><span class="sxs-lookup"><span data-stu-id="15601-116">If `wszTextOut` is null and `puiTextLength` is not null, the function returns the string length in `puiTextLength`.</span></span>  
  
-   <span data-ttu-id="15601-117">Pokud `wszTextOut` je hodnotou not null, funkce ukládá textu v `wszTextOut` až do umístění určeného v `puiTextLength`.</span><span class="sxs-lookup"><span data-stu-id="15601-117">If `wszTextOut` is not null, the function stores text in `wszTextOut` up to the location indicated by `puiTextLength`.</span></span> <span data-ttu-id="15601-118">Vrátí úspěšně Pokud byl dostatek místa ve vyrovnávací paměti nebo vrátí E_OUTOFMEMORY Pokud vyrovnávací paměť nebylo dost dlouhé.</span><span class="sxs-lookup"><span data-stu-id="15601-118">It returns successfully if there was enough room in the buffer, or returns E_OUTOFMEMORY if the buffer was not long enough.</span></span>  
  
-   <span data-ttu-id="15601-119">Část přechod funkce je ignorována, pokud `pTransitionContexts` a `puiTransitionContextCount` jsou oba hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="15601-119">The transition portion of the function is ignored if `pTransitionContexts` and `puiTransitionContextCount` are both null.</span></span> <span data-ttu-id="15601-120">V takovém případě funkce poskytuje volající s textového výstupu pouze názvy funkcí.</span><span class="sxs-lookup"><span data-stu-id="15601-120">In this case, the function provides callers with text output of only the function names.</span></span>  
  
-   <span data-ttu-id="15601-121">Pokud `pTransitionContexts` má hodnotu null a `puiTransitionContextCount` je hodnotou not null, funkce vrátí hodnotu potřebný počet položek kontextu v `puiTransitionContextCount`.</span><span class="sxs-lookup"><span data-stu-id="15601-121">If `pTransitionContexts` is null and `puiTransitionContextCount` is not null, the function returns the necessary number of context entries in `puiTransitionContextCount`.</span></span>  
  
-   <span data-ttu-id="15601-122">Pokud `pTransitionContexts` je hodnotou not null, funkce považuje se za pole struktury délky `puiTransitionContextCount`.</span><span class="sxs-lookup"><span data-stu-id="15601-122">If `pTransitionContexts` is not null, the function treats it as an array of structures of length `puiTransitionContextCount`.</span></span> <span data-ttu-id="15601-123">Je dán velikost struktury `uiSizeOfContext`, a musí být velikost [simplecontext –](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) nebo `CONTEXT` pro architekturu.</span><span class="sxs-lookup"><span data-stu-id="15601-123">The structure size is given by `uiSizeOfContext`, and must be the size of [SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) or `CONTEXT` for the architecture.</span></span>  
  
-   <span data-ttu-id="15601-124">`wszTextOut` je napsána v následujícím formátu:</span><span class="sxs-lookup"><span data-stu-id="15601-124">`wszTextOut` is written in the following format:</span></span>  
  
    ```  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
-   <span data-ttu-id="15601-125">Pokud posun v šestnáctkové soustavě 0x0, je zapsán posunutí.</span><span class="sxs-lookup"><span data-stu-id="15601-125">If the offset in hex is 0x0, no offset is written.</span></span>  
  
-   <span data-ttu-id="15601-126">Pokud je spravovaný kód ve vlákně aktuálně v kontextu, funkce vrátí hodnotu SOS_E_NOMANAGEDCODE.</span><span class="sxs-lookup"><span data-stu-id="15601-126">If there is no managed code on the thread currently in context, the function returns SOS_E_NOMANAGEDCODE.</span></span>  
  
-   <span data-ttu-id="15601-127">`Flags` Parametru se 0 nebo SOS_STACKTRACE_SHOWADDRESSES zobrazíte EBP a ESP před každou `module!functionname` řádku.</span><span class="sxs-lookup"><span data-stu-id="15601-127">The `Flags` parameter is either 0 or SOS_STACKTRACE_SHOWADDRESSES to see EBP and ESP in front of each `module!functionname` line.</span></span> <span data-ttu-id="15601-128">Ve výchozím nastavení je 0.</span><span class="sxs-lookup"><span data-stu-id="15601-128">By default, it is 0.</span></span>  
  
    ```  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a><span data-ttu-id="15601-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="15601-129">Requirements</span></span>  
 <span data-ttu-id="15601-130">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15601-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15601-131">**Záhlaví:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="15601-131">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="15601-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15601-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15601-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="15601-133">See Also</span></span>  
 [<span data-ttu-id="15601-134">Globální statické funkce pro ladění</span><span class="sxs-lookup"><span data-stu-id="15601-134">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
