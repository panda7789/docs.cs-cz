---
title: "IValidator – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IValidator
api_location: mscoree.dll
api_type: COM
f1_keywords: IValidator
helpviewer_keywords: IValidator interface [.NET Framework hosting]
ms.assetid: b297e3b0-20f9-478f-b707-5e2eecb2b5b2
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7d88bfa0a3e71f34a7439e97f4347a06aa2c4058
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ivalidator-interface"></a><span data-ttu-id="69570-102">IValidator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="69570-102">IValidator Interface</span></span>
<span data-ttu-id="69570-103">Poskytuje metody pro ověřování přenosné spustitelné bitové kopie (PE) a vytváření sestav chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="69570-103">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="69570-104">Metody</span><span class="sxs-lookup"><span data-stu-id="69570-104">Methods</span></span>  
  
|<span data-ttu-id="69570-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="69570-105">Method</span></span>|<span data-ttu-id="69570-106">Popis</span><span class="sxs-lookup"><span data-stu-id="69570-106">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="69570-107">Ověření</span><span class="sxs-lookup"><span data-stu-id="69570-107">Validate</span></span>|<span data-ttu-id="69570-108">Ověří zadaný soubor PE nebo Microsoft (MSIL intermediate language).</span><span class="sxs-lookup"><span data-stu-id="69570-108">Validates the specified PE or Microsoft intermediate language (MSIL) file.</span></span>|  
|<span data-ttu-id="69570-109">Formateventinfo –</span><span class="sxs-lookup"><span data-stu-id="69570-109">FormatEventInfo</span></span>|<span data-ttu-id="69570-110">Získá chybovou zprávu odpovídající zadané chybě.</span><span class="sxs-lookup"><span data-stu-id="69570-110">Gets the error message corresponding to the specified validation error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="69570-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="69570-111">Requirements</span></span>  
 <span data-ttu-id="69570-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69570-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69570-113">**Záhlaví:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="69570-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="69570-114">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="69570-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="69570-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69570-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69570-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="69570-116">See Also</span></span>  
 [<span data-ttu-id="69570-117">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="69570-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="69570-118">Corruntimehost – třída typu Coclass</span><span class="sxs-lookup"><span data-stu-id="69570-118">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
