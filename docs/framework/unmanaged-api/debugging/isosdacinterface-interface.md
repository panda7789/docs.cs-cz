---
title: ISOSDacInterface rozhraní
ms.date: 01/16/2019
api.name:
- ISOSDacInterface Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface Interface
helpviewer.keywords:
- ISOSDacInterface Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 5e037cf6fb88fff4886733ff4152dca0a827e0a3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491025"
---
# <a name="isosdacinterface-interface"></a><span data-ttu-id="8cf78-102">ISOSDacInterface rozhraní</span><span class="sxs-lookup"><span data-stu-id="8cf78-102">ISOSDacInterface Interface</span></span>

<span data-ttu-id="8cf78-103">Poskytuje pomocné metody pro přístup k datům z `SOS`.</span><span class="sxs-lookup"><span data-stu-id="8cf78-103">Provides helper methods to access data from `SOS`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="8cf78-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8cf78-104">Methods</span></span>

| <span data-ttu-id="8cf78-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8cf78-105">Method</span></span>                                                                                                               | <span data-ttu-id="8cf78-106">Popis</span><span class="sxs-lookup"><span data-stu-id="8cf78-106">Description</span></span>                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="8cf78-107">GetMethodDescData</span><span class="sxs-lookup"><span data-stu-id="8cf78-107">GetMethodDescData</span></span>](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-getmethoddescdata-method.md) | <span data-ttu-id="8cf78-108">Získá data dané [MethodDesc](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span><span class="sxs-lookup"><span data-stu-id="8cf78-108">Gets the data for the given [MethodDesc](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span></span> |

## <a name="remarks"></a><span data-ttu-id="8cf78-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8cf78-109">Remarks</span></span>

<span data-ttu-id="8cf78-110">Toto rozhraní se nachází uvnitř modulu runtime a není dostupná záhlaví nebo soubory knihoven.</span><span class="sxs-lookup"><span data-stu-id="8cf78-110">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="8cf78-111">Je však rozhraní modelu COM, která je odvozena z `IUnknown` s identifikátorem GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` , který můžete získat prostřednictvím obvykle COM mechanismů.</span><span class="sxs-lookup"><span data-stu-id="8cf78-111">However, it's a COM interface that derives from `IUnknown` with GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="8cf78-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8cf78-112">Requirements</span></span>

<span data-ttu-id="8cf78-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8cf78-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="8cf78-114">**Záhlaví:** Žádná</span><span class="sxs-lookup"><span data-stu-id="8cf78-114">**Header:** None</span></span>  
<span data-ttu-id="8cf78-115">**Knihovna:** Žádná</span><span class="sxs-lookup"><span data-stu-id="8cf78-115">**Library:** None</span></span>  
<span data-ttu-id="8cf78-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8cf78-116">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="8cf78-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8cf78-117">See also</span></span>

- [<span data-ttu-id="8cf78-118">Ladění</span><span class="sxs-lookup"><span data-stu-id="8cf78-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="8cf78-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="8cf78-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
