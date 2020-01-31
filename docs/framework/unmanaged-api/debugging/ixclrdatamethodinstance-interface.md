---
title: IXCLRDataMethodInstance – rozhraní
ms.date: 02/01/2019
api.name:
- IXCLRDataMethodInstance Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance Interface
helpviewer.keywords:
- IXCLRDataMethodInstance Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: c51825433bbc86c897c097475d5c15c855f6ec8b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790412"
---
# <a name="ixclrdatamethodinstance-interface"></a><span data-ttu-id="53e29-102">IXCLRDataMethodInstance – rozhraní</span><span class="sxs-lookup"><span data-stu-id="53e29-102">IXCLRDataMethodInstance Interface</span></span>

<span data-ttu-id="53e29-103">Poskytuje metody pro dotazování na informace o instanci metody.</span><span class="sxs-lookup"><span data-stu-id="53e29-103">Provides methods for querying information about a method instance.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="53e29-104">Metody</span><span class="sxs-lookup"><span data-stu-id="53e29-104">Methods</span></span>

| <span data-ttu-id="53e29-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="53e29-105">Method</span></span>                                                                                                                  | <span data-ttu-id="53e29-106">Popis</span><span class="sxs-lookup"><span data-stu-id="53e29-106">Description</span></span>                                 |
| ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| [<span data-ttu-id="53e29-107">GetILAddressMap</span><span class="sxs-lookup"><span data-stu-id="53e29-107">GetILAddressMap</span></span>](ixclrdatamethodinstance-getiladdressmap-method.md) | <span data-ttu-id="53e29-108">Získá informace o mapování IL na adresu.</span><span class="sxs-lookup"><span data-stu-id="53e29-108">Gets the IL to address mapping information.</span></span> |
| [<span data-ttu-id="53e29-109">GetRepresentativeEntryAddress</span><span class="sxs-lookup"><span data-stu-id="53e29-109">GetRepresentativeEntryAddress</span></span>](ixclrdatamethodinstance-getrepresentativeentryaddress-method.md) | <span data-ttu-id="53e29-110">Získá nejvíce reprezentativní adresu vstupní bod pro nativní kompilaci všech možných vstupních bodů pro metodu.</span><span class="sxs-lookup"><span data-stu-id="53e29-110">Gets the most representative entry point address for the native compilation of all the possible entry points for a method.</span></span> |

## <a name="remarks"></a><span data-ttu-id="53e29-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="53e29-111">Remarks</span></span>

<span data-ttu-id="53e29-112">Toto rozhraní je v modulu runtime a není zveřejněné prostřednictvím hlaviček nebo souborů knihoven.</span><span class="sxs-lookup"><span data-stu-id="53e29-112">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="53e29-113">Jedná se však o rozhraní modelu COM, které je odvozeno od `IUnknown` s identifikátorem GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5`, které lze získat prostřednictvím obvyklých mechanismů modelu COM.</span><span class="sxs-lookup"><span data-stu-id="53e29-113">However, it's a COM interface that derives from `IUnknown` with GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="53e29-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="53e29-114">Requirements</span></span>

<span data-ttu-id="53e29-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53e29-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="53e29-116">**Hlavička:** NTato</span><span class="sxs-lookup"><span data-stu-id="53e29-116">**Header:** None</span></span>  
<span data-ttu-id="53e29-117">**Knihovna:** NTato</span><span class="sxs-lookup"><span data-stu-id="53e29-117">**Library:** None</span></span>  
<span data-ttu-id="53e29-118">**Verze .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="53e29-118">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="53e29-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="53e29-119">See also</span></span>

- [<span data-ttu-id="53e29-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="53e29-120">Debugging</span></span>](index.md)
- [<span data-ttu-id="53e29-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="53e29-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
