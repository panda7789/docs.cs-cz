---
title: FLockClrVersionCallback – ukazatel na funkci
ms.date: 03/30/2017
api_name:
- FLockClrVersionCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FLockClrVersionCallback
helpviewer_keywords:
- FLockClrVersionCallback function pointer [.NET Framework hosting]
ms.assetid: 98a4762d-9ad2-45bd-9d03-39064a028b44
topic_type:
- apiref
ms.openlocfilehash: af42de820b2d835e8ea137a2643a51678e382ff0
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617279"
---
# <a name="flockclrversioncallback-function-pointer"></a><span data-ttu-id="4cf5c-102">FLockClrVersionCallback – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="4cf5c-102">FLockClrVersionCallback Function Pointer</span></span>
<span data-ttu-id="4cf5c-103">Odkazuje na funkci, která volá modul CLR (Common Language Runtime), aby označovala, že inicializace buď začala, nebo je dokončená.</span><span class="sxs-lookup"><span data-stu-id="4cf5c-103">Points to a function that the common language runtime (CLR) calls to indicate that initialization has either started or completed.</span></span>  
  
 <span data-ttu-id="4cf5c-104">Tento ukazatel funkce je zastaralý v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="4cf5c-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cf5c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4cf5c-105">Syntax</span></span>  
  
```cpp  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="4cf5c-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4cf5c-106">Remarks</span></span>  
 <span data-ttu-id="4cf5c-107">Tato funkce je implementovaná hostitelem.</span><span class="sxs-lookup"><span data-stu-id="4cf5c-107">This function is implemented by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cf5c-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4cf5c-108">Requirements</span></span>  
 <span data-ttu-id="4cf5c-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4cf5c-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cf5c-110">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4cf5c-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4cf5c-111">**Knihovna:** Knihovny Mscorwks. dll</span><span class="sxs-lookup"><span data-stu-id="4cf5c-111">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="4cf5c-112">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4cf5c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cf5c-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="4cf5c-113">See also</span></span>

- [<span data-ttu-id="4cf5c-114">LockClrVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="4cf5c-114">LockClrVersion Function</span></span>](lockclrversion-function.md)
- [<span data-ttu-id="4cf5c-115">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="4cf5c-115">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
