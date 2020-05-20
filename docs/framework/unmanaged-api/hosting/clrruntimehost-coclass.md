---
title: CLRRuntimeHost – třída typu coclass
ms.date: 03/30/2017
api_name:
- CLRRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CLRRuntimeHost
helpviewer_keywords:
- CLRRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 2ac9cbf5-8a2d-4e4f-8831-0dad8ef0a897
topic_type:
- apiref
ms.openlocfilehash: 40766ce5837053493f2e3f1f25fe7d1d63ec695f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616798"
---
# <a name="clrruntimehost-coclass"></a><span data-ttu-id="2fa5b-102">CLRRuntimeHost – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="2fa5b-102">CLRRuntimeHost Coclass</span></span>
<span data-ttu-id="2fa5b-103">Poskytuje rozhraní pro správu provádění kódu modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="2fa5b-103">Provides interfaces for managing code execution by the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fa5b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2fa5b-104">Syntax</span></span>  
  
```cpp  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="2fa5b-105">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="2fa5b-105">Interfaces</span></span>  
  
|<span data-ttu-id="2fa5b-106">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="2fa5b-106">Interface</span></span>|<span data-ttu-id="2fa5b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2fa5b-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="2fa5b-108">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2fa5b-108">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)|<span data-ttu-id="2fa5b-109">Poskytuje metody pro řízení provádění aplikací modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="2fa5b-109">Provides methods for controlling the execution of applications by the runtime.</span></span>|  
|[<span data-ttu-id="2fa5b-110">ICLRValidator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2fa5b-110">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)|<span data-ttu-id="2fa5b-111">Poskytuje metody pro ověření přenosných spustitelných imagí a podrobné hlášení chyb ověřování.</span><span class="sxs-lookup"><span data-stu-id="2fa5b-111">Provides methods for validation of portable executable images and for detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2fa5b-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2fa5b-112">Requirements</span></span>  
 <span data-ttu-id="2fa5b-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fa5b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fa5b-114">**Hlavička:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="2fa5b-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="2fa5b-115">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2fa5b-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2fa5b-116">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fa5b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fa5b-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="2fa5b-117">See also</span></span>

- [<span data-ttu-id="2fa5b-118">Třídy typu coclass hostování</span><span class="sxs-lookup"><span data-stu-id="2fa5b-118">Hosting Coclasses</span></span>](hosting-coclasses.md)
