---
title: 'IXCLRDataProcess:: EnumMethodInstanceByAddress – metoda'
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
ms.openlocfilehash: 142099ae5cf9637cc28e8c82aabcd831cc8f0f52
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420796"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a><span data-ttu-id="7bdf3-102">IXCLRDataProcess:: EnumMethodInstanceByAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="7bdf3-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span></span>

<span data-ttu-id="7bdf3-103">Vytvoří výčet instancí metody tohoto procesu počínaje posunem adresy.</span><span class="sxs-lookup"><span data-stu-id="7bdf3-103">Enumerates the method instances of this process starting at an address offset.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="7bdf3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7bdf3-104">Syntax</span></span>

```cpp
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

## <a name="parameters"></a><span data-ttu-id="7bdf3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7bdf3-105">Parameters</span></span>

`handle`\
<span data-ttu-id="7bdf3-106">pro Popisovač pro vytváření výčtu instancí metody.</span><span class="sxs-lookup"><span data-stu-id="7bdf3-106">[in] A handle for enumerating the method instances.</span></span>

`mod`\
<span data-ttu-id="7bdf3-107">mimo Instance metody výčtu.</span><span class="sxs-lookup"><span data-stu-id="7bdf3-107">[out] The enumerated method instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="7bdf3-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7bdf3-108">Remarks</span></span>

<span data-ttu-id="7bdf3-109">Poskytnutá metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá slotu vysílání 29. tabulky virtuálních metod.</span><span class="sxs-lookup"><span data-stu-id="7bdf3-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 29th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="7bdf3-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7bdf3-110">Requirements</span></span>

<span data-ttu-id="7bdf3-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bdf3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="7bdf3-112">**Hlavička:** Žádná **Knihovna:** žádné **.NET Framework verze:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7bdf3-112">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="7bdf3-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="7bdf3-113">See also</span></span>

- [<span data-ttu-id="7bdf3-114">Výčet CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="7bdf3-114">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="7bdf3-115">Ladění</span><span class="sxs-lookup"><span data-stu-id="7bdf3-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="7bdf3-116">IXCLRDataProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7bdf3-116">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
