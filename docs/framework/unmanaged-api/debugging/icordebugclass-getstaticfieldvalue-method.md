---
title: ICorDebugClass::GetStaticFieldValue – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetStaticFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 56e718b4-fabd-418b-a5b3-3cc33c745683
topic_type:
- apiref
ms.openlocfilehash: 867db3325f9b18b31f66429d01ea02be3603c0f6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125765"
---
# <a name="icordebugclassgetstaticfieldvalue-method"></a><span data-ttu-id="49fde-102">ICorDebugClass::GetStaticFieldValue – metoda</span><span class="sxs-lookup"><span data-stu-id="49fde-102">ICorDebugClass::GetStaticFieldValue Method</span></span>
<span data-ttu-id="49fde-103">Získá hodnotu zadaného statického pole.</span><span class="sxs-lookup"><span data-stu-id="49fde-103">Gets the value of the specified static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49fde-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49fde-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef         fieldDef,  
    [in]  ICorDebugFrame     *pFrame,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49fde-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="49fde-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="49fde-106">pro Pole `Def` token, který odkazuje na pole, které má být načteno.</span><span class="sxs-lookup"><span data-stu-id="49fde-106">[in] A field `Def` token that references the field to be retrieved.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="49fde-107">pro Ukazatel na objekt ICorDebugFrame, který představuje rámec, který má být použit k jednoznačnému rozlišení mezi statickými a doménovými doménami vlákna, kontextu nebo domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="49fde-107">[in] A pointer to an ICorDebugFrame object that represents the frame to be used to disambiguate among thread, context, or application domain statics.</span></span>  
  
 <span data-ttu-id="49fde-108">Pokud je statické pole relativní vzhledem k vláknu, kontextu nebo doméně aplikace, bude rámec určovat správnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="49fde-108">If the static field is relative to a thread, a context, or an application domain, the frame will determine the proper value.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="49fde-109">mimo Ukazatel na adresu objektu ICorDebugValue, který představuje hodnotu statického pole.</span><span class="sxs-lookup"><span data-stu-id="49fde-109">[out] A pointer to the address of an ICorDebugValue object that represents the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49fde-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="49fde-110">Remarks</span></span>  
 <span data-ttu-id="49fde-111">U parametrizovaných typů je hodnota statického pole relativní vzhledem k konkrétní instanci.</span><span class="sxs-lookup"><span data-stu-id="49fde-111">For parameterized types, the value of a static field is relative to the particular instantiation.</span></span> <span data-ttu-id="49fde-112">Proto pokud konstruktor třídy přebírá parametry typu <xref:System.Type>, zavolejte [ICorDebugType:: GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md) namísto `ICorDebugClass::GetStaticFieldValue`.</span><span class="sxs-lookup"><span data-stu-id="49fde-112">Therefore, if the class constructor takes parameters of type <xref:System.Type>, call [ICorDebugType::GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md) instead of `ICorDebugClass::GetStaticFieldValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49fde-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="49fde-113">Requirements</span></span>  
 <span data-ttu-id="49fde-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49fde-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49fde-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="49fde-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="49fde-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="49fde-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49fde-117">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49fde-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
