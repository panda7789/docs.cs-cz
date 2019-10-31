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
ms.openlocfilehash: 970468bc2f50144c62c6e3cbcf9c00c2027f7663
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138185"
---
# <a name="fexecuteinappdomaincallback-function-pointer"></a><span data-ttu-id="17636-102">FExecuteInAppDomainCallback – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="17636-102">FExecuteInAppDomainCallback Function Pointer</span></span>
<span data-ttu-id="17636-103">Odkazuje na funkci, která je volána modulem CLR (Common Language Runtime) ke spuštění spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="17636-103">Points to a function that is called by the common language runtime (CLR) to execute managed code.</span></span>  
  
 <span data-ttu-id="17636-104">Tento ukazatel funkce je zastaralý v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="17636-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17636-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17636-105">Syntax</span></span>  
  
```cpp  
typedef HRESULT (__stdcall *FExecuteInAppDomainCallback) (  
    [in] void  *cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17636-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="17636-106">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="17636-107">pro Ukazatel na neprůhlednou paměť přidělenou volajícímu, která obsahuje spravovaný kód, který má být proveden.</span><span class="sxs-lookup"><span data-stu-id="17636-107">[in] A pointer to opaque caller-allocated memory that contains the managed code to be executed.</span></span>  
  
 <span data-ttu-id="17636-108">Přidělení a životnost této paměti jsou ovládány volajícím (to znamená CLR).</span><span class="sxs-lookup"><span data-stu-id="17636-108">The allocation and lifetime of this memory are controlled by the caller (that is, the CLR).</span></span> <span data-ttu-id="17636-109">Toto není spravovaná technologie CLR – paměť haldy.</span><span class="sxs-lookup"><span data-stu-id="17636-109">This is not CLR managed-heap memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17636-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="17636-110">Requirements</span></span>  
 <span data-ttu-id="17636-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17636-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17636-112">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="17636-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="17636-113">**Knihovna:** Knihovny Mscorwks. dll</span><span class="sxs-lookup"><span data-stu-id="17636-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="17636-114">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17636-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17636-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="17636-115">See also</span></span>

- [<span data-ttu-id="17636-116">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="17636-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
