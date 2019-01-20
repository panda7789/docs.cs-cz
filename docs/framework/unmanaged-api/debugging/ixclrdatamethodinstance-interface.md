---
title: IXCLRDataMethodInstance Interface
ms.date: 01/16/2019
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
ms.openlocfilehash: 5bf724bc76591ae59c073b5b9a788ca065f51dc0
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416071"
---
# <a name="ixclrdatamethodinstance-interface"></a><span data-ttu-id="7e009-102">IXCLRDataMethodInstance Interface</span><span class="sxs-lookup"><span data-stu-id="7e009-102">IXCLRDataMethodInstance Interface</span></span>

<span data-ttu-id="7e009-103">Poskytuje metody pro dotazování na informace o metodu instance.</span><span class="sxs-lookup"><span data-stu-id="7e009-103">Provides methods for querying information about a method instance.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="7e009-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7e009-104">Methods</span></span>

| <span data-ttu-id="7e009-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7e009-105">Method</span></span>                                                                                                                  | <span data-ttu-id="7e009-106">Popis</span><span class="sxs-lookup"><span data-stu-id="7e009-106">Description</span></span>                                 |
| ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| [<span data-ttu-id="7e009-107">GetILAddressMap</span><span class="sxs-lookup"><span data-stu-id="7e009-107">GetILAddressMap</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-getiladdressmap-method.md) | <span data-ttu-id="7e009-108">Získá IL na informace o mapování adres.</span><span class="sxs-lookup"><span data-stu-id="7e009-108">Gets the IL to address mapping information.</span></span> |

## <a name="remarks"></a><span data-ttu-id="7e009-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7e009-109">Remarks</span></span>

<span data-ttu-id="7e009-110">Toto rozhraní se nachází uvnitř modulu runtime a není dostupná záhlaví nebo soubory knihoven.</span><span class="sxs-lookup"><span data-stu-id="7e009-110">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="7e009-111">Je však rozhraní modelu COM, která je odvozena z `IUnknown` s identifikátorem GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` , který můžete získat prostřednictvím obvykle COM mechanismů.</span><span class="sxs-lookup"><span data-stu-id="7e009-111">However, it's a COM interface that derives from `IUnknown` with GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="7e009-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7e009-112">Requirements</span></span>

<span data-ttu-id="7e009-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e009-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="7e009-114">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="7e009-114">**Header:** None</span></span>  
<span data-ttu-id="7e009-115">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="7e009-115">**Library:** None</span></span>  
<span data-ttu-id="7e009-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7e009-116">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="7e009-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="7e009-117">See Also</span></span>

- [<span data-ttu-id="7e009-118">Ladění</span><span class="sxs-lookup"><span data-stu-id="7e009-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="7e009-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="7e009-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
