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
ms.openlocfilehash: dacf76582916ad50f51ae7c8818b496f31f9553e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57353111"
---
# <a name="ixclrdatamethoddefinitionenuminstance-method"></a><span data-ttu-id="a4485-102">IXCLRDataMethodDefinition::EnumInstance – metoda</span><span class="sxs-lookup"><span data-stu-id="a4485-102">IXCLRDataMethodDefinition::EnumInstance Method</span></span>

<span data-ttu-id="a4485-103">Vytvoří výčet instancí definici této metody.</span><span class="sxs-lookup"><span data-stu-id="a4485-103">Enumerates the instances of this method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="a4485-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4485-104">Syntax</span></span>

```
HRESULT EnumInstance(
    [in, out] CLRDATA_ENUM         *handle,
    [out] IXCLRDataMethodInstance **instance
);
```

## <a name="parameters"></a><span data-ttu-id="a4485-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a4485-105">Parameters</span></span>

`handle`\
<span data-ttu-id="a4485-106">[out v] Popisovač pro vytváření výčtu instancí.</span><span class="sxs-lookup"><span data-stu-id="a4485-106">[in, out] A handle for enumerating the instances.</span></span>

`instance`\
<span data-ttu-id="a4485-107">[out] Instance výčtu.</span><span class="sxs-lookup"><span data-stu-id="a4485-107">[out] The enumerated instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="a4485-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a4485-108">Remarks</span></span>

<span data-ttu-id="a4485-109">Zadaná metoda je součástí `IXCLRDataMethodDefinition` rozhraní a odpovídá čtvrtý pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="a4485-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="a4485-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a4485-110">Requirements</span></span>

<span data-ttu-id="a4485-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4485-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="a4485-112">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="a4485-112">**Header:** None</span></span>  
<span data-ttu-id="a4485-113">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="a4485-113">**Library:** None</span></span>  
<span data-ttu-id="a4485-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a4485-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="a4485-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a4485-115">See also</span></span>

- [<span data-ttu-id="a4485-116">CLRDataSourceType Enumeration</span><span class="sxs-lookup"><span data-stu-id="a4485-116">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="a4485-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="a4485-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="a4485-118">IXCLRDataMethodDefinition rozhraní</span><span class="sxs-lookup"><span data-stu-id="a4485-118">IXCLRDataMethodDefinition Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md)
- [<span data-ttu-id="a4485-119">IXCLRDataMethodInstance Interface</span><span class="sxs-lookup"><span data-stu-id="a4485-119">IXCLRDataMethodInstance Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-interface.md)
