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
ms.openlocfilehash: 9ffddb8242b6627239a99bd9223b98762910b831
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753235"
---
# <a name="icordebugeval2createvaluefortype-method"></a><span data-ttu-id="fe3fd-102">ICorDebugEval2::CreateValueForType – metoda</span><span class="sxs-lookup"><span data-stu-id="fe3fd-102">ICorDebugEval2::CreateValueForType Method</span></span>
<span data-ttu-id="fe3fd-103">Získá ukazatel na novou ICorDebugValue zadaného typu, s počáteční hodnotou nula nebo hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="fe3fd-103">Gets a pointer to a new ICorDebugValue of the specified type, with an initial value of zero or null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe3fd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe3fd-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe3fd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fe3fd-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="fe3fd-106">[in] Ukazatel na objekt, který představuje typ ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="fe3fd-106">[in] Pointer to an ICorDebugType object that represents the type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="fe3fd-107">[out] Ukazatel na adresu `ICorDebugValue` objekt, který představuje hodnotu.</span><span class="sxs-lookup"><span data-stu-id="fe3fd-107">[out] Pointer to the address of an `ICorDebugValue` object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe3fd-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fe3fd-108">Remarks</span></span>  
 <span data-ttu-id="fe3fd-109">`CreateValueForType` zobecňuje [icordebugeval::createvalue –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md) , neboť umožňuje určit typ libovolného objektu, včetně vytvořený typy, jako `List<int>`.</span><span class="sxs-lookup"><span data-stu-id="fe3fd-109">`CreateValueForType` generalizes [ICorDebugEval::CreateValue](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md) by allowing you to specify an arbitrary object type, including constructed types such as `List<int>`.</span></span> <span data-ttu-id="fe3fd-110">Jediným účelem: Tato metoda se má generovat hodnotu, která může být předán vyhodnocení funkce.</span><span class="sxs-lookup"><span data-stu-id="fe3fd-110">The only purpose of this method is to generate a value that can be passed to a function evaluation.</span></span>  
  
 <span data-ttu-id="fe3fd-111">Typ musí být třída nebo hodnotového typu.</span><span class="sxs-lookup"><span data-stu-id="fe3fd-111">The type must be a class or a value type.</span></span> <span data-ttu-id="fe3fd-112">Tuto metodu nelze použít k vytvoření hodnoty pole nebo řetězec.</span><span class="sxs-lookup"><span data-stu-id="fe3fd-112">You cannot use this method to create array values or string values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe3fd-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fe3fd-113">Requirements</span></span>  
 <span data-ttu-id="fe3fd-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe3fd-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe3fd-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fe3fd-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fe3fd-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe3fd-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe3fd-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe3fd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
