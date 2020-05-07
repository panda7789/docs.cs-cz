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
ms.openlocfilehash: 734f8eaa7c520bbf1ad1208ece42751e967a208a
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859729"
---
# <a name="iclrmetadatalocator-interface"></a><span data-ttu-id="1499d-102">ICLRMetadataLocator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1499d-102">ICLRMetadataLocator Interface</span></span>
<span data-ttu-id="1499d-103">Používá se ve vrstvě služeb Data Access k vyhledání metadat sestavení v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="1499d-103">Used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1499d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1499d-104">Methods</span></span>  
  
|<span data-ttu-id="1499d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1499d-105">Method</span></span>|<span data-ttu-id="1499d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="1499d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1499d-107">GetMetadata – metoda</span><span class="sxs-lookup"><span data-stu-id="1499d-107">GetMetadata Method</span></span>](iclrmetadatalocator-getmetadata-method.md)|<span data-ttu-id="1499d-108">Načte metadata obrázku z cílového procesu.</span><span class="sxs-lookup"><span data-stu-id="1499d-108">Retrieves the metadata of an image from the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1499d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1499d-109">Remarks</span></span>  
 <span data-ttu-id="1499d-110">Klient API (tzn. ladicí program) musí implementovat toto rozhraní v závislosti na konkrétním cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="1499d-110">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="1499d-111">Například implementace pro živý proces se liší od výpisu paměti.</span><span class="sxs-lookup"><span data-stu-id="1499d-111">For example, the implementation for a live process would be different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1499d-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1499d-112">Requirements</span></span>  
 <span data-ttu-id="1499d-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1499d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1499d-114">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="1499d-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="1499d-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1499d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1499d-116">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1499d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1499d-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="1499d-117">See also</span></span>

- [<span data-ttu-id="1499d-118">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1499d-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
