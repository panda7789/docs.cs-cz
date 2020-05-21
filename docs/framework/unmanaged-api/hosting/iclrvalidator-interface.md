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
ms.openlocfilehash: e071f9cba7e991c59bf697647e0e4badea57573a
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762029"
---
# <a name="iclrvalidator-interface"></a><span data-ttu-id="a0c8f-102">ICLRValidator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a0c8f-102">ICLRValidator Interface</span></span>
<span data-ttu-id="a0c8f-103">Poskytuje metody pro ověřování přenosných spustitelných souborů (PE) a chyb ověřování sestav.</span><span class="sxs-lookup"><span data-stu-id="a0c8f-103">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a0c8f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a0c8f-104">Methods</span></span>  
  
|<span data-ttu-id="a0c8f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a0c8f-105">Method</span></span>|<span data-ttu-id="a0c8f-106">Popis</span><span class="sxs-lookup"><span data-stu-id="a0c8f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a0c8f-107">FormatEventInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="a0c8f-107">FormatEventInfo Method</span></span>](iclrvalidator-formateventinfo-method.md)|<span data-ttu-id="a0c8f-108">Získá podrobnou zprávu o zadané chybě ověřování.</span><span class="sxs-lookup"><span data-stu-id="a0c8f-108">Gets a detailed message about the specified validation error.</span></span>|  
|[<span data-ttu-id="a0c8f-109">Validate – metoda</span><span class="sxs-lookup"><span data-stu-id="a0c8f-109">Validate Method</span></span>](iclrvalidator-validate-method.md)|<span data-ttu-id="a0c8f-110">Ověří v zadaném souboru přenositelné spustitelné soubory nebo jazyk MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="a0c8f-110">Validates the portable executable or Microsoft intermediate language (MSIL) in the specified file.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a0c8f-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a0c8f-111">Requirements</span></span>  
 <span data-ttu-id="a0c8f-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0c8f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0c8f-113">**Hlavička:** IValidator. idl, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="a0c8f-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="a0c8f-114">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a0c8f-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a0c8f-115">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0c8f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0c8f-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0c8f-116">See also</span></span>

- [<span data-ttu-id="a0c8f-117">ICLRErrorReportingManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a0c8f-117">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="a0c8f-118">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="a0c8f-118">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="a0c8f-119">CLRRuntimeHost – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="a0c8f-119">CLRRuntimeHost Coclass</span></span>](clrruntimehost-coclass.md)
