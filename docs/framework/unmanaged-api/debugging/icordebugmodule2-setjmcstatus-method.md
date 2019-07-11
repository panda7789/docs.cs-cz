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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d438123dcefb901098954845596c210e5b76cea6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764103"
---
# <a name="icordebugmodule2setjmcstatus-method"></a><span data-ttu-id="84eed-102">ICorDebugModule2::SetJMCStatus – metoda</span><span class="sxs-lookup"><span data-stu-id="84eed-102">ICorDebugModule2::SetJMCStatus Method</span></span>
<span data-ttu-id="84eed-103">Nastaví stav pouze můj kód (JMC) všech metod všechny třídy v tomto icordebugmodule2 – se zadanou hodnotou, s výjimkou těch, `pTokens` pole, které se nastaví na opačnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="84eed-103">Sets the Just My Code (JMC) status of all methods of all the classes in this ICorDebugModule2 to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84eed-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84eed-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84eed-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="84eed-105">Parameters</span></span>  
 `bIsJustMycode`  
 <span data-ttu-id="84eed-106">[in] Nastavte na `true` Pokud bude ladění; v opačném případě je kód, nastavte na `false`.</span><span class="sxs-lookup"><span data-stu-id="84eed-106">[in] Set to `true` if the code is to be debugged; otherwise, set to `false`.</span></span>  
  
 `cTokens`  
 <span data-ttu-id="84eed-107">[in] Velikost `pTokens` pole.</span><span class="sxs-lookup"><span data-stu-id="84eed-107">[in] The size of the `pTokens` array.</span></span>  
  
 `pTokens`  
 <span data-ttu-id="84eed-108">[in] Pole `mdToken` hodnot, z nichž každý odkazuje na metodu, která budou mít stav JMC nastavena na!`bIsJustMycode`.</span><span class="sxs-lookup"><span data-stu-id="84eed-108">[in] An array of `mdToken` values, each of which refers to a method that will have its JMC status set to !`bIsJustMycode`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84eed-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="84eed-109">Remarks</span></span>  
 <span data-ttu-id="84eed-110">JMC stav každé metody, ve stanoveném `pTokens` pole nastavena na opak `bIsJustMycode` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="84eed-110">The JMC status of each method that is specified in the `pTokens` array is set to the opposite of the `bIsJustMycode` value.</span></span> <span data-ttu-id="84eed-111">Je nastaven stav všech metod v tomto modulu `bIsJustMycode` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="84eed-111">The status of all other methods in this module is set to the `bIsJustMycode` value.</span></span>  
  
 <span data-ttu-id="84eed-112">`SetJMCStatus` Metoda vymaže všechna předchozí nastavení JMC v tomto modulu.</span><span class="sxs-lookup"><span data-stu-id="84eed-112">The `SetJMCStatus` method erases all previous JMC settings in this module.</span></span>  
  
 <span data-ttu-id="84eed-113">`SetJMCStatus` Metoda vrátí hodnotu S_OK HRESULT, pokud všechny funkce byly úspěšně nastavené.</span><span class="sxs-lookup"><span data-stu-id="84eed-113">The `SetJMCStatus` method returns an S_OK HRESULT if all functions were set successfully.</span></span> <span data-ttu-id="84eed-114">Vrátí hodnotu HRESULT CORDBG_E_FUNCTION_NOT_DEBUGGABLE Pokud některé funkce, které jsou označeny `true` nejsou laditelný.</span><span class="sxs-lookup"><span data-stu-id="84eed-114">It returns a CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT if some functions that are marked `true` are not debuggable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84eed-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="84eed-115">Requirements</span></span>  
 <span data-ttu-id="84eed-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84eed-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84eed-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="84eed-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="84eed-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84eed-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84eed-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84eed-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
