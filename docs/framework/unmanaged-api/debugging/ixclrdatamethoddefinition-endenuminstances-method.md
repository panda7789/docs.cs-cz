---
title: IXCLRDataMethodDefinition::EndEnumInstances Method
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::EndEnumInstances Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::EndEnumInstances Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::EndEnumInstances Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 4a7cd8850778e9bbbc7d8d67f464c7787e40bc13
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566092"
---
# <a name="ixclrdatamethoddefinitionendenuminstances-method"></a><span data-ttu-id="96c93-102">IXCLRDataMethodDefinition::EndEnumInstances Method</span><span class="sxs-lookup"><span data-stu-id="96c93-102">IXCLRDataMethodDefinition::EndEnumInstances Method</span></span>

<span data-ttu-id="96c93-103">Uvolní prostředky využívané třídou interní iterátory využitých instance výčtu.</span><span class="sxs-lookup"><span data-stu-id="96c93-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="96c93-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96c93-104">Syntax</span></span>

```
HRESULT EndEnumInstances(
    [in] CLRDATA_ENUM handle
);
```

### <a name="parameters"></a><span data-ttu-id="96c93-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="96c93-105">Parameters</span></span>

<span data-ttu-id="96c93-106">`handle` [out] Popisovač pro vytváření výčtu instancí.</span><span class="sxs-lookup"><span data-stu-id="96c93-106">`handle` [out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="96c93-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="96c93-107">Remarks</span></span>

<span data-ttu-id="96c93-108">Zadaná metoda je součástí `IXCLRDataMethodDefinition` rozhraní a odpovídá na páté slot v tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="96c93-108">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the fifth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="96c93-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="96c93-109">Requirements</span></span>

<span data-ttu-id="96c93-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96c93-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="96c93-111">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="96c93-111">**Header:** None</span></span>  
<span data-ttu-id="96c93-112">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="96c93-112">**Library:** None</span></span>  
<span data-ttu-id="96c93-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="96c93-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="96c93-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="96c93-114">See also</span></span>

- [<span data-ttu-id="96c93-115">Ladění</span><span class="sxs-lookup"><span data-stu-id="96c93-115">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="96c93-116">IXCLRDataMethodDefinition rozhraní</span><span class="sxs-lookup"><span data-stu-id="96c93-116">IXCLRDataMethodDefinition Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md)
