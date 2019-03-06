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
ms.openlocfilehash: d19a4b8116573f2ff6469fe612e7b7736651ff03
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354528"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a><span data-ttu-id="a5810-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span><span class="sxs-lookup"><span data-stu-id="a5810-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span></span>

<span data-ttu-id="a5810-103">Vytvoří výčet metodu instance tohoto procesu začínající na posun adresy.</span><span class="sxs-lookup"><span data-stu-id="a5810-103">Enumerates the method instances of this process starting at an address offset.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="a5810-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5810-104">Syntax</span></span>

```
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

### <a name="parameters"></a><span data-ttu-id="a5810-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a5810-105">Parameters</span></span>

`handle`\
<span data-ttu-id="a5810-106">[in] Popisovač pro vytváření výčtu instancí metody.</span><span class="sxs-lookup"><span data-stu-id="a5810-106">[in] A handle for enumerating the method instances.</span></span>

`mod`\
<span data-ttu-id="a5810-107">[out] Instance výčtu metody.</span><span class="sxs-lookup"><span data-stu-id="a5810-107">[out] The enumerated method instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="a5810-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a5810-108">Remarks</span></span>

<span data-ttu-id="a5810-109">Zadaná metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá 28 pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="a5810-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 28th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="a5810-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a5810-110">Requirements</span></span>

<span data-ttu-id="a5810-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5810-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>   
<span data-ttu-id="a5810-112">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="a5810-112">**Header:** None</span></span>   
<span data-ttu-id="a5810-113">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="a5810-113">**Library:** None</span></span>   
<span data-ttu-id="a5810-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a5810-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>   
 
## <a name="see-also"></a><span data-ttu-id="a5810-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a5810-115">See also</span></span>
- [<span data-ttu-id="a5810-116">CLRDataSourceType Enumeration</span><span class="sxs-lookup"><span data-stu-id="a5810-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="a5810-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="a5810-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="a5810-118">IXCLRDataProcess Interface</span><span class="sxs-lookup"><span data-stu-id="a5810-118">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
