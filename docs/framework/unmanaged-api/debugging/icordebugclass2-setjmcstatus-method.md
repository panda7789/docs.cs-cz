---
title: ICorDebugClass2::SetJMCStatus – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugClass2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2::SetJMCStatus
helpviewer_keywords:
- ICorDebugClass2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 077e6c7f-f857-480c-bebb-76ee1de4e8fc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 23f248625753c15a4798ea69a1eb3b377b79f95d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747750"
---
# <a name="icordebugclass2setjmcstatus-method"></a><span data-ttu-id="5dddb-102">ICorDebugClass2::SetJMCStatus – metoda</span><span class="sxs-lookup"><span data-stu-id="5dddb-102">ICorDebugClass2::SetJMCStatus Method</span></span>
<span data-ttu-id="5dddb-103">Pro každou metodu třídy nastaví hodnotu, která určuje, zda je metoda uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="5dddb-103">For each method of the class, sets a value that indicates whether the method is user-defined code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5dddb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5dddb-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5dddb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5dddb-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="5dddb-106">[in] Nastavte na `true` k označení, že metoda je uživatelem definovaný kód; v opačném případě nastavte na `false`.</span><span class="sxs-lookup"><span data-stu-id="5dddb-106">[in] Set to `true` to indicate that the method is user-defined code; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5dddb-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5dddb-107">Remarks</span></span>  
 <span data-ttu-id="5dddb-108">Krokovač just my kód (JMC) přeskočí bez uživatelem definovaný kód.</span><span class="sxs-lookup"><span data-stu-id="5dddb-108">A just-my-code (JMC) stepper will skip non-user-defined code.</span></span> <span data-ttu-id="5dddb-109">Uživatelský kód musí být podmnožinou laditelný kód.</span><span class="sxs-lookup"><span data-stu-id="5dddb-109">User-defined code must be a subset of debuggable code.</span></span>  
  
 <span data-ttu-id="5dddb-110">`SetJMCStatus` Pokud se nezdaří nastavit hodnotu pro libovolnou metodu, i v případě, že úspěšně nastaví hodnotu pro všechny ostatní metody, vrátí hodnotu HRESULT S_FALSE.</span><span class="sxs-lookup"><span data-stu-id="5dddb-110">`SetJMCStatus` returns an HRESULT value of S_FALSE if it fails to set the value for any method, even if it successfully sets the value for all other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5dddb-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5dddb-111">Requirements</span></span>  
 <span data-ttu-id="5dddb-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5dddb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5dddb-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5dddb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5dddb-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5dddb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5dddb-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5dddb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
