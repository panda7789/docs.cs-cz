---
title: "ICorDebugFunction::GetILCode – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction.GetILCode
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction::GetILCode
helpviewer_keywords:
- ICorDebugFunction::GetILCode method [.NET Framework debugging]
- GetILCode method [.NET Framework debugging]
ms.assetid: f794dd47-a7cd-47f6-96e9-a41a4dae8e72
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: da955f6eb8e7480fb23192e1a77341166dd40f3b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugfunctiongetilcode-method"></a><span data-ttu-id="3a596-102">ICorDebugFunction::GetILCode – metoda</span><span class="sxs-lookup"><span data-stu-id="3a596-102">ICorDebugFunction::GetILCode Method</span></span>
<span data-ttu-id="3a596-103">Získá instanci ICorDebugCode, která představuje kód Microsoft (MSIL intermediate language) přidružené k tomuto objektu ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="3a596-103">Gets the ICorDebugCode instance that represents the Microsoft intermediate language (MSIL) code associated with this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a596-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3a596-104">Syntax</span></span>  
  
```  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3a596-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3a596-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="3a596-106">[out] Ukazatel `ICorDebugCode` instanci, nebo hodnotu null, pokud funkce nebyla zkompilovat do MSIL.</span><span class="sxs-lookup"><span data-stu-id="3a596-106">[out] A pointer to the `ICorDebugCode` instance, or null, if the function was not compiled into MSIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a596-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3a596-107">Remarks</span></span>  
 <span data-ttu-id="3a596-108">Pokud k této funkci byl povolen upravit a pokračovat `GetILCode` metoda získá kód MSIL odpovídající této funkce upravenou verzi kód v common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="3a596-108">If Edit and Continue has been allowed on this function, the `GetILCode` method will get the MSIL code corresponding to this function's edited version of the code in the common language runtime (CLR).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a596-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3a596-109">Requirements</span></span>  
 <span data-ttu-id="3a596-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a596-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a596-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3a596-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3a596-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a596-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a596-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a596-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
