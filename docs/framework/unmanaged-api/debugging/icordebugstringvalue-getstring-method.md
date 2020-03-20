---
title: ICorDebugStringValue::GetString – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue.GetString
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue::GetString
helpviewer_keywords:
- ICorDebugStringValue::GetString method [.NET Framework debugging]
- GetString method, ICorDebugStringValue interface [.NET Framework debugging]
ms.assetid: 2b94bda7-09ee-435d-91b9-c4e31af1896c
topic_type:
- apiref
ms.openlocfilehash: e23133176cbd703a58c92f9bf1ead530b0bbb8a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178503"
---
# <a name="icordebugstringvaluegetstring-method"></a><span data-ttu-id="b7a26-102">ICorDebugStringValue::GetString – metoda</span><span class="sxs-lookup"><span data-stu-id="b7a26-102">ICorDebugStringValue::GetString Method</span></span>
<span data-ttu-id="b7a26-103">Získá řetězec odkazuje tento ICorDebugStringValue.</span><span class="sxs-lookup"><span data-stu-id="b7a26-103">Gets the string referenced by this ICorDebugStringValue.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7a26-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7a26-104">Syntax</span></span>  
  
```cpp  
HRESULT GetString (  
    [in] ULONG32    cchString,  
    [out] ULONG32   *pcchString,  
    [out, size_is(cchString), length_is(*pcchString)]
        WCHAR       szString[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7a26-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b7a26-105">Parameters</span></span>  
 `cchString`  
 <span data-ttu-id="b7a26-106">[v] Velikost `szString` pole.</span><span class="sxs-lookup"><span data-stu-id="b7a26-106">[in] The size of the `szString` array.</span></span>  
  
 `pcchString`  
 <span data-ttu-id="b7a26-107">[out] Ukazatel na počet znaků vrácených `szString` v poli.</span><span class="sxs-lookup"><span data-stu-id="b7a26-107">[out] A pointer to the number of characters returned in the `szString` array.</span></span>  
  
 `szString`  
 <span data-ttu-id="b7a26-108">[out] Pole, které ukládá načtený řetězec.</span><span class="sxs-lookup"><span data-stu-id="b7a26-108">[out] An array that stores the retrieved string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7a26-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b7a26-109">Requirements</span></span>  
 <span data-ttu-id="b7a26-110">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7a26-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7a26-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7a26-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7a26-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7a26-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7a26-113">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7a26-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
