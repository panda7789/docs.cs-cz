---
title: IXCLRDataProcess::Metoda EnumMethodInstanceByAddress
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: afc5fc377dd45d5e8d4d2d7b3385ca0524df69e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176653"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a><span data-ttu-id="141f5-102">IXCLRDataProcess::Metoda EnumMethodInstanceByAddress</span><span class="sxs-lookup"><span data-stu-id="141f5-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span></span>

<span data-ttu-id="141f5-103">Vyjmenovává instance metody tohoto procesu počínaje posunem adresy.</span><span class="sxs-lookup"><span data-stu-id="141f5-103">Enumerates the method instances of this process starting at an address offset.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="141f5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="141f5-104">Syntax</span></span>

```cpp
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

## <a name="parameters"></a><span data-ttu-id="141f5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="141f5-105">Parameters</span></span>

`handle`\
<span data-ttu-id="141f5-106">[v] Popisovač pro výčet instance metody.</span><span class="sxs-lookup"><span data-stu-id="141f5-106">[in] A handle for enumerating the method instances.</span></span>

`mod`\
<span data-ttu-id="141f5-107">[out] Instance výčtové metody.</span><span class="sxs-lookup"><span data-stu-id="141f5-107">[out] The enumerated method instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="141f5-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="141f5-108">Remarks</span></span>

<span data-ttu-id="141f5-109">Poskytnutá metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá 28.</span><span class="sxs-lookup"><span data-stu-id="141f5-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 28th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="141f5-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="141f5-110">Requirements</span></span>

<span data-ttu-id="141f5-111">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="141f5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>
<span data-ttu-id="141f5-112">**Záhlaví:** Žádná **knihovna:** Žádné **verze rozhraní .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="141f5-112">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="141f5-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="141f5-113">See also</span></span>

- [<span data-ttu-id="141f5-114">Výčet clrdatasourcetype</span><span class="sxs-lookup"><span data-stu-id="141f5-114">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="141f5-115">ladění</span><span class="sxs-lookup"><span data-stu-id="141f5-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="141f5-116">IXCLRDataProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="141f5-116">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
