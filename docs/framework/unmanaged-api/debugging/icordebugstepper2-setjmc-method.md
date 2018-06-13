---
title: ICorDebugStepper2::SetJMC – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStepper2.SetJMC
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper2::SetJMC
helpviewer_keywords:
- ICorDebugStepper2::SetJMC method [.NET Framework debugging]
- SetJMC method [.NET Framework debugging]
ms.assetid: f5cdc135-6db4-4b32-9dd1-260ec58b774f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ad05d2f6226d570fc854fb48575851dd718e410
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418194"
---
# <a name="icordebugstepper2setjmc-method"></a><span data-ttu-id="1f8dd-102">ICorDebugStepper2::SetJMC – metoda</span><span class="sxs-lookup"><span data-stu-id="1f8dd-102">ICorDebugStepper2::SetJMC Method</span></span>
<span data-ttu-id="1f8dd-103">Nastaví hodnotu, která určuje, zda tento ICorDebugStepper kroky pouze prostřednictvím kód, který je vytvořená vývojáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="1f8dd-103">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span> <span data-ttu-id="1f8dd-104">Tento proces se označuje také jako můj (dále jen SVK) ladění kódu.</span><span class="sxs-lookup"><span data-stu-id="1f8dd-104">This process is also known as just my code (JMC) debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f8dd-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f8dd-105">Syntax</span></span>  
  
```  
HRESULT SetJMC (  
    [in] BOOL    fIsJMCStepper  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1f8dd-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1f8dd-106">Parameters</span></span>  
 `fIsJMCStepper`  
 <span data-ttu-id="1f8dd-107">[v] Nastavte na `true` ke kroku pouze prostřednictvím kódu, která je vytvořená aplikace vývojáře, jinak hodnota nastavena na `false`.</span><span class="sxs-lookup"><span data-stu-id="1f8dd-107">[in] Set to `true` to step only through code that is authored by an application's developer; otherwise, set to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f8dd-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1f8dd-108">Requirements</span></span>  
 <span data-ttu-id="1f8dd-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f8dd-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f8dd-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1f8dd-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f8dd-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f8dd-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f8dd-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f8dd-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
