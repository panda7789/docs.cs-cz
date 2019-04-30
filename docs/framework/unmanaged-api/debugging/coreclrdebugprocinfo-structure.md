---
title: CoreClrDebugProcInfo – struktura
ms.date: 03/30/2017
api_name:
- CoreClrDebugProcInfo
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CoreClrDebugProcInfo
helpviewer_keywords:
- remote debugging API [Silverlight]
- CoreClrDebugProcInfo structure
- Silverlight, remote debugging
ms.assetid: 4ddc37da-5c94-4beb-b61c-b54071c0e749
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9d4b27ca0bf454b42f15b849008e5a3019bb09a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864075"
---
# <a name="coreclrdebugprocinfo-structure"></a><span data-ttu-id="d92ed-102">CoreClrDebugProcInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="d92ed-102">CoreClrDebugProcInfo Structure</span></span>
<span data-ttu-id="d92ed-103">Představuje proces, který běží na vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="d92ed-103">Represents a process that is running on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d92ed-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d92ed-104">Syntax</span></span>  
  
```  
struct  CoreClrDebugProcInfo {  
    DWORD m_dwPID;  
    DWORD m_dwInternalID;  
    WCHAR m_wszName[256];  
};  
```  
  
## <a name="members"></a><span data-ttu-id="d92ed-105">Členové</span><span class="sxs-lookup"><span data-stu-id="d92ed-105">Members</span></span>  
  
|<span data-ttu-id="d92ed-106">Člen</span><span class="sxs-lookup"><span data-stu-id="d92ed-106">Member</span></span>|<span data-ttu-id="d92ed-107">Popis</span><span class="sxs-lookup"><span data-stu-id="d92ed-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwPID`|<span data-ttu-id="d92ed-108">Identifikátor procesu přiřazené operačního systému.</span><span class="sxs-lookup"><span data-stu-id="d92ed-108">OS-assigned process identifier.</span></span>|  
|`m_dwInternalID`|<span data-ttu-id="d92ed-109">Identifikátor procesu, která je přiřazena službou proxy vzdáleného ladění běžící na cílovém počítači.</span><span class="sxs-lookup"><span data-stu-id="d92ed-109">Process identifier that is assigned by the remote debugging proxy running on the target machine.</span></span> <span data-ttu-id="d92ed-110">Tento identifikátor se recykluje méně často než OS identifikátor.</span><span class="sxs-lookup"><span data-stu-id="d92ed-110">This identifier recycles less often than the OS identifier.</span></span>|  
|`m_wszName`|<span data-ttu-id="d92ed-111">Příkazový řádek procesu.</span><span class="sxs-lookup"><span data-stu-id="d92ed-111">Command-line of the process.</span></span> <span data-ttu-id="d92ed-112">Tento člen můžou být zkrácené.</span><span class="sxs-lookup"><span data-stu-id="d92ed-112">This member may be truncated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d92ed-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d92ed-113">Requirements</span></span>  
 <span data-ttu-id="d92ed-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d92ed-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d92ed-115">**Záhlaví:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="d92ed-115">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="d92ed-116">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="d92ed-116">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="d92ed-117">**Verze rozhraní .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="d92ed-117">**.NET Framework Versions:** 3.5 SP1</span></span>
