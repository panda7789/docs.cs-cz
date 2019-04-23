---
title: IXCLRDataMethodInstance Interface
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
ms.openlocfilehash: f62cbdc4b3e73f0c27492f7ed20b35378654d399
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59152955"
---
# <a name="ixclrdatamethodinstance-interface"></a><span data-ttu-id="105cd-102">IXCLRDataMethodInstance Interface</span><span class="sxs-lookup"><span data-stu-id="105cd-102">IXCLRDataMethodInstance Interface</span></span>

<span data-ttu-id="105cd-103">Poskytuje metody pro dotazování na informace o metodu instance.</span><span class="sxs-lookup"><span data-stu-id="105cd-103">Provides methods for querying information about a method instance.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="105cd-104">Metody</span><span class="sxs-lookup"><span data-stu-id="105cd-104">Methods</span></span>

| <span data-ttu-id="105cd-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="105cd-105">Method</span></span>                                                                                                                  | <span data-ttu-id="105cd-106">Popis</span><span class="sxs-lookup"><span data-stu-id="105cd-106">Description</span></span>                                 |
| ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| [<span data-ttu-id="105cd-107">GetILAddressMap</span><span class="sxs-lookup"><span data-stu-id="105cd-107">GetILAddressMap</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-getiladdressmap-method.md) | <span data-ttu-id="105cd-108">Získá IL na informace o mapování adres.</span><span class="sxs-lookup"><span data-stu-id="105cd-108">Gets the IL to address mapping information.</span></span> |
| [<span data-ttu-id="105cd-109">GetRepresentativeEntryAddress</span><span class="sxs-lookup"><span data-stu-id="105cd-109">GetRepresentativeEntryAddress</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-getrepresentativeentryaddress-method.md) | <span data-ttu-id="105cd-110">Získá adresu nejreprezentativnější vstupní bod pro nativní kompilace všechny vstupní body pro metodu.</span><span class="sxs-lookup"><span data-stu-id="105cd-110">Gets the most representative entry point address for the native compilation of all the possible entry points for a method.</span></span> |

## <a name="remarks"></a><span data-ttu-id="105cd-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="105cd-111">Remarks</span></span>

<span data-ttu-id="105cd-112">Toto rozhraní se nachází uvnitř modulu runtime a není dostupná záhlaví nebo soubory knihoven.</span><span class="sxs-lookup"><span data-stu-id="105cd-112">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="105cd-113">Je však rozhraní modelu COM, která je odvozena z `IUnknown` s identifikátorem GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` , který můžete získat prostřednictvím obvykle COM mechanismů.</span><span class="sxs-lookup"><span data-stu-id="105cd-113">However, it's a COM interface that derives from `IUnknown` with GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="105cd-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="105cd-114">Requirements</span></span>

<span data-ttu-id="105cd-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="105cd-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="105cd-116">**Záhlaví:** Žádné</span><span class="sxs-lookup"><span data-stu-id="105cd-116">**Header:** None</span></span>  
<span data-ttu-id="105cd-117">**Knihovna:** Žádný</span><span class="sxs-lookup"><span data-stu-id="105cd-117">**Library:** None</span></span>  
<span data-ttu-id="105cd-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="105cd-118">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="105cd-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="105cd-119">See also</span></span>

- [<span data-ttu-id="105cd-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="105cd-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="105cd-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="105cd-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
