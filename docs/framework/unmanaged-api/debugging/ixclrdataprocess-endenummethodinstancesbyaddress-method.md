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
ms.openlocfilehash: a48a7fc9a141354666c50b1f6da8f1aaa180ff6c
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416090"
---
# <a name="ixclrdataprocessendenummethodinstancesbyaddress-method"></a><span data-ttu-id="b2c20-102">IXCLRDataProcess::EndEnumMethodInstancesByAddress Method</span><span class="sxs-lookup"><span data-stu-id="b2c20-102">IXCLRDataProcess::EndEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="b2c20-103">Uvolní prostředky využívané třídou interní iterátory využitých instance výčtu.</span><span class="sxs-lookup"><span data-stu-id="b2c20-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="b2c20-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2c20-104">Syntax</span></span>

```
HRESULT EndEnumMethodInstancesByAddress(
    [in] CLRDATA_ENUM handle
);
```

### <a name="parameters"></a><span data-ttu-id="b2c20-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b2c20-105">Parameters</span></span>

<span data-ttu-id="b2c20-106">`handle` [out] Popisovač pro vytváření výčtu instancí metody.</span><span class="sxs-lookup"><span data-stu-id="b2c20-106">`handle` [out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="b2c20-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b2c20-107">Remarks</span></span>

<span data-ttu-id="b2c20-108">Zadaná metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá 29. pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="b2c20-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 29th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="b2c20-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b2c20-109">Requirements</span></span>

<span data-ttu-id="b2c20-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2c20-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="b2c20-111">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="b2c20-111">**Header:** None</span></span>  
<span data-ttu-id="b2c20-112">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="b2c20-112">**Library:** None</span></span>  
<span data-ttu-id="b2c20-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b2c20-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="b2c20-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="b2c20-114">See Also</span></span>

- [<span data-ttu-id="b2c20-115">CLRDataSourceType Enumeration</span><span class="sxs-lookup"><span data-stu-id="b2c20-115">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="b2c20-116">Ladění</span><span class="sxs-lookup"><span data-stu-id="b2c20-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="b2c20-117">IXCLRDataProcess Interface</span><span class="sxs-lookup"><span data-stu-id="b2c20-117">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
