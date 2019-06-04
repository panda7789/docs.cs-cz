---
title: LPTHREAD_START_ROUTINE – ukazatel na funkci
ms.date: 03/30/2017
api_name:
- LPTHREAD_START_ROUTINE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- LPTHREAD_START_ROUTINE
helpviewer_keywords:
- LPTHREAD_START_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 7b9b93b0-fe92-42ba-8693-701168a29dde
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a81e78c0a34f766e1598dd27506f62bd3132f348
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490157"
---
# <a name="lpthreadstartroutine-function-pointer"></a><span data-ttu-id="5a5e1-102">LPTHREAD_START_ROUTINE – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="5a5e1-102">LPTHREAD_START_ROUTINE Function Pointer</span></span>
<span data-ttu-id="5a5e1-103">Odkazuje na funkci, která upozorňuje hostitele na spuštěný podproces ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="5a5e1-103">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 <span data-ttu-id="5a5e1-104">Tento ukazatel na funkci se již nepoužívá v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="5a5e1-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a5e1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a5e1-105">Syntax</span></span>  
  
```  
typedef DWORD (__stdcall *LPTHREAD_START_ROUTINE) (  
    [in] LPVOID lpThreadParameter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a5e1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5a5e1-106">Parameters</span></span>  
 `lpThreadParameter`  
 <span data-ttu-id="5a5e1-107">[in] Ukazatel na kód, který byla spuštěna.</span><span class="sxs-lookup"><span data-stu-id="5a5e1-107">[in] A pointer to the code that has started executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a5e1-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5a5e1-108">Remarks</span></span>  
 <span data-ttu-id="5a5e1-109">Funkce, které `LPTHREAD_START_ROUTINE` body je funkce zpětného volání a musí být implementováno tvůrci hostitelské aplikace.</span><span class="sxs-lookup"><span data-stu-id="5a5e1-109">The function to which `LPTHREAD_START_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a5e1-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5a5e1-110">Requirements</span></span>  
 <span data-ttu-id="5a5e1-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a5e1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a5e1-112">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5a5e1-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5a5e1-113">**Knihovna:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="5a5e1-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="5a5e1-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a5e1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a5e1-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5a5e1-115">See also</span></span>

- [<span data-ttu-id="5a5e1-116">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="5a5e1-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
