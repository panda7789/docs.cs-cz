---
title: "ICLRDebuggingLibraryProvider – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebuggingLibraryProvider
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDebuggingLibraryProvider
helpviewer_keywords: ICLRDebuggingLibraryProvider interface [.NET Framework debugging]
ms.assetid: 67739617-6add-41a9-9de5-a3200c3109ce
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 82ed352e3f5fb83a2f464f2d82ff9a9885227fe7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdebugginglibraryprovider-interface"></a><span data-ttu-id="756d7-102">ICLRDebuggingLibraryProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="756d7-102">ICLRDebuggingLibraryProvider Interface</span></span>
<span data-ttu-id="756d7-103">Zahrnuje [providelibrary – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) metodu, která získá knihovny poskytovatele rozhraní zpětné volání, které umožňuje common language runtime specifické pro verzi ladění lze knihoven najít a načíst na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="756d7-103">Includes the [ProvideLibrary Method](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="756d7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="756d7-104">Methods</span></span>  
  
|<span data-ttu-id="756d7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="756d7-105">Method</span></span>|<span data-ttu-id="756d7-106">Popis</span><span class="sxs-lookup"><span data-stu-id="756d7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="756d7-107">Providelibrary – metoda</span><span class="sxs-lookup"><span data-stu-id="756d7-107">ProvideLibrary Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md)|<span data-ttu-id="756d7-108">Umožňuje ladicí program k poskytování popisovač pro modul, který slouží k načtení knihovny ladění.</span><span class="sxs-lookup"><span data-stu-id="756d7-108">Allows the debugger to provide a handle to a module which can be used to load a debug library.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="756d7-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="756d7-109">Requirements</span></span>  
 <span data-ttu-id="756d7-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="756d7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="756d7-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="756d7-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="756d7-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="756d7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="756d7-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="756d7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="756d7-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="756d7-114">See Also</span></span>  
 [<span data-ttu-id="756d7-115">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="756d7-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="756d7-116">Ladění</span><span class="sxs-lookup"><span data-stu-id="756d7-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
