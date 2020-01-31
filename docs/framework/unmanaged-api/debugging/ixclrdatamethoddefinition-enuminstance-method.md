---
title: 'IXCLRDataMethodDefinition:: EnumInstance – metoda'
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
ms.openlocfilehash: b6393d7fa4853c230203521e665bbe89d7b228e2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790433"
---
# <a name="ixclrdatamethoddefinitionenuminstance-method"></a><span data-ttu-id="a0529-102">IXCLRDataMethodDefinition:: EnumInstance – metoda</span><span class="sxs-lookup"><span data-stu-id="a0529-102">IXCLRDataMethodDefinition::EnumInstance Method</span></span>

<span data-ttu-id="a0529-103">Vytvoří výčet instancí této definice metody.</span><span class="sxs-lookup"><span data-stu-id="a0529-103">Enumerates the instances of this method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="a0529-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0529-104">Syntax</span></span>

```cpp
HRESULT EnumInstance(
    [in, out] CLRDATA_ENUM         *handle,
    [out] IXCLRDataMethodInstance **instance
);
```

## <a name="parameters"></a><span data-ttu-id="a0529-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a0529-105">Parameters</span></span>

`handle`\
<span data-ttu-id="a0529-106">[in, out] Popisovač pro vytváření výčtu instancí.</span><span class="sxs-lookup"><span data-stu-id="a0529-106">[in, out] A handle for enumerating the instances.</span></span>

`instance`\
<span data-ttu-id="a0529-107">mimo Výčtová instance.</span><span class="sxs-lookup"><span data-stu-id="a0529-107">[out] The enumerated instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="a0529-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a0529-108">Remarks</span></span>

<span data-ttu-id="a0529-109">Poskytnutá metoda je součástí rozhraní `IXCLRDataMethodDefinition` a odpovídá čtvrtému slotu tabulky virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="a0529-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="a0529-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a0529-110">Requirements</span></span>

<span data-ttu-id="a0529-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0529-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="a0529-112">**Hlavička:** NTato</span><span class="sxs-lookup"><span data-stu-id="a0529-112">**Header:** None</span></span>  
<span data-ttu-id="a0529-113">**Knihovna:** NTato</span><span class="sxs-lookup"><span data-stu-id="a0529-113">**Library:** None</span></span>  
<span data-ttu-id="a0529-114">**Verze .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a0529-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="a0529-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a0529-115">See also</span></span>

- [<span data-ttu-id="a0529-116">CLRDataSourceType Enumeration</span><span class="sxs-lookup"><span data-stu-id="a0529-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="a0529-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="a0529-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="a0529-118">Rozhraní IXCLRDataMethodDefinition</span><span class="sxs-lookup"><span data-stu-id="a0529-118">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
- [<span data-ttu-id="a0529-119">IXCLRDataMethodInstance Interface</span><span class="sxs-lookup"><span data-stu-id="a0529-119">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
