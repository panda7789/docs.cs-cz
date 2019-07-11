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
ms.openlocfilehash: ea54fdd83b9470db4a08daceaa695e450f5ca1af
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764819"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a><span data-ttu-id="279b9-102">ISOSDacInterface::GetMethodDescData – metoda</span><span class="sxs-lookup"><span data-stu-id="279b9-102">ISOSDacInterface::GetMethodDescData Method</span></span>

<span data-ttu-id="279b9-103">Získá data pro danou MethodDesc ukazatele.</span><span class="sxs-lookup"><span data-stu-id="279b9-103">Gets the data for the given MethodDesc pointer.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="279b9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="279b9-104">Syntax</span></span>

```cpp
HRESULT GetMethodDescData(
    CLRDATA_ADDRESS            methodDesc,
    CLRDATA_ADDRESS            ip,
    DacpMethodDescData *data,
    ULONG                      cRevertedRejitVersions,
    DacpReJitData      *rgRevertedRejitData,
    void                      *pcNeededRevertedRejitData
);
```

## <a name="parameters"></a><span data-ttu-id="279b9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="279b9-105">Parameters</span></span>

`methodDesc`\
<span data-ttu-id="279b9-106">[in] Adresa MethodDesc.</span><span class="sxs-lookup"><span data-stu-id="279b9-106">[in] The address of the MethodDesc.</span></span>

`ip`\
<span data-ttu-id="279b9-107">[in] IP adresa metody.</span><span class="sxs-lookup"><span data-stu-id="279b9-107">[in] The IP address of the method.</span></span>

`data`\
<span data-ttu-id="279b9-108">[out] Data související s MethodDesc vrácená z interních rozhraních API.</span><span class="sxs-lookup"><span data-stu-id="279b9-108">[out] The data associated with the MethodDesc as returned from the internal APIs.</span></span>

`cRevertedRejitVersions`\
<span data-ttu-id="279b9-109">[out] Počet verzí vrácený rejit.</span><span class="sxs-lookup"><span data-stu-id="279b9-109">[out] The number of reverted rejit versions.</span></span>

`rgRevertedRejitData`\
<span data-ttu-id="279b9-110">[out] Data související s verzí vrácený rejit vrácená z interních rozhraních API.</span><span class="sxs-lookup"><span data-stu-id="279b9-110">[out] The data associated with the reverted rejit versions as returned from the internal APIs.</span></span>

`pcNeededRevertedRejitData`\
<span data-ttu-id="279b9-111">[out] Počet bajtů vyžadovaných k uložení dat spojené s vrácený ReJit verze.</span><span class="sxs-lookup"><span data-stu-id="279b9-111">[out] The number of bytes required to store the data associated with the reverted ReJit versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="279b9-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="279b9-112">Remarks</span></span>

<span data-ttu-id="279b9-113">Zadaná metoda je součástí `ISOSDacInterface` rozhraní a odpovídá 20. prosincem pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="279b9-113">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 20th slot of the virtual method table.</span></span> <span data-ttu-id="279b9-114">Abyste mohli využít, [ `CLRDATA_ADDRESS` ](../common-data-types-unmanaged-api-reference.md) musí být definován jako 64-bit znaménka.</span><span class="sxs-lookup"><span data-stu-id="279b9-114">To be able to use them, [`CLRDATA_ADDRESS`](../common-data-types-unmanaged-api-reference.md) must be defined as a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="279b9-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="279b9-115">Requirements</span></span>

<span data-ttu-id="279b9-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="279b9-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="279b9-117">**Záhlaví:** Žádný</span><span class="sxs-lookup"><span data-stu-id="279b9-117">**Header:** None</span></span>  
<span data-ttu-id="279b9-118">**Knihovna:** Žádný</span><span class="sxs-lookup"><span data-stu-id="279b9-118">**Library:** None</span></span>  
<span data-ttu-id="279b9-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="279b9-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="279b9-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="279b9-120">See also</span></span>

- [<span data-ttu-id="279b9-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="279b9-121">Debugging</span></span>](index.md)
- [<span data-ttu-id="279b9-122">ISOSDacInterface rozhraní</span><span class="sxs-lookup"><span data-stu-id="279b9-122">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
