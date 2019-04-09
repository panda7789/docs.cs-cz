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
ms.openlocfilehash: a02a60668ae6caaad1940395822758331b93f550
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119792"
---
# <a name="ixclrdatamodulerequest-method"></a><span data-ttu-id="9691c-102">IXCLRDataModule::Request – metoda</span><span class="sxs-lookup"><span data-stu-id="9691c-102">IXCLRDataModule::Request Method</span></span>

<span data-ttu-id="9691c-103">Požadavky k naplnění vyrovnávací paměť přidělená s daty modulu.</span><span class="sxs-lookup"><span data-stu-id="9691c-103">Requests to populate the buffer given with the module's data.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="9691c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9691c-104">Syntax</span></span>
```
HRESULT Request([in] ULONG32 reqCode,
    [in] ULONG32 inBufferSize,
    [in, size_is(inBufferSize)] BYTE* inBuffer,
    [in] ULONG32 outBufferSize,
    [out, size_is(outBufferSize)] BYTE* outBuffer);
```

## <a name="parameters"></a><span data-ttu-id="9691c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9691c-105">Parameters</span></span>

`reqCode`\
<span data-ttu-id="9691c-106">[in] Typ k odeslání žádosti.</span><span class="sxs-lookup"><span data-stu-id="9691c-106">[in] Request type to be sent.</span></span>

`inBufferSize`\
<span data-ttu-id="9691c-107">[in] velikost vstupní vyrovnávací paměť musí být předány.</span><span class="sxs-lookup"><span data-stu-id="9691c-107">[in] size of the input buffer to be passed in.</span></span>

`inBuffer`\
<span data-ttu-id="9691c-108">[in, size_is(inBufferSize)] Ukazatele na vyrovnávací paměti pro nezpracovaná data se odešle požadavek.</span><span class="sxs-lookup"><span data-stu-id="9691c-108">[in, size_is(inBufferSize)] Buffer pointer for the raw data to be sent in the request.</span></span>

`outBufferSize`\
<span data-ttu-id="9691c-109">[in] Velikost výstupní vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="9691c-109">[in] Size of the output buffer.</span></span>

`outBuffer`\
<span data-ttu-id="9691c-110">[out, size_is(outBufferSize)] Ukazatel vyrovnávací paměť pro ukládání odpovědi na požadavek.</span><span class="sxs-lookup"><span data-stu-id="9691c-110">[out, size_is(outBufferSize)] Buffer pointer to used to store the request response.</span></span>

## <a name="remarks"></a><span data-ttu-id="9691c-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9691c-111">Remarks</span></span>

<span data-ttu-id="9691c-112">Zadaná metoda je součástí `IXCLRDataModule` rozhraní a odpovídá 36 pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="9691c-112">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 36th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="9691c-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9691c-113">Requirements</span></span>

<span data-ttu-id="9691c-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9691c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="9691c-115">**Záhlaví:** Žádné</span><span class="sxs-lookup"><span data-stu-id="9691c-115">**Header:** None</span></span>   
<span data-ttu-id="9691c-116">**Knihovna:** Žádné</span><span class="sxs-lookup"><span data-stu-id="9691c-116">**Library:** None</span></span>  
**<span data-ttu-id="9691c-117">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="9691c-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a><span data-ttu-id="9691c-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9691c-118">See also</span></span>

- [<span data-ttu-id="9691c-119">Ladění</span><span class="sxs-lookup"><span data-stu-id="9691c-119">Debugging</span></span>](index.md)
- [<span data-ttu-id="9691c-120">IXCLRDataModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9691c-120">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)