---
title: ICorDebugModule2::SetJMCStatus – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::SetJMCStatus
helpviewer_keywords:
- SetJMCStatus method, ICorDebugModule2 interface [.NET Framework debugging]
- ICorDebugModule2::SetJMCStatus method [.NET Framework debugging]
ms.assetid: 8c6d2089-4dbb-4715-b9e9-2a4491c8c9ce
topic_type:
- apiref
ms.openlocfilehash: d5109043a8601d7997f52e88ea472644f1b9ca03
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208769"
---
# <a name="icordebugmodule2setjmcstatus-method"></a><span data-ttu-id="87a96-102">ICorDebugModule2::SetJMCStatus – metoda</span><span class="sxs-lookup"><span data-stu-id="87a96-102">ICorDebugModule2::SetJMCStatus Method</span></span>
<span data-ttu-id="87a96-103">Nastaví Pouze můj kód (JMC) pro všechny metody všech tříd v této ICorDebugModule2 na zadanou hodnotu, s výjimkou těch v `pTokens` poli, které nastaví na opačnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="87a96-103">Sets the Just My Code (JMC) status of all methods of all the classes in this ICorDebugModule2 to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87a96-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87a96-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87a96-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="87a96-105">Parameters</span></span>  
 `bIsJustMycode`  
 <span data-ttu-id="87a96-106">pro Nastavte na, `true` Pokud má být kód laděn. jinak nastavte na `false` .</span><span class="sxs-lookup"><span data-stu-id="87a96-106">[in] Set to `true` if the code is to be debugged; otherwise, set to `false`.</span></span>  
  
 `cTokens`  
 <span data-ttu-id="87a96-107">pro Velikost `pTokens` pole.</span><span class="sxs-lookup"><span data-stu-id="87a96-107">[in] The size of the `pTokens` array.</span></span>  
  
 `pTokens`  
 <span data-ttu-id="87a96-108">pro Pole `mdToken` hodnot, z nichž každá odkazuje na metodu, která bude mít stav JMC nastaven na! `bIsJustMycode` .</span><span class="sxs-lookup"><span data-stu-id="87a96-108">[in] An array of `mdToken` values, each of which refers to a method that will have its JMC status set to !`bIsJustMycode`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87a96-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="87a96-109">Remarks</span></span>  
 <span data-ttu-id="87a96-110">Stav JMC jednotlivých metod, které jsou zadány v `pTokens` poli, je nastaven na opak `bIsJustMycode` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="87a96-110">The JMC status of each method that is specified in the `pTokens` array is set to the opposite of the `bIsJustMycode` value.</span></span> <span data-ttu-id="87a96-111">Stav všech ostatních metod v tomto modulu je nastaven na `bIsJustMycode` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="87a96-111">The status of all other methods in this module is set to the `bIsJustMycode` value.</span></span>  
  
 <span data-ttu-id="87a96-112">`SetJMCStatus`Metoda vymaže všechna předchozí nastavení JMC v tomto modulu.</span><span class="sxs-lookup"><span data-stu-id="87a96-112">The `SetJMCStatus` method erases all previous JMC settings in this module.</span></span>  
  
 <span data-ttu-id="87a96-113">`SetJMCStatus`Metoda vrátí S_OK HRESULT, pokud byly všechny funkce nastaveny úspěšně.</span><span class="sxs-lookup"><span data-stu-id="87a96-113">The `SetJMCStatus` method returns an S_OK HRESULT if all functions were set successfully.</span></span> <span data-ttu-id="87a96-114">Vrátí CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT, pokud některé funkce, které jsou označeny, `true` nelze ladit.</span><span class="sxs-lookup"><span data-stu-id="87a96-114">It returns a CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT if some functions that are marked `true` are not debuggable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87a96-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="87a96-115">Requirements</span></span>  
 <span data-ttu-id="87a96-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87a96-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87a96-117">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="87a96-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="87a96-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="87a96-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87a96-119">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87a96-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
