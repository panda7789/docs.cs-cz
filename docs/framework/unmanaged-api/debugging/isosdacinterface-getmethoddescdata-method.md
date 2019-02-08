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
ms.openlocfilehash: 47cea4810b764005e87d00966c15cf138f5913a7
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/07/2019
ms.locfileid: "55825950"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a><span data-ttu-id="3fa15-102">ISOSDacInterface::GetMethodDescData – metoda</span><span class="sxs-lookup"><span data-stu-id="3fa15-102">ISOSDacInterface::GetMethodDescData Method</span></span>

<span data-ttu-id="3fa15-103">Získá data pro danou MethodDesc ukazatele.</span><span class="sxs-lookup"><span data-stu-id="3fa15-103">Gets the data for the given MethodDesc pointer.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="3fa15-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3fa15-104">Syntax</span></span>

```
HRESULT GetMethodDescData(
    CLRDATA_ADDRESS            methodDesc,
    CLRDATA_ADDRESS            ip,
    DacpMethodDescData *data,
    ULONG                      cRevertedRejitVersions,
    DacpReJitData      *rgRevertedRejitData,
    void                      *pcNeededRevertedRejitData
);
```

### <a name="parameters"></a><span data-ttu-id="3fa15-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3fa15-105">Parameters</span></span>

<span data-ttu-id="3fa15-106">`methodDesc` [in] Adresa MethodDesc.</span><span class="sxs-lookup"><span data-stu-id="3fa15-106">`methodDesc` [in] The address of the MethodDesc.</span></span>

<span data-ttu-id="3fa15-107">`ip` [in] IP adresa metody.</span><span class="sxs-lookup"><span data-stu-id="3fa15-107">`ip` [in] The IP address of the method.</span></span>

<span data-ttu-id="3fa15-108">`data` [out] Data související s MethodDesc vrácená z interních rozhraních API.</span><span class="sxs-lookup"><span data-stu-id="3fa15-108">`data` [out] The data associated with the MethodDesc as returned from the internal APIs.</span></span>

<span data-ttu-id="3fa15-109">`cRevertedRejitVersions` [out] Počet verzí vrácený rejit.</span><span class="sxs-lookup"><span data-stu-id="3fa15-109">`cRevertedRejitVersions` [out] The number of reverted rejit versions.</span></span>

<span data-ttu-id="3fa15-110">`rgRevertedRejitData` [out] Data související s verzí vrácený rejit vrácená z interních rozhraních API.</span><span class="sxs-lookup"><span data-stu-id="3fa15-110">`rgRevertedRejitData` [out] The data associated with the reverted rejit versions as returned from the internal APIs.</span></span>

<span data-ttu-id="3fa15-111">`pcNeededRevertedRejitData` [out] Počet bajtů vyžadovaných k uložení dat spojené s vrácený ReJit verze.</span><span class="sxs-lookup"><span data-stu-id="3fa15-111">`pcNeededRevertedRejitData` [out] The number of bytes required to store the data associated with the reverted ReJit versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="3fa15-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3fa15-112">Remarks</span></span>

<span data-ttu-id="3fa15-113">Zadaná metoda je součástí `ISOSDacInterface` rozhraní a odpovídá 20. prosincem pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="3fa15-113">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 20th slot of the virtual method table.</span></span> <span data-ttu-id="3fa15-114">Abyste mohli využít, [ `CLRDATA_ADDRESS` ](../common-data-types-unmanaged-api-reference.md) musí být definován jako 64-bit znaménka.</span><span class="sxs-lookup"><span data-stu-id="3fa15-114">To be able to use them, [`CLRDATA_ADDRESS`](../common-data-types-unmanaged-api-reference.md) must be defined as a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="3fa15-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3fa15-115">Requirements</span></span>

<span data-ttu-id="3fa15-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fa15-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="3fa15-117">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="3fa15-117">**Header:** None</span></span>  
<span data-ttu-id="3fa15-118">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="3fa15-118">**Library:** None</span></span>  
<span data-ttu-id="3fa15-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3fa15-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="3fa15-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3fa15-120">See also</span></span>

- [<span data-ttu-id="3fa15-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="3fa15-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="3fa15-122">ISOSDacInterface rozhraní</span><span class="sxs-lookup"><span data-stu-id="3fa15-122">ISOSDacInterface Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-interface.md)
