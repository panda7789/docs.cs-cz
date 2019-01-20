---
title: IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
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
ms.openlocfilehash: 88ce9dd928871d71058fe28c243a9fb51b729778
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416114"
---
# <a name="ixclrdataprocessstartenummethodinstancesbyaddress-method"></a><span data-ttu-id="4cd81-102">IXCLRDataProcess::StartEnumMethodInstancesByAddress Method</span><span class="sxs-lookup"><span data-stu-id="4cd81-102">IXCLRDataProcess::StartEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="4cd81-103">Poskytuje popisovač vytvořit výčet instancí metoda `AppDomain` spuštění na dané adrese.</span><span class="sxs-lookup"><span data-stu-id="4cd81-103">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="4cd81-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4cd81-104">Syntax</span></span>

```
HRESULT StartEnumMethodInstancesByAddress(
    [in] CLRDATA_ADDRESS     address,
    [in] IXCLRDataAppDomain *appDomain,
    [out] CLRDATA_ENUM      *handle
);
```

### <a name="parameters"></a><span data-ttu-id="4cd81-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4cd81-105">Parameters</span></span>

<span data-ttu-id="4cd81-106">`address` [in] Adresa první instanci metody.</span><span class="sxs-lookup"><span data-stu-id="4cd81-106">`address` [in] The address of the first method instance.</span></span>

<span data-ttu-id="4cd81-107">`appDomain` [in] AppDomain metodu instance.</span><span class="sxs-lookup"><span data-stu-id="4cd81-107">`appDomain` [in] The AppDomain of the method instances.</span></span>

<span data-ttu-id="4cd81-108">`handle` [out] Popisovač pro vytváření výčtu instancí metody.</span><span class="sxs-lookup"><span data-stu-id="4cd81-108">`handle` [out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="4cd81-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4cd81-109">Remarks</span></span>

<span data-ttu-id="4cd81-110">Zadaná metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá 27 pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="4cd81-110">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 27th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="4cd81-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4cd81-111">Requirements</span></span>

<span data-ttu-id="4cd81-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4cd81-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="4cd81-113">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="4cd81-113">**Header:** None</span></span>  
<span data-ttu-id="4cd81-114">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="4cd81-114">**Library:** None</span></span>  
<span data-ttu-id="4cd81-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4cd81-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="4cd81-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="4cd81-116">See Also</span></span>

- [<span data-ttu-id="4cd81-117">CLRDataSourceType Enumeration</span><span class="sxs-lookup"><span data-stu-id="4cd81-117">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="4cd81-118">Ladění</span><span class="sxs-lookup"><span data-stu-id="4cd81-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="4cd81-119">IXCLRDataProcess Interface</span><span class="sxs-lookup"><span data-stu-id="4cd81-119">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
