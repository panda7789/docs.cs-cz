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
ms.openlocfilehash: 11551221732e454e48111d48d60ca9b72f7f9b66
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61914703"
---
# <a name="userthread-structure"></a><span data-ttu-id="beb5d-102">USER_THREAD – struktura</span><span class="sxs-lookup"><span data-stu-id="beb5d-102">USER_THREAD Structure</span></span>
<span data-ttu-id="beb5d-103">Poskytuje informace o vlákno ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="beb5d-103">Provides information to a debugger about a thread.</span></span> <span data-ttu-id="beb5d-104">Další informace najdete v tématu [inotifysource2::setnotifyfilter –](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="beb5d-104">For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="beb5d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="beb5d-105">Syntax</span></span>  
  
```  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a><span data-ttu-id="beb5d-106">Členové</span><span class="sxs-lookup"><span data-stu-id="beb5d-106">Members</span></span>  
  
|<span data-ttu-id="beb5d-107">Člen</span><span class="sxs-lookup"><span data-stu-id="beb5d-107">Member</span></span>|<span data-ttu-id="beb5d-108">Popis</span><span class="sxs-lookup"><span data-stu-id="beb5d-108">Description</span></span>|  
|------------|-----------------|  
|`pSidBuffer`|<span data-ttu-id="beb5d-109">Adresa vyrovnávací paměti pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="beb5d-109">Address of thread buffer.</span></span>|  
|`dwSidLen`|<span data-ttu-id="beb5d-110">Délka vyrovnávací paměti vlákna, v bajtech.</span><span class="sxs-lookup"><span data-stu-id="beb5d-110">Length of thread buffer, in bytes.</span></span>|  
|`dwTid`|<span data-ttu-id="beb5d-111">ID vlákna.</span><span class="sxs-lookup"><span data-stu-id="beb5d-111">Thread ID.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="beb5d-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="beb5d-112">Requirements</span></span>  
 <span data-ttu-id="beb5d-113">**Záhlaví:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="beb5d-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="beb5d-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="beb5d-114">See also</span></span>

- [<span data-ttu-id="beb5d-115">SetNotifyFilter – metoda</span><span class="sxs-lookup"><span data-stu-id="beb5d-115">SetNotifyFilter Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)
- [<span data-ttu-id="beb5d-116">Struktury pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="beb5d-116">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
