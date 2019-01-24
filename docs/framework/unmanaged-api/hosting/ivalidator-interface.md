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
ms.openlocfilehash: 9f307ad5689602b030c609a51f6834bdbb0ec4f8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717711"
---
# <a name="ivalidator-interface"></a><span data-ttu-id="8daf9-102">IValidator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8daf9-102">IValidator Interface</span></span>
<span data-ttu-id="8daf9-103">Poskytuje metody pro ověřování přenosné spustitelné (PE) bitové kopie a oznamování chyb ověřování.</span><span class="sxs-lookup"><span data-stu-id="8daf9-103">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8daf9-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8daf9-104">Methods</span></span>  
  
|<span data-ttu-id="8daf9-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8daf9-105">Method</span></span>|<span data-ttu-id="8daf9-106">Popis</span><span class="sxs-lookup"><span data-stu-id="8daf9-106">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="8daf9-107">Ověření</span><span class="sxs-lookup"><span data-stu-id="8daf9-107">Validate</span></span>|<span data-ttu-id="8daf9-108">Ověří zadaný soubor PE nebo Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="8daf9-108">Validates the specified PE or Microsoft intermediate language (MSIL) file.</span></span>|  
|<span data-ttu-id="8daf9-109">FormatEventInfo</span><span class="sxs-lookup"><span data-stu-id="8daf9-109">FormatEventInfo</span></span>|<span data-ttu-id="8daf9-110">Získá odpovídající zadaným ověřovéní chybovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="8daf9-110">Gets the error message corresponding to the specified validation error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8daf9-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8daf9-111">Requirements</span></span>  
 <span data-ttu-id="8daf9-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8daf9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8daf9-113">**Záhlaví:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="8daf9-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="8daf9-114">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8daf9-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8daf9-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8daf9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8daf9-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8daf9-116">See also</span></span>
- [<span data-ttu-id="8daf9-117">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="8daf9-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="8daf9-118">CorRuntimeHost – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="8daf9-118">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
