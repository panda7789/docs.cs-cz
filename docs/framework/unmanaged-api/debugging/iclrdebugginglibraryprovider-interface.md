---
title: ICLRDebuggingLibraryProvider – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRDebuggingLibraryProvider
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebuggingLibraryProvider
helpviewer_keywords:
- ICLRDebuggingLibraryProvider interface [.NET Framework debugging]
ms.assetid: 67739617-6add-41a9-9de5-a3200c3109ce
topic_type:
- apiref
ms.openlocfilehash: 81b9ffe5979ad553a5bdfbc27111469b2ff4db6f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73111381"
---
# <a name="iclrdebugginglibraryprovider-interface"></a><span data-ttu-id="20bff-102">ICLRDebuggingLibraryProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="20bff-102">ICLRDebuggingLibraryProvider Interface</span></span>
<span data-ttu-id="20bff-103">Obsahuje metodu [metody ProvideLibrary –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) , která získá rozhraní zpětného volání zprostředkovatele knihovny, které umožňuje umístění a načtení knihoven ladění pro Common Language Runtime v konkrétní verzi.</span><span class="sxs-lookup"><span data-stu-id="20bff-103">Includes the [ProvideLibrary Method](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="20bff-104">Metody</span><span class="sxs-lookup"><span data-stu-id="20bff-104">Methods</span></span>  
  
|<span data-ttu-id="20bff-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="20bff-105">Method</span></span>|<span data-ttu-id="20bff-106">Popis</span><span class="sxs-lookup"><span data-stu-id="20bff-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="20bff-107">ProvideLibrary – metoda</span><span class="sxs-lookup"><span data-stu-id="20bff-107">ProvideLibrary Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md)|<span data-ttu-id="20bff-108">Umožňuje ladicímu programu poskytnout popisovač pro modul, který lze použít k načtení knihovny ladění.</span><span class="sxs-lookup"><span data-stu-id="20bff-108">Allows the debugger to provide a handle to a module which can be used to load a debug library.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="20bff-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="20bff-109">Requirements</span></span>  
 <span data-ttu-id="20bff-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20bff-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20bff-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="20bff-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="20bff-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="20bff-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20bff-113">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20bff-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20bff-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="20bff-114">See also</span></span>

- [<span data-ttu-id="20bff-115">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="20bff-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="20bff-116">Ladění</span><span class="sxs-lookup"><span data-stu-id="20bff-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
