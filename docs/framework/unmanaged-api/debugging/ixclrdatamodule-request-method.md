---
title: IXCLRDataModule::Request – metoda
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::Request Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::Request Method
helpviewer.keywords:
- IXCLRDataModule::Request Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 2cc712e6560fc58af7526428ba40c424be388eee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54746658"
---
# <a name="ixclrdatamodulerequest-method"></a><span data-ttu-id="7cc64-102">IXCLRDataModule::Request – metoda</span><span class="sxs-lookup"><span data-stu-id="7cc64-102">IXCLRDataModule::Request Method</span></span>

<span data-ttu-id="7cc64-103">Požadavky k naplnění vyrovnávací paměť přidělená s daty modulu.</span><span class="sxs-lookup"><span data-stu-id="7cc64-103">Requests to populate the buffer given with the module's data.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="7cc64-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7cc64-104">Syntax</span></span>
```
HRESULT Request([in] ULONG32 reqCode,
    [in] ULONG32 inBufferSize,
    [in, size_is(inBufferSize)] BYTE* inBuffer,
    [in] ULONG32 outBufferSize,
    [out, size_is(outBufferSize)] BYTE* outBuffer);
```

### <a name="parameters"></a><span data-ttu-id="7cc64-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7cc64-105">Parameters</span></span>

<span data-ttu-id="7cc64-106">`reqCode` [in] Typ k odeslání žádosti.</span><span class="sxs-lookup"><span data-stu-id="7cc64-106">`reqCode` [in] Request type to be sent.</span></span>

<span data-ttu-id="7cc64-107">`inBufferSize` [in] velikost vstupní vyrovnávací paměť musí být předány.</span><span class="sxs-lookup"><span data-stu-id="7cc64-107">`inBufferSize` [in] size of the input buffer to be passed in.</span></span>

<span data-ttu-id="7cc64-108">`inBuffer` [in, size_is(inBufferSize)] Ukazatele na vyrovnávací paměti pro nezpracovaná data se odešle požadavek.</span><span class="sxs-lookup"><span data-stu-id="7cc64-108">`inBuffer` [in, size_is(inBufferSize)] Buffer pointer for the raw data to be sent in the request.</span></span>

<span data-ttu-id="7cc64-109">`outBufferSize` [in] Velikost výstupní vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="7cc64-109">`outBufferSize` [in] Size of the output buffer.</span></span>

<span data-ttu-id="7cc64-110">`outBuffer` [out, size_is(outBufferSize)] Ukazatel vyrovnávací paměť pro ukládání odpovědi na požadavek.</span><span class="sxs-lookup"><span data-stu-id="7cc64-110">`outBuffer` [out, size_is(outBufferSize)] Buffer pointer to used to store the request response.</span></span>

## <a name="remarks"></a><span data-ttu-id="7cc64-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7cc64-111">Remarks</span></span>

<span data-ttu-id="7cc64-112">Zadaná metoda je součástí `IXCLRDataModule` rozhraní a odpovídá 36 pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="7cc64-112">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 36th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="7cc64-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7cc64-113">Requirements</span></span>

<span data-ttu-id="7cc64-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cc64-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="7cc64-115">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="7cc64-115">**Header:** None</span></span>   
<span data-ttu-id="7cc64-116">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="7cc64-116">**Library:** None</span></span>  
<span data-ttu-id="7cc64-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7cc64-117">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="7cc64-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7cc64-118">See also</span></span>
- [<span data-ttu-id="7cc64-119">Ladění</span><span class="sxs-lookup"><span data-stu-id="7cc64-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="7cc64-120">IXCLRDataModule Interface</span><span class="sxs-lookup"><span data-stu-id="7cc64-120">IXCLRDataModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-interface.md)
