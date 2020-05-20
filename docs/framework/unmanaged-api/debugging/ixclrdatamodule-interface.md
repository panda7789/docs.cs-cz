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
ms.openlocfilehash: 3c2bc771c0a131329b9403c99a33ca7b79023771
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420848"
---
# <a name="ixclrdatamodule-interface"></a><span data-ttu-id="fbb97-102">IXCLRDataModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fbb97-102">IXCLRDataModule Interface</span></span>

<span data-ttu-id="fbb97-103">Poskytuje metody pro dotazování na informace o načteném modulu.</span><span class="sxs-lookup"><span data-stu-id="fbb97-103">Provides methods for querying information about a loaded module.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="fbb97-104">Metody</span><span class="sxs-lookup"><span data-stu-id="fbb97-104">Methods</span></span>

| <span data-ttu-id="fbb97-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="fbb97-105">Method</span></span>                                                                                                                                | <span data-ttu-id="fbb97-106">Popis</span><span class="sxs-lookup"><span data-stu-id="fbb97-106">Description</span></span>                                                         |
| ------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="fbb97-107">GetMethodDefinitionByToken</span><span class="sxs-lookup"><span data-stu-id="fbb97-107">GetMethodDefinitionByToken</span></span>](ixclrdatamodule-getmethoddefinitionbytoken-method.md) | <span data-ttu-id="fbb97-108">Získá definici metody odpovídající danému tokenu metadat.</span><span class="sxs-lookup"><span data-stu-id="fbb97-108">Gets the method definition corresponding to a given metadata token.</span></span> |
| [<span data-ttu-id="fbb97-109">Žádost</span><span class="sxs-lookup"><span data-stu-id="fbb97-109">Request</span></span>](ixclrdatamodule-request-method.md)                                       | <span data-ttu-id="fbb97-110">Žádosti o naplnění vyrovnávací paměti dané daty modulu.</span><span class="sxs-lookup"><span data-stu-id="fbb97-110">Requests to populate the buffer given with the module's data.</span></span>       |
| [<span data-ttu-id="fbb97-111">GetVersionId</span><span class="sxs-lookup"><span data-stu-id="fbb97-111">GetVersionId</span></span>](ixclrdatamodule-getversionid-method.md)                             | <span data-ttu-id="fbb97-112">Získá ID verze modulu.</span><span class="sxs-lookup"><span data-stu-id="fbb97-112">Gets the module's version ID.</span></span>                                       |

## <a name="remarks"></a><span data-ttu-id="fbb97-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fbb97-113">Remarks</span></span>

<span data-ttu-id="fbb97-114">Toto rozhraní je v modulu runtime a není zveřejněné prostřednictvím hlaviček nebo souborů knihoven.</span><span class="sxs-lookup"><span data-stu-id="fbb97-114">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="fbb97-115">Jedná se však o rozhraní modelu COM, které je odvozeno z `IUnknown` identifikátoru GUID `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` , který lze získat prostřednictvím obvyklých mechanismů modelu COM.</span><span class="sxs-lookup"><span data-stu-id="fbb97-115">However, it's a COM interface that derives from `IUnknown` with GUID `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="fbb97-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fbb97-116">Requirements</span></span>

<span data-ttu-id="fbb97-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbb97-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="fbb97-118">**Hlavička:** NTato</span><span class="sxs-lookup"><span data-stu-id="fbb97-118">**Header:** None</span></span>  
<span data-ttu-id="fbb97-119">**Knihovna:** NTato</span><span class="sxs-lookup"><span data-stu-id="fbb97-119">**Library:** None</span></span>  
<span data-ttu-id="fbb97-120">**Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="fbb97-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="fbb97-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="fbb97-121">See also</span></span>

- [<span data-ttu-id="fbb97-122">Ladění</span><span class="sxs-lookup"><span data-stu-id="fbb97-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="fbb97-123">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fbb97-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
