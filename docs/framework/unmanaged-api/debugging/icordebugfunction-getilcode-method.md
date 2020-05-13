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
ms.openlocfilehash: 8c7be2d48a30a9f649c6d86e4edbc10085195b68
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213618"
---
# <a name="icordebugfunctiongetilcode-method"></a><span data-ttu-id="7ced9-102">ICorDebugFunction::GetILCode – metoda</span><span class="sxs-lookup"><span data-stu-id="7ced9-102">ICorDebugFunction::GetILCode Method</span></span>
<span data-ttu-id="7ced9-103">Získá instanci ICorDebugCode, která představuje kód jazyka MSIL (Microsoft Intermediate Language) přidružený k tomuto objektu ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="7ced9-103">Gets the ICorDebugCode instance that represents the Microsoft intermediate language (MSIL) code associated with this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ced9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ced9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ced9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7ced9-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="7ced9-106">mimo Ukazatel na `ICorDebugCode` instanci nebo hodnotu null, pokud funkce nebyla zkompilována do jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="7ced9-106">[out] A pointer to the `ICorDebugCode` instance, or null, if the function was not compiled into MSIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ced9-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7ced9-107">Remarks</span></span>  
 <span data-ttu-id="7ced9-108">Pokud je u této funkce povolená možnost upravit a pokračovat, `GetILCode` Metoda získá kód jazyka MSIL odpovídající upravované verzi kódu této funkce v modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="7ced9-108">If Edit and Continue has been allowed on this function, the `GetILCode` method will get the MSIL code corresponding to this function's edited version of the code in the common language runtime (CLR).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ced9-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7ced9-109">Requirements</span></span>  
 <span data-ttu-id="7ced9-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ced9-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ced9-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7ced9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7ced9-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7ced9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ced9-113">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ced9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
