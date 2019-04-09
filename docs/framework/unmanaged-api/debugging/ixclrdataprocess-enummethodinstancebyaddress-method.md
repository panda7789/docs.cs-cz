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
ms.openlocfilehash: a51c709b0b331127b74d98c4dc42e2772fd7f2db
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166436"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a><span data-ttu-id="9b88e-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span><span class="sxs-lookup"><span data-stu-id="9b88e-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span></span>

<span data-ttu-id="9b88e-103">Vytvoří výčet metodu instance tohoto procesu začínající na posun adresy.</span><span class="sxs-lookup"><span data-stu-id="9b88e-103">Enumerates the method instances of this process starting at an address offset.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="9b88e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b88e-104">Syntax</span></span>

```
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

## <a name="parameters"></a><span data-ttu-id="9b88e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9b88e-105">Parameters</span></span>

`handle`\
<span data-ttu-id="9b88e-106">[in] Popisovač pro vytváření výčtu instancí metody.</span><span class="sxs-lookup"><span data-stu-id="9b88e-106">[in] A handle for enumerating the method instances.</span></span>

`mod`\
<span data-ttu-id="9b88e-107">[out] Instance výčtu metody.</span><span class="sxs-lookup"><span data-stu-id="9b88e-107">[out] The enumerated method instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="9b88e-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9b88e-108">Remarks</span></span>

<span data-ttu-id="9b88e-109">Zadaná metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá 28 pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="9b88e-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 28th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="9b88e-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9b88e-110">Requirements</span></span>

<span data-ttu-id="9b88e-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b88e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>   
<span data-ttu-id="9b88e-112">**Záhlaví:** Žádné</span><span class="sxs-lookup"><span data-stu-id="9b88e-112">**Header:** None</span></span>   
<span data-ttu-id="9b88e-113">**Knihovna:** Žádné</span><span class="sxs-lookup"><span data-stu-id="9b88e-113">**Library:** None</span></span>   
**<span data-ttu-id="9b88e-114">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="9b88e-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]   
 
## <a name="see-also"></a><span data-ttu-id="9b88e-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9b88e-115">See also</span></span>

- [<span data-ttu-id="9b88e-116">CLRDataSourceType Enumeration</span><span class="sxs-lookup"><span data-stu-id="9b88e-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="9b88e-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="9b88e-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="9b88e-118">IXCLRDataProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9b88e-118">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
