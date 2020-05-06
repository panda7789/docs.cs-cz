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
ms.openlocfilehash: 40dbfc60f8bde1198fd56a4a8aeed1dd6879d1ae
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795622"
---
# <a name="coreclrdebugprocinfo-structure"></a><span data-ttu-id="8b03c-102">CoreClrDebugProcInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="8b03c-102">CoreClrDebugProcInfo Structure</span></span>
<span data-ttu-id="8b03c-103">Představuje proces, který je spuštěn ve vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="8b03c-103">Represents a process that is running on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b03c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b03c-104">Syntax</span></span>  
  
```cpp  
struct  CoreClrDebugProcInfo {  
    DWORD m_dwPID;  
    DWORD m_dwInternalID;  
    WCHAR m_wszName[256];  
};  
```  
  
## <a name="members"></a><span data-ttu-id="8b03c-105">Členové</span><span class="sxs-lookup"><span data-stu-id="8b03c-105">Members</span></span>  
  
|<span data-ttu-id="8b03c-106">Člen</span><span class="sxs-lookup"><span data-stu-id="8b03c-106">Member</span></span>|<span data-ttu-id="8b03c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8b03c-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwPID`|<span data-ttu-id="8b03c-108">Identifikátor procesu přiřazený operačním systémem.</span><span class="sxs-lookup"><span data-stu-id="8b03c-108">OS-assigned process identifier.</span></span>|  
|`m_dwInternalID`|<span data-ttu-id="8b03c-109">Identifikátor procesu, který je přiřazený proxy vzdáleného ladění, který běží na cílovém počítači.</span><span class="sxs-lookup"><span data-stu-id="8b03c-109">Process identifier that is assigned by the remote debugging proxy running on the target machine.</span></span> <span data-ttu-id="8b03c-110">Tento identifikátor recykluje méně často než identifikátor operačního systému.</span><span class="sxs-lookup"><span data-stu-id="8b03c-110">This identifier recycles less often than the OS identifier.</span></span>|  
|`m_wszName`|<span data-ttu-id="8b03c-111">Příkazový řádek procesu.</span><span class="sxs-lookup"><span data-stu-id="8b03c-111">Command-line of the process.</span></span> <span data-ttu-id="8b03c-112">Tento člen může být zkrácen.</span><span class="sxs-lookup"><span data-stu-id="8b03c-112">This member may be truncated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8b03c-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8b03c-113">Requirements</span></span>  
 <span data-ttu-id="8b03c-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b03c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b03c-115">**Hlavička:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="8b03c-115">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="8b03c-116">**Knihovna:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="8b03c-116">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="8b03c-117">**Verze .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="8b03c-117">**.NET Framework Versions:** 3.5 SP1</span></span>
