---
title: 'IXCLRDataMethodDefinition:: StartEnumInstances – metoda'
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
ms.openlocfilehash: b0c37c666f23f04239ed827246b87c43ee8d5ad9
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420926"
---
# <a name="ixclrdatamethoddefinitionstartenuminstances-method"></a><span data-ttu-id="8cea7-102">IXCLRDataMethodDefinition:: StartEnumInstances – metoda</span><span class="sxs-lookup"><span data-stu-id="8cea7-102">IXCLRDataMethodDefinition::StartEnumInstances Method</span></span>

<span data-ttu-id="8cea7-103">Poskytuje popisovač pro výčet instancí metody pro daný objekt `IXCLRDataAppDomain` .</span><span class="sxs-lookup"><span data-stu-id="8cea7-103">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="8cea7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8cea7-104">Syntax</span></span>

```cpp
HRESULT StartEnumInstances(
    [in] IXCLRDataAppDomain* appDomain,
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a><span data-ttu-id="8cea7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8cea7-105">Parameters</span></span>

`appDomain`\
<span data-ttu-id="8cea7-106">pro Doména AppDomain pro výčet.</span><span class="sxs-lookup"><span data-stu-id="8cea7-106">[in] An AppDomain for the enumeration.</span></span>

`handle`\
<span data-ttu-id="8cea7-107">mimo Popisovač pro vytváření výčtu instancí.</span><span class="sxs-lookup"><span data-stu-id="8cea7-107">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="8cea7-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8cea7-108">Remarks</span></span>

<span data-ttu-id="8cea7-109">Poskytnutá metoda je součástí `IXCLRDataMethodDefinition` rozhraní a odpovídá 5. pozici tabulky virtuálních metod.</span><span class="sxs-lookup"><span data-stu-id="8cea7-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the 5th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="8cea7-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8cea7-110">Requirements</span></span>

<span data-ttu-id="8cea7-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8cea7-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="8cea7-112">**Hlavička:** NTato</span><span class="sxs-lookup"><span data-stu-id="8cea7-112">**Header:** None</span></span>  
<span data-ttu-id="8cea7-113">**Knihovna:** NTato</span><span class="sxs-lookup"><span data-stu-id="8cea7-113">**Library:** None</span></span>  
<span data-ttu-id="8cea7-114">**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8cea7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="8cea7-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="8cea7-115">See also</span></span>

- [<span data-ttu-id="8cea7-116">Výčet CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="8cea7-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="8cea7-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="8cea7-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="8cea7-118">IXCLRDataMethodDefinition – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8cea7-118">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
