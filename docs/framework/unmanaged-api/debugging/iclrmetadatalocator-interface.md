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
ms.openlocfilehash: e5dd77783c03d6a61d0b5831e44db97a731d8074
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/07/2019
ms.locfileid: "55825885"
---
# <a name="iclrmetadatalocator-interface"></a><span data-ttu-id="dcb24-102">ICLRMetadataLocator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dcb24-102">ICLRMetadataLocator Interface</span></span>
<span data-ttu-id="dcb24-103">Používaná vrstvou služeb přístupu k data k nalezení metadata sestavení v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="dcb24-103">Used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dcb24-104">Metody</span><span class="sxs-lookup"><span data-stu-id="dcb24-104">Methods</span></span>  
  
|<span data-ttu-id="dcb24-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="dcb24-105">Method</span></span>|<span data-ttu-id="dcb24-106">Popis</span><span class="sxs-lookup"><span data-stu-id="dcb24-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dcb24-107">GetMetadata – metoda</span><span class="sxs-lookup"><span data-stu-id="dcb24-107">GetMetadata Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-getmetadata-method.md)|<span data-ttu-id="dcb24-108">Načte metadata obrázek z cílového procesu.</span><span class="sxs-lookup"><span data-stu-id="dcb24-108">Retrieves the metadata of an image from the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dcb24-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dcb24-109">Remarks</span></span>  
 <span data-ttu-id="dcb24-110">Klient API (tzn. ladicí program) musí implementovat toto rozhraní v závislosti na konkrétním cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="dcb24-110">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="dcb24-111">Implementace pro živý proces bude například liší od výpis paměti.</span><span class="sxs-lookup"><span data-stu-id="dcb24-111">For example, the implementation for a live process would be different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcb24-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dcb24-112">Requirements</span></span>  
 <span data-ttu-id="dcb24-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcb24-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcb24-114">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="dcb24-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="dcb24-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dcb24-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dcb24-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcb24-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcb24-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dcb24-117">See also</span></span>
- [<span data-ttu-id="dcb24-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="dcb24-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
