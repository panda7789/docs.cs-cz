---
title: "ICLRMetadataLocator – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a06997c47a85ced56dc579759192f7256def4f5a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmetadatalocator-interface"></a><span data-ttu-id="2bfb3-102">ICLRMetadataLocator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2bfb3-102">ICLRMetadataLocator Interface</span></span>
<span data-ttu-id="2bfb3-103">Používá vrstvy služby přístupu k datům v Cílový proces najít metadata sestavení.</span><span class="sxs-lookup"><span data-stu-id="2bfb3-103">Used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2bfb3-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2bfb3-104">Methods</span></span>  
  
|<span data-ttu-id="2bfb3-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2bfb3-105">Method</span></span>|<span data-ttu-id="2bfb3-106">Popis</span><span class="sxs-lookup"><span data-stu-id="2bfb3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2bfb3-107">GetMetadata – metoda</span><span class="sxs-lookup"><span data-stu-id="2bfb3-107">GetMetadata Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-getmetadata-method.md)|<span data-ttu-id="2bfb3-108">Načte metadata bitové kopie z tento cílový proces.</span><span class="sxs-lookup"><span data-stu-id="2bfb3-108">Retrieves the metadata of an image from the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2bfb3-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2bfb3-109">Remarks</span></span>  
 <span data-ttu-id="2bfb3-110">Klient API (tzn. ladicí program) musí implementovat toto rozhraní v závislosti na konkrétním cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="2bfb3-110">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="2bfb3-111">Implementace za provozu procesu by být například z výpis stavu paměti.</span><span class="sxs-lookup"><span data-stu-id="2bfb3-111">For example, the implementation for a live process would be different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bfb3-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2bfb3-112">Requirements</span></span>  
 <span data-ttu-id="2bfb3-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bfb3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bfb3-114">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="2bfb3-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="2bfb3-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2bfb3-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2bfb3-116">**.**</span><span class="sxs-lookup"><span data-stu-id="2bfb3-116">**.**</span></span> <span data-ttu-id="2bfb3-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bfb3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bfb3-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="2bfb3-118">See Also</span></span>  
 [<span data-ttu-id="2bfb3-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="2bfb3-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
