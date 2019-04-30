---
title: IXCLRDataProcess::EndEnumMethodInstancesByAddress Method
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
ms.openlocfilehash: 072e775d11d44dfbca27f1616889e388ae61d467
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775476"
---
# <a name="ixclrdataprocessendenummethodinstancesbyaddress-method"></a><span data-ttu-id="2fa5d-102">IXCLRDataProcess::EndEnumMethodInstancesByAddress Method</span><span class="sxs-lookup"><span data-stu-id="2fa5d-102">IXCLRDataProcess::EndEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="2fa5d-103">Uvolní prostředky využívané třídou interní iterátory využitých instance výčtu.</span><span class="sxs-lookup"><span data-stu-id="2fa5d-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="2fa5d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2fa5d-104">Syntax</span></span>

```
HRESULT EndEnumMethodInstancesByAddress(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="2fa5d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2fa5d-105">Parameters</span></span>

`handle`\
<span data-ttu-id="2fa5d-106">[out] Popisovač pro vytváření výčtu instancí metody.</span><span class="sxs-lookup"><span data-stu-id="2fa5d-106">[out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="2fa5d-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2fa5d-107">Remarks</span></span>

<span data-ttu-id="2fa5d-108">Zadaná metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá 29. pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="2fa5d-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 29th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="2fa5d-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2fa5d-109">Requirements</span></span>

<span data-ttu-id="2fa5d-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fa5d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="2fa5d-111">**Záhlaví:** Žádné</span><span class="sxs-lookup"><span data-stu-id="2fa5d-111">**Header:** None</span></span>  
<span data-ttu-id="2fa5d-112">**Knihovna:** Žádný</span><span class="sxs-lookup"><span data-stu-id="2fa5d-112">**Library:** None</span></span>  
<span data-ttu-id="2fa5d-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2fa5d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="2fa5d-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2fa5d-114">See also</span></span>

- [<span data-ttu-id="2fa5d-115">CLRDataSourceType Enumeration</span><span class="sxs-lookup"><span data-stu-id="2fa5d-115">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="2fa5d-116">Ladění</span><span class="sxs-lookup"><span data-stu-id="2fa5d-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="2fa5d-117">IXCLRDataProcess Interface</span><span class="sxs-lookup"><span data-stu-id="2fa5d-117">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
