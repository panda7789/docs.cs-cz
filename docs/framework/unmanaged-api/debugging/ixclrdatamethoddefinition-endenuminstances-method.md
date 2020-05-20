---
title: 'IXCLRDataMethodDefinition:: EndEnumInstances – metoda'
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
ms.openlocfilehash: 7271c9594a679af205c404f59ff6731821aa0acf
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420991"
---
# <a name="ixclrdatamethoddefinitionendenuminstances-method"></a><span data-ttu-id="81868-102">IXCLRDataMethodDefinition:: EndEnumInstances – metoda</span><span class="sxs-lookup"><span data-stu-id="81868-102">IXCLRDataMethodDefinition::EndEnumInstances Method</span></span>

<span data-ttu-id="81868-103">Uvolní prostředky používané interními iterátory použitými během výčtu instance.</span><span class="sxs-lookup"><span data-stu-id="81868-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="81868-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81868-104">Syntax</span></span>

```cpp
HRESULT EndEnumInstances(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="81868-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="81868-105">Parameters</span></span>

`handle`\
<span data-ttu-id="81868-106">mimo Popisovač pro vytváření výčtu instancí.</span><span class="sxs-lookup"><span data-stu-id="81868-106">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="81868-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="81868-107">Remarks</span></span>

<span data-ttu-id="81868-108">Poskytnutá metoda je součástí `IXCLRDataMethodDefinition` rozhraní a odpovídá 7. pozici tabulky virtuálních metod.</span><span class="sxs-lookup"><span data-stu-id="81868-108">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the 7th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="81868-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="81868-109">Requirements</span></span>

<span data-ttu-id="81868-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81868-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="81868-111">**Hlavička:** NTato</span><span class="sxs-lookup"><span data-stu-id="81868-111">**Header:** None</span></span>  
<span data-ttu-id="81868-112">**Knihovna:** NTato</span><span class="sxs-lookup"><span data-stu-id="81868-112">**Library:** None</span></span>  
<span data-ttu-id="81868-113">**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="81868-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="81868-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="81868-114">See also</span></span>

- [<span data-ttu-id="81868-115">Ladění</span><span class="sxs-lookup"><span data-stu-id="81868-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="81868-116">IXCLRDataMethodDefinition – rozhraní</span><span class="sxs-lookup"><span data-stu-id="81868-116">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
