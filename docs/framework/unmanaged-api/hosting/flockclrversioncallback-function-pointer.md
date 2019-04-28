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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61628012"
---
# <a name="flockclrversioncallback-function-pointer"></a><span data-ttu-id="0b213-102">FLockClrVersionCallback – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="0b213-102">FLockClrVersionCallback Function Pointer</span></span>
<span data-ttu-id="0b213-103">Odkazuje na funkci, která běžné volání jazyka runtime (CLR) k označení, že inicializace je zahájena nebo dokončena.</span><span class="sxs-lookup"><span data-stu-id="0b213-103">Points to a function that the common language runtime (CLR) calls to indicate that initialization has either started or completed.</span></span>  
  
 <span data-ttu-id="0b213-104">Tento ukazatel na funkci se už nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0b213-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b213-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b213-105">Syntax</span></span>  
  
```  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="0b213-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0b213-106">Remarks</span></span>  
 <span data-ttu-id="0b213-107">Tato funkce je implementováno hostitele.</span><span class="sxs-lookup"><span data-stu-id="0b213-107">This function is implemented by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b213-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0b213-108">Requirements</span></span>  
 <span data-ttu-id="0b213-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b213-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b213-110">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0b213-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0b213-111">**Knihovna:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="0b213-111">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="0b213-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b213-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b213-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0b213-113">See also</span></span>

- [<span data-ttu-id="0b213-114">LockClrVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="0b213-114">LockClrVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)
- [<span data-ttu-id="0b213-115">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="0b213-115">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
