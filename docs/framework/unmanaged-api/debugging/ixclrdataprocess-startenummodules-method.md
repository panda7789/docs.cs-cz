---
title: 'IXCLRDataProcess:: StartEnumModules – metoda'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::StartEnumModules Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::StartEnumModules Method
helpviewer.keywords:
- IXCLRDataProcess::StartEnumModules Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: d55b07ea3fada73237919bf677163a9096d5ad04
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420718"
---
# <a name="ixclrdataprocessstartenummodules-method"></a><span data-ttu-id="b87c2-102">IXCLRDataProcess:: StartEnumModules – metoda</span><span class="sxs-lookup"><span data-stu-id="b87c2-102">IXCLRDataProcess::StartEnumModules Method</span></span>

<span data-ttu-id="b87c2-103">Poskytuje popisovač pro zobrazení výčtu modulů procesu.</span><span class="sxs-lookup"><span data-stu-id="b87c2-103">Provides a handle to enumerate the modules of a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="b87c2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b87c2-104">Syntax</span></span>

```cpp
HRESULT StartEnumModules(
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a><span data-ttu-id="b87c2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b87c2-105">Parameters</span></span>

`handle`\
<span data-ttu-id="b87c2-106">mimo Popisovač pro vytváření výčtu modulů.</span><span class="sxs-lookup"><span data-stu-id="b87c2-106">[out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="b87c2-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b87c2-107">Remarks</span></span>

<span data-ttu-id="b87c2-108">Poskytnutá metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá slotu 24 července tabulky virtuálních metod.</span><span class="sxs-lookup"><span data-stu-id="b87c2-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 24th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="b87c2-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b87c2-109">Requirements</span></span>

<span data-ttu-id="b87c2-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b87c2-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="b87c2-111">**Hlavička:** NTato</span><span class="sxs-lookup"><span data-stu-id="b87c2-111">**Header:** None</span></span>  
<span data-ttu-id="b87c2-112">**Knihovna:** NTato</span><span class="sxs-lookup"><span data-stu-id="b87c2-112">**Library:** None</span></span>  
<span data-ttu-id="b87c2-113">**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b87c2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="b87c2-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="b87c2-114">See also</span></span>

- [<span data-ttu-id="b87c2-115">Výčet CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="b87c2-115">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="b87c2-116">Ladění</span><span class="sxs-lookup"><span data-stu-id="b87c2-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="b87c2-117">IXCLRDataProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b87c2-117">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
