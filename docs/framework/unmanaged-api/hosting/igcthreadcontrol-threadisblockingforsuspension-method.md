---
title: IGCThreadControl::ThreadIsBlockingForSuspension – metoda
ms.date: 03/30/2017
api_name:
- IGCThreadControl.ThreadIsBlockingForSuspension
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ThreadIsBlockingForSuspension
helpviewer_keywords:
- IGCThreadControl::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: ed5b5b58-7db7-46b5-9e2c-278db7159cee
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6f4b767fe7134833ee2e404be30bb51bf1385ec9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437034"
---
# <a name="igcthreadcontrolthreadisblockingforsuspension-method"></a><span data-ttu-id="02076-102">IGCThreadControl::ThreadIsBlockingForSuspension – metoda</span><span class="sxs-lookup"><span data-stu-id="02076-102">IGCThreadControl::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="02076-103">Upozorní hostitele, že vlákno, které je uskutečněním hovoru se chystáte se zablokovat, případně pro uvolnění paměti nebo jiných pozastavení.</span><span class="sxs-lookup"><span data-stu-id="02076-103">Notifies the host that the thread that is making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02076-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="02076-104">Syntax</span></span>  
  
```  
HRESULT ThreadIsBlockingForSuspension ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="02076-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="02076-105">Remarks</span></span>  
 <span data-ttu-id="02076-106">Hostitel rozhodnout, že v rámci `ThreadIsBlockingForSuspension` zpětného volání jestli se má změnit plán naplánovaných vlákna.</span><span class="sxs-lookup"><span data-stu-id="02076-106">The host may choose within the `ThreadIsBlockingForSuspension` callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02076-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="02076-107">Requirements</span></span>  
 <span data-ttu-id="02076-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02076-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02076-109">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="02076-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="02076-110">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="02076-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="02076-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02076-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02076-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="02076-112">See Also</span></span>  
 [<span data-ttu-id="02076-113">IGCThreadControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="02076-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
