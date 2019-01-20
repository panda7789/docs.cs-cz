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
ms.openlocfilehash: a81da147c1483e7649612050f4aba29a2cc63b49
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416119"
---
# <a name="ixclrdataprocessstartenummodules-method"></a><span data-ttu-id="d6291-102">IXCLRDataProcess::StartEnumModules – metoda</span><span class="sxs-lookup"><span data-stu-id="d6291-102">IXCLRDataProcess::StartEnumModules Method</span></span>

<span data-ttu-id="d6291-103">Poskytuje popisovač na výčet modulů procesů.</span><span class="sxs-lookup"><span data-stu-id="d6291-103">Provides a handle to enumerate the modules of a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="d6291-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6291-104">Syntax</span></span>

```
HRESULT StartEnumModules(
    [out] CLRDATA_ENUM *handle
);
```

### <a name="parameters"></a><span data-ttu-id="d6291-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d6291-105">Parameters</span></span>

<span data-ttu-id="d6291-106">`handle` [out] Popisovač pro vytvoření výčtu moduly.</span><span class="sxs-lookup"><span data-stu-id="d6291-106">`handle` [out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="d6291-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d6291-107">Remarks</span></span>

<span data-ttu-id="d6291-108">Zadaná metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá 24. pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="d6291-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 24th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="d6291-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d6291-109">Requirements</span></span>

<span data-ttu-id="d6291-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6291-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="d6291-111">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="d6291-111">**Header:** None</span></span>  
<span data-ttu-id="d6291-112">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="d6291-112">**Library:** None</span></span>  
<span data-ttu-id="d6291-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d6291-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="d6291-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="d6291-114">See Also</span></span>

- [<span data-ttu-id="d6291-115">CLRDataSourceType Enumeration</span><span class="sxs-lookup"><span data-stu-id="d6291-115">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="d6291-116">Ladění</span><span class="sxs-lookup"><span data-stu-id="d6291-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="d6291-117">IXCLRDataProcess Interface</span><span class="sxs-lookup"><span data-stu-id="d6291-117">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
