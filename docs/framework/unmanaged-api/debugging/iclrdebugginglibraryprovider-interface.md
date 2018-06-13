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
ms.openlocfilehash: 7537d3d6f741f36ab81d73751963a8539de0a36c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404466"
---
# <a name="iclrdebugginglibraryprovider-interface"></a><span data-ttu-id="f9bfa-102">ICLRDebuggingLibraryProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f9bfa-102">ICLRDebuggingLibraryProvider Interface</span></span>
<span data-ttu-id="f9bfa-103">Zahrnuje [providelibrary – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) metodu, která získá knihovny poskytovatele rozhraní zpětné volání, které umožňuje common language runtime specifické pro verzi ladění lze knihoven najít a načíst na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="f9bfa-103">Includes the [ProvideLibrary Method](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f9bfa-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f9bfa-104">Methods</span></span>  
  
|<span data-ttu-id="f9bfa-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f9bfa-105">Method</span></span>|<span data-ttu-id="f9bfa-106">Popis</span><span class="sxs-lookup"><span data-stu-id="f9bfa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f9bfa-107">ProvideLibrary – metoda</span><span class="sxs-lookup"><span data-stu-id="f9bfa-107">ProvideLibrary Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md)|<span data-ttu-id="f9bfa-108">Umožňuje ladicí program k poskytování popisovač pro modul, který slouží k načtení knihovny ladění.</span><span class="sxs-lookup"><span data-stu-id="f9bfa-108">Allows the debugger to provide a handle to a module which can be used to load a debug library.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f9bfa-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f9bfa-109">Requirements</span></span>  
 <span data-ttu-id="f9bfa-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9bfa-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9bfa-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f9bfa-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f9bfa-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9bfa-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9bfa-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9bfa-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9bfa-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="f9bfa-114">See Also</span></span>  
 [<span data-ttu-id="f9bfa-115">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="f9bfa-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="f9bfa-116">Ladění</span><span class="sxs-lookup"><span data-stu-id="f9bfa-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
