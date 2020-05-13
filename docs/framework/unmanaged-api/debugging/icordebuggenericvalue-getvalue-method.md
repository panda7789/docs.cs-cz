---
title: ICorDebugGenericValue::GetValue – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue.GetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue::GetValue
helpviewer_keywords:
- ICorDebugGenericValue::GetValue method [.NET Framework debugging]
- GetValue method, ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: 4e95d7cb-144d-4ccf-8a69-d605f4744be2
topic_type:
- apiref
ms.openlocfilehash: 646b2661148e38f3c918fc18fce5c9cd0b1134a1
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213020"
---
# <a name="icordebuggenericvaluegetvalue-method"></a><span data-ttu-id="067bd-102">ICorDebugGenericValue::GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="067bd-102">ICorDebugGenericValue::GetValue Method</span></span>
<span data-ttu-id="067bd-103">Zkopíruje hodnotu tohoto obecného do zadané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="067bd-103">Copies the value of this generic into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="067bd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="067bd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue (  
    [out] void     *pTo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="067bd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="067bd-105">Parameters</span></span>  
 `pTo`  
 <span data-ttu-id="067bd-106">mimo Ukazatel na hodnotu, která je reprezentovaná tímto objektem ICorDebugGenericValue.</span><span class="sxs-lookup"><span data-stu-id="067bd-106">[out] A pointer to the value that is represented by this ICorDebugGenericValue object.</span></span> <span data-ttu-id="067bd-107">Hodnota může být jednoduchý typ nebo typ odkazu (tj. ukazatel).</span><span class="sxs-lookup"><span data-stu-id="067bd-107">The value may be a simple type or a reference type (that is, a pointer).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="067bd-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="067bd-108">Requirements</span></span>  
 <span data-ttu-id="067bd-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="067bd-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="067bd-110">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="067bd-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="067bd-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="067bd-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="067bd-112">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="067bd-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
