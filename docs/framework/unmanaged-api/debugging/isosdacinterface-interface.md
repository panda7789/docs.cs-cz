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
ms.openlocfilehash: 94349a3f7b18c8ce29bb3a71cb9d10ee4eac8036
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790483"
---
# <a name="isosdacinterface-interface"></a><span data-ttu-id="e7682-102">ISOSDacInterface – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e7682-102">ISOSDacInterface Interface</span></span>

<span data-ttu-id="e7682-103">Poskytuje pomocné metody pro přístup k datům z `SOS`.</span><span class="sxs-lookup"><span data-stu-id="e7682-103">Provides helper methods to access data from `SOS`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="e7682-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e7682-104">Methods</span></span>

| <span data-ttu-id="e7682-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e7682-105">Method</span></span>                                                                                                               | <span data-ttu-id="e7682-106">Popis</span><span class="sxs-lookup"><span data-stu-id="e7682-106">Description</span></span>                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="e7682-107">GetMethodDescData</span><span class="sxs-lookup"><span data-stu-id="e7682-107">GetMethodDescData</span></span>](isosdacinterface-getmethoddescdata-method.md) | <span data-ttu-id="e7682-108">Načte data pro daný ukazatel MethodDesc.</span><span class="sxs-lookup"><span data-stu-id="e7682-108">Gets the data for the given MethodDesc pointer.</span></span> |
| [<span data-ttu-id="e7682-109">GetMethodDescPtrFromIP</span><span class="sxs-lookup"><span data-stu-id="e7682-109">GetMethodDescPtrFromIP</span></span>](isosdacinterface-getmethoddescptrfromip-method.md) | <span data-ttu-id="e7682-110">Načte ukazatel MethodDesc odpovídající metodě, která obsahuje danou adresu nativní instrukce.</span><span class="sxs-lookup"><span data-stu-id="e7682-110">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span> |
| [<span data-ttu-id="e7682-111">GetModuleData</span><span class="sxs-lookup"><span data-stu-id="e7682-111">GetModuleData</span></span>](isosdacinterface-getmoduledata-method.md)| <span data-ttu-id="e7682-112">Načte data odpovídající modulu načtenému na dané adrese.</span><span class="sxs-lookup"><span data-stu-id="e7682-112">Fetches the data corresponding to the module loaded at a given address.</span></span> |

## <a name="remarks"></a><span data-ttu-id="e7682-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e7682-113">Remarks</span></span>

<span data-ttu-id="e7682-114">Toto rozhraní je v modulu runtime a není zveřejněné prostřednictvím hlaviček nebo souborů knihoven.</span><span class="sxs-lookup"><span data-stu-id="e7682-114">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="e7682-115">Jedná se však o rozhraní modelu COM, které je odvozeno od `IUnknown` s identifikátorem GUID `436f00f2-b42a-4b9f-870c-e73db66ae930`, které lze získat prostřednictvím obvyklých mechanismů modelu COM.</span><span class="sxs-lookup"><span data-stu-id="e7682-115">However, it's a COM interface that derives from `IUnknown` with GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="e7682-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e7682-116">Requirements</span></span>

<span data-ttu-id="e7682-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7682-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="e7682-118">**Hlavička:** NTato</span><span class="sxs-lookup"><span data-stu-id="e7682-118">**Header:** None</span></span>  
<span data-ttu-id="e7682-119">**Knihovna:** NTato</span><span class="sxs-lookup"><span data-stu-id="e7682-119">**Library:** None</span></span>  
<span data-ttu-id="e7682-120">**Verze .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e7682-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e7682-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e7682-121">See also</span></span>

- [<span data-ttu-id="e7682-122">Ladění</span><span class="sxs-lookup"><span data-stu-id="e7682-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="e7682-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e7682-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
