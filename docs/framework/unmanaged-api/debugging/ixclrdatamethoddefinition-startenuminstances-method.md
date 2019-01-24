---
title: IXCLRDataMethodDefinition::StartEnumInstances – metoda
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::StartEnumInstances Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::StartEnumInstances Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::StartEnumInstances Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: c78af112e9239143c4854e34e9b6aa8e99344ec3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54623648"
---
# <a name="ixclrdatamethoddefinitionstartenuminstances-method"></a><span data-ttu-id="450e7-102">IXCLRDataMethodDefinition::StartEnumInstances – metoda</span><span class="sxs-lookup"><span data-stu-id="450e7-102">IXCLRDataMethodDefinition::StartEnumInstances Method</span></span>

<span data-ttu-id="450e7-103">Poskytuje popisovač pro výčet metodu instance danou `IXCLRDataAppDomain`.</span><span class="sxs-lookup"><span data-stu-id="450e7-103">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="450e7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="450e7-104">Syntax</span></span>

```
HRESULT StartEnumInstances(
    [in] IXCLRDataAppDomain* appDomain,
    [out] CLRDATA_ENUM *handle
);
```

### <a name="parameters"></a><span data-ttu-id="450e7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="450e7-105">Parameters</span></span>

<span data-ttu-id="450e7-106">`appDomain` [in] Doména AppDomain pro výčet.</span><span class="sxs-lookup"><span data-stu-id="450e7-106">`appDomain` [in] An AppDomain for the enumeration.</span></span>

<span data-ttu-id="450e7-107">`handle` [out] Popisovač pro vytváření výčtu instancí.</span><span class="sxs-lookup"><span data-stu-id="450e7-107">`handle` [out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="450e7-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="450e7-108">Remarks</span></span>

<span data-ttu-id="450e7-109">Zadaná metoda je součástí `IXCLRDataMethodDefinition` rozhraní a odpovídá třetí slot v tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="450e7-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the third slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="450e7-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="450e7-110">Requirements</span></span>

<span data-ttu-id="450e7-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="450e7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="450e7-112">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="450e7-112">**Header:** None</span></span>  
<span data-ttu-id="450e7-113">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="450e7-113">**Library:** None</span></span>  
<span data-ttu-id="450e7-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="450e7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="450e7-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="450e7-115">See also</span></span>

- [<span data-ttu-id="450e7-116">CLRDataSourceType Enumeration</span><span class="sxs-lookup"><span data-stu-id="450e7-116">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="450e7-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="450e7-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="450e7-118">IXCLRDataMethodDefinition rozhraní</span><span class="sxs-lookup"><span data-stu-id="450e7-118">IXCLRDataMethodDefinition Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md)
