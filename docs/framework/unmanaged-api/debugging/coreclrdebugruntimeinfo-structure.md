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
ms.openlocfilehash: 2c41e7db32ee8557a6c03217b95fd5b040655c70
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860938"
---
# <a name="coreclrdebugruntimeinfo-structure"></a><span data-ttu-id="d7bdc-102">CoreClrDebugRuntimeInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="d7bdc-102">CoreClrDebugRuntimeInfo Structure</span></span>
<span data-ttu-id="d7bdc-103">Představuje instanci modulu CLR (Common Language Runtime), která je načtena v procesu ve vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="d7bdc-103">Represents a common language runtime (CLR) instance that is loaded in a process on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7bdc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7bdc-104">Syntax</span></span>  
  
```cpp  
struct  CoreClrDebugRuntimeInfo {  
    DWORD m_dwInternalID;  
};  
```  
  
## <a name="members"></a><span data-ttu-id="d7bdc-105">Členové</span><span class="sxs-lookup"><span data-stu-id="d7bdc-105">Members</span></span>  
  
|<span data-ttu-id="d7bdc-106">Člen</span><span class="sxs-lookup"><span data-stu-id="d7bdc-106">Member</span></span>|<span data-ttu-id="d7bdc-107">Popis</span><span class="sxs-lookup"><span data-stu-id="d7bdc-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwInternalID`|<span data-ttu-id="d7bdc-108">Identifikátor modulu runtime, který je přiřazený proxy vzdáleného ladění, který běží na cílovém počítači.</span><span class="sxs-lookup"><span data-stu-id="d7bdc-108">Runtime identifier that is assigned by the remote debugging proxy running on the target machine.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d7bdc-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d7bdc-109">Requirements</span></span>  
 <span data-ttu-id="d7bdc-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7bdc-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7bdc-111">**Hlavička:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="d7bdc-111">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="d7bdc-112">**Knihovna:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="d7bdc-112">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="d7bdc-113">**Verze .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="d7bdc-113">**.NET Framework Versions:** 3.5 SP1</span></span>
