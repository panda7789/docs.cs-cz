---
title: "ICorDebugStringValue::GetString – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStringValue.GetString
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStringValue::GetString
helpviewer_keywords:
- ICorDebugStringValue::GetString method [.NET Framework debugging]
- GetString method, ICorDebugStringValue interface [.NET Framework debugging]
ms.assetid: 2b94bda7-09ee-435d-91b9-c4e31af1896c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 077f8488419cee434a8dc8266b0814dfd4196b03
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugstringvaluegetstring-method"></a><span data-ttu-id="ee9c3-102">ICorDebugStringValue::GetString – metoda</span><span class="sxs-lookup"><span data-stu-id="ee9c3-102">ICorDebugStringValue::GetString Method</span></span>
<span data-ttu-id="ee9c3-103">Získá řetězec, který odkazuje tento ICorDebugStringValue.</span><span class="sxs-lookup"><span data-stu-id="ee9c3-103">Gets the string referenced by this ICorDebugStringValue.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee9c3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ee9c3-104">Syntax</span></span>  
  
```  
HRESULT GetString (  
    [in] ULONG32    cchString,  
    [out] ULONG32   *pcchString,  
    [out, size_is(cchString), length_is(*pcchString)]   
        WCHAR       szString[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ee9c3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ee9c3-105">Parameters</span></span>  
 `cchString`  
 <span data-ttu-id="ee9c3-106">[v] Velikost `szString` pole.</span><span class="sxs-lookup"><span data-stu-id="ee9c3-106">[in] The size of the `szString` array.</span></span>  
  
 `pcchString`  
 <span data-ttu-id="ee9c3-107">[out] Ukazatel na počet znaků, vrátí se v `szString` pole.</span><span class="sxs-lookup"><span data-stu-id="ee9c3-107">[out] A pointer to the number of characters returned in the `szString` array.</span></span>  
  
 `szString`  
 <span data-ttu-id="ee9c3-108">[out] Pole, které ukládá načtené řetězec.</span><span class="sxs-lookup"><span data-stu-id="ee9c3-108">[out] An array that stores the retrieved string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee9c3-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ee9c3-109">Requirements</span></span>  
 <span data-ttu-id="ee9c3-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee9c3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee9c3-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ee9c3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ee9c3-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee9c3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee9c3-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee9c3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
