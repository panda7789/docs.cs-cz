---
title: "ICorDebugBoxValue::GetObject – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugBoxValue.GetObject
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugBoxValue::GetObject
helpviewer_keywords:
- ICorDebugBoxValue::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugBoxValue interface [.NET Framework debugging]
ms.assetid: 3a867a5b-bf94-493f-a4f5-b28685cf5325
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 072e5d3ee444444ff9288ffc4243f4a61355f1a9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugboxvaluegetobject-method"></a><span data-ttu-id="29f66-102">ICorDebugBoxValue::GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="29f66-102">ICorDebugBoxValue::GetObject Method</span></span>
<span data-ttu-id="29f66-103">Získá zabalené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="29f66-103">Gets the boxed value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29f66-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29f66-104">Syntax</span></span>  
  
```  
HRESULT GetObject (  
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="29f66-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="29f66-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="29f66-106">[out] Ukazatel na adresu ICorDebugObjectValue objekt, který reprezentuje zabalené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="29f66-106">[out] A pointer to the address of an ICorDebugObjectValue object that represents the boxed value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29f66-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="29f66-107">Requirements</span></span>  
 <span data-ttu-id="29f66-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29f66-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29f66-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="29f66-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29f66-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29f66-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29f66-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29f66-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
