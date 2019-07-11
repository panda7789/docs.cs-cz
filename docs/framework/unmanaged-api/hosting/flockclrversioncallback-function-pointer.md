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
ms.openlocfilehash: 46e3356df6578f2adf2ceee00b1363b65fd014ea
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760238"
---
# <a name="flockclrversioncallback-function-pointer"></a><span data-ttu-id="fbc55-102">FLockClrVersionCallback – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="fbc55-102">FLockClrVersionCallback Function Pointer</span></span>
<span data-ttu-id="fbc55-103">Odkazuje na funkci, která běžné volání jazyka runtime (CLR) k označení, že inicializace je zahájena nebo dokončena.</span><span class="sxs-lookup"><span data-stu-id="fbc55-103">Points to a function that the common language runtime (CLR) calls to indicate that initialization has either started or completed.</span></span>  
  
 <span data-ttu-id="fbc55-104">Tento ukazatel na funkci se již nepoužívá v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="fbc55-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbc55-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fbc55-105">Syntax</span></span>  
  
```cpp  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="fbc55-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fbc55-106">Remarks</span></span>  
 <span data-ttu-id="fbc55-107">Tato funkce je implementováno hostitele.</span><span class="sxs-lookup"><span data-stu-id="fbc55-107">This function is implemented by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbc55-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fbc55-108">Requirements</span></span>  
 <span data-ttu-id="fbc55-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbc55-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbc55-110">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fbc55-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fbc55-111">**Knihovna:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="fbc55-111">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="fbc55-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbc55-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbc55-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fbc55-113">See also</span></span>

- [<span data-ttu-id="fbc55-114">LockClrVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="fbc55-114">LockClrVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)
- [<span data-ttu-id="fbc55-115">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="fbc55-115">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
