---
title: "FExecuteInAppDomainCallback – ukazatel na funkci"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- FExecuteInAppDomainCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FExecuteInAppDomainCallback
helpviewer_keywords:
- FExecuteInAppDomainCallback function pointer [.NET Framework hosting]
ms.assetid: 2709f18f-3eee-497f-bc33-3ab7a485599b
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9852abbf2f69dda5c4c3b06f48adbd1bc33f5a1e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="fexecuteinappdomaincallback-function-pointer"></a><span data-ttu-id="48412-102">FExecuteInAppDomainCallback – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="48412-102">FExecuteInAppDomainCallback Function Pointer</span></span>
<span data-ttu-id="48412-103">Odkazuje na funkci, která je volána modulem common language runtime (CLR) k provedení spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="48412-103">Points to a function that is called by the common language runtime (CLR) to execute managed code.</span></span>  
  
 <span data-ttu-id="48412-104">Tento ukazatel na funkci se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="48412-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48412-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48412-105">Syntax</span></span>  
  
```  
typedef HRESULT (__stdcall *FExecuteInAppDomainCallback) (  
    [in] void  *cookie  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="48412-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="48412-106">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="48412-107">[v] Ukazatel na neprůhledné volající přidělené paměti, která obsahuje spravovaného kódu, které by šlo spustit.</span><span class="sxs-lookup"><span data-stu-id="48412-107">[in] A pointer to opaque caller-allocated memory that contains the managed code to be executed.</span></span>  
  
 <span data-ttu-id="48412-108">Přidělení a dobu života tuto paměť jsou řízeny volající (modulu CLR).</span><span class="sxs-lookup"><span data-stu-id="48412-108">The allocation and lifetime of this memory are controlled by the caller (that is, the CLR).</span></span> <span data-ttu-id="48412-109">Toto není CLR spravovaná halda paměti.</span><span class="sxs-lookup"><span data-stu-id="48412-109">This is not CLR managed-heap memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48412-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="48412-110">Requirements</span></span>  
 <span data-ttu-id="48412-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48412-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48412-112">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="48412-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="48412-113">**Knihovna:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="48412-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="48412-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48412-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48412-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="48412-115">See Also</span></span>  
 [<span data-ttu-id="48412-116">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="48412-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
