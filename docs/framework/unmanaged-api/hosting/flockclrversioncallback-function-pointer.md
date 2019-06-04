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
ms.openlocfilehash: ef308b624525c3a139c892e6118a24d6adb6e14a
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490459"
---
# <a name="flockclrversioncallback-function-pointer"></a><span data-ttu-id="6d4c0-102">FLockClrVersionCallback – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="6d4c0-102">FLockClrVersionCallback Function Pointer</span></span>
<span data-ttu-id="6d4c0-103">Odkazuje na funkci, která běžné volání jazyka runtime (CLR) k označení, že inicializace je zahájena nebo dokončena.</span><span class="sxs-lookup"><span data-stu-id="6d4c0-103">Points to a function that the common language runtime (CLR) calls to indicate that initialization has either started or completed.</span></span>  
  
 <span data-ttu-id="6d4c0-104">Tento ukazatel na funkci se již nepoužívá v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="6d4c0-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d4c0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d4c0-105">Syntax</span></span>  
  
```  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="6d4c0-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6d4c0-106">Remarks</span></span>  
 <span data-ttu-id="6d4c0-107">Tato funkce je implementováno hostitele.</span><span class="sxs-lookup"><span data-stu-id="6d4c0-107">This function is implemented by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d4c0-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6d4c0-108">Requirements</span></span>  
 <span data-ttu-id="6d4c0-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d4c0-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d4c0-110">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6d4c0-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6d4c0-111">**Knihovna:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="6d4c0-111">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="6d4c0-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d4c0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d4c0-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6d4c0-113">See also</span></span>

- [<span data-ttu-id="6d4c0-114">LockClrVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="6d4c0-114">LockClrVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)
- [<span data-ttu-id="6d4c0-115">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="6d4c0-115">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
