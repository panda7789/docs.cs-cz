---
title: IXCLRDataModule Interface
ms.date: 01/16/2019
api.name:
- IXCLRDataModule Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule Interface
helpviewer.keywords:
- IXCLRDataModule Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: c8d6e36687fd43bbc59304eee64dd42eb78101e3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676520"
---
# <a name="ixclrdatamodule-interface"></a><span data-ttu-id="66096-102">IXCLRDataModule Interface</span><span class="sxs-lookup"><span data-stu-id="66096-102">IXCLRDataModule Interface</span></span>

<span data-ttu-id="66096-103">Poskytuje metody pro dotazování na informace o u načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="66096-103">Provides methods for querying information about a loaded module.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="66096-104">Metody</span><span class="sxs-lookup"><span data-stu-id="66096-104">Methods</span></span>

| <span data-ttu-id="66096-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="66096-105">Method</span></span>                                                                                                                                | <span data-ttu-id="66096-106">Popis</span><span class="sxs-lookup"><span data-stu-id="66096-106">Description</span></span>                                                         |
| ------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="66096-107">GetMethodDefinitionByToken</span><span class="sxs-lookup"><span data-stu-id="66096-107">GetMethodDefinitionByToken</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-getmethoddefinitionbytoken-method.md) | <span data-ttu-id="66096-108">Získá definici metody odpovídající token daná metadata.</span><span class="sxs-lookup"><span data-stu-id="66096-108">Gets the method definition corresponding to a given metadata token.</span></span> |
| [<span data-ttu-id="66096-109">Požadavek</span><span class="sxs-lookup"><span data-stu-id="66096-109">Request</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-request-method.md)                                       | <span data-ttu-id="66096-110">Požadavky k naplnění vyrovnávací paměť přidělená s daty modulu.</span><span class="sxs-lookup"><span data-stu-id="66096-110">Requests to populate the buffer given with the module's data.</span></span>       |
| [<span data-ttu-id="66096-111">GetVersionId</span><span class="sxs-lookup"><span data-stu-id="66096-111">GetVersionId</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-getversionid-method.md)                             | <span data-ttu-id="66096-112">Získá ID modulu verze.</span><span class="sxs-lookup"><span data-stu-id="66096-112">Gets the module's version ID.</span></span>                                       |

## <a name="remarks"></a><span data-ttu-id="66096-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="66096-113">Remarks</span></span>

<span data-ttu-id="66096-114">Toto rozhraní se nachází uvnitř modulu runtime a není dostupná záhlaví nebo soubory knihoven.</span><span class="sxs-lookup"><span data-stu-id="66096-114">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="66096-115">Je však rozhraní modelu COM, která je odvozena z `IUnknown` s identifikátorem GUID `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` , který můžete získat prostřednictvím obvykle COM mechanismů.</span><span class="sxs-lookup"><span data-stu-id="66096-115">However, it's a COM interface that derives from `IUnknown` with GUID `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="66096-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="66096-116">Requirements</span></span>

<span data-ttu-id="66096-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66096-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="66096-118">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="66096-118">**Header:** None</span></span>  
<span data-ttu-id="66096-119">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="66096-119">**Library:** None</span></span>  
<span data-ttu-id="66096-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="66096-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="66096-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="66096-121">See also</span></span>

- [<span data-ttu-id="66096-122">Ladění</span><span class="sxs-lookup"><span data-stu-id="66096-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="66096-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="66096-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
