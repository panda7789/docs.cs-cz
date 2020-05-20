---
title: 'IXCLRDataMethodInstance:: GetRepresentativeEntryAddress – metoda'
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
ms.openlocfilehash: d546cda5c68732e75550a3de286089f7df261c91
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420900"
---
# <a name="ixclrdatamethodinstancegetrepresentativeentryaddress-method"></a><span data-ttu-id="61d02-102">IXCLRDataMethodInstance:: GetRepresentativeEntryAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="61d02-102">IXCLRDataMethodInstance::GetRepresentativeEntryAddress Method</span></span>

<span data-ttu-id="61d02-103">Získá nejvíce reprezentativní adresu vstupní bod pro nativní kompilaci všech možných vstupních bodů pro metodu.</span><span class="sxs-lookup"><span data-stu-id="61d02-103">Gets the most representative entry point address for the native compilation of all the possible entry points for a method.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="61d02-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61d02-104">Syntax</span></span>

```cpp
HRESULT GetRepresentativeEntryAddress(
    [out] CLRDATA_ADDRESS* addr
);
```

## <a name="parameters"></a><span data-ttu-id="61d02-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="61d02-105">Parameters</span></span>

`addr`\
<span data-ttu-id="61d02-106">mimo Adresa největšího reprezentativního nativního vstupního bodu pro metodu.</span><span class="sxs-lookup"><span data-stu-id="61d02-106">[out] The address of the most representative native entry point for the method.</span></span>

## <a name="remarks"></a><span data-ttu-id="61d02-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="61d02-107">Remarks</span></span>

<span data-ttu-id="61d02-108">Poskytnutá metoda je součástí [ `IXCLRDataMethodInstance` rozhraní](ixclrdatamethodinstance-interface.md) a odpovídá dvacátému slotu tabulky virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="61d02-108">The provided method is part of the [`IXCLRDataMethodInstance` interface](ixclrdatamethodinstance-interface.md) and corresponds to the 20th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="61d02-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="61d02-109">Requirements</span></span>

<span data-ttu-id="61d02-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61d02-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="61d02-111">**Hlavička:** NTato</span><span class="sxs-lookup"><span data-stu-id="61d02-111">**Header:** None</span></span>  
<span data-ttu-id="61d02-112">**Knihovna:** NTato</span><span class="sxs-lookup"><span data-stu-id="61d02-112">**Library:** None</span></span>  
<span data-ttu-id="61d02-113">**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="61d02-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="61d02-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="61d02-114">See also</span></span>

- [<span data-ttu-id="61d02-115">Ladění</span><span class="sxs-lookup"><span data-stu-id="61d02-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="61d02-116">IXCLRDataMethodInstance – rozhraní</span><span class="sxs-lookup"><span data-stu-id="61d02-116">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
