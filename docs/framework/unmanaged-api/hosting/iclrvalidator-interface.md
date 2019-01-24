---
title: ICLRValidator – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRValidator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator
helpviewer_keywords:
- ICLRValidator interface [.NET Framework hosting]
ms.assetid: 2edd0a10-77fb-4173-91eb-f2970cc364d0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6f34a9aac31fe50974a6f88416d0a00cd72aca8e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54511927"
---
# <a name="iclrvalidator-interface"></a><span data-ttu-id="c5847-102">ICLRValidator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c5847-102">ICLRValidator Interface</span></span>
<span data-ttu-id="c5847-103">Poskytuje metody pro ověřování přenosné spustitelné (PE) bitové kopie a oznamování chyb ověřování.</span><span class="sxs-lookup"><span data-stu-id="c5847-103">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c5847-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c5847-104">Methods</span></span>  
  
|<span data-ttu-id="c5847-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c5847-105">Method</span></span>|<span data-ttu-id="c5847-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c5847-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c5847-107">FormatEventInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="c5847-107">FormatEventInfo Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-formateventinfo-method.md)|<span data-ttu-id="c5847-108">Získá podrobnou zprávu o chybě ověření pro zadané.</span><span class="sxs-lookup"><span data-stu-id="c5847-108">Gets a detailed message about the specified validation error.</span></span>|  
|[<span data-ttu-id="c5847-109">Validate – metoda</span><span class="sxs-lookup"><span data-stu-id="c5847-109">Validate Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md)|<span data-ttu-id="c5847-110">Ověří přenosný spustitelný soubor nebo jazyk Microsoft intermediate language (MSIL) do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="c5847-110">Validates the portable executable or Microsoft intermediate language (MSIL) in the specified file.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c5847-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c5847-111">Requirements</span></span>  
 <span data-ttu-id="c5847-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5847-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5847-113">**Záhlaví:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="c5847-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="c5847-114">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c5847-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c5847-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5847-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5847-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c5847-116">See also</span></span>
- [<span data-ttu-id="c5847-117">ICLRErrorReportingManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c5847-117">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="c5847-118">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="c5847-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="c5847-119">CLRRuntimeHost – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="c5847-119">CLRRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
