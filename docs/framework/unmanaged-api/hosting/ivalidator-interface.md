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
ms.openlocfilehash: d8e5ab607f9310341ded482b35f02f3845926328
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008557"
---
# <a name="ivalidator-interface"></a><span data-ttu-id="270e7-102">IValidator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="270e7-102">IValidator Interface</span></span>
<span data-ttu-id="270e7-103">Poskytuje metody pro ověřování přenosných spustitelných souborů (PE) a chyb ověřování sestav.</span><span class="sxs-lookup"><span data-stu-id="270e7-103">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="270e7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="270e7-104">Methods</span></span>  
  
|<span data-ttu-id="270e7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="270e7-105">Method</span></span>|<span data-ttu-id="270e7-106">Description</span><span class="sxs-lookup"><span data-stu-id="270e7-106">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="270e7-107">Ověření</span><span class="sxs-lookup"><span data-stu-id="270e7-107">Validate</span></span>|<span data-ttu-id="270e7-108">Ověří zadané soubory PE nebo jazyka MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="270e7-108">Validates the specified PE or Microsoft intermediate language (MSIL) file.</span></span>|  
|<span data-ttu-id="270e7-109">Formateventinfo –</span><span class="sxs-lookup"><span data-stu-id="270e7-109">FormatEventInfo</span></span>|<span data-ttu-id="270e7-110">Načte chybovou zprávu odpovídající zadané chybě ověřování.</span><span class="sxs-lookup"><span data-stu-id="270e7-110">Gets the error message corresponding to the specified validation error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="270e7-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="270e7-111">Requirements</span></span>  
 <span data-ttu-id="270e7-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="270e7-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="270e7-113">**Hlavička:** IValidator. idl, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="270e7-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="270e7-114">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="270e7-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="270e7-115">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="270e7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="270e7-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="270e7-116">See also</span></span>

- [<span data-ttu-id="270e7-117">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="270e7-117">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="270e7-118">CorRuntimeHost – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="270e7-118">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
