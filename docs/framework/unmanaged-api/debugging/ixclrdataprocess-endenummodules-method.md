---
title: IXCLRDataProcess::EndEnumModules – metoda
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
ms.openlocfilehash: de30384b4c12c4fcac3eafe580484685f8a43fa4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775424"
---
# <a name="ixclrdataprocessendenummodules-method"></a><span data-ttu-id="9f697-102">IXCLRDataProcess::EndEnumModules – metoda</span><span class="sxs-lookup"><span data-stu-id="9f697-102">IXCLRDataProcess::EndEnumModules Method</span></span>

<span data-ttu-id="9f697-103">Uvolní prostředky využívané třídou interní iterátory využitých modulu výčtu.</span><span class="sxs-lookup"><span data-stu-id="9f697-103">Releases the resources used by internal iterators used during module enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="9f697-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f697-104">Syntax</span></span>

```cpp
HRESULT EndEnumModules(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="9f697-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9f697-105">Parameters</span></span>

`handle`\
<span data-ttu-id="9f697-106">[out] Popisovač pro vytvoření výčtu moduly.</span><span class="sxs-lookup"><span data-stu-id="9f697-106">[out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="9f697-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9f697-107">Remarks</span></span>

<span data-ttu-id="9f697-108">Zadaná metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá 26. pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="9f697-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 26th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="9f697-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9f697-109">Requirements</span></span>

<span data-ttu-id="9f697-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f697-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>
<span data-ttu-id="9f697-111">**Záhlaví:** Žádný **knihovny:** Žádný **verze rozhraní .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9f697-111">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="9f697-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f697-112">See also</span></span>

- [<span data-ttu-id="9f697-113">Ladění</span><span class="sxs-lookup"><span data-stu-id="9f697-113">Debugging</span></span>](index.md)
- [<span data-ttu-id="9f697-114">IXCLRDataProcess Interface</span><span class="sxs-lookup"><span data-stu-id="9f697-114">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
