---
title: ICorDebugBoxValue::GetObject – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugBoxValue.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBoxValue::GetObject
helpviewer_keywords:
- ICorDebugBoxValue::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugBoxValue interface [.NET Framework debugging]
ms.assetid: 3a867a5b-bf94-493f-a4f5-b28685cf5325
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 30038d383e78c23715b844df0bee7c1124885a69
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745218"
---
# <a name="icordebugboxvaluegetobject-method"></a><span data-ttu-id="2c49b-102">ICorDebugBoxValue::GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="2c49b-102">ICorDebugBoxValue::GetObject Method</span></span>
<span data-ttu-id="2c49b-103">Získá zabalené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2c49b-103">Gets the boxed value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c49b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c49b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c49b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2c49b-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="2c49b-106">[out] Ukazatel na adresu objektu ICorDebugObjectValue představující zabalený hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2c49b-106">[out] A pointer to the address of an ICorDebugObjectValue object that represents the boxed value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c49b-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2c49b-107">Requirements</span></span>  
 <span data-ttu-id="2c49b-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c49b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c49b-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2c49b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2c49b-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c49b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c49b-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c49b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
