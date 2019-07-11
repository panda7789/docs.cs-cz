---
title: ICorDebugHandleValue::Dispose – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue.Dispose
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue::Dispose
helpviewer_keywords:
- ICorDebugHandleValue::Dispose method [.NET Framework debugging]
- Dispose method [.NET Framework debugging]
ms.assetid: c1542811-0a7f-4235-bcfd-b24370d6f24b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d21703aa911b5222fff71282e6da26aa5c0e2853
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756854"
---
# <a name="icordebughandlevaluedispose-method"></a><span data-ttu-id="32aab-102">ICorDebugHandleValue::Dispose – metoda</span><span class="sxs-lookup"><span data-stu-id="32aab-102">ICorDebugHandleValue::Dispose Method</span></span>
<span data-ttu-id="32aab-103">Uvolní popisovač odkazuje tento objekt icordebughandlevalue – bez explicitně ukazatel rozhraní.</span><span class="sxs-lookup"><span data-stu-id="32aab-103">Releases the handle referenced by this ICorDebugHandleValue object without explicitly releasing the interface pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32aab-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32aab-104">Syntax</span></span>  
  
```cpp  
HRESULT Dispose ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="32aab-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="32aab-105">Requirements</span></span>  
 <span data-ttu-id="32aab-106">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32aab-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32aab-107">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="32aab-107">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="32aab-108">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32aab-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32aab-109">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32aab-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
