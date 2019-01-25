---
title: IXCLRDataMethodDefinition::EnumInstance – metoda
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::EnumInstance Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::EnumInstance Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::EnumInstance Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 0fbb246f8c4bf791dd705aedf8eab6ef8bfeae56
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680259"
---
# <a name="ixclrdatamethoddefinitionenuminstance-method"></a><span data-ttu-id="4caef-102">IXCLRDataMethodDefinition::EnumInstance – metoda</span><span class="sxs-lookup"><span data-stu-id="4caef-102">IXCLRDataMethodDefinition::EnumInstance Method</span></span>

<span data-ttu-id="4caef-103">Vytvoří výčet instancí definici této metody.</span><span class="sxs-lookup"><span data-stu-id="4caef-103">Enumerates the instances of this method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="4caef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4caef-104">Syntax</span></span>

```
HRESULT EnumInstance(
    [in, out] CLRDATA_ENUM         *handle,
    [out] IXCLRDataMethodInstance **instance
);
```

### <a name="parameters"></a><span data-ttu-id="4caef-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4caef-105">Parameters</span></span>

<span data-ttu-id="4caef-106">`handle` [out v] Popisovač pro vytváření výčtu instancí.</span><span class="sxs-lookup"><span data-stu-id="4caef-106">`handle` [in, out] A handle for enumerating the instances.</span></span>

<span data-ttu-id="4caef-107">`instance` [out] Instance výčtu.</span><span class="sxs-lookup"><span data-stu-id="4caef-107">`instance` [out] The enumerated instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="4caef-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4caef-108">Remarks</span></span>

<span data-ttu-id="4caef-109">Zadaná metoda je součástí `IXCLRDataMethodDefinition` rozhraní a odpovídá čtvrtý pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="4caef-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="4caef-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4caef-110">Requirements</span></span>

<span data-ttu-id="4caef-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4caef-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="4caef-112">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="4caef-112">**Header:** None</span></span>  
<span data-ttu-id="4caef-113">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="4caef-113">**Library:** None</span></span>  
<span data-ttu-id="4caef-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4caef-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="4caef-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4caef-115">See also</span></span>

- [<span data-ttu-id="4caef-116">CLRDataSourceType Enumeration</span><span class="sxs-lookup"><span data-stu-id="4caef-116">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="4caef-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="4caef-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="4caef-118">IXCLRDataMethodDefinition rozhraní</span><span class="sxs-lookup"><span data-stu-id="4caef-118">IXCLRDataMethodDefinition Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md)
- [<span data-ttu-id="4caef-119">IXCLRDataMethodInstance Interface</span><span class="sxs-lookup"><span data-stu-id="4caef-119">IXCLRDataMethodInstance Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-interface.md)
