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
ms.openlocfilehash: 0191f1fa17d436944fcb590d88dd4004adfa1aba
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744297"
---
# <a name="userthread-structure"></a><span data-ttu-id="fe471-102">USER_THREAD – struktura</span><span class="sxs-lookup"><span data-stu-id="fe471-102">USER_THREAD Structure</span></span>
<span data-ttu-id="fe471-103">Poskytuje informace o vlákno ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="fe471-103">Provides information to a debugger about a thread.</span></span> <span data-ttu-id="fe471-104">Další informace najdete v tématu [inotifysource2::setnotifyfilter –](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="fe471-104">For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe471-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe471-105">Syntax</span></span>  
  
```cpp  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a><span data-ttu-id="fe471-106">Členové</span><span class="sxs-lookup"><span data-stu-id="fe471-106">Members</span></span>  
  
|<span data-ttu-id="fe471-107">Člen</span><span class="sxs-lookup"><span data-stu-id="fe471-107">Member</span></span>|<span data-ttu-id="fe471-108">Popis</span><span class="sxs-lookup"><span data-stu-id="fe471-108">Description</span></span>|  
|------------|-----------------|  
|`pSidBuffer`|<span data-ttu-id="fe471-109">Adresa vyrovnávací paměti pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="fe471-109">Address of thread buffer.</span></span>|  
|`dwSidLen`|<span data-ttu-id="fe471-110">Délka vyrovnávací paměti vlákna, v bajtech.</span><span class="sxs-lookup"><span data-stu-id="fe471-110">Length of thread buffer, in bytes.</span></span>|  
|`dwTid`|<span data-ttu-id="fe471-111">ID vlákna.</span><span class="sxs-lookup"><span data-stu-id="fe471-111">Thread ID.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fe471-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fe471-112">Requirements</span></span>  
 <span data-ttu-id="fe471-113">**Záhlaví:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="fe471-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe471-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fe471-114">See also</span></span>

- [<span data-ttu-id="fe471-115">SetNotifyFilter – metoda</span><span class="sxs-lookup"><span data-stu-id="fe471-115">SetNotifyFilter Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)
- [<span data-ttu-id="fe471-116">Struktury pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="fe471-116">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
