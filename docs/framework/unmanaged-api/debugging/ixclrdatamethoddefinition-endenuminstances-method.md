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
ms.openlocfilehash: 7901ba3ac95052e265df619d06996b4c9ce8baa6
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416076"
---
# <a name="ixclrdatamethoddefinitionendenuminstances-method"></a><span data-ttu-id="4e3ce-102">IXCLRDataMethodDefinition::EndEnumInstances Method</span><span class="sxs-lookup"><span data-stu-id="4e3ce-102">IXCLRDataMethodDefinition::EndEnumInstances Method</span></span>

<span data-ttu-id="4e3ce-103">Uvolní prostředky využívané třídou interní iterátory využitých instance výčtu.</span><span class="sxs-lookup"><span data-stu-id="4e3ce-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="4e3ce-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e3ce-104">Syntax</span></span>

```
HRESULT EndEnumInstances(
    [in] CLRDATA_ENUM handle
);
```

### <a name="parameters"></a><span data-ttu-id="4e3ce-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4e3ce-105">Parameters</span></span>

<span data-ttu-id="4e3ce-106">`handle` [out] Popisovač pro vytváření výčtu instancí.</span><span class="sxs-lookup"><span data-stu-id="4e3ce-106">`handle` [out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="4e3ce-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4e3ce-107">Remarks</span></span>

<span data-ttu-id="4e3ce-108">Zadaná metoda je součástí `IXCLRDataMethodDefinition` rozhraní a odpovídá na páté slot v tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="4e3ce-108">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the fifth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="4e3ce-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4e3ce-109">Requirements</span></span>

<span data-ttu-id="4e3ce-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e3ce-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="4e3ce-111">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="4e3ce-111">**Header:** None</span></span>  
<span data-ttu-id="4e3ce-112">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="4e3ce-112">**Library:** None</span></span>  
<span data-ttu-id="4e3ce-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4e3ce-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="4e3ce-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="4e3ce-114">See Also</span></span>

- [<span data-ttu-id="4e3ce-115">Ladění</span><span class="sxs-lookup"><span data-stu-id="4e3ce-115">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="4e3ce-116">IXCLRDataMethodDefinition rozhraní</span><span class="sxs-lookup"><span data-stu-id="4e3ce-116">IXCLRDataMethodDefinition Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md)
