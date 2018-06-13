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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402067"
---
# <a name="coreclrdebugruntimeinfo-structure"></a><span data-ttu-id="78160-102">CoreClrDebugRuntimeInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="78160-102">CoreClrDebugRuntimeInfo Structure</span></span>
<span data-ttu-id="78160-103">Představuje běžné instance jazyka runtime (CLR), který je načten do procesu ve vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="78160-103">Represents a common language runtime (CLR) instance that is loaded in a process on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78160-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78160-104">Syntax</span></span>  
  
```  
struct  CoreClrDebugRuntimeInfo {  
    DWORD m_dwInternalID;  
};  
```  
  
## <a name="members"></a><span data-ttu-id="78160-105">Členové</span><span class="sxs-lookup"><span data-stu-id="78160-105">Members</span></span>  
  
|<span data-ttu-id="78160-106">Člen</span><span class="sxs-lookup"><span data-stu-id="78160-106">Member</span></span>|<span data-ttu-id="78160-107">Popis</span><span class="sxs-lookup"><span data-stu-id="78160-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwInternalID`|<span data-ttu-id="78160-108">Modul runtime identifikátor, který je přiřazen nástrojem proxy vzdáleného ladění na cílovém počítači spuštěna.</span><span class="sxs-lookup"><span data-stu-id="78160-108">Runtime identifier that is assigned by the remote debugging proxy running on the target machine.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="78160-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="78160-109">Requirements</span></span>  
 <span data-ttu-id="78160-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78160-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78160-111">**Záhlaví:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="78160-111">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="78160-112">**Knihovna:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="78160-112">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="78160-113">**Verze rozhraní .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="78160-113">**.NET Framework Versions:** 3.5 SP1</span></span>
