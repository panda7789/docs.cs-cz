---
title: 'IXCLRDataMethodInstance:: GetILAddressMap – metoda'
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodInstance::GetILAddressMap Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance::GetILAddressMap Method
helpviewer.keywords:
- IXCLRDataMethodInstance::GetILAddressMap Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 7c4dcf59ce159434d5012120043f5bb548d49731
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396817"
---
# <a name="ixclrdatamethodinstancegetiladdressmap-method"></a><span data-ttu-id="176d2-102">IXCLRDataMethodInstance:: GetILAddressMap – metoda</span><span class="sxs-lookup"><span data-stu-id="176d2-102">IXCLRDataMethodInstance::GetILAddressMap Method</span></span>

<span data-ttu-id="176d2-103">Získá informace o mapování IL na adresu.</span><span class="sxs-lookup"><span data-stu-id="176d2-103">Gets the IL to address mapping information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="176d2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="176d2-104">Syntax</span></span>

```cpp
HRESULT GetILAddressMap(
    [in] ULONG32                                   mapLen,
    [out] ULONG32                                 *mapNeeded,
    [out, size_is(mapLen)] CLRDATA_IL_ADDRESS_MAP  maps[]
);
```

## <a name="parameters"></a><span data-ttu-id="176d2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="176d2-105">Parameters</span></span>

`mapLen`\
<span data-ttu-id="176d2-106">pro Délka zadaného pole Maps</span><span class="sxs-lookup"><span data-stu-id="176d2-106">[in] The length of the provided maps array.</span></span>

`mapNeeded`\
<span data-ttu-id="176d2-107">mimo Počet položek mapování, které metoda potřebuje.</span><span class="sxs-lookup"><span data-stu-id="176d2-107">[out] The number of map entries that the method needs.</span></span>

`maps`\
<span data-ttu-id="176d2-108">[out, size_is (mapLen)] Pole pro ukládání položek mapy</span><span class="sxs-lookup"><span data-stu-id="176d2-108">[out, size_is(mapLen)] The array for storing the map entries.</span></span>

## <a name="remarks"></a><span data-ttu-id="176d2-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="176d2-109">Remarks</span></span>

<span data-ttu-id="176d2-110">Poskytnutá metoda je součástí `IXCLRDataMethodInstance` rozhraní a odpovídá 15. pozici tabulky virtuálních metod.</span><span class="sxs-lookup"><span data-stu-id="176d2-110">The provided method is part of the `IXCLRDataMethodInstance` interface and corresponds to the 15th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="176d2-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="176d2-111">Requirements</span></span>

<span data-ttu-id="176d2-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="176d2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="176d2-113">**Hlavička:** NTato</span><span class="sxs-lookup"><span data-stu-id="176d2-113">**Header:** None</span></span>  
<span data-ttu-id="176d2-114">**Knihovna:** NTato</span><span class="sxs-lookup"><span data-stu-id="176d2-114">**Library:** None</span></span>  
<span data-ttu-id="176d2-115">**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="176d2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="176d2-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="176d2-116">See also</span></span>

- [<span data-ttu-id="176d2-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="176d2-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="176d2-118">IXCLRDataMethodInstance – rozhraní</span><span class="sxs-lookup"><span data-stu-id="176d2-118">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
