---
title: ICorDebugEval2::CreateValueForType – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CreateValueForType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CreateValueForType
helpviewer_keywords:
- CreateValueForType method [.NET Framework debugging]
- ICorDebugEval2::CreateValueForType method [.NET Framework debugging]
ms.assetid: ea38ae20-7e0a-427a-be77-d78fae719d82
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 683457c249915708becadaeda9dec265666e2023
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412104"
---
# <a name="icordebugeval2createvaluefortype-method"></a><span data-ttu-id="20b18-102">ICorDebugEval2::CreateValueForType – metoda</span><span class="sxs-lookup"><span data-stu-id="20b18-102">ICorDebugEval2::CreateValueForType Method</span></span>
<span data-ttu-id="20b18-103">Získá ukazatel na nové ICorDebugValue zadaného typu, s počáteční hodnotou nula nebo hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="20b18-103">Gets a pointer to a new ICorDebugValue of the specified type, with an initial value of zero or null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20b18-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20b18-104">Syntax</span></span>  
  
```  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20b18-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="20b18-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="20b18-106">[v] Ukazatel na ICorDebugType objekt, který představuje typ.</span><span class="sxs-lookup"><span data-stu-id="20b18-106">[in] Pointer to an ICorDebugType object that represents the type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="20b18-107">[out] Ukazatel na adresu `ICorDebugValue` objekt, který představuje hodnotu.</span><span class="sxs-lookup"><span data-stu-id="20b18-107">[out] Pointer to the address of an `ICorDebugValue` object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20b18-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="20b18-108">Remarks</span></span>  
 <span data-ttu-id="20b18-109">`CreateValueForType` Umožňuje zobecnit [icordebugeval::createvalue –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md) tím, že se k zadání typu libovolného objektu, včetně sestavený typy, jako `List<int>`.</span><span class="sxs-lookup"><span data-stu-id="20b18-109">`CreateValueForType` generalizes [ICorDebugEval::CreateValue](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md) by allowing you to specify an arbitrary object type, including constructed types such as `List<int>`.</span></span> <span data-ttu-id="20b18-110">Jediným účelem: Tato metoda je ke generování hodnotu, která se dá předat do vyhodnocení funkce.</span><span class="sxs-lookup"><span data-stu-id="20b18-110">The only purpose of this method is to generate a value that can be passed to a function evaluation.</span></span>  
  
 <span data-ttu-id="20b18-111">Typ musí být třídu nebo typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="20b18-111">The type must be a class or a value type.</span></span> <span data-ttu-id="20b18-112">Tuto metodu nelze použít k vytvoření hodnoty pole nebo hodnoty řetězce.</span><span class="sxs-lookup"><span data-stu-id="20b18-112">You cannot use this method to create array values or string values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20b18-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="20b18-113">Requirements</span></span>  
 <span data-ttu-id="20b18-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20b18-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20b18-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="20b18-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="20b18-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20b18-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20b18-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20b18-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
