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
ms.openlocfilehash: 7f45a5b13e767fa6849f307ee96fb822447f1263
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629948"
---
# <a name="ixclrdatamethoddefinitionstartenuminstances-method"></a><span data-ttu-id="585e5-102">IXCLRDataMethodDefinition::StartEnumInstances – metoda</span><span class="sxs-lookup"><span data-stu-id="585e5-102">IXCLRDataMethodDefinition::StartEnumInstances Method</span></span>

<span data-ttu-id="585e5-103">Poskytuje popisovač pro výčet metodu instance danou `IXCLRDataAppDomain`.</span><span class="sxs-lookup"><span data-stu-id="585e5-103">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="585e5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="585e5-104">Syntax</span></span>

```
HRESULT StartEnumInstances(
    [in] IXCLRDataAppDomain* appDomain,
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a><span data-ttu-id="585e5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="585e5-105">Parameters</span></span>

`appDomain`\
<span data-ttu-id="585e5-106">[in] Doména AppDomain pro výčet.</span><span class="sxs-lookup"><span data-stu-id="585e5-106">[in] An AppDomain for the enumeration.</span></span>

`handle`\
<span data-ttu-id="585e5-107">[out] Popisovač pro vytváření výčtu instancí.</span><span class="sxs-lookup"><span data-stu-id="585e5-107">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="585e5-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="585e5-108">Remarks</span></span>

<span data-ttu-id="585e5-109">Zadaná metoda je součástí `IXCLRDataMethodDefinition` rozhraní a odpovídá třetí slot v tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="585e5-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the third slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="585e5-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="585e5-110">Requirements</span></span>

<span data-ttu-id="585e5-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="585e5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="585e5-112">**Záhlaví:** Žádný</span><span class="sxs-lookup"><span data-stu-id="585e5-112">**Header:** None</span></span>  
<span data-ttu-id="585e5-113">**Knihovna:** Žádné</span><span class="sxs-lookup"><span data-stu-id="585e5-113">**Library:** None</span></span>  
<span data-ttu-id="585e5-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="585e5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="585e5-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="585e5-115">See also</span></span>

- [<span data-ttu-id="585e5-116">CLRDataSourceType Enumeration</span><span class="sxs-lookup"><span data-stu-id="585e5-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="585e5-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="585e5-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="585e5-118">IXCLRDataMethodDefinition rozhraní</span><span class="sxs-lookup"><span data-stu-id="585e5-118">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
