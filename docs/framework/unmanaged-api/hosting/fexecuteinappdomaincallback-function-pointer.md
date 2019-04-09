---
title: FExecuteInAppDomainCallback – ukazatel na funkci
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9981e97e3be58f6646612dc5c3a50a9e7650e376
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108443"
---
# <a name="fexecuteinappdomaincallback-function-pointer"></a><span data-ttu-id="f8f3b-102">FExecuteInAppDomainCallback – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="f8f3b-102">FExecuteInAppDomainCallback Function Pointer</span></span>
<span data-ttu-id="f8f3b-103">Odkazuje na funkci, která je volána modulem common language runtime (CLR) pro spuštění spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="f8f3b-103">Points to a function that is called by the common language runtime (CLR) to execute managed code.</span></span>  
  
 <span data-ttu-id="f8f3b-104">Tento ukazatel na funkci se už nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f8f3b-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8f3b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8f3b-105">Syntax</span></span>  
  
```  
typedef HRESULT (__stdcall *FExecuteInAppDomainCallback) (  
    [in] void  *cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8f3b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f8f3b-106">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="f8f3b-107">[in] Ukazatel na neprůhledné paměť přidělenou volajícímu, který obsahuje spravovaný kód, který se spustí.</span><span class="sxs-lookup"><span data-stu-id="f8f3b-107">[in] A pointer to opaque caller-allocated memory that contains the managed code to be executed.</span></span>  
  
 <span data-ttu-id="f8f3b-108">Přidělování a životnosti tato paměť se řídí volající (modulu CLR).</span><span class="sxs-lookup"><span data-stu-id="f8f3b-108">The allocation and lifetime of this memory are controlled by the caller (that is, the CLR).</span></span> <span data-ttu-id="f8f3b-109">Toto není spravované haldy paměti CLR.</span><span class="sxs-lookup"><span data-stu-id="f8f3b-109">This is not CLR managed-heap memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8f3b-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f8f3b-110">Requirements</span></span>  
 <span data-ttu-id="f8f3b-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8f3b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8f3b-112">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f8f3b-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f8f3b-113">**Knihovna:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="f8f3b-113">**Library:** MSCorWks.dll</span></span>  
  
 **<span data-ttu-id="f8f3b-114">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="f8f3b-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f8f3b-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f8f3b-115">See also</span></span>

- [<span data-ttu-id="f8f3b-116">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="f8f3b-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
