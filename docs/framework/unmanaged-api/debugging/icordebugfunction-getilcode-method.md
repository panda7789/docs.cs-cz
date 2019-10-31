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
ms.openlocfilehash: c2ce4b95de75bef3928e144656b565676568caa0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137902"
---
# <a name="icordebugfunctiongetilcode-method"></a><span data-ttu-id="f5465-102">ICorDebugFunction::GetILCode – metoda</span><span class="sxs-lookup"><span data-stu-id="f5465-102">ICorDebugFunction::GetILCode Method</span></span>
<span data-ttu-id="f5465-103">Získá instanci ICorDebugCode, která představuje kód jazyka MSIL (Microsoft Intermediate Language) přidružený k tomuto objektu ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="f5465-103">Gets the ICorDebugCode instance that represents the Microsoft intermediate language (MSIL) code associated with this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5465-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5465-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5465-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5465-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="f5465-106">mimo Ukazatel na instanci `ICorDebugCode` nebo hodnotu null, pokud funkce nebyla zkompilována do jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="f5465-106">[out] A pointer to the `ICorDebugCode` instance, or null, if the function was not compiled into MSIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5465-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f5465-107">Remarks</span></span>  
 <span data-ttu-id="f5465-108">Pokud je u této funkce povolená možnost upravit a pokračovat, metoda `GetILCode` získá kód jazyka MSIL odpovídající upravované verzi kódu této funkce v modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="f5465-108">If Edit and Continue has been allowed on this function, the `GetILCode` method will get the MSIL code corresponding to this function's edited version of the code in the common language runtime (CLR).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5465-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f5465-109">Requirements</span></span>  
 <span data-ttu-id="f5465-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5465-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5465-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f5465-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5465-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f5465-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5465-113">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5465-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
