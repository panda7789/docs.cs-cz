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
ms.openlocfilehash: 79c4e0ed99a068d7d806d5c25580dc477aac6475
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752626"
---
# <a name="ixclrdataprocessstartenummodules-method"></a><span data-ttu-id="c8643-102">IXCLRDataProcess::StartEnumModules – metoda</span><span class="sxs-lookup"><span data-stu-id="c8643-102">IXCLRDataProcess::StartEnumModules Method</span></span>

<span data-ttu-id="c8643-103">Poskytuje popisovač na výčet modulů procesů.</span><span class="sxs-lookup"><span data-stu-id="c8643-103">Provides a handle to enumerate the modules of a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="c8643-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8643-104">Syntax</span></span>

```cpp
HRESULT StartEnumModules(
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a><span data-ttu-id="c8643-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c8643-105">Parameters</span></span>

`handle`\
<span data-ttu-id="c8643-106">[out] Popisovač pro vytvoření výčtu moduly.</span><span class="sxs-lookup"><span data-stu-id="c8643-106">[out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="c8643-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c8643-107">Remarks</span></span>

<span data-ttu-id="c8643-108">Zadaná metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá 24. pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="c8643-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 24th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="c8643-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c8643-109">Requirements</span></span>

<span data-ttu-id="c8643-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8643-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="c8643-111">**Záhlaví:** Žádné</span><span class="sxs-lookup"><span data-stu-id="c8643-111">**Header:** None</span></span>  
<span data-ttu-id="c8643-112">**Knihovna:** Žádné</span><span class="sxs-lookup"><span data-stu-id="c8643-112">**Library:** None</span></span>  
<span data-ttu-id="c8643-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c8643-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="c8643-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c8643-114">See also</span></span>

- [<span data-ttu-id="c8643-115">CLRDataSourceType Enumeration</span><span class="sxs-lookup"><span data-stu-id="c8643-115">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="c8643-116">Ladění</span><span class="sxs-lookup"><span data-stu-id="c8643-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="c8643-117">IXCLRDataProcess Interface</span><span class="sxs-lookup"><span data-stu-id="c8643-117">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
