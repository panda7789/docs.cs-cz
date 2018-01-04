---
title: "CoreClrDebugProcInfo – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CoreClrDebugProcInfo
api_location: mscordbi_macx86.dll
api_type: COM
f1_keywords: CoreClrDebugProcInfo
helpviewer_keywords:
- remote debugging API [Silverlight]
- CoreClrDebugProcInfo structure
- Silverlight, remote debugging
ms.assetid: 4ddc37da-5c94-4beb-b61c-b54071c0e749
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d341b875f9f64b9aa1fcdcf21668dafea0beac12
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="coreclrdebugprocinfo-structure"></a><span data-ttu-id="a6d68-102">CoreClrDebugProcInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="a6d68-102">CoreClrDebugProcInfo Structure</span></span>
<span data-ttu-id="a6d68-103">Představuje proces, který běží na vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="a6d68-103">Represents a process that is running on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6d68-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6d68-104">Syntax</span></span>  
  
```  
struct  CoreClrDebugProcInfo {  
    DWORD m_dwPID;  
    DWORD m_dwInternalID;  
    WCHAR m_wszName[256];  
};  
```  
  
## <a name="members"></a><span data-ttu-id="a6d68-105">Členové</span><span class="sxs-lookup"><span data-stu-id="a6d68-105">Members</span></span>  
  
|<span data-ttu-id="a6d68-106">Člen</span><span class="sxs-lookup"><span data-stu-id="a6d68-106">Member</span></span>|<span data-ttu-id="a6d68-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a6d68-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwPID`|<span data-ttu-id="a6d68-108">Identifikátor procesu přiřazené operačního systému.</span><span class="sxs-lookup"><span data-stu-id="a6d68-108">OS-assigned process identifier.</span></span>|  
|`m_dwInternalID`|<span data-ttu-id="a6d68-109">Identifikátor procesu, který je přiřazen nástrojem proxy vzdáleného ladění na cílovém počítači spuštěna.</span><span class="sxs-lookup"><span data-stu-id="a6d68-109">Process identifier that is assigned by the remote debugging proxy running on the target machine.</span></span> <span data-ttu-id="a6d68-110">Tento identifikátor recyklování méně často než identifikátor operačního systému.</span><span class="sxs-lookup"><span data-stu-id="a6d68-110">This identifier recycles less often than the OS identifier.</span></span>|  
|`m_wszName`|<span data-ttu-id="a6d68-111">Příkazového řádku procesu.</span><span class="sxs-lookup"><span data-stu-id="a6d68-111">Command-line of the process.</span></span> <span data-ttu-id="a6d68-112">Tento člen mohou být zkráceny.</span><span class="sxs-lookup"><span data-stu-id="a6d68-112">This member may be truncated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a6d68-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a6d68-113">Requirements</span></span>  
 <span data-ttu-id="a6d68-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6d68-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6d68-115">**Záhlaví:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="a6d68-115">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="a6d68-116">**Knihovna:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="a6d68-116">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="a6d68-117">**Verze rozhraní .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="a6d68-117">**.NET Framework Versions:** 3.5 SP1</span></span>
