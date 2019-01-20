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
ms.openlocfilehash: 420acda89858713f12ea87a8c8d3909682a3f5e3
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416122"
---
# <a name="ixclrdatamethoddefinitionenuminstance-method"></a><span data-ttu-id="4e242-102">IXCLRDataMethodDefinition::EnumInstance – metoda</span><span class="sxs-lookup"><span data-stu-id="4e242-102">IXCLRDataMethodDefinition::EnumInstance Method</span></span>

<span data-ttu-id="4e242-103">Vytvoří výčet instancí definici této metody.</span><span class="sxs-lookup"><span data-stu-id="4e242-103">Enumerates the instances of this method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="4e242-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e242-104">Syntax</span></span>

```
HRESULT EnumInstance(
    [in, out] CLRDATA_ENUM         *handle,
    [out] IXCLRDataMethodInstance **instance
);
```

### <a name="parameters"></a><span data-ttu-id="4e242-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4e242-105">Parameters</span></span>

<span data-ttu-id="4e242-106">`handle` [out v] Popisovač pro vytváření výčtu instancí.</span><span class="sxs-lookup"><span data-stu-id="4e242-106">`handle` [in, out] A handle for enumerating the instances.</span></span>

<span data-ttu-id="4e242-107">`instance` [out] Instance výčtu.</span><span class="sxs-lookup"><span data-stu-id="4e242-107">`instance` [out] The enumerated instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="4e242-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4e242-108">Remarks</span></span>

<span data-ttu-id="4e242-109">Zadaná metoda je součástí `IXCLRDataMethodDefinition` rozhraní a odpovídá čtvrtý pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="4e242-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="4e242-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4e242-110">Requirements</span></span>

<span data-ttu-id="4e242-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e242-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="4e242-112">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="4e242-112">**Header:** None</span></span>  
<span data-ttu-id="4e242-113">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="4e242-113">**Library:** None</span></span>  
<span data-ttu-id="4e242-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4e242-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="4e242-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="4e242-115">See Also</span></span>

- [<span data-ttu-id="4e242-116">CLRDataSourceType Enumeration</span><span class="sxs-lookup"><span data-stu-id="4e242-116">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="4e242-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="4e242-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="4e242-118">IXCLRDataMethodDefinition rozhraní</span><span class="sxs-lookup"><span data-stu-id="4e242-118">IXCLRDataMethodDefinition Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md)
- [<span data-ttu-id="4e242-119">IXCLRDataMethodInstance Interface</span><span class="sxs-lookup"><span data-stu-id="4e242-119">IXCLRDataMethodInstance Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-interface.md)
