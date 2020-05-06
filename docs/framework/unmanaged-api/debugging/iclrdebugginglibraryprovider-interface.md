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
ms.openlocfilehash: 77c2011ce677d1bd2823d47740782f48151b408a
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860279"
---
# <a name="iclrdebugginglibraryprovider-interface"></a><span data-ttu-id="7c460-102">ICLRDebuggingLibraryProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7c460-102">ICLRDebuggingLibraryProvider Interface</span></span>
<span data-ttu-id="7c460-103">Obsahuje metodu [metody ProvideLibrary –](iclrdebugginglibraryprovider-providelibrary-method.md) , která získá rozhraní zpětného volání zprostředkovatele knihovny, které umožňuje umístění a načtení knihoven ladění pro Common Language Runtime v konkrétní verzi.</span><span class="sxs-lookup"><span data-stu-id="7c460-103">Includes the [ProvideLibrary Method](iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7c460-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7c460-104">Methods</span></span>  
  
|<span data-ttu-id="7c460-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7c460-105">Method</span></span>|<span data-ttu-id="7c460-106">Popis</span><span class="sxs-lookup"><span data-stu-id="7c460-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7c460-107">ProvideLibrary – metoda</span><span class="sxs-lookup"><span data-stu-id="7c460-107">ProvideLibrary Method</span></span>](iclrdebugginglibraryprovider-providelibrary-method.md)|<span data-ttu-id="7c460-108">Umožňuje ladicímu programu poskytnout popisovač pro modul, který lze použít k načtení knihovny ladění.</span><span class="sxs-lookup"><span data-stu-id="7c460-108">Allows the debugger to provide a handle to a module which can be used to load a debug library.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7c460-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7c460-109">Requirements</span></span>  
 <span data-ttu-id="7c460-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c460-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c460-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7c460-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7c460-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7c460-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c460-113">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c460-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c460-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c460-114">See also</span></span>

- [<span data-ttu-id="7c460-115">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7c460-115">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="7c460-116">Ladění</span><span class="sxs-lookup"><span data-stu-id="7c460-116">Debugging</span></span>](index.md)
