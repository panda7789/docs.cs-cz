---
title: IXCLRDataProcess::EnumMethodInstanceByAddress Method
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
ms.openlocfilehash: b42939e8e64e75337478ace67a9a91c6a03a94e3
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416113"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a><span data-ttu-id="efa32-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span><span class="sxs-lookup"><span data-stu-id="efa32-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span></span>

<span data-ttu-id="efa32-103">Vytvoří výčet metodu instance tohoto procesu začínající na posun adresy.</span><span class="sxs-lookup"><span data-stu-id="efa32-103">Enumerates the method instances of this process starting at an address offset.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="efa32-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="efa32-104">Syntax</span></span>

```
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

### <a name="parameters"></a><span data-ttu-id="efa32-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="efa32-105">Parameters</span></span>

<span data-ttu-id="efa32-106">`handle` [in] Popisovač pro vytváření výčtu instancí metody.</span><span class="sxs-lookup"><span data-stu-id="efa32-106">`handle` [in] A handle for enumerating the method instances.</span></span>

<span data-ttu-id="efa32-107">`mod` [out] Instance výčtu metody.</span><span class="sxs-lookup"><span data-stu-id="efa32-107">`mod` [out] The enumerated method instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="efa32-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="efa32-108">Remarks</span></span>

<span data-ttu-id="efa32-109">Zadaná metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá 28 pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="efa32-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 28th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="efa32-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="efa32-110">Requirements</span></span>

<span data-ttu-id="efa32-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efa32-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>   
<span data-ttu-id="efa32-112">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="efa32-112">**Header:** None</span></span>   
<span data-ttu-id="efa32-113">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="efa32-113">**Library:** None</span></span>   
<span data-ttu-id="efa32-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="efa32-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>   
 
## <a name="see-also"></a><span data-ttu-id="efa32-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="efa32-115">See Also</span></span>
- [<span data-ttu-id="efa32-116">CLRDataSourceType Enumeration</span><span class="sxs-lookup"><span data-stu-id="efa32-116">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="efa32-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="efa32-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="efa32-118">IXCLRDataProcess Interface</span><span class="sxs-lookup"><span data-stu-id="efa32-118">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
