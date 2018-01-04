---
title: "ICorDebugRemoteTarget – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRemoteTarget
api_location: CorDebug.dll
api_type: COM
f1_keywords: ICorDebugRemoteTarget
helpviewer_keywords: ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: bd9936a6-cc24-4869-8761-0988664464e6
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fcfdab2857745dee7c40823ad25592de5dc833ea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugremotetarget-interface"></a><span data-ttu-id="1fee4-102">ICorDebugRemoteTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1fee4-102">ICorDebugRemoteTarget Interface</span></span>
<span data-ttu-id="1fee4-103">Poskytuje metody, které vývojářům umožňuje ladit aplikace založená na technologii Silverlight v běžné prostředí runtime (CLR) jazyk.</span><span class="sxs-lookup"><span data-stu-id="1fee4-103">Provides methods that enable developers to debug Silverlight-based applications in the common language runtime (CLR) environment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fee4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1fee4-104">Syntax</span></span>  
  
```  
interface ICorDebugRemoteTarget  : IUnknown  
{  
    HRESULT GetHostName (  
        [in]  ULONG32                    cchHostName,  
        [out] ULONG32*                   pcchHostName,  
        [out, size_is(cchHostName),  
              length_is(*pcchHostName)]  
                  WCHAR szHostName[]  
        );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="1fee4-105">Metody</span><span class="sxs-lookup"><span data-stu-id="1fee4-105">Methods</span></span>  
  
|<span data-ttu-id="1fee4-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="1fee4-106">Method</span></span>|<span data-ttu-id="1fee4-107">Popis</span><span class="sxs-lookup"><span data-stu-id="1fee4-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1fee4-108">ICorDebugRemoteTarget::GetHostName – metoda</span><span class="sxs-lookup"><span data-stu-id="1fee4-108">ICorDebugRemoteTarget::GetHostName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-gethostname-method.md)|<span data-ttu-id="1fee4-109">Vrátí název hostitele nebo IP adresu vzdáleného počítače.</span><span class="sxs-lookup"><span data-stu-id="1fee4-109">Returns the host name or the IP address of a remote machine.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1fee4-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1fee4-110">Remarks</span></span>  
 <span data-ttu-id="1fee4-111">Ladění ve smíšeném režimu (to znamená, spravovaná a nativní kód) není podporována v systému Windows 95, Windows 98 nebo Windows ME nebo na jiný x86 platformy (například IA-64 a AMD64).</span><span class="sxs-lookup"><span data-stu-id="1fee4-111">Mixed-mode (that is, managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA-64 and AMD64).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fee4-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1fee4-112">Requirements</span></span>  
 <span data-ttu-id="1fee4-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1fee4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fee4-114">**Záhlaví:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="1fee4-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="1fee4-115">**Knihovna:** : CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1fee4-115">**Library:** : CorGuids.lib</span></span>  
  
 <span data-ttu-id="1fee4-116">**Verze rozhraní .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="1fee4-116">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fee4-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="1fee4-117">See Also</span></span>  
 [<span data-ttu-id="1fee4-118">ICorDebugRemote – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1fee4-118">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 [<span data-ttu-id="1fee4-119">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1fee4-119">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [<span data-ttu-id="1fee4-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="1fee4-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
