---
title: "ICorDebugModule2::SetJMCStatus – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule2.SetJMCStatus
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule2::SetJMCStatus
helpviewer_keywords:
- SetJMCStatus method, ICorDebugModule2 interface [.NET Framework debugging]
- ICorDebugModule2::SetJMCStatus method [.NET Framework debugging]
ms.assetid: 8c6d2089-4dbb-4715-b9e9-2a4491c8c9ce
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ca4b53acc69d0a56b94526de0c3b16fd1abde077
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodule2setjmcstatus-method"></a><span data-ttu-id="858c3-102">ICorDebugModule2::SetJMCStatus – metoda</span><span class="sxs-lookup"><span data-stu-id="858c3-102">ICorDebugModule2::SetJMCStatus Method</span></span>
<span data-ttu-id="858c3-103">Nastaví stav pouze můj kód (SVK) ze všech metod všechny třídy v této ICorDebugModule2 se zadanou hodnotou, s výjimkou těch, `pTokens` pole, které se nastaví na opačné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="858c3-103">Sets the Just My Code (JMC) status of all methods of all the classes in this ICorDebugModule2 to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="858c3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="858c3-104">Syntax</span></span>  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="858c3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="858c3-105">Parameters</span></span>  
 `bIsJustMycode`  
 <span data-ttu-id="858c3-106">[v] Nastavte na `true` Pokud kód je být vyladěnou jinak, nastavit `false`.</span><span class="sxs-lookup"><span data-stu-id="858c3-106">[in] Set to `true` if the code is to be debugged; otherwise, set to `false`.</span></span>  
  
 `cTokens`  
 <span data-ttu-id="858c3-107">[v] Velikost `pTokens` pole.</span><span class="sxs-lookup"><span data-stu-id="858c3-107">[in] The size of the `pTokens` array.</span></span>  
  
 `pTokens`  
 <span data-ttu-id="858c3-108">[v] Pole `mdToken` hodnoty, každý z nich odkazuje na metodu, která bude mít SVK stav nastavit na!`bIsJustMycode`.</span><span class="sxs-lookup"><span data-stu-id="858c3-108">[in] An array of `mdToken` values, each of which refers to a method that will have its JMC status set to !`bIsJustMycode`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="858c3-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="858c3-109">Remarks</span></span>  
 <span data-ttu-id="858c3-110">Stav SVK každá metoda, která je zadána v `pTokens` pole je nastaven na opakem `bIsJustMycode` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="858c3-110">The JMC status of each method that is specified in the `pTokens` array is set to the opposite of the `bIsJustMycode` value.</span></span> <span data-ttu-id="858c3-111">Stav všech metod v tomto modulu nastaven na `bIsJustMycode` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="858c3-111">The status of all other methods in this module is set to the `bIsJustMycode` value.</span></span>  
  
 <span data-ttu-id="858c3-112">`SetJMCStatus` Metoda vymaže všechna předchozí nastavení SVK v tomto modulu.</span><span class="sxs-lookup"><span data-stu-id="858c3-112">The `SetJMCStatus` method erases all previous JMC settings in this module.</span></span>  
  
 <span data-ttu-id="858c3-113">`SetJMCStatus` Metoda vrátí hodnotu S_OK HRESULT všechny funkce byla úspěšně nastavena.</span><span class="sxs-lookup"><span data-stu-id="858c3-113">The `SetJMCStatus` method returns an S_OK HRESULT if all functions were set successfully.</span></span> <span data-ttu-id="858c3-114">Vrátí CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT, pokud se některé funkce, které jsou označeny `true` nejsou debuggable.</span><span class="sxs-lookup"><span data-stu-id="858c3-114">It returns a CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT if some functions that are marked `true` are not debuggable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="858c3-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="858c3-115">Requirements</span></span>  
 <span data-ttu-id="858c3-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="858c3-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="858c3-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="858c3-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="858c3-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="858c3-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="858c3-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="858c3-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
