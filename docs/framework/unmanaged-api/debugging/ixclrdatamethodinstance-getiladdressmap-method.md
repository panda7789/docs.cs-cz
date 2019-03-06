---
title: IXCLRDataMethodInstance::GetILAddressMap – metoda
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
ms.openlocfilehash: 5e6fde6e4e5bf006da00b62b035cee112efae1d7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373488"
---
# <a name="ixclrdatamethodinstancegetiladdressmap-method"></a><span data-ttu-id="9d417-102">IXCLRDataMethodInstance::GetILAddressMap – metoda</span><span class="sxs-lookup"><span data-stu-id="9d417-102">IXCLRDataMethodInstance::GetILAddressMap Method</span></span>

<span data-ttu-id="9d417-103">Získá IL na informace o mapování adres.</span><span class="sxs-lookup"><span data-stu-id="9d417-103">Gets the IL to address mapping information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="9d417-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d417-104">Syntax</span></span>

```
HRESULT GetILAddressMap(
    [in] ULONG32                                   mapLen,
    [out] ULONG32                                 *mapNeeded,
    [out, size_is(mapLen)] CLRDATA_IL_ADDRESS_MAP  maps[]
);
```

### <a name="parameters"></a><span data-ttu-id="9d417-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d417-105">Parameters</span></span>

`mapLen`\
<span data-ttu-id="9d417-106">[in] Délka zadaného mapování pole.</span><span class="sxs-lookup"><span data-stu-id="9d417-106">[in] The length of the provided maps array.</span></span>

`mapNeeded`\
<span data-ttu-id="9d417-107">[out] Počet položek mapování, které potřebuje metodě.</span><span class="sxs-lookup"><span data-stu-id="9d417-107">[out] The number of map entries that the method needs.</span></span>

`maps`\
<span data-ttu-id="9d417-108">[out, size_is(mapLen)] Pole pro ukládání položek mapování.</span><span class="sxs-lookup"><span data-stu-id="9d417-108">[out, size_is(mapLen)] The array for storing the map entries.</span></span>

## <a name="remarks"></a><span data-ttu-id="9d417-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9d417-109">Remarks</span></span>

<span data-ttu-id="9d417-110">Zadaná metoda je součástí `IXCLRDataMethodInstance` rozhraní a odpovídá 14. pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="9d417-110">The provided method is part of the `IXCLRDataMethodInstance` interface and corresponds to the 14th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="9d417-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9d417-111">Requirements</span></span>

<span data-ttu-id="9d417-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d417-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="9d417-113">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="9d417-113">**Header:** None</span></span>  
<span data-ttu-id="9d417-114">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="9d417-114">**Library:** None</span></span>  
<span data-ttu-id="9d417-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9d417-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="9d417-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9d417-116">See also</span></span>

- [<span data-ttu-id="9d417-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="9d417-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="9d417-118">IXCLRDataMethodInstance Interface</span><span class="sxs-lookup"><span data-stu-id="9d417-118">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
