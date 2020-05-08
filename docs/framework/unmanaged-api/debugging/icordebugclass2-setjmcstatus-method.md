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
ms.openlocfilehash: 9fb2f960098e970b4d3d9f0be499f4d9fda6558e
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893899"
---
# <a name="icordebugclass2setjmcstatus-method"></a><span data-ttu-id="153de-102">ICorDebugClass2::SetJMCStatus – metoda</span><span class="sxs-lookup"><span data-stu-id="153de-102">ICorDebugClass2::SetJMCStatus Method</span></span>
<span data-ttu-id="153de-103">Pro každou metodu třídy nastaví hodnotu, která označuje, zda je metoda uživatelem definovaný kód.</span><span class="sxs-lookup"><span data-stu-id="153de-103">For each method of the class, sets a value that indicates whether the method is user-defined code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="153de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="153de-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="153de-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="153de-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="153de-106">pro Nastavte na `true` k označení toho, že metoda je uživatelsky definovaný kód; v opačném případě `false`nastavte na.</span><span class="sxs-lookup"><span data-stu-id="153de-106">[in] Set to `true` to indicate that the method is user-defined code; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="153de-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="153de-107">Remarks</span></span>  
 <span data-ttu-id="153de-108">JMC (Just-The-Code) stepper přeskočí neuživatelsky definovaný kód.</span><span class="sxs-lookup"><span data-stu-id="153de-108">A just-my-code (JMC) stepper will skip non-user-defined code.</span></span> <span data-ttu-id="153de-109">Uživatelsky definovaný kód musí být podmnožinou laděného kódu.</span><span class="sxs-lookup"><span data-stu-id="153de-109">User-defined code must be a subset of debuggable code.</span></span>  
  
 <span data-ttu-id="153de-110">`SetJMCStatus`Vrátí hodnotu HRESULT S_FALSE, pokud se nepodaří nastavit hodnotu pro jakoukoliv metodu, i když úspěšně nastaví hodnotu pro všechny ostatní metody.</span><span class="sxs-lookup"><span data-stu-id="153de-110">`SetJMCStatus` returns an HRESULT value of S_FALSE if it fails to set the value for any method, even if it successfully sets the value for all other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="153de-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="153de-111">Requirements</span></span>  
 <span data-ttu-id="153de-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="153de-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="153de-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="153de-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="153de-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="153de-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="153de-115">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="153de-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
