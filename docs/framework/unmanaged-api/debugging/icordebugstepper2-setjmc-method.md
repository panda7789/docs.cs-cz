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
ms.openlocfilehash: ab1351af042aba5042cc7a04614bc3cf14f7d7ae
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379465"
---
# <a name="icordebugstepper2setjmc-method"></a><span data-ttu-id="20355-102">ICorDebugStepper2::SetJMC – metoda</span><span class="sxs-lookup"><span data-stu-id="20355-102">ICorDebugStepper2::SetJMC Method</span></span>
<span data-ttu-id="20355-103">Nastaví hodnotu, která určuje, zda jsou tyto ICorDebugStepper kroky pouze prostřednictvím kódu, který je vytvořen vývojářem aplikace.</span><span class="sxs-lookup"><span data-stu-id="20355-103">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span> <span data-ttu-id="20355-104">Tento proces je také známý jako ladění pouze můj kód (JMC).</span><span class="sxs-lookup"><span data-stu-id="20355-104">This process is also known as just my code (JMC) debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20355-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20355-105">Syntax</span></span>  
  
```cpp  
HRESULT SetJMC (  
    [in] BOOL    fIsJMCStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20355-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="20355-106">Parameters</span></span>  
 `fIsJMCStepper`  
 <span data-ttu-id="20355-107">pro Nastavte na `true` krok pouze pomocí kódu, který je vytvořen vývojářem aplikace. v opačném případě nastavte na `false` .</span><span class="sxs-lookup"><span data-stu-id="20355-107">[in] Set to `true` to step only through code that is authored by an application's developer; otherwise, set to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20355-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="20355-108">Requirements</span></span>  
 <span data-ttu-id="20355-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20355-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20355-110">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="20355-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="20355-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="20355-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20355-112">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20355-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
