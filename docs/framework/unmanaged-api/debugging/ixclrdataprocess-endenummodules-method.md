---
title: 'IXCLRDataProcess:: EndEnumModules – metoda'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EndEnumModules Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EndEnumModules Method
helpviewer.keywords:
- IXCLRDataProcess::EndEnumModules Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 9a7a23e53f5c2bc7d643046830cf335fec780f11
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420835"
---
# <a name="ixclrdataprocessendenummodules-method"></a><span data-ttu-id="8113b-102">IXCLRDataProcess:: EndEnumModules – metoda</span><span class="sxs-lookup"><span data-stu-id="8113b-102">IXCLRDataProcess::EndEnumModules Method</span></span>

<span data-ttu-id="8113b-103">Uvolňuje prostředky používané vnitřními iterátory použitými při výčtu modulů.</span><span class="sxs-lookup"><span data-stu-id="8113b-103">Releases the resources used by internal iterators used during module enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="8113b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8113b-104">Syntax</span></span>

```cpp
HRESULT EndEnumModules(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="8113b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8113b-105">Parameters</span></span>

`handle`\
<span data-ttu-id="8113b-106">mimo Popisovač pro vytváření výčtu modulů.</span><span class="sxs-lookup"><span data-stu-id="8113b-106">[out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="8113b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8113b-107">Remarks</span></span>

<span data-ttu-id="8113b-108">Poskytnutá metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá slotu 26 tabulky virtuálních metod.</span><span class="sxs-lookup"><span data-stu-id="8113b-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 26th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="8113b-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8113b-109">Requirements</span></span>

<span data-ttu-id="8113b-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8113b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="8113b-111">**Hlavička:** Žádná **Knihovna:** žádné **.NET Framework verze:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8113b-111">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="8113b-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="8113b-112">See also</span></span>

- [<span data-ttu-id="8113b-113">Ladění</span><span class="sxs-lookup"><span data-stu-id="8113b-113">Debugging</span></span>](index.md)
- [<span data-ttu-id="8113b-114">IXCLRDataProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8113b-114">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
