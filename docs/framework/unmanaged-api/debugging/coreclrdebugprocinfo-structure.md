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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402188"
---
# <a name="coreclrdebugprocinfo-structure"></a><span data-ttu-id="e0279-102">CoreClrDebugProcInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="e0279-102">CoreClrDebugProcInfo Structure</span></span>
<span data-ttu-id="e0279-103">Představuje proces, který běží na vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="e0279-103">Represents a process that is running on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0279-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0279-104">Syntax</span></span>  
  
```  
struct  CoreClrDebugProcInfo {  
    DWORD m_dwPID;  
    DWORD m_dwInternalID;  
    WCHAR m_wszName[256];  
};  
```  
  
## <a name="members"></a><span data-ttu-id="e0279-105">Členové</span><span class="sxs-lookup"><span data-stu-id="e0279-105">Members</span></span>  
  
|<span data-ttu-id="e0279-106">Člen</span><span class="sxs-lookup"><span data-stu-id="e0279-106">Member</span></span>|<span data-ttu-id="e0279-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e0279-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwPID`|<span data-ttu-id="e0279-108">Identifikátor procesu přiřazené operačního systému.</span><span class="sxs-lookup"><span data-stu-id="e0279-108">OS-assigned process identifier.</span></span>|  
|`m_dwInternalID`|<span data-ttu-id="e0279-109">Identifikátor procesu, který je přiřazen nástrojem proxy vzdáleného ladění na cílovém počítači spuštěna.</span><span class="sxs-lookup"><span data-stu-id="e0279-109">Process identifier that is assigned by the remote debugging proxy running on the target machine.</span></span> <span data-ttu-id="e0279-110">Tento identifikátor recyklování méně často než identifikátor operačního systému.</span><span class="sxs-lookup"><span data-stu-id="e0279-110">This identifier recycles less often than the OS identifier.</span></span>|  
|`m_wszName`|<span data-ttu-id="e0279-111">Příkazového řádku procesu.</span><span class="sxs-lookup"><span data-stu-id="e0279-111">Command-line of the process.</span></span> <span data-ttu-id="e0279-112">Tento člen mohou být zkráceny.</span><span class="sxs-lookup"><span data-stu-id="e0279-112">This member may be truncated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e0279-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e0279-113">Requirements</span></span>  
 <span data-ttu-id="e0279-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0279-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0279-115">**Záhlaví:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="e0279-115">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="e0279-116">**Knihovna:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="e0279-116">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="e0279-117">**Verze rozhraní .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="e0279-117">**.NET Framework Versions:** 3.5 SP1</span></span>
