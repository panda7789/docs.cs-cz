---
title: ISOSDacInterface::GetMethodDescData – metoda
ms.date: 01/16/2019
api.name:
- ISOSDacInterface::GetMethodDescData Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetMethodDescData Method
helpviewer.keywords:
- ISOSDacInterface::GetMethodDescData Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 3f22752446413c622a20340541b0ac328f63c77b
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416123"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a><span data-ttu-id="8243b-102">ISOSDacInterface::GetMethodDescData – metoda</span><span class="sxs-lookup"><span data-stu-id="8243b-102">ISOSDacInterface::GetMethodDescData Method</span></span>

<span data-ttu-id="8243b-103">Získá data dané [MethodDesc](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span><span class="sxs-lookup"><span data-stu-id="8243b-103">Gets the data for the given [MethodDesc](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="8243b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8243b-104">Syntax</span></span>

```
HRESULT GetMethodDescData(
    CLRDATA_ADDRESS            methodDesc,
    CLRDATA_ADDRESS            ip,
    void                       *data,
    ULONG                      cRevertedRejitVersions,
    void                      *rgRevertedRejitData,
    void                      *pcNeededRevertedRejitData
);
```

### <a name="parameters"></a><span data-ttu-id="8243b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8243b-105">Parameters</span></span>

<span data-ttu-id="8243b-106">`methodDesc` [in] Adresa MethodDesc.</span><span class="sxs-lookup"><span data-stu-id="8243b-106">`methodDesc` [in] The address of the MethodDesc.</span></span>

<span data-ttu-id="8243b-107">`ip` [in] IP adresa metody.</span><span class="sxs-lookup"><span data-stu-id="8243b-107">`ip` [in] The IP address of the method.</span></span>

<span data-ttu-id="8243b-108">`data` [out] Data související s MethodDesc vrácená z interních rozhraních API.</span><span class="sxs-lookup"><span data-stu-id="8243b-108">`data` [out] The data associated with the MethodDesc as returned from the internal APIs.</span></span> <span data-ttu-id="8243b-109">Struktura potřebuje aspoň 168 bajtů.</span><span class="sxs-lookup"><span data-stu-id="8243b-109">The structure needs at least 168 bytes.</span></span>

<span data-ttu-id="8243b-110">`cRevertedRejitVersions` [out] Počet verzí vrácený rejit.</span><span class="sxs-lookup"><span data-stu-id="8243b-110">`cRevertedRejitVersions` [out] The number of reverted rejit versions.</span></span>

<span data-ttu-id="8243b-111">`rgRevertedRejitData` [out] Data související s verzí vrácený rejit vrácená z interních rozhraních API.</span><span class="sxs-lookup"><span data-stu-id="8243b-111">`rgRevertedRejitData` [out] The data associated with the reverted rejit versions as returned from the internal APIs.</span></span> <span data-ttu-id="8243b-112">Struktura potřebuje aspoň 24 bajtů.</span><span class="sxs-lookup"><span data-stu-id="8243b-112">The structure needs at least 24 bytes.</span></span>

<span data-ttu-id="8243b-113">`pcNeededRevertedRejitData` [out] Počet bajtů vyžadovaných k uložení dat spojené s vrácený ReJit verze.</span><span class="sxs-lookup"><span data-stu-id="8243b-113">`pcNeededRevertedRejitData` [out] The number of bytes required to store the data associated with the reverted ReJit versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="8243b-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8243b-114">Remarks</span></span>

<span data-ttu-id="8243b-115">Zadaná metoda je součástí `ISOSDacInterface` rozhraní a odpovídá 20. prosincem pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="8243b-115">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 20th slot of the virtual method table.</span></span> <span data-ttu-id="8243b-116">Také `CLRDATA_ADDRESS` jsou 64bitové celé číslo bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="8243b-116">Also the `CLRDATA_ADDRESS` are 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="8243b-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8243b-117">Requirements</span></span>

<span data-ttu-id="8243b-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8243b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="8243b-119">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="8243b-119">**Header:** None</span></span>  
<span data-ttu-id="8243b-120">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="8243b-120">**Library:** None</span></span>  
<span data-ttu-id="8243b-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8243b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="8243b-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="8243b-122">See Also</span></span>

- [<span data-ttu-id="8243b-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="8243b-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="8243b-124">ISOSDacInterface rozhraní</span><span class="sxs-lookup"><span data-stu-id="8243b-124">ISOSDacInterface Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-interface.md)
