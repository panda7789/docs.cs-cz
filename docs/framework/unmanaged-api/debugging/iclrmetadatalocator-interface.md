---
title: ICLRMetadataLocator – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRMetadataLocator
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRMetadataLocator
helpviewer_keywords:
- ICLRMetadataLocator interface [.NET Framework debugging]
ms.assetid: 43c944f4-406a-4df6-981e-0eabb33dd5d0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ddc0429a6fa921e8e6ba3c55f3efe5373bea9576
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59123770"
---
# <a name="iclrmetadatalocator-interface"></a><span data-ttu-id="48a30-102">ICLRMetadataLocator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="48a30-102">ICLRMetadataLocator Interface</span></span>
<span data-ttu-id="48a30-103">Používaná vrstvou služeb přístupu k data k nalezení metadata sestavení v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="48a30-103">Used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="48a30-104">Metody</span><span class="sxs-lookup"><span data-stu-id="48a30-104">Methods</span></span>  
  
|<span data-ttu-id="48a30-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="48a30-105">Method</span></span>|<span data-ttu-id="48a30-106">Popis</span><span class="sxs-lookup"><span data-stu-id="48a30-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="48a30-107">GetMetadata – metoda</span><span class="sxs-lookup"><span data-stu-id="48a30-107">GetMetadata Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-getmetadata-method.md)|<span data-ttu-id="48a30-108">Načte metadata obrázek z cílového procesu.</span><span class="sxs-lookup"><span data-stu-id="48a30-108">Retrieves the metadata of an image from the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48a30-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="48a30-109">Remarks</span></span>  
 <span data-ttu-id="48a30-110">Klient API (tzn. ladicí program) musí implementovat toto rozhraní v závislosti na konkrétním cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="48a30-110">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="48a30-111">Implementace pro živý proces bude například liší od výpis paměti.</span><span class="sxs-lookup"><span data-stu-id="48a30-111">For example, the implementation for a live process would be different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48a30-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="48a30-112">Requirements</span></span>  
 <span data-ttu-id="48a30-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48a30-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48a30-114">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="48a30-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="48a30-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48a30-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48a30-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48a30-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48a30-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="48a30-117">See also</span></span>

- [<span data-ttu-id="48a30-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="48a30-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
