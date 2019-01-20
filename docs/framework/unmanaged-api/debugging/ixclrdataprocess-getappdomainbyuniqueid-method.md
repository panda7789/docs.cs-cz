---
title: IXCLRDataProcess::GetAppDomainByUniqueId Method
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::GetAppDomainByUniqueId Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::GetAppDomainByUniqueId Method
helpviewer.keywords:
- IXCLRDataProcess::GetAppDomainByUniqueId Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 83e7d4e1a4ff3c2e6f573d6c097c7cdb9c5f3c54
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416116"
---
# <a name="ixclrdataprocessgetappdomainbyuniqueid-method"></a><span data-ttu-id="1c0c3-102">IXCLRDataProcess::GetAppDomainByUniqueId Method</span><span class="sxs-lookup"><span data-stu-id="1c0c3-102">IXCLRDataProcess::GetAppDomainByUniqueId Method</span></span>

<span data-ttu-id="1c0c3-103">Získá `AppDomain` v procesu podle jejího jedinečného identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="1c0c3-103">Gets an `AppDomain` in a process based on its unique identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="1c0c3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c0c3-104">Syntax</span></span>
```
HRESULT GetAppDomainByUniqueID(
    [in] ULONG64               id,
    [out] IXCLRDataAppDomain **appDomain
);
```

### <a name="parameters"></a><span data-ttu-id="1c0c3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1c0c3-105">Parameters</span></span>
<span data-ttu-id="1c0c3-106">`id` [in] Jedinečný identifikátor třídy AppDomain</span><span class="sxs-lookup"><span data-stu-id="1c0c3-106">`id` [in] The unique identifier of the AppDomain</span></span>

<span data-ttu-id="1c0c3-107">`appDomain` [out] Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="1c0c3-107">`appDomain` [out] The AppDomain</span></span>

## <a name="remarks"></a><span data-ttu-id="1c0c3-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1c0c3-108">Remarks</span></span>

<span data-ttu-id="1c0c3-109">Zadaná metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá 20. prosincem pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="1c0c3-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 20th slot of the virtual method table.</span></span> <span data-ttu-id="1c0c3-110">`IXCLRDataAppDomain*` Vrátila se používá k interakci s ostatními rozhraními API.</span><span class="sxs-lookup"><span data-stu-id="1c0c3-110">The `IXCLRDataAppDomain*` returned is used for interaction with other APIs.</span></span>

## <a name="requirements"></a><span data-ttu-id="1c0c3-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1c0c3-111">Requirements</span></span>
<span data-ttu-id="1c0c3-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c0c3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="1c0c3-113">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="1c0c3-113">**Header:** None</span></span>  
<span data-ttu-id="1c0c3-114">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="1c0c3-114">**Library:** None</span></span>  
<span data-ttu-id="1c0c3-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1c0c3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="1c0c3-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="1c0c3-116">See Also</span></span>
- [<span data-ttu-id="1c0c3-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="1c0c3-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="1c0c3-118">IXCLRDataProcess Interface</span><span class="sxs-lookup"><span data-stu-id="1c0c3-118">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
