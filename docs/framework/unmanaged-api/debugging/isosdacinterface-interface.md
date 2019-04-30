---
title: ISOSDacInterface – rozhraní
ms.date: 02/01/2019
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
ms.openlocfilehash: ccaf479fc4fb90007b4999e95ee03bdd0529321e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61922145"
---
# <a name="isosdacinterface-interface"></a><span data-ttu-id="2d57b-102">ISOSDacInterface – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2d57b-102">ISOSDacInterface Interface</span></span>

<span data-ttu-id="2d57b-103">Poskytuje pomocné metody pro přístup k datům z `SOS`.</span><span class="sxs-lookup"><span data-stu-id="2d57b-103">Provides helper methods to access data from `SOS`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="2d57b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2d57b-104">Methods</span></span>

| <span data-ttu-id="2d57b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2d57b-105">Method</span></span>                                                                                                               | <span data-ttu-id="2d57b-106">Popis</span><span class="sxs-lookup"><span data-stu-id="2d57b-106">Description</span></span>                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="2d57b-107">GetMethodDescData</span><span class="sxs-lookup"><span data-stu-id="2d57b-107">GetMethodDescData</span></span>](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-getmethoddescdata-method.md) | <span data-ttu-id="2d57b-108">Získá data pro danou MethodDesc ukazatele.</span><span class="sxs-lookup"><span data-stu-id="2d57b-108">Gets the data for the given MethodDesc pointer.</span></span> |
| [<span data-ttu-id="2d57b-109">GetMethodDescPtrFromIP</span><span class="sxs-lookup"><span data-stu-id="2d57b-109">GetMethodDescPtrFromIP</span></span>](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-getmethoddescptrfromip-method.md) | <span data-ttu-id="2d57b-110">Načte ukazatel MethodDesc odpovídající metodu obsahující uvedené instrukce nativní adresu.</span><span class="sxs-lookup"><span data-stu-id="2d57b-110">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span> |
| [<span data-ttu-id="2d57b-111">GetModuleData</span><span class="sxs-lookup"><span data-stu-id="2d57b-111">GetModuleData</span></span>](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-getmoduledata-method.md)| <span data-ttu-id="2d57b-112">Načte data odpovídající modul načíst na dané adrese.</span><span class="sxs-lookup"><span data-stu-id="2d57b-112">Fetches the data corresponding to the module loaded at a given address.</span></span> |

## <a name="remarks"></a><span data-ttu-id="2d57b-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2d57b-113">Remarks</span></span>

<span data-ttu-id="2d57b-114">Toto rozhraní se nachází uvnitř modulu runtime a není dostupná záhlaví nebo soubory knihoven.</span><span class="sxs-lookup"><span data-stu-id="2d57b-114">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="2d57b-115">Je však rozhraní modelu COM, která je odvozena z `IUnknown` s identifikátorem GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` , který můžete získat prostřednictvím obvykle COM mechanismů.</span><span class="sxs-lookup"><span data-stu-id="2d57b-115">However, it's a COM interface that derives from `IUnknown` with GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="2d57b-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2d57b-116">Requirements</span></span>

<span data-ttu-id="2d57b-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d57b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="2d57b-118">**Záhlaví:** Žádné</span><span class="sxs-lookup"><span data-stu-id="2d57b-118">**Header:** None</span></span>  
<span data-ttu-id="2d57b-119">**Knihovna:** Žádné</span><span class="sxs-lookup"><span data-stu-id="2d57b-119">**Library:** None</span></span>  
<span data-ttu-id="2d57b-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2d57b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="2d57b-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d57b-121">See also</span></span>

- [<span data-ttu-id="2d57b-122">Ladění</span><span class="sxs-lookup"><span data-stu-id="2d57b-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="2d57b-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="2d57b-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
