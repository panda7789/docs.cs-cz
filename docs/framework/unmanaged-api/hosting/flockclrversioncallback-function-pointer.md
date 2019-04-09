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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8062ab151efc6175aa68cb0563cd2ad042ee9cd8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59189050"
---
# <a name="flockclrversioncallback-function-pointer"></a><span data-ttu-id="ecea7-102">FLockClrVersionCallback – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="ecea7-102">FLockClrVersionCallback Function Pointer</span></span>
<span data-ttu-id="ecea7-103">Odkazuje na funkci, která běžné volání jazyka runtime (CLR) k označení, že inicializace je zahájena nebo dokončena.</span><span class="sxs-lookup"><span data-stu-id="ecea7-103">Points to a function that the common language runtime (CLR) calls to indicate that initialization has either started or completed.</span></span>  
  
 <span data-ttu-id="ecea7-104">Tento ukazatel na funkci se už nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ecea7-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecea7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ecea7-105">Syntax</span></span>  
  
```  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="ecea7-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ecea7-106">Remarks</span></span>  
 <span data-ttu-id="ecea7-107">Tato funkce je implementováno hostitele.</span><span class="sxs-lookup"><span data-stu-id="ecea7-107">This function is implemented by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecea7-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ecea7-108">Requirements</span></span>  
 <span data-ttu-id="ecea7-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecea7-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecea7-110">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ecea7-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ecea7-111">**Knihovna:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="ecea7-111">**Library:** MSCorWks.dll</span></span>  
  
 **<span data-ttu-id="ecea7-112">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="ecea7-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ecea7-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ecea7-113">See also</span></span>

- [<span data-ttu-id="ecea7-114">LockClrVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="ecea7-114">LockClrVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)
- [<span data-ttu-id="ecea7-115">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="ecea7-115">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
