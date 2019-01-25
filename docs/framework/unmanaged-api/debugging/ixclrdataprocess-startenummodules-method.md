---
title: IXCLRDataProcess::StartEnumModules – metoda
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
ms.openlocfilehash: 4a086157b27b7426cb6d5f17f13426c0f26d2b2d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658218"
---
# <a name="ixclrdataprocessstartenummodules-method"></a><span data-ttu-id="0b9fe-102">IXCLRDataProcess::StartEnumModules – metoda</span><span class="sxs-lookup"><span data-stu-id="0b9fe-102">IXCLRDataProcess::StartEnumModules Method</span></span>

<span data-ttu-id="0b9fe-103">Poskytuje popisovač na výčet modulů procesů.</span><span class="sxs-lookup"><span data-stu-id="0b9fe-103">Provides a handle to enumerate the modules of a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="0b9fe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b9fe-104">Syntax</span></span>

```
HRESULT StartEnumModules(
    [out] CLRDATA_ENUM *handle
);
```

### <a name="parameters"></a><span data-ttu-id="0b9fe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0b9fe-105">Parameters</span></span>

<span data-ttu-id="0b9fe-106">`handle` [out] Popisovač pro vytvoření výčtu moduly.</span><span class="sxs-lookup"><span data-stu-id="0b9fe-106">`handle` [out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="0b9fe-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0b9fe-107">Remarks</span></span>

<span data-ttu-id="0b9fe-108">Zadaná metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá 24. pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="0b9fe-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 24th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="0b9fe-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0b9fe-109">Requirements</span></span>

<span data-ttu-id="0b9fe-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b9fe-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="0b9fe-111">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="0b9fe-111">**Header:** None</span></span>  
<span data-ttu-id="0b9fe-112">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="0b9fe-112">**Library:** None</span></span>  
<span data-ttu-id="0b9fe-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0b9fe-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="0b9fe-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0b9fe-114">See also</span></span>

- [<span data-ttu-id="0b9fe-115">CLRDataSourceType Enumeration</span><span class="sxs-lookup"><span data-stu-id="0b9fe-115">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="0b9fe-116">Ladění</span><span class="sxs-lookup"><span data-stu-id="0b9fe-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="0b9fe-117">IXCLRDataProcess Interface</span><span class="sxs-lookup"><span data-stu-id="0b9fe-117">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
