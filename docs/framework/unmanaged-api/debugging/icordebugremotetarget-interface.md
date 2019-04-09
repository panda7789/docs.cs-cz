---
title: ICorDebugRemoteTarget – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugRemoteTarget
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget
helpviewer_keywords:
- ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: bd9936a6-cc24-4869-8761-0988664464e6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae31506d4ba34bf262f49bc2321c6cfcd30f1b60
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197318"
---
# <a name="icordebugremotetarget-interface"></a><span data-ttu-id="b94af-102">ICorDebugRemoteTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b94af-102">ICorDebugRemoteTarget Interface</span></span>
<span data-ttu-id="b94af-103">Poskytuje metody, které umožňují vývojářům ladit aplikace programu Silverlight v prostředí common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="b94af-103">Provides methods that enable developers to debug Silverlight-based applications in the common language runtime (CLR) environment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b94af-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b94af-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="b94af-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b94af-105">Methods</span></span>  
  
|<span data-ttu-id="b94af-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="b94af-106">Method</span></span>|<span data-ttu-id="b94af-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b94af-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b94af-108">ICorDebugRemoteTarget::GetHostName – metoda</span><span class="sxs-lookup"><span data-stu-id="b94af-108">ICorDebugRemoteTarget::GetHostName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-gethostname-method.md)|<span data-ttu-id="b94af-109">Vrátí název hostitele nebo IP adresu vzdáleného počítače.</span><span class="sxs-lookup"><span data-stu-id="b94af-109">Returns the host name or the IP address of a remote machine.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b94af-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b94af-110">Remarks</span></span>  
 <span data-ttu-id="b94af-111">Ladění ve smíšeném režimu (tj. spravovaný a nativní kód) není podporováno ve Windows 95, Windows 98 nebo Windows ME, nebo na platformách x x86 (například IA-64 a AMD64).</span><span class="sxs-lookup"><span data-stu-id="b94af-111">Mixed-mode (that is, managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA-64 and AMD64).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b94af-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b94af-112">Requirements</span></span>  
 <span data-ttu-id="b94af-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b94af-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b94af-114">**Záhlaví:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="b94af-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="b94af-115">**Knihovna:** : CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b94af-115">**Library:** : CorGuids.lib</span></span>  
  
 <span data-ttu-id="b94af-116">**Verze rozhraní .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="b94af-116">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b94af-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b94af-117">See also</span></span>

- [<span data-ttu-id="b94af-118">ICorDebugRemote – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b94af-118">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [<span data-ttu-id="b94af-119">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b94af-119">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="b94af-120">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b94af-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
