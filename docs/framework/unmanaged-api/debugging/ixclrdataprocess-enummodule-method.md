---
title: IXCLRDataProcess::EnumModule – metoda
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EnumModule Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EnumModule Method
helpviewer.keywords:
- IXCLRDataProcess::EnumModule Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: a0398d18f9568754231082d63b4c6a2c865d8c6f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775262"
---
# <a name="ixclrdataprocessenummodule-method"></a><span data-ttu-id="45df8-102">IXCLRDataProcess::EnumModule – metoda</span><span class="sxs-lookup"><span data-stu-id="45df8-102">IXCLRDataProcess::EnumModule Method</span></span>

<span data-ttu-id="45df8-103">Vytvoří výčet modulů tohoto procesu.</span><span class="sxs-lookup"><span data-stu-id="45df8-103">Enumerates the modules of this process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="45df8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45df8-104">Syntax</span></span>

```
HRESULT EnumModule(
    [in, out] CLRDATA_ENUM  *handle,
    [out] IXCLRDataModule  **mod
);
```

## <a name="parameters"></a><span data-ttu-id="45df8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="45df8-105">Parameters</span></span>

`handle`\
<span data-ttu-id="45df8-106">[out v] Popisovač pro vytvoření výčtu moduly.</span><span class="sxs-lookup"><span data-stu-id="45df8-106">[in, out] A handle for enumerating the modules.</span></span>

`mod`\
<span data-ttu-id="45df8-107">[out] Výčtový modul.</span><span class="sxs-lookup"><span data-stu-id="45df8-107">[out] The enumerated module.</span></span>

## <a name="remarks"></a><span data-ttu-id="45df8-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="45df8-108">Remarks</span></span>

<span data-ttu-id="45df8-109">Zadaná metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá 25 pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="45df8-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="45df8-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="45df8-110">Requirements</span></span>

<span data-ttu-id="45df8-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45df8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="45df8-112">**Záhlaví:** Žádný</span><span class="sxs-lookup"><span data-stu-id="45df8-112">**Header:** None</span></span>  
<span data-ttu-id="45df8-113">**Knihovna:** Žádné</span><span class="sxs-lookup"><span data-stu-id="45df8-113">**Library:** None</span></span>  
<span data-ttu-id="45df8-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="45df8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="45df8-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="45df8-115">See also</span></span>

- [<span data-ttu-id="45df8-116">CLRDataSourceType Enumeration</span><span class="sxs-lookup"><span data-stu-id="45df8-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="45df8-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="45df8-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="45df8-118">IXCLRDataModule Interface</span><span class="sxs-lookup"><span data-stu-id="45df8-118">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
- [<span data-ttu-id="45df8-119">IXCLRDataProcess Interface</span><span class="sxs-lookup"><span data-stu-id="45df8-119">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
