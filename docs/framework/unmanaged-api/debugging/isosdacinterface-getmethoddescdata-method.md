---
title: 'ISOSDacInterface:: GetMethodDescData – metoda'
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
ms.openlocfilehash: 105149d0abf312c33a8498e7428e3a8b23d6ae7d
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421017"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a><span data-ttu-id="df872-102">ISOSDacInterface:: GetMethodDescData – metoda</span><span class="sxs-lookup"><span data-stu-id="df872-102">ISOSDacInterface::GetMethodDescData Method</span></span>

<span data-ttu-id="df872-103">Načte data pro daný ukazatel MethodDesc.</span><span class="sxs-lookup"><span data-stu-id="df872-103">Gets the data for the given MethodDesc pointer.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="df872-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df872-104">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="df872-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="df872-105">Parameters</span></span>

`methodDesc`\
<span data-ttu-id="df872-106">pro Adresa MethodDesc.</span><span class="sxs-lookup"><span data-stu-id="df872-106">[in] The address of the MethodDesc.</span></span>

`ip`\
<span data-ttu-id="df872-107">pro IP adresa metody</span><span class="sxs-lookup"><span data-stu-id="df872-107">[in] The IP address of the method.</span></span>

`data`\
<span data-ttu-id="df872-108">mimo Data přidružená k MethodDesc, která se vrací z interních rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="df872-108">[out] The data associated with the MethodDesc as returned from the internal APIs.</span></span>

`cRevertedRejitVersions`\
<span data-ttu-id="df872-109">mimo Počet vrácených verzí ReJIT.</span><span class="sxs-lookup"><span data-stu-id="df872-109">[out] The number of reverted rejit versions.</span></span>

`rgRevertedRejitData`\
<span data-ttu-id="df872-110">mimo Data přidružená k obnoveným verzím ReJIT, která se vrátila z interních rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="df872-110">[out] The data associated with the reverted rejit versions as returned from the internal APIs.</span></span>

`pcNeededRevertedRejitData`\
<span data-ttu-id="df872-111">mimo Počet bajtů vyžadovaných k uložení dat přidružených k vráceným verzím ReJit.</span><span class="sxs-lookup"><span data-stu-id="df872-111">[out] The number of bytes required to store the data associated with the reverted ReJit versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="df872-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="df872-112">Remarks</span></span>

<span data-ttu-id="df872-113">Poskytnutá metoda je součástí `ISOSDacInterface` rozhraní a odpovídá 21. pozici tabulky virtuálních metod.</span><span class="sxs-lookup"><span data-stu-id="df872-113">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 21st slot of the virtual method table.</span></span> <span data-ttu-id="df872-114">Aby je bylo možné použít, [`CLRDATA_ADDRESS`](../common-data-types-unmanaged-api-reference.md) musí být definován jako 64-bit unsigned integer.</span><span class="sxs-lookup"><span data-stu-id="df872-114">To be able to use them, [`CLRDATA_ADDRESS`](../common-data-types-unmanaged-api-reference.md) must be defined as a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="df872-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="df872-115">Requirements</span></span>

<span data-ttu-id="df872-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df872-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="df872-117">**Hlavička:** NTato</span><span class="sxs-lookup"><span data-stu-id="df872-117">**Header:** None</span></span>  
<span data-ttu-id="df872-118">**Knihovna:** NTato</span><span class="sxs-lookup"><span data-stu-id="df872-118">**Library:** None</span></span>  
<span data-ttu-id="df872-119">**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="df872-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="df872-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="df872-120">See also</span></span>

- [<span data-ttu-id="df872-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="df872-121">Debugging</span></span>](index.md)
- [<span data-ttu-id="df872-122">ISOSDacInterface – rozhraní</span><span class="sxs-lookup"><span data-stu-id="df872-122">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
