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
ms.openlocfilehash: 7ad1a9957e9bffd7b28aa241723dedba1d11f4cd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775878"
---
# <a name="ixclrdatamethoddefinitionenuminstance-method"></a><span data-ttu-id="7fb2a-102">IXCLRDataMethodDefinition::EnumInstance – metoda</span><span class="sxs-lookup"><span data-stu-id="7fb2a-102">IXCLRDataMethodDefinition::EnumInstance Method</span></span>

<span data-ttu-id="7fb2a-103">Vytvoří výčet instancí definici této metody.</span><span class="sxs-lookup"><span data-stu-id="7fb2a-103">Enumerates the instances of this method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="7fb2a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7fb2a-104">Syntax</span></span>

```cpp
HRESULT EnumInstance(
    [in, out] CLRDATA_ENUM         *handle,
    [out] IXCLRDataMethodInstance **instance
);
```

## <a name="parameters"></a><span data-ttu-id="7fb2a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7fb2a-105">Parameters</span></span>

`handle`\
<span data-ttu-id="7fb2a-106">[out v] Popisovač pro vytváření výčtu instancí.</span><span class="sxs-lookup"><span data-stu-id="7fb2a-106">[in, out] A handle for enumerating the instances.</span></span>

`instance`\
<span data-ttu-id="7fb2a-107">[out] Instance výčtu.</span><span class="sxs-lookup"><span data-stu-id="7fb2a-107">[out] The enumerated instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="7fb2a-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7fb2a-108">Remarks</span></span>

<span data-ttu-id="7fb2a-109">Zadaná metoda je součástí `IXCLRDataMethodDefinition` rozhraní a odpovídá čtvrtý pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="7fb2a-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="7fb2a-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7fb2a-110">Requirements</span></span>

<span data-ttu-id="7fb2a-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fb2a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="7fb2a-112">**Záhlaví:** Žádný</span><span class="sxs-lookup"><span data-stu-id="7fb2a-112">**Header:** None</span></span>  
<span data-ttu-id="7fb2a-113">**Knihovna:** Žádné</span><span class="sxs-lookup"><span data-stu-id="7fb2a-113">**Library:** None</span></span>  
<span data-ttu-id="7fb2a-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7fb2a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="7fb2a-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7fb2a-115">See also</span></span>

- [<span data-ttu-id="7fb2a-116">CLRDataSourceType Enumeration</span><span class="sxs-lookup"><span data-stu-id="7fb2a-116">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="7fb2a-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="7fb2a-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="7fb2a-118">IXCLRDataMethodDefinition rozhraní</span><span class="sxs-lookup"><span data-stu-id="7fb2a-118">IXCLRDataMethodDefinition Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md)
- [<span data-ttu-id="7fb2a-119">IXCLRDataMethodInstance Interface</span><span class="sxs-lookup"><span data-stu-id="7fb2a-119">IXCLRDataMethodInstance Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-interface.md)
