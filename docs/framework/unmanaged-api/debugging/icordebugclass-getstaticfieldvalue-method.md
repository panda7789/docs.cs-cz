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
ms.openlocfilehash: 873dd5a1eb2c9356049d2d0c0cb495b963c2ae46
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784194"
---
# <a name="icordebugclassgetstaticfieldvalue-method"></a><span data-ttu-id="112b0-102">ICorDebugClass::GetStaticFieldValue – metoda</span><span class="sxs-lookup"><span data-stu-id="112b0-102">ICorDebugClass::GetStaticFieldValue Method</span></span>
<span data-ttu-id="112b0-103">Získá hodnotu zadaného statického pole.</span><span class="sxs-lookup"><span data-stu-id="112b0-103">Gets the value of the specified static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="112b0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="112b0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef         fieldDef,  
    [in]  ICorDebugFrame     *pFrame,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="112b0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="112b0-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="112b0-106">pro Pole `Def` token, který odkazuje na pole, které má být načteno.</span><span class="sxs-lookup"><span data-stu-id="112b0-106">[in] A field `Def` token that references the field to be retrieved.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="112b0-107">pro Ukazatel na objekt ICorDebugFrame, který představuje rámec, který má být použit k jednoznačnému rozlišení mezi statickými a doménovými doménami vlákna, kontextu nebo domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="112b0-107">[in] A pointer to an ICorDebugFrame object that represents the frame to be used to disambiguate among thread, context, or application domain statics.</span></span>  
  
 <span data-ttu-id="112b0-108">Pokud je statické pole relativní vzhledem k vláknu, kontextu nebo doméně aplikace, bude rámec určovat správnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="112b0-108">If the static field is relative to a thread, a context, or an application domain, the frame will determine the proper value.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="112b0-109">mimo Ukazatel na adresu objektu ICorDebugValue, který představuje hodnotu statického pole.</span><span class="sxs-lookup"><span data-stu-id="112b0-109">[out] A pointer to the address of an ICorDebugValue object that represents the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="112b0-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="112b0-110">Remarks</span></span>  
 <span data-ttu-id="112b0-111">U parametrizovaných typů je hodnota statického pole relativní vzhledem k konkrétní instanci.</span><span class="sxs-lookup"><span data-stu-id="112b0-111">For parameterized types, the value of a static field is relative to the particular instantiation.</span></span> <span data-ttu-id="112b0-112">Proto pokud konstruktor třídy přebírá parametry typu <xref:System.Type>, zavolejte [ICorDebugType:: GetStaticFieldValue](icordebugtype-getstaticfieldvalue-method.md) namísto `ICorDebugClass::GetStaticFieldValue`.</span><span class="sxs-lookup"><span data-stu-id="112b0-112">Therefore, if the class constructor takes parameters of type <xref:System.Type>, call [ICorDebugType::GetStaticFieldValue](icordebugtype-getstaticfieldvalue-method.md) instead of `ICorDebugClass::GetStaticFieldValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="112b0-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="112b0-113">Requirements</span></span>  
 <span data-ttu-id="112b0-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="112b0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="112b0-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="112b0-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="112b0-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="112b0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="112b0-117">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="112b0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
