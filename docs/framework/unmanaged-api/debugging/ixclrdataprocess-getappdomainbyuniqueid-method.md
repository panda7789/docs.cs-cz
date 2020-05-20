---
title: 'IXCLRDataProcess:: GetAppDomainByUniqueId – metoda'
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
ms.openlocfilehash: bb02ffed09cbcc31e653bfd3165050c247908c5d
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420778"
---
# <a name="ixclrdataprocessgetappdomainbyuniqueid-method"></a><span data-ttu-id="6931d-102">IXCLRDataProcess:: GetAppDomainByUniqueId – metoda</span><span class="sxs-lookup"><span data-stu-id="6931d-102">IXCLRDataProcess::GetAppDomainByUniqueId Method</span></span>

<span data-ttu-id="6931d-103">Načte `AppDomain` v procesu na základě jeho jedinečného identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="6931d-103">Gets an `AppDomain` in a process based on its unique identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="6931d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6931d-104">Syntax</span></span>

```cpp
HRESULT GetAppDomainByUniqueID(
    [in] ULONG64               id,
    [out] IXCLRDataAppDomain **appDomain
);
```

## <a name="parameters"></a><span data-ttu-id="6931d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6931d-105">Parameters</span></span>

`id`\
<span data-ttu-id="6931d-106">pro Jedinečný identifikátor domény aplikace</span><span class="sxs-lookup"><span data-stu-id="6931d-106">[in] The unique identifier of the AppDomain</span></span>

`appDomain`\
<span data-ttu-id="6931d-107">mimo Doména AppDomain</span><span class="sxs-lookup"><span data-stu-id="6931d-107">[out] The AppDomain</span></span>

## <a name="remarks"></a><span data-ttu-id="6931d-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6931d-108">Remarks</span></span>

<span data-ttu-id="6931d-109">Poskytnutá metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá dvacátému slotu tabulky virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="6931d-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 20th slot of the virtual method table.</span></span> <span data-ttu-id="6931d-110">`IXCLRDataAppDomain*`Vráceno se používá pro interakci s jinými rozhraními API.</span><span class="sxs-lookup"><span data-stu-id="6931d-110">The `IXCLRDataAppDomain*` returned is used for interaction with other APIs.</span></span>

## <a name="requirements"></a><span data-ttu-id="6931d-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6931d-111">Requirements</span></span>

<span data-ttu-id="6931d-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6931d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="6931d-113">**Hlavička:** Žádná **Knihovna:** žádné **.NET Framework verze:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6931d-113">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="6931d-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="6931d-114">See also</span></span>

- [<span data-ttu-id="6931d-115">Ladění</span><span class="sxs-lookup"><span data-stu-id="6931d-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="6931d-116">IXCLRDataProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6931d-116">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
