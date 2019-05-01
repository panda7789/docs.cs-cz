---
title: ICorDebugFunction::GetILCode – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetILCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetILCode
helpviewer_keywords:
- ICorDebugFunction::GetILCode method [.NET Framework debugging]
- GetILCode method [.NET Framework debugging]
ms.assetid: f794dd47-a7cd-47f6-96e9-a41a4dae8e72
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f34a2fe2bb1f92e75f77c086b03776ec59495600
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995745"
---
# <a name="icordebugfunctiongetilcode-method"></a><span data-ttu-id="52403-102">ICorDebugFunction::GetILCode – metoda</span><span class="sxs-lookup"><span data-stu-id="52403-102">ICorDebugFunction::GetILCode Method</span></span>
<span data-ttu-id="52403-103">Získá instanci ICorDebugCode, který představuje kód Microsoft intermediate language (MSIL) asociovaném s tímto objektem ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="52403-103">Gets the ICorDebugCode instance that represents the Microsoft intermediate language (MSIL) code associated with this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52403-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52403-104">Syntax</span></span>  
  
```  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52403-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="52403-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="52403-106">[out] Ukazatel `ICorDebugCode` instanci, nebo hodnotu null, pokud funkce nebyla zkompilována do jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="52403-106">[out] A pointer to the `ICorDebugCode` instance, or null, if the function was not compiled into MSIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52403-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="52403-107">Remarks</span></span>  
 <span data-ttu-id="52403-108">Pokud u této funkce bylo povoleno upravit a pokračovat `GetILCode` metoda se zobrazí kód jazyka MSIL, který odpovídá této funkce upravenou verzi kódu v modulu common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="52403-108">If Edit and Continue has been allowed on this function, the `GetILCode` method will get the MSIL code corresponding to this function's edited version of the code in the common language runtime (CLR).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52403-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="52403-109">Requirements</span></span>  
 <span data-ttu-id="52403-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52403-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52403-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="52403-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="52403-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52403-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52403-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52403-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
