---
title: "USER_THREAD – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- USER_THREAD
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- USER_THREAD
helpviewer_keywords:
- USER_THREAD structure [.NET Framework debugging]
ms.assetid: a57c7d71-c4b0-41f9-a964-0c5ee84a3124
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 50533ce25812ad49d538c5a6a6c814d7a9704053
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="userthread-structure"></a><span data-ttu-id="3ea63-102">USER_THREAD – struktura</span><span class="sxs-lookup"><span data-stu-id="3ea63-102">USER_THREAD Structure</span></span>
<span data-ttu-id="3ea63-103">Poskytuje informace o ladicí program o vlákna.</span><span class="sxs-lookup"><span data-stu-id="3ea63-103">Provides information to a debugger about a thread.</span></span> <span data-ttu-id="3ea63-104">Další informace najdete v tématu [inotifysource2::setnotifyfilter –](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="3ea63-104">For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ea63-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ea63-105">Syntax</span></span>  
  
```  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a><span data-ttu-id="3ea63-106">Členové</span><span class="sxs-lookup"><span data-stu-id="3ea63-106">Members</span></span>  
  
|<span data-ttu-id="3ea63-107">Člen</span><span class="sxs-lookup"><span data-stu-id="3ea63-107">Member</span></span>|<span data-ttu-id="3ea63-108">Popis</span><span class="sxs-lookup"><span data-stu-id="3ea63-108">Description</span></span>|  
|------------|-----------------|  
|`pSidBuffer`|<span data-ttu-id="3ea63-109">Adresa vyrovnávací paměti pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="3ea63-109">Address of thread buffer.</span></span>|  
|`dwSidLen`|<span data-ttu-id="3ea63-110">Délka vyrovnávací paměti přístup z více vláken v bajtech.</span><span class="sxs-lookup"><span data-stu-id="3ea63-110">Length of thread buffer, in bytes.</span></span>|  
|`dwTid`|<span data-ttu-id="3ea63-111">ID vlákna.</span><span class="sxs-lookup"><span data-stu-id="3ea63-111">Thread ID.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3ea63-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3ea63-112">Requirements</span></span>  
 <span data-ttu-id="3ea63-113">**Záhlaví:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="3ea63-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ea63-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="3ea63-114">See Also</span></span>  
 [<span data-ttu-id="3ea63-115">SetNotifyFilter – metoda</span><span class="sxs-lookup"><span data-stu-id="3ea63-115">SetNotifyFilter Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)  
 [<span data-ttu-id="3ea63-116">Struktury pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="3ea63-116">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
