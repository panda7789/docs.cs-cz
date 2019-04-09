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
ms.openlocfilehash: 257fa2cf03a62ea888b76519aa5c9f9e84038045
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59126500"
---
# <a name="ixclrdataprocessgetappdomainbyuniqueid-method"></a><span data-ttu-id="0fd22-102">IXCLRDataProcess::GetAppDomainByUniqueId Method</span><span class="sxs-lookup"><span data-stu-id="0fd22-102">IXCLRDataProcess::GetAppDomainByUniqueId Method</span></span>

<span data-ttu-id="0fd22-103">Získá `AppDomain` v procesu podle jejího jedinečného identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="0fd22-103">Gets an `AppDomain` in a process based on its unique identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="0fd22-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0fd22-104">Syntax</span></span>
```
HRESULT GetAppDomainByUniqueID(
    [in] ULONG64               id,
    [out] IXCLRDataAppDomain **appDomain
);
```

## <a name="parameters"></a><span data-ttu-id="0fd22-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0fd22-105">Parameters</span></span>

`id`\
<span data-ttu-id="0fd22-106">[in] Jedinečný identifikátor třídy AppDomain</span><span class="sxs-lookup"><span data-stu-id="0fd22-106">[in] The unique identifier of the AppDomain</span></span>

`appDomain`\
<span data-ttu-id="0fd22-107">[out] Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="0fd22-107">[out] The AppDomain</span></span>

## <a name="remarks"></a><span data-ttu-id="0fd22-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0fd22-108">Remarks</span></span>

<span data-ttu-id="0fd22-109">Zadaná metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá 20. prosincem pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="0fd22-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 20th slot of the virtual method table.</span></span> <span data-ttu-id="0fd22-110">`IXCLRDataAppDomain*` Vrátila se používá k interakci s ostatními rozhraními API.</span><span class="sxs-lookup"><span data-stu-id="0fd22-110">The `IXCLRDataAppDomain*` returned is used for interaction with other APIs.</span></span>

## <a name="requirements"></a><span data-ttu-id="0fd22-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0fd22-111">Requirements</span></span>
<span data-ttu-id="0fd22-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0fd22-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="0fd22-113">**Záhlaví:** Žádný</span><span class="sxs-lookup"><span data-stu-id="0fd22-113">**Header:** None</span></span>  
<span data-ttu-id="0fd22-114">**Knihovna:** Žádné</span><span class="sxs-lookup"><span data-stu-id="0fd22-114">**Library:** None</span></span>  
**<span data-ttu-id="0fd22-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="0fd22-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a><span data-ttu-id="0fd22-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0fd22-116">See also</span></span>

- [<span data-ttu-id="0fd22-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="0fd22-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="0fd22-118">IXCLRDataProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0fd22-118">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
