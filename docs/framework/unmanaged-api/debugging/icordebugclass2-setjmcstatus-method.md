---
title: "ICorDebugClass2::SetJMCStatus – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugClass2.SetJMCStatus
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugClass2::SetJMCStatus
helpviewer_keywords:
- ICorDebugClass2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 077e6c7f-f857-480c-bebb-76ee1de4e8fc
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: da9f61bd9a652b4c8e340ddecdee4b48bbdb086e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugclass2setjmcstatus-method"></a><span data-ttu-id="ac91d-102">ICorDebugClass2::SetJMCStatus – metoda</span><span class="sxs-lookup"><span data-stu-id="ac91d-102">ICorDebugClass2::SetJMCStatus Method</span></span>
<span data-ttu-id="ac91d-103">Pro každou metodu třídy nastaví hodnotu, která určuje, zda je metoda kód definovaný uživatelem.</span><span class="sxs-lookup"><span data-stu-id="ac91d-103">For each method of the class, sets a value that indicates whether the method is user-defined code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac91d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac91d-104">Syntax</span></span>  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ac91d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ac91d-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="ac91d-106">[v] Nastavte na `true` označuje, že metoda uživatelem definované kód; jinak hodnota nastavena na `false`.</span><span class="sxs-lookup"><span data-stu-id="ac91d-106">[in] Set to `true` to indicate that the method is user-defined code; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac91d-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ac91d-107">Remarks</span></span>  
 <span data-ttu-id="ac91d-108">Krokovač právě my kódu (dále jen SVK) přeskočí bez uživatelem definované kódu.</span><span class="sxs-lookup"><span data-stu-id="ac91d-108">A just-my-code (JMC) stepper will skip non-user-defined code.</span></span> <span data-ttu-id="ac91d-109">Uživatelem definované kód musí být podmnožinou debuggable kódu.</span><span class="sxs-lookup"><span data-stu-id="ac91d-109">User-defined code must be a subset of debuggable code.</span></span>  
  
 <span data-ttu-id="ac91d-110">`SetJMCStatus`Vrátí hodnotu HRESULT S_FALSE, pokud se nepodaří nastavit hodnotu pro libovolnou metodu, i když úspěšně nastaví hodnotu pro všechny ostatní metody.</span><span class="sxs-lookup"><span data-stu-id="ac91d-110">`SetJMCStatus` returns an HRESULT value of S_FALSE if it fails to set the value for any method, even if it successfully sets the value for all other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac91d-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ac91d-111">Requirements</span></span>  
 <span data-ttu-id="ac91d-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac91d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac91d-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ac91d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ac91d-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac91d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac91d-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac91d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
