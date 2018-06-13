---
title: USER_THREAD – struktura
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 93e96d6f8570e6aef7bfc18ef2859dc1e86ec8fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429028"
---
# <a name="userthread-structure"></a><span data-ttu-id="370ca-102">USER_THREAD – struktura</span><span class="sxs-lookup"><span data-stu-id="370ca-102">USER_THREAD Structure</span></span>
<span data-ttu-id="370ca-103">Poskytuje informace o ladicí program o vlákna.</span><span class="sxs-lookup"><span data-stu-id="370ca-103">Provides information to a debugger about a thread.</span></span> <span data-ttu-id="370ca-104">Další informace najdete v tématu [inotifysource2::setnotifyfilter –](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="370ca-104">For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="370ca-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="370ca-105">Syntax</span></span>  
  
```  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a><span data-ttu-id="370ca-106">Členové</span><span class="sxs-lookup"><span data-stu-id="370ca-106">Members</span></span>  
  
|<span data-ttu-id="370ca-107">Člen</span><span class="sxs-lookup"><span data-stu-id="370ca-107">Member</span></span>|<span data-ttu-id="370ca-108">Popis</span><span class="sxs-lookup"><span data-stu-id="370ca-108">Description</span></span>|  
|------------|-----------------|  
|`pSidBuffer`|<span data-ttu-id="370ca-109">Adresa vyrovnávací paměti pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="370ca-109">Address of thread buffer.</span></span>|  
|`dwSidLen`|<span data-ttu-id="370ca-110">Délka vyrovnávací paměti přístup z více vláken v bajtech.</span><span class="sxs-lookup"><span data-stu-id="370ca-110">Length of thread buffer, in bytes.</span></span>|  
|`dwTid`|<span data-ttu-id="370ca-111">ID vlákna.</span><span class="sxs-lookup"><span data-stu-id="370ca-111">Thread ID.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="370ca-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="370ca-112">Requirements</span></span>  
 <span data-ttu-id="370ca-113">**Záhlaví:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="370ca-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="370ca-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="370ca-114">See Also</span></span>  
 [<span data-ttu-id="370ca-115">SetNotifyFilter – metoda</span><span class="sxs-lookup"><span data-stu-id="370ca-115">SetNotifyFilter Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)  
 [<span data-ttu-id="370ca-116">Struktury pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="370ca-116">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
