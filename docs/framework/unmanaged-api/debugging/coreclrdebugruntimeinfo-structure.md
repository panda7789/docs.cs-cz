---
title: "CoreClrDebugRuntimeInfo – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CoreClrDebugRuntimeInfo
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CoreClrDebugRuntimeInfo
helpviewer_keywords:
- remote debugging API [Silverlight]
- CoreDebugRuntimeInfo structure
- Silverlight, remote debugging
ms.assetid: bd01c30f-b7a8-4179-9497-622b6599b1a6
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: effcc44b3f3b0926c1d711955fa77aa3e71a1592
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="coreclrdebugruntimeinfo-structure"></a><span data-ttu-id="21657-102">CoreClrDebugRuntimeInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="21657-102">CoreClrDebugRuntimeInfo Structure</span></span>
<span data-ttu-id="21657-103">Představuje běžné instance jazyka runtime (CLR), který je načten do procesu ve vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="21657-103">Represents a common language runtime (CLR) instance that is loaded in a process on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21657-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21657-104">Syntax</span></span>  
  
```  
struct  CoreClrDebugRuntimeInfo {  
    DWORD m_dwInternalID;  
};  
```  
  
## <a name="members"></a><span data-ttu-id="21657-105">Členové</span><span class="sxs-lookup"><span data-stu-id="21657-105">Members</span></span>  
  
|<span data-ttu-id="21657-106">Člen</span><span class="sxs-lookup"><span data-stu-id="21657-106">Member</span></span>|<span data-ttu-id="21657-107">Popis</span><span class="sxs-lookup"><span data-stu-id="21657-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwInternalID`|<span data-ttu-id="21657-108">Modul runtime identifikátor, který je přiřazen nástrojem proxy vzdáleného ladění na cílovém počítači spuštěna.</span><span class="sxs-lookup"><span data-stu-id="21657-108">Runtime identifier that is assigned by the remote debugging proxy running on the target machine.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="21657-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="21657-109">Requirements</span></span>  
 <span data-ttu-id="21657-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21657-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21657-111">**Záhlaví:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="21657-111">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="21657-112">**Knihovna:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="21657-112">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="21657-113">**Verze rozhraní .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="21657-113">**.NET Framework Versions:** 3.5 SP1</span></span>
