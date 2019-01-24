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
ms.openlocfilehash: 5d1d767de88b239c96cb98130b6ff006e3f75b09
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54495029"
---
# <a name="iclrmetadatalocator-interface"></a><span data-ttu-id="3cf56-102">ICLRMetadataLocator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3cf56-102">ICLRMetadataLocator Interface</span></span>
<span data-ttu-id="3cf56-103">Používaná vrstvou služeb přístupu k data k nalezení metadata sestavení v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="3cf56-103">Used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3cf56-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3cf56-104">Methods</span></span>  
  
|<span data-ttu-id="3cf56-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3cf56-105">Method</span></span>|<span data-ttu-id="3cf56-106">Popis</span><span class="sxs-lookup"><span data-stu-id="3cf56-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3cf56-107">GetMetadata – metoda</span><span class="sxs-lookup"><span data-stu-id="3cf56-107">GetMetadata Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-getmetadata-method.md)|<span data-ttu-id="3cf56-108">Načte metadata obrázek z cílového procesu.</span><span class="sxs-lookup"><span data-stu-id="3cf56-108">Retrieves the metadata of an image from the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3cf56-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3cf56-109">Remarks</span></span>  
 <span data-ttu-id="3cf56-110">Klient API (tzn. ladicí program) musí implementovat toto rozhraní v závislosti na konkrétním cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="3cf56-110">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="3cf56-111">Implementace pro živý proces bude například liší od výpis paměti.</span><span class="sxs-lookup"><span data-stu-id="3cf56-111">For example, the implementation for a live process would be different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cf56-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3cf56-112">Requirements</span></span>  
 <span data-ttu-id="3cf56-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3cf56-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3cf56-114">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="3cf56-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="3cf56-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3cf56-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3cf56-116">**.**</span><span class="sxs-lookup"><span data-stu-id="3cf56-116">**.**</span></span> <span data-ttu-id="3cf56-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cf56-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cf56-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3cf56-118">See also</span></span>
- [<span data-ttu-id="3cf56-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="3cf56-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
