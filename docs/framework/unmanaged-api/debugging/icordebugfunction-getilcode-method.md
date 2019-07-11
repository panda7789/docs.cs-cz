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
ms.openlocfilehash: e32ce10b708afa5741d83cbd05f14accb4b2014f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754678"
---
# <a name="icordebugfunctiongetilcode-method"></a><span data-ttu-id="9e09a-102">ICorDebugFunction::GetILCode – metoda</span><span class="sxs-lookup"><span data-stu-id="9e09a-102">ICorDebugFunction::GetILCode Method</span></span>
<span data-ttu-id="9e09a-103">Získá instanci ICorDebugCode, který představuje kód Microsoft intermediate language (MSIL) asociovaném s tímto objektem ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="9e09a-103">Gets the ICorDebugCode instance that represents the Microsoft intermediate language (MSIL) code associated with this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e09a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9e09a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e09a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9e09a-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="9e09a-106">[out] Ukazatel `ICorDebugCode` instanci, nebo hodnotu null, pokud funkce nebyla zkompilována do jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="9e09a-106">[out] A pointer to the `ICorDebugCode` instance, or null, if the function was not compiled into MSIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e09a-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9e09a-107">Remarks</span></span>  
 <span data-ttu-id="9e09a-108">Pokud u této funkce bylo povoleno upravit a pokračovat `GetILCode` metoda se zobrazí kód jazyka MSIL, který odpovídá této funkce upravenou verzi kódu v modulu common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="9e09a-108">If Edit and Continue has been allowed on this function, the `GetILCode` method will get the MSIL code corresponding to this function's edited version of the code in the common language runtime (CLR).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e09a-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9e09a-109">Requirements</span></span>  
 <span data-ttu-id="9e09a-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e09a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e09a-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9e09a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9e09a-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e09a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e09a-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e09a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
