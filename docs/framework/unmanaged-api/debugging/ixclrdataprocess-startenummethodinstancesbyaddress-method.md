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
ms.openlocfilehash: 8d0494e53705493de814ed4d4caa869e1e8a700f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374567"
---
# <a name="ixclrdataprocessstartenummethodinstancesbyaddress-method"></a><span data-ttu-id="4af42-102">IXCLRDataProcess::StartEnumMethodInstancesByAddress Method</span><span class="sxs-lookup"><span data-stu-id="4af42-102">IXCLRDataProcess::StartEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="4af42-103">Poskytuje popisovač vytvořit výčet instancí metoda `AppDomain` spuštění na dané adrese.</span><span class="sxs-lookup"><span data-stu-id="4af42-103">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="4af42-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4af42-104">Syntax</span></span>

```
HRESULT StartEnumMethodInstancesByAddress(
    [in] CLRDATA_ADDRESS     address,
    [in] IXCLRDataAppDomain *appDomain,
    [out] CLRDATA_ENUM      *handle
);
```

### <a name="parameters"></a><span data-ttu-id="4af42-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4af42-105">Parameters</span></span>

`address`\
<span data-ttu-id="4af42-106">[in] Adresa první instanci metody.</span><span class="sxs-lookup"><span data-stu-id="4af42-106">[in] The address of the first method instance.</span></span>

`appDomain`\
<span data-ttu-id="4af42-107">[in] AppDomain metodu instance.</span><span class="sxs-lookup"><span data-stu-id="4af42-107">[in] The AppDomain of the method instances.</span></span>

`handle`\
<span data-ttu-id="4af42-108">[out] Popisovač pro vytváření výčtu instancí metody.</span><span class="sxs-lookup"><span data-stu-id="4af42-108">[out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="4af42-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4af42-109">Remarks</span></span>

<span data-ttu-id="4af42-110">Zadaná metoda je součástí `IXCLRDataProcess` rozhraní a odpovídá 27 pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="4af42-110">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 27th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="4af42-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4af42-111">Requirements</span></span>

<span data-ttu-id="4af42-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4af42-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="4af42-113">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="4af42-113">**Header:** None</span></span>  
<span data-ttu-id="4af42-114">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="4af42-114">**Library:** None</span></span>  
<span data-ttu-id="4af42-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4af42-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="4af42-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4af42-116">See also</span></span>

- [<span data-ttu-id="4af42-117">CLRDataSourceType Enumeration</span><span class="sxs-lookup"><span data-stu-id="4af42-117">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="4af42-118">Ladění</span><span class="sxs-lookup"><span data-stu-id="4af42-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="4af42-119">IXCLRDataProcess Interface</span><span class="sxs-lookup"><span data-stu-id="4af42-119">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
