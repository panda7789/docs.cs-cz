---
title: 'IXCLRDataModule:: Request – metoda'
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
ms.openlocfilehash: 44ee4fc7fc2368b65f6f2fffe6ac239beddc6293
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395272"
---
# <a name="ixclrdatamodulerequest-method"></a><span data-ttu-id="b2454-102">IXCLRDataModule:: Request – metoda</span><span class="sxs-lookup"><span data-stu-id="b2454-102">IXCLRDataModule::Request Method</span></span>

<span data-ttu-id="b2454-103">Žádosti o naplnění vyrovnávací paměti dané daty modulu.</span><span class="sxs-lookup"><span data-stu-id="b2454-103">Requests to populate the buffer given with the module's data.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="b2454-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2454-104">Syntax</span></span>

```cpp
HRESULT Request([in] ULONG32 reqCode,
    [in] ULONG32 inBufferSize,
    [in, size_is(inBufferSize)] BYTE* inBuffer,
    [in] ULONG32 outBufferSize,
    [out, size_is(outBufferSize)] BYTE* outBuffer);
```

## <a name="parameters"></a><span data-ttu-id="b2454-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b2454-105">Parameters</span></span>

`reqCode`\
<span data-ttu-id="b2454-106">pro Typ požadavku, který se má odeslat</span><span class="sxs-lookup"><span data-stu-id="b2454-106">[in] Request type to be sent.</span></span>

`inBufferSize`\
<span data-ttu-id="b2454-107">[in] velikost vstupní vyrovnávací paměti, která má být předána.</span><span class="sxs-lookup"><span data-stu-id="b2454-107">[in] size of the input buffer to be passed in.</span></span>

`inBuffer`\
<span data-ttu-id="b2454-108">[in, size_is (inBufferSize)] Ukazatel vyrovnávací paměti pro nezpracovaná data, která se mají v žádosti odeslat.</span><span class="sxs-lookup"><span data-stu-id="b2454-108">[in, size_is(inBufferSize)] Buffer pointer for the raw data to be sent in the request.</span></span>

`outBufferSize`\
<span data-ttu-id="b2454-109">pro Velikost výstupní vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="b2454-109">[in] Size of the output buffer.</span></span>

`outBuffer`\
<span data-ttu-id="b2454-110">[out, size_is (outBufferSize)] Ukazatel vyrovnávací paměti, který se použije k uložení odpovědi na žádost</span><span class="sxs-lookup"><span data-stu-id="b2454-110">[out, size_is(outBufferSize)] Buffer pointer to used to store the request response.</span></span>

## <a name="remarks"></a><span data-ttu-id="b2454-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b2454-111">Remarks</span></span>

<span data-ttu-id="b2454-112">Poskytnutá metoda je součástí `IXCLRDataModule` rozhraní a odpovídá slotu 37th tabulky virtuálních metod.</span><span class="sxs-lookup"><span data-stu-id="b2454-112">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 37th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="b2454-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b2454-113">Requirements</span></span>

<span data-ttu-id="b2454-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2454-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>
<span data-ttu-id="b2454-115">**Hlavička:** Žádná **Knihovna:** žádné **.NET Framework verze:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b2454-115">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="b2454-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="b2454-116">See also</span></span>

- [<span data-ttu-id="b2454-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="b2454-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="b2454-118">IXCLRDataModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b2454-118">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
