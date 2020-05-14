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
ms.openlocfilehash: 04ce8f44b0c9f532951666de7bfb9de475c14746
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395257"
---
# <a name="ixclrdataprocessendenummethodinstancesbyaddress-method"></a><span data-ttu-id="0f4be-102">IXCLRDataProcess:: EndEnumMethodInstancesByAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="0f4be-102">IXCLRDataProcess::EndEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="0f4be-103">Uvolní prostředky používané interními iterátory použitými během výčtu instance.</span><span class="sxs-lookup"><span data-stu-id="0f4be-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="0f4be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f4be-104">Syntax</span></span>

```cpp
HRESULT EndEnumMethodInstancesByAddress(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="0f4be-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0f4be-105">Parameters</span></span>

`handle`\
<span data-ttu-id="0f4be-106">mimo Popisovač pro vytváření výčtu instancí metody.</span><span class="sxs-lookup"><span data-stu-id="0f4be-106">[out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="0f4be-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0f4be-107">Remarks</span></span>

<span data-ttu-id="0f4be-108">Poskytnutá metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá 30 slotu tabulky virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="0f4be-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 30th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="0f4be-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0f4be-109">Requirements</span></span>

<span data-ttu-id="0f4be-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f4be-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="0f4be-111">**Hlavička:** NTato</span><span class="sxs-lookup"><span data-stu-id="0f4be-111">**Header:** None</span></span>  
<span data-ttu-id="0f4be-112">**Knihovna:** NTato</span><span class="sxs-lookup"><span data-stu-id="0f4be-112">**Library:** None</span></span>  
<span data-ttu-id="0f4be-113">**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0f4be-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="0f4be-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="0f4be-114">See also</span></span>

- [<span data-ttu-id="0f4be-115">Výčet CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="0f4be-115">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="0f4be-116">Ladění</span><span class="sxs-lookup"><span data-stu-id="0f4be-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="0f4be-117">IXCLRDataProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0f4be-117">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
