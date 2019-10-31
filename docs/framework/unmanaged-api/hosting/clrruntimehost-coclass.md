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
ms.openlocfilehash: b1e595e1a4f1b462437f47207b998829a8bd774d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129456"
---
# <a name="clrruntimehost-coclass"></a><span data-ttu-id="4cf66-102">CLRRuntimeHost – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="4cf66-102">CLRRuntimeHost Coclass</span></span>
<span data-ttu-id="4cf66-103">Poskytuje rozhraní pro správu provádění kódu modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="4cf66-103">Provides interfaces for managing code execution by the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cf66-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4cf66-104">Syntax</span></span>  
  
```cpp  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="4cf66-105">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="4cf66-105">Interfaces</span></span>  
  
|<span data-ttu-id="4cf66-106">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="4cf66-106">Interface</span></span>|<span data-ttu-id="4cf66-107">Popis</span><span class="sxs-lookup"><span data-stu-id="4cf66-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="4cf66-108">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4cf66-108">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)|<span data-ttu-id="4cf66-109">Poskytuje metody pro řízení provádění aplikací modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="4cf66-109">Provides methods for controlling the execution of applications by the runtime.</span></span>|  
|[<span data-ttu-id="4cf66-110">ICLRValidator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4cf66-110">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)|<span data-ttu-id="4cf66-111">Poskytuje metody pro ověření přenosných spustitelných imagí a podrobné hlášení chyb ověřování.</span><span class="sxs-lookup"><span data-stu-id="4cf66-111">Provides methods for validation of portable executable images and for detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4cf66-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4cf66-112">Requirements</span></span>  
 <span data-ttu-id="4cf66-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4cf66-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cf66-114">**Hlavička:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="4cf66-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="4cf66-115">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4cf66-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4cf66-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4cf66-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cf66-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4cf66-117">See also</span></span>

- [<span data-ttu-id="4cf66-118">Třídy typu coclass pro hostování</span><span class="sxs-lookup"><span data-stu-id="4cf66-118">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
