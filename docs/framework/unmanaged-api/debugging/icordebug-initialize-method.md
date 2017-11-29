---
title: "ICorDebug::Initialize – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.Initialize
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug::Initialize
helpviewer_keywords:
- Initialize method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Initialize method [.NET Framework debugging]
ms.assetid: 6fae3b23-5c9f-47c0-85d8-6bb75e050786
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 12665472b201e6d89be9c5cc6c78b82de067d6a6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebuginitialize-method"></a><span data-ttu-id="18234-102">ICorDebug::Initialize – metoda</span><span class="sxs-lookup"><span data-stu-id="18234-102">ICorDebug::Initialize Method</span></span>
<span data-ttu-id="18234-103">Inicializuje `ICorDebug` objektu.</span><span class="sxs-lookup"><span data-stu-id="18234-103">Initializes the `ICorDebug` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18234-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18234-104">Syntax</span></span>  
  
```  
HRESULT Initialize ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="18234-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="18234-105">Remarks</span></span>  
 <span data-ttu-id="18234-106">Ladicí program musí volat `Initialize` při vytváření času k chybě při inicializaci ladění služeb.</span><span class="sxs-lookup"><span data-stu-id="18234-106">The debugger must call `Initialize` at creation time to initialize the debugging services.</span></span> <span data-ttu-id="18234-107">Tato metoda musí být volána před jinou metodu na `ICorDebug` je volána.</span><span class="sxs-lookup"><span data-stu-id="18234-107">This method must be called before any other method on `ICorDebug` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18234-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="18234-108">Requirements</span></span>  
 <span data-ttu-id="18234-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18234-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18234-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="18234-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="18234-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="18234-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="18234-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18234-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18234-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="18234-113">See Also</span></span>  
 [<span data-ttu-id="18234-114">ICorDebug – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="18234-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
