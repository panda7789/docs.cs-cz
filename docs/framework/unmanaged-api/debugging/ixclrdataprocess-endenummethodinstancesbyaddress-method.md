---
title: 'IXCLRDataProcess:: EndEnumMethodInstancesByAddress – metoda'
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
ms.openlocfilehash: 5960d08ccfc09010a20d28a22c2e2f3f5b339c7d
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420822"
---
# <a name="ixclrdataprocessendenummethodinstancesbyaddress-method"></a><span data-ttu-id="11892-102">IXCLRDataProcess:: EndEnumMethodInstancesByAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="11892-102">IXCLRDataProcess::EndEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="11892-103">Uvolní prostředky používané interními iterátory použitými během výčtu instance.</span><span class="sxs-lookup"><span data-stu-id="11892-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="11892-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11892-104">Syntax</span></span>

```cpp
HRESULT EndEnumMethodInstancesByAddress(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="11892-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="11892-105">Parameters</span></span>

`handle`\
<span data-ttu-id="11892-106">mimo Popisovač pro vytváření výčtu instancí metody.</span><span class="sxs-lookup"><span data-stu-id="11892-106">[out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="11892-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="11892-107">Remarks</span></span>

<span data-ttu-id="11892-108">Poskytnutá metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá 30 slotu tabulky virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="11892-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 30th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="11892-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="11892-109">Requirements</span></span>

<span data-ttu-id="11892-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11892-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="11892-111">**Hlavička:** NTato</span><span class="sxs-lookup"><span data-stu-id="11892-111">**Header:** None</span></span>  
<span data-ttu-id="11892-112">**Knihovna:** NTato</span><span class="sxs-lookup"><span data-stu-id="11892-112">**Library:** None</span></span>  
<span data-ttu-id="11892-113">**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="11892-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="11892-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="11892-114">See also</span></span>

- [<span data-ttu-id="11892-115">Výčet CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="11892-115">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="11892-116">Ladění</span><span class="sxs-lookup"><span data-stu-id="11892-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="11892-117">IXCLRDataProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="11892-117">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
