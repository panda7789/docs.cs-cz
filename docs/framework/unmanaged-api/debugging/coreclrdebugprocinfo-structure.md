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
ms.openlocfilehash: 53616fb8e947d2a301dcfcb4e3870a9a9dc36ec1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="coreclrdebugprocinfo-structure"></a><span data-ttu-id="e5c3f-102">CoreClrDebugProcInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="e5c3f-102">CoreClrDebugProcInfo Structure</span></span>
<span data-ttu-id="e5c3f-103">Představuje proces, který běží na vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="e5c3f-103">Represents a process that is running on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5c3f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5c3f-104">Syntax</span></span>  
  
```  
struct  CoreClrDebugProcInfo {  
    DWORD m_dwPID;  
    DWORD m_dwInternalID;  
    WCHAR m_wszName[256];  
};  
```  
  
## <a name="members"></a><span data-ttu-id="e5c3f-105">Členové</span><span class="sxs-lookup"><span data-stu-id="e5c3f-105">Members</span></span>  
  
|<span data-ttu-id="e5c3f-106">Člen</span><span class="sxs-lookup"><span data-stu-id="e5c3f-106">Member</span></span>|<span data-ttu-id="e5c3f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e5c3f-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwPID`|<span data-ttu-id="e5c3f-108">Identifikátor procesu přiřazené operačního systému.</span><span class="sxs-lookup"><span data-stu-id="e5c3f-108">OS-assigned process identifier.</span></span>|  
|`m_dwInternalID`|<span data-ttu-id="e5c3f-109">Identifikátor procesu, který je přiřazen nástrojem proxy vzdáleného ladění na cílovém počítači spuštěna.</span><span class="sxs-lookup"><span data-stu-id="e5c3f-109">Process identifier that is assigned by the remote debugging proxy running on the target machine.</span></span> <span data-ttu-id="e5c3f-110">Tento identifikátor recyklování méně často než identifikátor operačního systému.</span><span class="sxs-lookup"><span data-stu-id="e5c3f-110">This identifier recycles less often than the OS identifier.</span></span>|  
|`m_wszName`|<span data-ttu-id="e5c3f-111">Příkazového řádku procesu.</span><span class="sxs-lookup"><span data-stu-id="e5c3f-111">Command-line of the process.</span></span> <span data-ttu-id="e5c3f-112">Tento člen mohou být zkráceny.</span><span class="sxs-lookup"><span data-stu-id="e5c3f-112">This member may be truncated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e5c3f-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e5c3f-113">Requirements</span></span>  
 <span data-ttu-id="e5c3f-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5c3f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5c3f-115">**Záhlaví:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="e5c3f-115">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="e5c3f-116">**Knihovna:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="e5c3f-116">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="e5c3f-117">**Verze rozhraní .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="e5c3f-117">**.NET Framework Versions:** 3.5 SP1</span></span>
