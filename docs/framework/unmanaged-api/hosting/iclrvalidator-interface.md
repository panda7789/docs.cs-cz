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
ms.openlocfilehash: 05287d3674e55a87cfe359fc08f74fa46000d79f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763296"
---
# <a name="iclrvalidator-interface"></a><span data-ttu-id="192cf-102">ICLRValidator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="192cf-102">ICLRValidator Interface</span></span>
<span data-ttu-id="192cf-103">Poskytuje metody pro ověřování přenosné spustitelné (PE) bitové kopie a oznamování chyb ověřování.</span><span class="sxs-lookup"><span data-stu-id="192cf-103">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="192cf-104">Metody</span><span class="sxs-lookup"><span data-stu-id="192cf-104">Methods</span></span>  
  
|<span data-ttu-id="192cf-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="192cf-105">Method</span></span>|<span data-ttu-id="192cf-106">Popis</span><span class="sxs-lookup"><span data-stu-id="192cf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="192cf-107">FormatEventInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="192cf-107">FormatEventInfo Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-formateventinfo-method.md)|<span data-ttu-id="192cf-108">Získá podrobnou zprávu o chybě ověření pro zadané.</span><span class="sxs-lookup"><span data-stu-id="192cf-108">Gets a detailed message about the specified validation error.</span></span>|  
|[<span data-ttu-id="192cf-109">Validate – metoda</span><span class="sxs-lookup"><span data-stu-id="192cf-109">Validate Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md)|<span data-ttu-id="192cf-110">Ověří přenosný spustitelný soubor nebo jazyk Microsoft intermediate language (MSIL) do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="192cf-110">Validates the portable executable or Microsoft intermediate language (MSIL) in the specified file.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="192cf-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="192cf-111">Requirements</span></span>  
 <span data-ttu-id="192cf-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="192cf-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="192cf-113">**Záhlaví:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="192cf-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="192cf-114">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="192cf-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="192cf-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="192cf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="192cf-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="192cf-116">See also</span></span>

- [<span data-ttu-id="192cf-117">ICLRErrorReportingManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="192cf-117">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="192cf-118">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="192cf-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="192cf-119">CLRRuntimeHost – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="192cf-119">CLRRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
