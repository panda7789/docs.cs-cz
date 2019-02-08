---
title: IXCLRDataMethodInstance::GetRepresentativeEntryAddress – metoda
ms.date: 02/01/2019
api.name:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress
helpviewer.keywords:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 52b2fdaaefd16a49300641f44041b8352141385b
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/07/2019
ms.locfileid: "55828537"
---
# <a name="ixclrdatamethodinstancegetrepresentativeentryaddress-method"></a><span data-ttu-id="fac52-102">IXCLRDataMethodInstance::GetRepresentativeEntryAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="fac52-102">IXCLRDataMethodInstance::GetRepresentativeEntryAddress Method</span></span>

<span data-ttu-id="fac52-103">Získá adresu nejreprezentativnější vstupní bod pro nativní kompilace všechny vstupní body pro metodu.</span><span class="sxs-lookup"><span data-stu-id="fac52-103">Gets the most representative entry point address for the native compilation of all the possible entry points for a method.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="fac52-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fac52-104">Syntax</span></span>

```
HRESULT GetRepresentativeEntryAddress(
    [out] CLRDATA_ADDRESS* addr
);
```

### <a name="parameters"></a><span data-ttu-id="fac52-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fac52-105">Parameters</span></span>

<span data-ttu-id="fac52-106">`addr` [out] Adresa nejreprezentativnější nativní vstupní bod pro metodu.</span><span class="sxs-lookup"><span data-stu-id="fac52-106">`addr` [out] The address of the most representative native entry point for the method.</span></span>

## <a name="remarks"></a><span data-ttu-id="fac52-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fac52-107">Remarks</span></span>

<span data-ttu-id="fac52-108">Zadaná metoda je součástí [ `IXCLRDataMethodInstance` rozhraní](ixclrdatamethodinstance-interface.md) a odpovídá 19. pozice tabulce virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="fac52-108">The provided method is part of the [`IXCLRDataMethodInstance` interface](ixclrdatamethodinstance-interface.md) and corresponds to the 19th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="fac52-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fac52-109">Requirements</span></span>

<span data-ttu-id="fac52-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fac52-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="fac52-111">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="fac52-111">**Header:** None</span></span>  
<span data-ttu-id="fac52-112">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="fac52-112">**Library:** None</span></span>  
<span data-ttu-id="fac52-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="fac52-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="fac52-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fac52-114">See also</span></span>

- [<span data-ttu-id="fac52-115">Ladění</span><span class="sxs-lookup"><span data-stu-id="fac52-115">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="fac52-116">IXCLRDataMethodInstance Interface</span><span class="sxs-lookup"><span data-stu-id="fac52-116">IXCLRDataMethodInstance Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-interface.md)
