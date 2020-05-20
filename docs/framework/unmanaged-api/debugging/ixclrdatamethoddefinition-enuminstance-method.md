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
ms.openlocfilehash: ae1ef2a3c8cf9e042ab9ab233ed993f8e36b2fce
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420939"
---
# <a name="ixclrdatamethoddefinitionenuminstance-method"></a><span data-ttu-id="0f8c7-102">IXCLRDataMethodDefinition:: EnumInstance – metoda</span><span class="sxs-lookup"><span data-stu-id="0f8c7-102">IXCLRDataMethodDefinition::EnumInstance Method</span></span>

<span data-ttu-id="0f8c7-103">Vytvoří výčet instancí této definice metody.</span><span class="sxs-lookup"><span data-stu-id="0f8c7-103">Enumerates the instances of this method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="0f8c7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f8c7-104">Syntax</span></span>

```cpp
HRESULT EnumInstance(
    [in, out] CLRDATA_ENUM         *handle,
    [out] IXCLRDataMethodInstance **instance
);
```

## <a name="parameters"></a><span data-ttu-id="0f8c7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0f8c7-105">Parameters</span></span>

`handle`\
<span data-ttu-id="0f8c7-106">[in, out] Popisovač pro vytváření výčtu instancí.</span><span class="sxs-lookup"><span data-stu-id="0f8c7-106">[in, out] A handle for enumerating the instances.</span></span>

`instance`\
<span data-ttu-id="0f8c7-107">mimo Výčtová instance.</span><span class="sxs-lookup"><span data-stu-id="0f8c7-107">[out] The enumerated instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="0f8c7-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0f8c7-108">Remarks</span></span>

<span data-ttu-id="0f8c7-109">Poskytnutá metoda je součástí `IXCLRDataMethodDefinition` rozhraní a odpovídá šesté pozici tabulky virtuálních metod.</span><span class="sxs-lookup"><span data-stu-id="0f8c7-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the 6th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="0f8c7-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0f8c7-110">Requirements</span></span>

<span data-ttu-id="0f8c7-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f8c7-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="0f8c7-112">**Hlavička:** NTato</span><span class="sxs-lookup"><span data-stu-id="0f8c7-112">**Header:** None</span></span>  
<span data-ttu-id="0f8c7-113">**Knihovna:** NTato</span><span class="sxs-lookup"><span data-stu-id="0f8c7-113">**Library:** None</span></span>  
<span data-ttu-id="0f8c7-114">**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0f8c7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="0f8c7-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="0f8c7-115">See also</span></span>

- [<span data-ttu-id="0f8c7-116">Výčet CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="0f8c7-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="0f8c7-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="0f8c7-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="0f8c7-118">IXCLRDataMethodDefinition – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0f8c7-118">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
- [<span data-ttu-id="0f8c7-119">IXCLRDataMethodInstance – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0f8c7-119">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
