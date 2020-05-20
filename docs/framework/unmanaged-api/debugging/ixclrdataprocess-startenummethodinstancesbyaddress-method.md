---
title: 'IXCLRDataProcess:: StartEnumMethodInstancesByAddress – metoda'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 52d533f1c86b34b7b9febade8590e7ab58d8221e
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420731"
---
# <a name="ixclrdataprocessstartenummethodinstancesbyaddress-method"></a><span data-ttu-id="11182-102">IXCLRDataProcess:: StartEnumMethodInstancesByAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="11182-102">IXCLRDataProcess::StartEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="11182-103">Poskytuje popisovač pro zobrazení výčtu instancí metod, které `AppDomain` začínají na dané adrese.</span><span class="sxs-lookup"><span data-stu-id="11182-103">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="11182-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11182-104">Syntax</span></span>

```cpp
HRESULT StartEnumMethodInstancesByAddress(
    [in] CLRDATA_ADDRESS     address,
    [in] IXCLRDataAppDomain *appDomain,
    [out] CLRDATA_ENUM      *handle
);
```

## <a name="parameters"></a><span data-ttu-id="11182-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="11182-105">Parameters</span></span>

`address`\
<span data-ttu-id="11182-106">pro Adresa první instance metody.</span><span class="sxs-lookup"><span data-stu-id="11182-106">[in] The address of the first method instance.</span></span>

`appDomain`\
<span data-ttu-id="11182-107">pro Doména AppDomain instancí metody.</span><span class="sxs-lookup"><span data-stu-id="11182-107">[in] The AppDomain of the method instances.</span></span>

`handle`\
<span data-ttu-id="11182-108">mimo Popisovač pro vytváření výčtu instancí metody.</span><span class="sxs-lookup"><span data-stu-id="11182-108">[out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="11182-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="11182-109">Remarks</span></span>

<span data-ttu-id="11182-110">Poskytnutá metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá slotu 28 tabulky virtuálních metod.</span><span class="sxs-lookup"><span data-stu-id="11182-110">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 28th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="11182-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="11182-111">Requirements</span></span>

<span data-ttu-id="11182-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11182-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="11182-113">**Hlavička:** NTato</span><span class="sxs-lookup"><span data-stu-id="11182-113">**Header:** None</span></span>  
<span data-ttu-id="11182-114">**Knihovna:** NTato</span><span class="sxs-lookup"><span data-stu-id="11182-114">**Library:** None</span></span>  
<span data-ttu-id="11182-115">**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="11182-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="11182-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="11182-116">See also</span></span>

- [<span data-ttu-id="11182-117">Výčet CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="11182-117">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="11182-118">Ladění</span><span class="sxs-lookup"><span data-stu-id="11182-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="11182-119">IXCLRDataProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="11182-119">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
