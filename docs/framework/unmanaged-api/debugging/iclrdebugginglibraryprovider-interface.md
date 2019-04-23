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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c62079a87c09bcbe09167a137fd39530652ae3e5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59106337"
---
# <a name="iclrdebugginglibraryprovider-interface"></a><span data-ttu-id="0eed6-102">ICLRDebuggingLibraryProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0eed6-102">ICLRDebuggingLibraryProvider Interface</span></span>
<span data-ttu-id="0eed6-103">Zahrnuje [ProvideLibrary – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) metodu, která získá rozhraní zpětného volání, které umožňuje knihovnám ladění specifickým pro verzi modulu runtime k vyhledání a načtení na požádání zprostředkovatele knihovny.</span><span class="sxs-lookup"><span data-stu-id="0eed6-103">Includes the [ProvideLibrary Method](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0eed6-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0eed6-104">Methods</span></span>  
  
|<span data-ttu-id="0eed6-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0eed6-105">Method</span></span>|<span data-ttu-id="0eed6-106">Popis</span><span class="sxs-lookup"><span data-stu-id="0eed6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0eed6-107">ProvideLibrary – metoda</span><span class="sxs-lookup"><span data-stu-id="0eed6-107">ProvideLibrary Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md)|<span data-ttu-id="0eed6-108">Umožňuje ladicí program poskytuje popisovač pro modul, který slouží k načtení knihovny ladění.</span><span class="sxs-lookup"><span data-stu-id="0eed6-108">Allows the debugger to provide a handle to a module which can be used to load a debug library.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0eed6-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0eed6-109">Requirements</span></span>  
 <span data-ttu-id="0eed6-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0eed6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0eed6-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0eed6-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0eed6-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0eed6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0eed6-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0eed6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0eed6-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0eed6-114">See also</span></span>

- [<span data-ttu-id="0eed6-115">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="0eed6-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="0eed6-116">Ladění</span><span class="sxs-lookup"><span data-stu-id="0eed6-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
