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
ms.openlocfilehash: febe6766c7a35228820421eee975c777988efd1f
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396494"
---
# <a name="ixclrdatamethoddefinitionendenuminstances-method"></a><span data-ttu-id="9af47-102">IXCLRDataMethodDefinition:: EndEnumInstances – metoda</span><span class="sxs-lookup"><span data-stu-id="9af47-102">IXCLRDataMethodDefinition::EndEnumInstances Method</span></span>

<span data-ttu-id="9af47-103">Uvolní prostředky používané interními iterátory použitými během výčtu instance.</span><span class="sxs-lookup"><span data-stu-id="9af47-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="9af47-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9af47-104">Syntax</span></span>

```cpp
HRESULT EndEnumInstances(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="9af47-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9af47-105">Parameters</span></span>

`handle`\
<span data-ttu-id="9af47-106">mimo Popisovač pro vytváření výčtu instancí.</span><span class="sxs-lookup"><span data-stu-id="9af47-106">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="9af47-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9af47-107">Remarks</span></span>

<span data-ttu-id="9af47-108">Poskytnutá metoda je součástí `IXCLRDataMethodDefinition` rozhraní a odpovídá 7. pozici tabulky virtuálních metod.</span><span class="sxs-lookup"><span data-stu-id="9af47-108">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the 7th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="9af47-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9af47-109">Requirements</span></span>

<span data-ttu-id="9af47-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9af47-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="9af47-111">**Hlavička:** NTato</span><span class="sxs-lookup"><span data-stu-id="9af47-111">**Header:** None</span></span>  
<span data-ttu-id="9af47-112">**Knihovna:** NTato</span><span class="sxs-lookup"><span data-stu-id="9af47-112">**Library:** None</span></span>  
<span data-ttu-id="9af47-113">**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9af47-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="9af47-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="9af47-114">See also</span></span>

- [<span data-ttu-id="9af47-115">Ladění</span><span class="sxs-lookup"><span data-stu-id="9af47-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="9af47-116">IXCLRDataMethodDefinition – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9af47-116">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
