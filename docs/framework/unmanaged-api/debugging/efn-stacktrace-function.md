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
ms.openlocfilehash: 9035d9a53c4b0c8822b79e641aef092b4a48c418
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895043"
---
# <a name="_efn_stacktrace-function"></a><span data-ttu-id="1d0ff-102">\_EFN\_– funkce trasování zásobníku</span><span class="sxs-lookup"><span data-stu-id="1d0ff-102">\_EFN\_StackTrace Function</span></span>
<span data-ttu-id="1d0ff-103">Poskytuje textovou reprezentaci spravovaného trasování zásobníku a pole `CONTEXT` záznamů, jednu pro každý přechod mezi nespravovaným a spravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="1d0ff-103">Provides a text representation of a managed stack trace and an array of `CONTEXT` records, one for each transition between unmanaged and managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d0ff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d0ff-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="1d0ff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1d0ff-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="1d0ff-106">pro Probíhá ladění klienta.</span><span class="sxs-lookup"><span data-stu-id="1d0ff-106">[in] The client being debugged.</span></span>  
  
 `wszTextOut`  
 <span data-ttu-id="1d0ff-107">mimo Textová reprezentace trasování zásobníku.</span><span class="sxs-lookup"><span data-stu-id="1d0ff-107">[out] The text representation of the stack trace.</span></span>  
  
 `puiTextLength`  
 <span data-ttu-id="1d0ff-108">mimo Ukazatel na počet znaků v `wszTextOut`.</span><span class="sxs-lookup"><span data-stu-id="1d0ff-108">[out] A pointer to the number of characters in `wszTextOut`.</span></span>  
  
 `pTransitionContexts`  
 <span data-ttu-id="1d0ff-109">mimo Pole kontextů přechodu.</span><span class="sxs-lookup"><span data-stu-id="1d0ff-109">[out] The array of transition contexts.</span></span>  
  
 `puiTransitionContextCount`  
 <span data-ttu-id="1d0ff-110">mimo Ukazatel na počet kontextů přechodu v poli.</span><span class="sxs-lookup"><span data-stu-id="1d0ff-110">[out] A pointer to the number of transition contexts in the array.</span></span>  
  
 `uiSizeOfContext`  
 <span data-ttu-id="1d0ff-111">pro Velikost struktury kontextu.</span><span class="sxs-lookup"><span data-stu-id="1d0ff-111">[in] The size of the context structure.</span></span>  
  
 `Flags`  
 <span data-ttu-id="1d0ff-112">pro Nastavte na hodnotu 0 nebo SOS_STACKTRACE_SHOWADDRESSES (0x01), aby se zobrazil registr EBP a jako ukazatel na zadání zásobníku (ESP) před každým `module!functionname` řádkem.</span><span class="sxs-lookup"><span data-stu-id="1d0ff-112">[in] Set to either 0 or SOS_STACKTRACE_SHOWADDRESSES (0x01) to show the EBP register and the enter stack pointer (ESP) in front of each `module!functionname` line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d0ff-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1d0ff-113">Remarks</span></span>  
 <span data-ttu-id="1d0ff-114">`_EFN_StackTrace` Struktura může být volána z programového rozhraní WinDbg.</span><span class="sxs-lookup"><span data-stu-id="1d0ff-114">The `_EFN_StackTrace` structure can be called from a WinDbg programmatic interface.</span></span> <span data-ttu-id="1d0ff-115">Parametry se používají takto:</span><span class="sxs-lookup"><span data-stu-id="1d0ff-115">Parameters are used as follows:</span></span>  
  
- <span data-ttu-id="1d0ff-116">Pokud `wszTextOut` má hodnotu null `puiTextLength` a není null, funkce vrátí délku řetězce v `puiTextLength`.</span><span class="sxs-lookup"><span data-stu-id="1d0ff-116">If `wszTextOut` is null and `puiTextLength` is not null, the function returns the string length in `puiTextLength`.</span></span>  
  
- <span data-ttu-id="1d0ff-117">Pokud `wszTextOut` není null, funkce ukládá `wszTextOut` text až `puiTextLength`do umístění, které je uvedeno v.</span><span class="sxs-lookup"><span data-stu-id="1d0ff-117">If `wszTextOut` is not null, the function stores text in `wszTextOut` up to the location indicated by `puiTextLength`.</span></span> <span data-ttu-id="1d0ff-118">Pokud byla ve vyrovnávací paměti dostatek místa, vrátí se úspěšně, nebo pokud vyrovnávací paměť není dost velká, vrátí E_OUTOFMEMORY.</span><span class="sxs-lookup"><span data-stu-id="1d0ff-118">It returns successfully if there was enough room in the buffer, or returns E_OUTOFMEMORY if the buffer was not long enough.</span></span>  
  
- <span data-ttu-id="1d0ff-119">Část přechodu funkce je ignorována, pokud `pTransitionContexts` a `puiTransitionContextCount` jsou obě hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="1d0ff-119">The transition portion of the function is ignored if `pTransitionContexts` and `puiTransitionContextCount` are both null.</span></span> <span data-ttu-id="1d0ff-120">V tomto případě funkce poskytuje volajícím textový výstup pouze názvů funkcí.</span><span class="sxs-lookup"><span data-stu-id="1d0ff-120">In this case, the function provides callers with text output of only the function names.</span></span>  
  
- <span data-ttu-id="1d0ff-121">Pokud `pTransitionContexts` má hodnotu null `puiTransitionContextCount` a není null, funkce vrátí potřebný počet kontextových položek v `puiTransitionContextCount`.</span><span class="sxs-lookup"><span data-stu-id="1d0ff-121">If `pTransitionContexts` is null and `puiTransitionContextCount` is not null, the function returns the necessary number of context entries in `puiTransitionContextCount`.</span></span>  
  
- <span data-ttu-id="1d0ff-122">Pokud `pTransitionContexts` hodnota není null, funkce ji zpracuje jako pole struktury délky `puiTransitionContextCount`.</span><span class="sxs-lookup"><span data-stu-id="1d0ff-122">If `pTransitionContexts` is not null, the function treats it as an array of structures of length `puiTransitionContextCount`.</span></span> <span data-ttu-id="1d0ff-123">Velikost struktury je dána `uiSizeOfContext`, a musí se jednat o velikost [SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) nebo `CONTEXT` pro architekturu.</span><span class="sxs-lookup"><span data-stu-id="1d0ff-123">The structure size is given by `uiSizeOfContext`, and must be the size of [SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) or `CONTEXT` for the architecture.</span></span>  
  
- <span data-ttu-id="1d0ff-124">`wszTextOut`je zapsán v následujícím formátu:</span><span class="sxs-lookup"><span data-stu-id="1d0ff-124">`wszTextOut` is written in the following format:</span></span>  
  
    ```output  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
- <span data-ttu-id="1d0ff-125">Pokud je posun v šestnáctkové soustavě 0x0, není zapsán žádný posun.</span><span class="sxs-lookup"><span data-stu-id="1d0ff-125">If the offset in hex is 0x0, no offset is written.</span></span>  
  
- <span data-ttu-id="1d0ff-126">Pokud není ve vlákně aktuálně v kontextu žádný spravovaný kód, funkce vrátí SOS_E_NOMANAGEDCODE.</span><span class="sxs-lookup"><span data-stu-id="1d0ff-126">If there is no managed code on the thread currently in context, the function returns SOS_E_NOMANAGEDCODE.</span></span>  
  
- <span data-ttu-id="1d0ff-127">Parametr je buď 0, nebo SOS_STACKTRACE_SHOWADDRESSES, aby se zobrazily EBP a ESP před `module!functionname` každým řádkem. `Flags`</span><span class="sxs-lookup"><span data-stu-id="1d0ff-127">The `Flags` parameter is either 0 or SOS_STACKTRACE_SHOWADDRESSES to see EBP and ESP in front of each `module!functionname` line.</span></span> <span data-ttu-id="1d0ff-128">Ve výchozím nastavení má hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="1d0ff-128">By default, it is 0.</span></span>  
  
    ```cpp  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a><span data-ttu-id="1d0ff-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1d0ff-129">Requirements</span></span>  
 <span data-ttu-id="1d0ff-130">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d0ff-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d0ff-131">**Hlaviček** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="1d0ff-131">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="1d0ff-132">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d0ff-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d0ff-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1d0ff-133">See also</span></span>

- [<span data-ttu-id="1d0ff-134">Globální statické funkce pro ladění</span><span class="sxs-lookup"><span data-stu-id="1d0ff-134">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
