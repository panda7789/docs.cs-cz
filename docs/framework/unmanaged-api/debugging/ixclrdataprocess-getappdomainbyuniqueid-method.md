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
ms.openlocfilehash: d4226bd73c7ae0c1faf510ed63b644116b064fb2
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375074"
---
# <a name="ixclrdataprocessgetappdomainbyuniqueid-method"></a><span data-ttu-id="bcff4-102">IXCLRDataProcess::GetAppDomainByUniqueId Method</span><span class="sxs-lookup"><span data-stu-id="bcff4-102">IXCLRDataProcess::GetAppDomainByUniqueId Method</span></span>

<span data-ttu-id="bcff4-103">Získá `AppDomain` v procesu podle jejího jedinečného identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="bcff4-103">Gets an `AppDomain` in a process based on its unique identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="bcff4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bcff4-104">Syntax</span></span>
```
HRESULT GetAppDomainByUniqueID(
    [in] ULONG64               id,
    [out] IXCLRDataAppDomain **appDomain
);
```

## <a name="parameters"></a><span data-ttu-id="bcff4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bcff4-105">Parameters</span></span>

`id`\
<span data-ttu-id="bcff4-106">[in] Jedinečný identifikátor třídy AppDomain</span><span class="sxs-lookup"><span data-stu-id="bcff4-106">[in] The unique identifier of the AppDomain</span></span>

`appDomain`\
<span data-ttu-id="bcff4-107">[out] Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="bcff4-107">[out] The AppDomain</span></span>

## <a name="remarks"></a><span data-ttu-id="bcff4-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bcff4-108">Remarks</span></span>

<span data-ttu-id="bcff4-109">Zadaná metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá 20. prosincem pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="bcff4-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 20th slot of the virtual method table.</span></span> <span data-ttu-id="bcff4-110">`IXCLRDataAppDomain*` Vrátila se používá k interakci s ostatními rozhraními API.</span><span class="sxs-lookup"><span data-stu-id="bcff4-110">The `IXCLRDataAppDomain*` returned is used for interaction with other APIs.</span></span>

## <a name="requirements"></a><span data-ttu-id="bcff4-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bcff4-111">Requirements</span></span>
<span data-ttu-id="bcff4-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bcff4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="bcff4-113">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="bcff4-113">**Header:** None</span></span>  
<span data-ttu-id="bcff4-114">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="bcff4-114">**Library:** None</span></span>  
<span data-ttu-id="bcff4-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bcff4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="bcff4-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bcff4-116">See also</span></span>
- [<span data-ttu-id="bcff4-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="bcff4-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="bcff4-118">IXCLRDataProcess Interface</span><span class="sxs-lookup"><span data-stu-id="bcff4-118">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
