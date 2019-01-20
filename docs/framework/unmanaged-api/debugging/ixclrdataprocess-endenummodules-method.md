---
title: IXCLRDataProcess::EndEnumModules – metoda
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EndEnumModules Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EndEnumModules Method
helpviewer.keywords:
- IXCLRDataProcess::EndEnumModules Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: cd49ae5fa274c577cfa3c04ec599e488384dfc64
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416097"
---
# <a name="ixclrdataprocessendenummodules-method"></a><span data-ttu-id="83864-102">IXCLRDataProcess::EndEnumModules – metoda</span><span class="sxs-lookup"><span data-stu-id="83864-102">IXCLRDataProcess::EndEnumModules Method</span></span>

<span data-ttu-id="83864-103">Uvolní prostředky využívané třídou interní iterátory využitých modulu výčtu.</span><span class="sxs-lookup"><span data-stu-id="83864-103">Releases the resources used by internal iterators used during module enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="83864-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83864-104">Syntax</span></span>
```
HRESULT EndEnumModules(
    [in] CLRDATA_ENUM handle
);
```

### <a name="parameters"></a><span data-ttu-id="83864-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="83864-105">Parameters</span></span>
<span data-ttu-id="83864-106">`handle` [out] Popisovač pro vytvoření výčtu moduly.</span><span class="sxs-lookup"><span data-stu-id="83864-106">`handle` [out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="83864-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="83864-107">Remarks</span></span>

<span data-ttu-id="83864-108">Zadaná metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá 26. pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="83864-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 26th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="83864-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="83864-109">Requirements</span></span>

<span data-ttu-id="83864-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83864-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>   
<span data-ttu-id="83864-111">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="83864-111">**Header:** None</span></span>   
<span data-ttu-id="83864-112">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="83864-112">**Library:** None</span></span>   
<span data-ttu-id="83864-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="83864-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>   

## <a name="see-also"></a><span data-ttu-id="83864-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="83864-114">See Also</span></span>

- [<span data-ttu-id="83864-115">Ladění</span><span class="sxs-lookup"><span data-stu-id="83864-115">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="83864-116">IXCLRDataProcess Interface</span><span class="sxs-lookup"><span data-stu-id="83864-116">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
