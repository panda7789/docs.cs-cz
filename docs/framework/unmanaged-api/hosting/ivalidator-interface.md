---
title: IValidator – rozhraní
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2f516bf1f19e4d4a77e2d6af834a1c3d4e34c327
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765346"
---
# <a name="ivalidator-interface"></a><span data-ttu-id="8851d-102">IValidator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8851d-102">IValidator Interface</span></span>
<span data-ttu-id="8851d-103">Poskytuje metody pro ověřování přenosné spustitelné (PE) bitové kopie a oznamování chyb ověřování.</span><span class="sxs-lookup"><span data-stu-id="8851d-103">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8851d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8851d-104">Methods</span></span>  
  
|<span data-ttu-id="8851d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8851d-105">Method</span></span>|<span data-ttu-id="8851d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="8851d-106">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="8851d-107">Ověření</span><span class="sxs-lookup"><span data-stu-id="8851d-107">Validate</span></span>|<span data-ttu-id="8851d-108">Ověří zadaný soubor PE nebo Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="8851d-108">Validates the specified PE or Microsoft intermediate language (MSIL) file.</span></span>|  
|<span data-ttu-id="8851d-109">FormatEventInfo</span><span class="sxs-lookup"><span data-stu-id="8851d-109">FormatEventInfo</span></span>|<span data-ttu-id="8851d-110">Získá odpovídající zadaným ověřovéní chybovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="8851d-110">Gets the error message corresponding to the specified validation error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8851d-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8851d-111">Requirements</span></span>  
 <span data-ttu-id="8851d-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8851d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8851d-113">**Záhlaví:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="8851d-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="8851d-114">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8851d-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8851d-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8851d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8851d-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8851d-116">See also</span></span>

- [<span data-ttu-id="8851d-117">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="8851d-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="8851d-118">CorRuntimeHost – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="8851d-118">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
