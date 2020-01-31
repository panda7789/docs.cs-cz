---
title: IXCLRDataModule – rozhraní
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
ms.openlocfilehash: 8757642db6c4375cf55d1f7288669c4c8a752a38
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790397"
---
# <a name="ixclrdatamodule-interface"></a><span data-ttu-id="e2977-102">IXCLRDataModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e2977-102">IXCLRDataModule Interface</span></span>

<span data-ttu-id="e2977-103">Poskytuje metody pro dotazování na informace o načteném modulu.</span><span class="sxs-lookup"><span data-stu-id="e2977-103">Provides methods for querying information about a loaded module.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="e2977-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e2977-104">Methods</span></span>

| <span data-ttu-id="e2977-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e2977-105">Method</span></span>                                                                                                                                | <span data-ttu-id="e2977-106">Popis</span><span class="sxs-lookup"><span data-stu-id="e2977-106">Description</span></span>                                                         |
| ------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="e2977-107">GetMethodDefinitionByToken</span><span class="sxs-lookup"><span data-stu-id="e2977-107">GetMethodDefinitionByToken</span></span>](ixclrdatamodule-getmethoddefinitionbytoken-method.md) | <span data-ttu-id="e2977-108">Získá definici metody odpovídající danému tokenu metadat.</span><span class="sxs-lookup"><span data-stu-id="e2977-108">Gets the method definition corresponding to a given metadata token.</span></span> |
| [<span data-ttu-id="e2977-109">Požadavek</span><span class="sxs-lookup"><span data-stu-id="e2977-109">Request</span></span>](ixclrdatamodule-request-method.md)                                       | <span data-ttu-id="e2977-110">Žádosti o naplnění vyrovnávací paměti dané daty modulu.</span><span class="sxs-lookup"><span data-stu-id="e2977-110">Requests to populate the buffer given with the module's data.</span></span>       |
| [<span data-ttu-id="e2977-111">GetVersionId</span><span class="sxs-lookup"><span data-stu-id="e2977-111">GetVersionId</span></span>](ixclrdatamodule-getversionid-method.md)                             | <span data-ttu-id="e2977-112">Získá ID verze modulu.</span><span class="sxs-lookup"><span data-stu-id="e2977-112">Gets the module's version ID.</span></span>                                       |

## <a name="remarks"></a><span data-ttu-id="e2977-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e2977-113">Remarks</span></span>

<span data-ttu-id="e2977-114">Toto rozhraní je v modulu runtime a není zveřejněné prostřednictvím hlaviček nebo souborů knihoven.</span><span class="sxs-lookup"><span data-stu-id="e2977-114">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="e2977-115">Jedná se však o rozhraní modelu COM, které je odvozeno od `IUnknown` s identifikátorem GUID `88E32849-0A0A-4cb0-9022-7CD2E9E139E2`, které lze získat prostřednictvím obvyklých mechanismů modelu COM.</span><span class="sxs-lookup"><span data-stu-id="e2977-115">However, it's a COM interface that derives from `IUnknown` with GUID `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="e2977-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e2977-116">Requirements</span></span>

<span data-ttu-id="e2977-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2977-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="e2977-118">**Hlavička:** NTato</span><span class="sxs-lookup"><span data-stu-id="e2977-118">**Header:** None</span></span>  
<span data-ttu-id="e2977-119">**Knihovna:** NTato</span><span class="sxs-lookup"><span data-stu-id="e2977-119">**Library:** None</span></span>  
<span data-ttu-id="e2977-120">**Verze .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e2977-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="e2977-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e2977-121">See also</span></span>

- [<span data-ttu-id="e2977-122">Ladění</span><span class="sxs-lookup"><span data-stu-id="e2977-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="e2977-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e2977-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
