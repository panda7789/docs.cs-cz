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
ms.openlocfilehash: 28cd15a793d303e1d6e64c52c1d0095e8d619c7b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378929"
---
# <a name="ixclrdatamethoddefinitionendenuminstances-method"></a><span data-ttu-id="72188-102">IXCLRDataMethodDefinition::EndEnumInstances Method</span><span class="sxs-lookup"><span data-stu-id="72188-102">IXCLRDataMethodDefinition::EndEnumInstances Method</span></span>

<span data-ttu-id="72188-103">Uvolní prostředky využívané třídou interní iterátory využitých instance výčtu.</span><span class="sxs-lookup"><span data-stu-id="72188-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="72188-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72188-104">Syntax</span></span>

```
HRESULT EndEnumInstances(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="72188-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="72188-105">Parameters</span></span>

`handle`\
<span data-ttu-id="72188-106">[out] Popisovač pro vytváření výčtu instancí.</span><span class="sxs-lookup"><span data-stu-id="72188-106">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="72188-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="72188-107">Remarks</span></span>

<span data-ttu-id="72188-108">Zadaná metoda je součástí `IXCLRDataMethodDefinition` rozhraní a odpovídá na páté slot v tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="72188-108">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the fifth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="72188-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="72188-109">Requirements</span></span>

<span data-ttu-id="72188-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72188-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="72188-111">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="72188-111">**Header:** None</span></span>  
<span data-ttu-id="72188-112">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="72188-112">**Library:** None</span></span>  
<span data-ttu-id="72188-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="72188-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="72188-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="72188-114">See also</span></span>

- [<span data-ttu-id="72188-115">Ladění</span><span class="sxs-lookup"><span data-stu-id="72188-115">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="72188-116">IXCLRDataMethodDefinition rozhraní</span><span class="sxs-lookup"><span data-stu-id="72188-116">IXCLRDataMethodDefinition Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md)
