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
ms.openlocfilehash: cfc8800915009912716ec2ed9044a633a8ad0582
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401742"
---
# <a name="icordebugboxvaluegetobject-method"></a><span data-ttu-id="88ef2-102">ICorDebugBoxValue::GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="88ef2-102">ICorDebugBoxValue::GetObject Method</span></span>
<span data-ttu-id="88ef2-103">Získá zabalené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="88ef2-103">Gets the boxed value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88ef2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88ef2-104">Syntax</span></span>  
  
```  
HRESULT GetObject (  
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="88ef2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="88ef2-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="88ef2-106">[out] Ukazatel na adresu ICorDebugObjectValue objekt, který reprezentuje zabalené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="88ef2-106">[out] A pointer to the address of an ICorDebugObjectValue object that represents the boxed value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88ef2-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="88ef2-107">Requirements</span></span>  
 <span data-ttu-id="88ef2-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88ef2-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88ef2-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="88ef2-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="88ef2-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="88ef2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88ef2-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88ef2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
