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
ms.openlocfilehash: e12882e53d1aa2120ab5c4b6793d7f2e34be76eb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132167"
---
# <a name="coreclrdebugprocinfo-structure"></a><span data-ttu-id="90b4d-102">CoreClrDebugProcInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="90b4d-102">CoreClrDebugProcInfo Structure</span></span>
<span data-ttu-id="90b4d-103">Představuje proces, který je spuštěn ve vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="90b4d-103">Represents a process that is running on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90b4d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90b4d-104">Syntax</span></span>  
  
```cpp  
struct  CoreClrDebugProcInfo {  
    DWORD m_dwPID;  
    DWORD m_dwInternalID;  
    WCHAR m_wszName[256];  
};  
```  
  
## <a name="members"></a><span data-ttu-id="90b4d-105">Členové</span><span class="sxs-lookup"><span data-stu-id="90b4d-105">Members</span></span>  
  
|<span data-ttu-id="90b4d-106">Člen</span><span class="sxs-lookup"><span data-stu-id="90b4d-106">Member</span></span>|<span data-ttu-id="90b4d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="90b4d-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwPID`|<span data-ttu-id="90b4d-108">Identifikátor procesu přiřazený operačním systémem.</span><span class="sxs-lookup"><span data-stu-id="90b4d-108">OS-assigned process identifier.</span></span>|  
|`m_dwInternalID`|<span data-ttu-id="90b4d-109">Identifikátor procesu, který je přiřazený proxy vzdáleného ladění, který běží na cílovém počítači.</span><span class="sxs-lookup"><span data-stu-id="90b4d-109">Process identifier that is assigned by the remote debugging proxy running on the target machine.</span></span> <span data-ttu-id="90b4d-110">Tento identifikátor recykluje méně často než identifikátor operačního systému.</span><span class="sxs-lookup"><span data-stu-id="90b4d-110">This identifier recycles less often than the OS identifier.</span></span>|  
|`m_wszName`|<span data-ttu-id="90b4d-111">Příkazový řádek procesu.</span><span class="sxs-lookup"><span data-stu-id="90b4d-111">Command-line of the process.</span></span> <span data-ttu-id="90b4d-112">Tento člen může být zkrácen.</span><span class="sxs-lookup"><span data-stu-id="90b4d-112">This member may be truncated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="90b4d-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="90b4d-113">Requirements</span></span>  
 <span data-ttu-id="90b4d-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90b4d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90b4d-115">**Hlavička:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="90b4d-115">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="90b4d-116">**Knihovna:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="90b4d-116">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="90b4d-117">**Verze .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="90b4d-117">**.NET Framework Versions:** 3.5 SP1</span></span>
