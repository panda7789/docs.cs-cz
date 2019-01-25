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
ms.openlocfilehash: 1648e53df5f36f7615831b425d2b5d764731c5c4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54738128"
---
# <a name="ixclrdataprocessenummodule-method"></a><span data-ttu-id="14a1d-102">IXCLRDataProcess::EnumModule – metoda</span><span class="sxs-lookup"><span data-stu-id="14a1d-102">IXCLRDataProcess::EnumModule Method</span></span>

<span data-ttu-id="14a1d-103">Vytvoří výčet modulů tohoto procesu.</span><span class="sxs-lookup"><span data-stu-id="14a1d-103">Enumerates the modules of this process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="14a1d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14a1d-104">Syntax</span></span>

```
HRESULT EnumModule(
    [in, out] CLRDATA_ENUM  *handle,
    [out] IXCLRDataModule  **mod
);
```

### <a name="parameters"></a><span data-ttu-id="14a1d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="14a1d-105">Parameters</span></span>

<span data-ttu-id="14a1d-106">`handle` [out v] Popisovač pro vytvoření výčtu moduly.</span><span class="sxs-lookup"><span data-stu-id="14a1d-106">`handle` [in, out] A handle for enumerating the modules.</span></span>

<span data-ttu-id="14a1d-107">`mod` [out] Výčtový modul.</span><span class="sxs-lookup"><span data-stu-id="14a1d-107">`mod` [out] The enumerated module.</span></span>

## <a name="remarks"></a><span data-ttu-id="14a1d-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="14a1d-108">Remarks</span></span>

<span data-ttu-id="14a1d-109">Zadaná metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá 25 pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="14a1d-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="14a1d-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="14a1d-110">Requirements</span></span>

<span data-ttu-id="14a1d-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14a1d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="14a1d-112">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="14a1d-112">**Header:** None</span></span>  
<span data-ttu-id="14a1d-113">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="14a1d-113">**Library:** None</span></span>  
<span data-ttu-id="14a1d-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="14a1d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="14a1d-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="14a1d-115">See also</span></span>

- [<span data-ttu-id="14a1d-116">CLRDataSourceType Enumeration</span><span class="sxs-lookup"><span data-stu-id="14a1d-116">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="14a1d-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="14a1d-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="14a1d-118">IXCLRDataModule Interface</span><span class="sxs-lookup"><span data-stu-id="14a1d-118">IXCLRDataModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-interface.md)
- [<span data-ttu-id="14a1d-119">IXCLRDataProcess Interface</span><span class="sxs-lookup"><span data-stu-id="14a1d-119">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
