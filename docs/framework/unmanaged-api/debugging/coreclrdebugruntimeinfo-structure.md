---
title: CoreClrDebugRuntimeInfo – struktura
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88fcc5959054f1cdf7c9543674584a4bde26d896
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61966039"
---
# <a name="coreclrdebugruntimeinfo-structure"></a><span data-ttu-id="7be4e-102">CoreClrDebugRuntimeInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="7be4e-102">CoreClrDebugRuntimeInfo Structure</span></span>
<span data-ttu-id="7be4e-103">Představuje common language runtime (CLR) instanci, který je načten v procesu ve vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="7be4e-103">Represents a common language runtime (CLR) instance that is loaded in a process on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7be4e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7be4e-104">Syntax</span></span>  
  
```  
struct  CoreClrDebugRuntimeInfo {  
    DWORD m_dwInternalID;  
};  
```  
  
## <a name="members"></a><span data-ttu-id="7be4e-105">Členové</span><span class="sxs-lookup"><span data-stu-id="7be4e-105">Members</span></span>  
  
|<span data-ttu-id="7be4e-106">Člen</span><span class="sxs-lookup"><span data-stu-id="7be4e-106">Member</span></span>|<span data-ttu-id="7be4e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7be4e-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwInternalID`|<span data-ttu-id="7be4e-108">Identifikátor modulu runtime, která je přiřazena službou proxy vzdáleného ladění běžící na cílovém počítači.</span><span class="sxs-lookup"><span data-stu-id="7be4e-108">Runtime identifier that is assigned by the remote debugging proxy running on the target machine.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7be4e-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7be4e-109">Requirements</span></span>  
 <span data-ttu-id="7be4e-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7be4e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7be4e-111">**Záhlaví:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="7be4e-111">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="7be4e-112">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="7be4e-112">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="7be4e-113">**Verze rozhraní .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="7be4e-113">**.NET Framework Versions:** 3.5 SP1</span></span>
