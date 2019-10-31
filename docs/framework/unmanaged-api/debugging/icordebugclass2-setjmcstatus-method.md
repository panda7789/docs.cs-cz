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
ms.openlocfilehash: a862dd3f6a9c10c6b3a5a0bb41208d351c4ca9f1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125694"
---
# <a name="icordebugclass2setjmcstatus-method"></a><span data-ttu-id="6a923-102">ICorDebugClass2::SetJMCStatus – metoda</span><span class="sxs-lookup"><span data-stu-id="6a923-102">ICorDebugClass2::SetJMCStatus Method</span></span>
<span data-ttu-id="6a923-103">Pro každou metodu třídy nastaví hodnotu, která označuje, zda je metoda uživatelem definovaný kód.</span><span class="sxs-lookup"><span data-stu-id="6a923-103">For each method of the class, sets a value that indicates whether the method is user-defined code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a923-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a923-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a923-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6a923-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="6a923-106">pro Nastavte na `true` pro indikaci, že metoda je uživatelsky definovaný kód; v opačném případě nastavte na `false`.</span><span class="sxs-lookup"><span data-stu-id="6a923-106">[in] Set to `true` to indicate that the method is user-defined code; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a923-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6a923-107">Remarks</span></span>  
 <span data-ttu-id="6a923-108">JMC (Just-The-Code) stepper přeskočí neuživatelsky definovaný kód.</span><span class="sxs-lookup"><span data-stu-id="6a923-108">A just-my-code (JMC) stepper will skip non-user-defined code.</span></span> <span data-ttu-id="6a923-109">Uživatelsky definovaný kód musí být podmnožinou laděného kódu.</span><span class="sxs-lookup"><span data-stu-id="6a923-109">User-defined code must be a subset of debuggable code.</span></span>  
  
 <span data-ttu-id="6a923-110">`SetJMCStatus` vrátí hodnotu HRESULT S_FALSE, pokud se nepodaří nastavit hodnotu pro jakoukoliv metodu, i když úspěšně nastaví hodnotu pro všechny ostatní metody.</span><span class="sxs-lookup"><span data-stu-id="6a923-110">`SetJMCStatus` returns an HRESULT value of S_FALSE if it fails to set the value for any method, even if it successfully sets the value for all other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a923-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6a923-111">Requirements</span></span>  
 <span data-ttu-id="6a923-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a923-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a923-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6a923-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a923-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6a923-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a923-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a923-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
