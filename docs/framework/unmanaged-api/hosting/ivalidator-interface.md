---
title: "IValidator – rozhraní"
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
- IValidator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IValidator
helpviewer_keywords:
- IValidator interface [.NET Framework hosting]
ms.assetid: b297e3b0-20f9-478f-b707-5e2eecb2b5b2
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1afa255fa0b1baec35dbd8aa6e0beef62d240c31
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ivalidator-interface"></a><span data-ttu-id="c8a6f-102">IValidator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c8a6f-102">IValidator Interface</span></span>
<span data-ttu-id="c8a6f-103">Poskytuje metody pro ověřování přenosné spustitelné bitové kopie (PE) a vytváření sestav chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-103">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c8a6f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c8a6f-104">Methods</span></span>  
  
|<span data-ttu-id="c8a6f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c8a6f-105">Method</span></span>|<span data-ttu-id="c8a6f-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c8a6f-106">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="c8a6f-107">Ověření</span><span class="sxs-lookup"><span data-stu-id="c8a6f-107">Validate</span></span>|<span data-ttu-id="c8a6f-108">Ověří zadaný soubor PE nebo Microsoft (MSIL intermediate language).</span><span class="sxs-lookup"><span data-stu-id="c8a6f-108">Validates the specified PE or Microsoft intermediate language (MSIL) file.</span></span>|  
|<span data-ttu-id="c8a6f-109">Formateventinfo –</span><span class="sxs-lookup"><span data-stu-id="c8a6f-109">FormatEventInfo</span></span>|<span data-ttu-id="c8a6f-110">Získá chybovou zprávu odpovídající zadané chybě.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-110">Gets the error message corresponding to the specified validation error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c8a6f-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c8a6f-111">Requirements</span></span>  
 <span data-ttu-id="c8a6f-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8a6f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8a6f-113">**Záhlaví:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="c8a6f-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="c8a6f-114">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c8a6f-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c8a6f-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8a6f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8a6f-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="c8a6f-116">See Also</span></span>  
 [<span data-ttu-id="c8a6f-117">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="c8a6f-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="c8a6f-118">CorRuntimeHost – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="c8a6f-118">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
