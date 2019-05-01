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
ms.openlocfilehash: d871ca5dfd62dbca309f4ccc3dcedf959033a41e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986554"
---
# <a name="ixclrdataprocessstartenummodules-method"></a><span data-ttu-id="b0e21-102">IXCLRDataProcess::StartEnumModules – metoda</span><span class="sxs-lookup"><span data-stu-id="b0e21-102">IXCLRDataProcess::StartEnumModules Method</span></span>

<span data-ttu-id="b0e21-103">Poskytuje popisovač na výčet modulů procesů.</span><span class="sxs-lookup"><span data-stu-id="b0e21-103">Provides a handle to enumerate the modules of a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="b0e21-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0e21-104">Syntax</span></span>

```
HRESULT StartEnumModules(
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a><span data-ttu-id="b0e21-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b0e21-105">Parameters</span></span>

`handle`\
<span data-ttu-id="b0e21-106">[out] Popisovač pro vytvoření výčtu moduly.</span><span class="sxs-lookup"><span data-stu-id="b0e21-106">[out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="b0e21-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b0e21-107">Remarks</span></span>

<span data-ttu-id="b0e21-108">Zadaná metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá 24. pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="b0e21-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 24th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="b0e21-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b0e21-109">Requirements</span></span>

<span data-ttu-id="b0e21-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0e21-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="b0e21-111">**Záhlaví:** Žádný</span><span class="sxs-lookup"><span data-stu-id="b0e21-111">**Header:** None</span></span>  
<span data-ttu-id="b0e21-112">**Knihovna:** Žádné</span><span class="sxs-lookup"><span data-stu-id="b0e21-112">**Library:** None</span></span>  
<span data-ttu-id="b0e21-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b0e21-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="b0e21-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b0e21-114">See also</span></span>

- [<span data-ttu-id="b0e21-115">CLRDataSourceType Enumeration</span><span class="sxs-lookup"><span data-stu-id="b0e21-115">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="b0e21-116">Ladění</span><span class="sxs-lookup"><span data-stu-id="b0e21-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="b0e21-117">IXCLRDataProcess Interface</span><span class="sxs-lookup"><span data-stu-id="b0e21-117">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
