---
title: "CALL_ID – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CALL_ID
api_location: diasymreader.dll
api_type: COM
f1_keywords: CALL_ID
helpviewer_keywords: CALL_ID structure [.NET Framework debugging]
ms.assetid: bfd46324-afec-4782-9c18-586d81fb4740
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 71fd69cbcced1440839b9eedf8fbe3d8f5b90646
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="callid-structure"></a><span data-ttu-id="25b69-102">CALL_ID – struktura</span><span class="sxs-lookup"><span data-stu-id="25b69-102">CALL_ID Structure</span></span>
<span data-ttu-id="25b69-103">Poskytuje informace o funkci, která je volána ladicí program.</span><span class="sxs-lookup"><span data-stu-id="25b69-103">Provides information to a debugger about a function that is being called.</span></span> <span data-ttu-id="25b69-104">Najdete v článku [inotifysink2 –](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) rozhraní pro další informace.</span><span class="sxs-lookup"><span data-stu-id="25b69-104">See the [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) interface for more information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25b69-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25b69-105">Syntax</span></span>  
  
```  
typedef struct tagCALL_ID  
{  
    LPCOLESTR       szMachine;  
    DWORD           dwPid;  
    USER_THREAD     *pUserThread;  
    STACK_ADDRESS   addrStackPointer;  
    LPCOLESTR       szEntryPoint;  
    LPCOLESTR       szDestinationMachine;  
} CALL_ID;  
```  
  
## <a name="members"></a><span data-ttu-id="25b69-106">Členové</span><span class="sxs-lookup"><span data-stu-id="25b69-106">Members</span></span>  
  
|<span data-ttu-id="25b69-107">Člen</span><span class="sxs-lookup"><span data-stu-id="25b69-107">Member</span></span>|<span data-ttu-id="25b69-108">Popis</span><span class="sxs-lookup"><span data-stu-id="25b69-108">Description</span></span>|  
|------------|-----------------|  
|`szMachine`|<span data-ttu-id="25b69-109">Identifikuje počítač, který je uskutečněním hovoru.</span><span class="sxs-lookup"><span data-stu-id="25b69-109">Identifies the machine that is making the call.</span></span>|  
|`dwPid`|<span data-ttu-id="25b69-110">Identifikuje počítač procesoru.</span><span class="sxs-lookup"><span data-stu-id="25b69-110">Identifies the machine processor.</span></span>|  
|`pUserThread`|<span data-ttu-id="25b69-111">Identifikuje vlákno, které provádí volání.</span><span class="sxs-lookup"><span data-stu-id="25b69-111">Identifies the thread that is executing the call.</span></span>|  
|`addrStackPointer`|<span data-ttu-id="25b69-112">Určuje adresu zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="25b69-112">Specifies the address of the call stack.</span></span>|  
|`szEntryPoint`|<span data-ttu-id="25b69-113">Určuje adresu volání.</span><span class="sxs-lookup"><span data-stu-id="25b69-113">Specifies the address of the call.</span></span>|  
|`szDestinationMachine`|<span data-ttu-id="25b69-114">Identifikuje počítač, který provede volání.</span><span class="sxs-lookup"><span data-stu-id="25b69-114">Identifies the machine that will execute the call.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="25b69-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="25b69-115">Requirements</span></span>  
 <span data-ttu-id="25b69-116">**Záhlaví:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="25b69-116">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25b69-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="25b69-117">See Also</span></span>  
 [<span data-ttu-id="25b69-118">INotifySink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="25b69-118">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="25b69-119">Struktury pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="25b69-119">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
