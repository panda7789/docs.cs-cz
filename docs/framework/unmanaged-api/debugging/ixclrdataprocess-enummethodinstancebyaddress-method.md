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
ms.openlocfilehash: 825cb8ea94bee980f9e10b90cddf04db32c1a33f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491906"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a><span data-ttu-id="3e124-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span><span class="sxs-lookup"><span data-stu-id="3e124-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span></span>

<span data-ttu-id="3e124-103">Vytvoří výčet metodu instance tohoto procesu začínající na posun adresy.</span><span class="sxs-lookup"><span data-stu-id="3e124-103">Enumerates the method instances of this process starting at an address offset.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="3e124-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e124-104">Syntax</span></span>

```
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

### <a name="parameters"></a><span data-ttu-id="3e124-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3e124-105">Parameters</span></span>

<span data-ttu-id="3e124-106">`handle` [in] Popisovač pro vytváření výčtu instancí metody.</span><span class="sxs-lookup"><span data-stu-id="3e124-106">`handle` [in] A handle for enumerating the method instances.</span></span>

<span data-ttu-id="3e124-107">`mod` [out] Instance výčtu metody.</span><span class="sxs-lookup"><span data-stu-id="3e124-107">`mod` [out] The enumerated method instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="3e124-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3e124-108">Remarks</span></span>

<span data-ttu-id="3e124-109">Zadaná metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá 28 pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="3e124-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 28th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="3e124-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3e124-110">Requirements</span></span>

<span data-ttu-id="3e124-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e124-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>   
<span data-ttu-id="3e124-112">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="3e124-112">**Header:** None</span></span>   
<span data-ttu-id="3e124-113">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="3e124-113">**Library:** None</span></span>   
<span data-ttu-id="3e124-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3e124-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>   
 
## <a name="see-also"></a><span data-ttu-id="3e124-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3e124-115">See also</span></span>
- [<span data-ttu-id="3e124-116">CLRDataSourceType Enumeration</span><span class="sxs-lookup"><span data-stu-id="3e124-116">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="3e124-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="3e124-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="3e124-118">IXCLRDataProcess Interface</span><span class="sxs-lookup"><span data-stu-id="3e124-118">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
