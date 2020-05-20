---
title: CALL_ID – struktura
ms.date: 03/30/2017
api_name:
- CALL_ID
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- CALL_ID
helpviewer_keywords:
- CALL_ID structure [.NET Framework debugging]
ms.assetid: bfd46324-afec-4782-9c18-586d81fb4740
topic_type:
- apiref
ms.openlocfilehash: 1c795ee536483a7def9c0339efae66a013898a77
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420627"
---
# <a name="call_id-structure"></a><span data-ttu-id="67198-102">CALL_ID – struktura</span><span class="sxs-lookup"><span data-stu-id="67198-102">CALL_ID Structure</span></span>
<span data-ttu-id="67198-103">Poskytuje informace ladicímu programu o funkci, která je volána.</span><span class="sxs-lookup"><span data-stu-id="67198-103">Provides information to a debugger about a function that is being called.</span></span> <span data-ttu-id="67198-104">Další informace najdete v rozhraní [INotifySink2](inotifysink2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="67198-104">See the [INotifySink2](inotifysink2-interface.md) interface for more information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67198-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="67198-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="67198-106">Členové</span><span class="sxs-lookup"><span data-stu-id="67198-106">Members</span></span>  
  
|<span data-ttu-id="67198-107">Člen</span><span class="sxs-lookup"><span data-stu-id="67198-107">Member</span></span>|<span data-ttu-id="67198-108">Popis</span><span class="sxs-lookup"><span data-stu-id="67198-108">Description</span></span>|  
|------------|-----------------|  
|`szMachine`|<span data-ttu-id="67198-109">Identifikuje počítač, který provádí volání.</span><span class="sxs-lookup"><span data-stu-id="67198-109">Identifies the machine that is making the call.</span></span>|  
|`dwPid`|<span data-ttu-id="67198-110">Identifikuje procesor počítače.</span><span class="sxs-lookup"><span data-stu-id="67198-110">Identifies the machine processor.</span></span>|  
|`pUserThread`|<span data-ttu-id="67198-111">Identifikuje vlákno, které provádí volání.</span><span class="sxs-lookup"><span data-stu-id="67198-111">Identifies the thread that is executing the call.</span></span>|  
|`addrStackPointer`|<span data-ttu-id="67198-112">Určuje adresu zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="67198-112">Specifies the address of the call stack.</span></span>|  
|`szEntryPoint`|<span data-ttu-id="67198-113">Určuje adresu volání.</span><span class="sxs-lookup"><span data-stu-id="67198-113">Specifies the address of the call.</span></span>|  
|`szDestinationMachine`|<span data-ttu-id="67198-114">Identifikuje počítač, který spustí volání.</span><span class="sxs-lookup"><span data-stu-id="67198-114">Identifies the machine that will execute the call.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="67198-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="67198-115">Requirements</span></span>  
 <span data-ttu-id="67198-116">**Hlavička:** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="67198-116">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67198-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="67198-117">See also</span></span>

- [<span data-ttu-id="67198-118">INotifySink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="67198-118">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="67198-119">Struktury úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="67198-119">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)
