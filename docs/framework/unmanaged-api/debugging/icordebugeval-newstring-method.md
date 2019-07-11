---
title: ICorDebugEval::NewString – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewString
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewString
helpviewer_keywords:
- NewString method [.NET Framework debugging]
- ICorDebugEval::NewString method [.NET Framework debugging]
ms.assetid: 29e7a14b-d50e-4852-bfda-011b76c0c9ee
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 50a18f435063b74b837dbfe9e4f1d986bb735039
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753341"
---
# <a name="icordebugevalnewstring-method"></a><span data-ttu-id="9e495-102">ICorDebugEval::NewString – metoda</span><span class="sxs-lookup"><span data-stu-id="9e495-102">ICorDebugEval::NewString Method</span></span>
<span data-ttu-id="9e495-103">Přidělí novou instanci řetězce se zadaným obsahem.</span><span class="sxs-lookup"><span data-stu-id="9e495-103">Allocates a new string instance with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e495-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9e495-104">Syntax</span></span>  
  
```cpp  
HRESULT NewString (  
    [in] LPCWSTR   string  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e495-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9e495-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="9e495-106">[in] Ukazatel na obsah řetězce.</span><span class="sxs-lookup"><span data-stu-id="9e495-106">[in] Pointer to the contents for the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e495-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9e495-107">Remarks</span></span>  
 <span data-ttu-id="9e495-108">Řetězec se vždy vytvoří v aplikační doméně, ve které vlákno právě probíhá.</span><span class="sxs-lookup"><span data-stu-id="9e495-108">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e495-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9e495-109">Requirements</span></span>  
 <span data-ttu-id="9e495-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e495-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e495-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9e495-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9e495-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e495-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e495-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e495-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
