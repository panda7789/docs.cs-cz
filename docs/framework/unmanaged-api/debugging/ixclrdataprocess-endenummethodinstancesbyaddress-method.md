---
title: IXCLRDataProcess::EndEnumMethodInstancesByAddress Method
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 67978e49a8c23c4b25234ecbb3639c696c7232f4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655644"
---
# <a name="ixclrdataprocessendenummethodinstancesbyaddress-method"></a><span data-ttu-id="b97be-102">IXCLRDataProcess::EndEnumMethodInstancesByAddress Method</span><span class="sxs-lookup"><span data-stu-id="b97be-102">IXCLRDataProcess::EndEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="b97be-103">Uvolní prostředky využívané třídou interní iterátory využitých instance výčtu.</span><span class="sxs-lookup"><span data-stu-id="b97be-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="b97be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b97be-104">Syntax</span></span>

```
HRESULT EndEnumMethodInstancesByAddress(
    [in] CLRDATA_ENUM handle
);
```

### <a name="parameters"></a><span data-ttu-id="b97be-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b97be-105">Parameters</span></span>

<span data-ttu-id="b97be-106">`handle` [out] Popisovač pro vytváření výčtu instancí metody.</span><span class="sxs-lookup"><span data-stu-id="b97be-106">`handle` [out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="b97be-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b97be-107">Remarks</span></span>

<span data-ttu-id="b97be-108">Zadaná metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá 29. pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="b97be-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 29th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="b97be-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b97be-109">Requirements</span></span>

<span data-ttu-id="b97be-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b97be-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="b97be-111">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="b97be-111">**Header:** None</span></span>  
<span data-ttu-id="b97be-112">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="b97be-112">**Library:** None</span></span>  
<span data-ttu-id="b97be-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b97be-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="b97be-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b97be-114">See also</span></span>

- [<span data-ttu-id="b97be-115">CLRDataSourceType Enumeration</span><span class="sxs-lookup"><span data-stu-id="b97be-115">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="b97be-116">Ladění</span><span class="sxs-lookup"><span data-stu-id="b97be-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="b97be-117">IXCLRDataProcess Interface</span><span class="sxs-lookup"><span data-stu-id="b97be-117">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
