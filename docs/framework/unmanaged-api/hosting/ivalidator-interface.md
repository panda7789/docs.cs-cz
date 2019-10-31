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
ms.openlocfilehash: 1a732e59d539c330f91e8665e81dc4771b40e2d0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123289"
---
# <a name="ivalidator-interface"></a><span data-ttu-id="5b5da-102">IValidator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5b5da-102">IValidator Interface</span></span>
<span data-ttu-id="5b5da-103">Poskytuje metody pro ověřování přenosných spustitelných souborů (PE) a chyb ověřování sestav.</span><span class="sxs-lookup"><span data-stu-id="5b5da-103">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5b5da-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5b5da-104">Methods</span></span>  
  
|<span data-ttu-id="5b5da-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5b5da-105">Method</span></span>|<span data-ttu-id="5b5da-106">Popis</span><span class="sxs-lookup"><span data-stu-id="5b5da-106">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="5b5da-107">Oproti</span><span class="sxs-lookup"><span data-stu-id="5b5da-107">Validate</span></span>|<span data-ttu-id="5b5da-108">Ověří zadané soubory PE nebo jazyka MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="5b5da-108">Validates the specified PE or Microsoft intermediate language (MSIL) file.</span></span>|  
|<span data-ttu-id="5b5da-109">Formateventinfo –</span><span class="sxs-lookup"><span data-stu-id="5b5da-109">FormatEventInfo</span></span>|<span data-ttu-id="5b5da-110">Načte chybovou zprávu odpovídající zadané chybě ověřování.</span><span class="sxs-lookup"><span data-stu-id="5b5da-110">Gets the error message corresponding to the specified validation error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5b5da-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5b5da-111">Requirements</span></span>  
 <span data-ttu-id="5b5da-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b5da-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b5da-113">**Hlavička:** IValidator. idl, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="5b5da-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="5b5da-114">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5b5da-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5b5da-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b5da-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b5da-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5b5da-116">See also</span></span>

- [<span data-ttu-id="5b5da-117">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="5b5da-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="5b5da-118">CorRuntimeHost – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="5b5da-118">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
