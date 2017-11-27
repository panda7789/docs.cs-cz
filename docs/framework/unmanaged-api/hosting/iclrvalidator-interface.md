---
title: "ICLRValidator – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRValidator
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRValidator
helpviewer_keywords: ICLRValidator interface [.NET Framework hosting]
ms.assetid: 2edd0a10-77fb-4173-91eb-f2970cc364d0
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0057be1457ad369b84f311008180dc7c4a3c323d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrvalidator-interface"></a><span data-ttu-id="90055-102">ICLRValidator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="90055-102">ICLRValidator Interface</span></span>
<span data-ttu-id="90055-103">Poskytuje metody pro ověřování přenosné spustitelné bitové kopie (PE) a vytváření sestav chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="90055-103">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="90055-104">Metody</span><span class="sxs-lookup"><span data-stu-id="90055-104">Methods</span></span>  
  
|<span data-ttu-id="90055-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="90055-105">Method</span></span>|<span data-ttu-id="90055-106">Popis</span><span class="sxs-lookup"><span data-stu-id="90055-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="90055-107">Formateventinfo – metoda</span><span class="sxs-lookup"><span data-stu-id="90055-107">FormatEventInfo Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-formateventinfo-method.md)|<span data-ttu-id="90055-108">Získá podrobná zpráva o chybě zadaný ověření.</span><span class="sxs-lookup"><span data-stu-id="90055-108">Gets a detailed message about the specified validation error.</span></span>|  
|[<span data-ttu-id="90055-109">Validate – metoda</span><span class="sxs-lookup"><span data-stu-id="90055-109">Validate Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md)|<span data-ttu-id="90055-110">Ověří přenosné spustitelný soubor nebo Microsoft (MSIL intermediate language) do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="90055-110">Validates the portable executable or Microsoft intermediate language (MSIL) in the specified file.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="90055-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="90055-111">Requirements</span></span>  
 <span data-ttu-id="90055-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90055-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90055-113">**Záhlaví:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="90055-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="90055-114">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="90055-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="90055-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90055-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90055-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="90055-116">See Also</span></span>  
 [<span data-ttu-id="90055-117">Iclrerrorreportingmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="90055-117">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 [<span data-ttu-id="90055-118">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="90055-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="90055-119">Clrruntimehost – třída typu Coclass</span><span class="sxs-lookup"><span data-stu-id="90055-119">CLRRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
