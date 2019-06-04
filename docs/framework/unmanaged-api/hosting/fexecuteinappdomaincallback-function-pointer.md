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
ms.openlocfilehash: 26b3de456bc28f51cb20ab72b3934041ec6b06ae
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490453"
---
# <a name="fexecuteinappdomaincallback-function-pointer"></a><span data-ttu-id="815eb-102">FExecuteInAppDomainCallback – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="815eb-102">FExecuteInAppDomainCallback Function Pointer</span></span>
<span data-ttu-id="815eb-103">Odkazuje na funkci, která je volána modulem common language runtime (CLR) pro spuštění spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="815eb-103">Points to a function that is called by the common language runtime (CLR) to execute managed code.</span></span>  
  
 <span data-ttu-id="815eb-104">Tento ukazatel na funkci se již nepoužívá v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="815eb-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="815eb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="815eb-105">Syntax</span></span>  
  
```  
typedef HRESULT (__stdcall *FExecuteInAppDomainCallback) (  
    [in] void  *cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="815eb-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="815eb-106">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="815eb-107">[in] Ukazatel na neprůhledné paměť přidělenou volajícímu, který obsahuje spravovaný kód, který se spustí.</span><span class="sxs-lookup"><span data-stu-id="815eb-107">[in] A pointer to opaque caller-allocated memory that contains the managed code to be executed.</span></span>  
  
 <span data-ttu-id="815eb-108">Přidělování a životnosti tato paměť se řídí volající (modulu CLR).</span><span class="sxs-lookup"><span data-stu-id="815eb-108">The allocation and lifetime of this memory are controlled by the caller (that is, the CLR).</span></span> <span data-ttu-id="815eb-109">Toto není spravované haldy paměti CLR.</span><span class="sxs-lookup"><span data-stu-id="815eb-109">This is not CLR managed-heap memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="815eb-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="815eb-110">Requirements</span></span>  
 <span data-ttu-id="815eb-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="815eb-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="815eb-112">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="815eb-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="815eb-113">**Knihovna:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="815eb-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="815eb-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="815eb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="815eb-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="815eb-115">See also</span></span>

- [<span data-ttu-id="815eb-116">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="815eb-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
