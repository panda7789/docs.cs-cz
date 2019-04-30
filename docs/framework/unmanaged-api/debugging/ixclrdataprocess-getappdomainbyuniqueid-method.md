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
ms.openlocfilehash: 8b468d40ef8eb523ba8881627fae15cf9b7c7b80
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775255"
---
# <a name="ixclrdataprocessgetappdomainbyuniqueid-method"></a><span data-ttu-id="89c34-102">IXCLRDataProcess::GetAppDomainByUniqueId Method</span><span class="sxs-lookup"><span data-stu-id="89c34-102">IXCLRDataProcess::GetAppDomainByUniqueId Method</span></span>

<span data-ttu-id="89c34-103">Získá `AppDomain` v procesu podle jejího jedinečného identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="89c34-103">Gets an `AppDomain` in a process based on its unique identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="89c34-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89c34-104">Syntax</span></span>

```cpp
HRESULT GetAppDomainByUniqueID(
    [in] ULONG64               id,
    [out] IXCLRDataAppDomain **appDomain
);
```

## <a name="parameters"></a><span data-ttu-id="89c34-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="89c34-105">Parameters</span></span>

`id`\
<span data-ttu-id="89c34-106">[in] Jedinečný identifikátor třídy AppDomain</span><span class="sxs-lookup"><span data-stu-id="89c34-106">[in] The unique identifier of the AppDomain</span></span>

`appDomain`\
<span data-ttu-id="89c34-107">[out] Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="89c34-107">[out] The AppDomain</span></span>

## <a name="remarks"></a><span data-ttu-id="89c34-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="89c34-108">Remarks</span></span>

<span data-ttu-id="89c34-109">Zadaná metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá 20. prosincem pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="89c34-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 20th slot of the virtual method table.</span></span> <span data-ttu-id="89c34-110">`IXCLRDataAppDomain*` Vrátila se používá k interakci s ostatními rozhraními API.</span><span class="sxs-lookup"><span data-stu-id="89c34-110">The `IXCLRDataAppDomain*` returned is used for interaction with other APIs.</span></span>

## <a name="requirements"></a><span data-ttu-id="89c34-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="89c34-111">Requirements</span></span>

<span data-ttu-id="89c34-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89c34-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>
<span data-ttu-id="89c34-113">**Záhlaví:** Žádný **knihovny:** Žádný **verze rozhraní .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="89c34-113">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="89c34-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="89c34-114">See also</span></span>

- [<span data-ttu-id="89c34-115">Ladění</span><span class="sxs-lookup"><span data-stu-id="89c34-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="89c34-116">IXCLRDataProcess Interface</span><span class="sxs-lookup"><span data-stu-id="89c34-116">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
