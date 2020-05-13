---
title: ICorDebugType::GetType – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetType
helpviewer_keywords:
- ICorDebugType::GetType method [.NET Framework debugging]
- GetType method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: d6e64534-4d47-4ad0-a340-7590e07e2b4a
topic_type:
- apiref
ms.openlocfilehash: ac42c6254182ea775377a448a54d527b234c97dc
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379929"
---
# <a name="icordebugtypegettype-method"></a><span data-ttu-id="c667c-102">ICorDebugType::GetType – metoda</span><span class="sxs-lookup"><span data-stu-id="c667c-102">ICorDebugType::GetType Method</span></span>
<span data-ttu-id="c667c-103">Získá hodnotu CorElementType –, která popisuje nativní typ modulu CLR (Common Language Runtime) <xref:System.Type> reprezentovaného tímto ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="c667c-103">Gets a CorElementType value that describes the native type of the common language runtime (CLR) <xref:System.Type> represented by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c667c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c667c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c667c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c667c-105">Parameters</span></span>  
 `ty`  
 <span data-ttu-id="c667c-106">mimo Ukazatel na hodnotu `CorElementType` výčtu, která označuje CLR <xref:System.Type> , který `ICorDebugType` představuje.</span><span class="sxs-lookup"><span data-stu-id="c667c-106">[out] A pointer to a value of the `CorElementType` enumeration that indicates the CLR <xref:System.Type> that this `ICorDebugType` represents.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c667c-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c667c-107">Remarks</span></span>  
 <span data-ttu-id="c667c-108">Pokud `ty` je hodnota buď ELEMENT_TYPE_CLASS nebo ELEMENT_TYPE_VALUETYPE, může být volána metoda [ICorDebugType:: GetClass](icordebugtype-getclass-method.md) pro získání nevytvořeného typu pro obecný typ. v opačném případě Nevolejte `ICorDebugType::GetClass` .</span><span class="sxs-lookup"><span data-stu-id="c667c-108">If the value of `ty` is either ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, the [ICorDebugType::GetClass](icordebugtype-getclass-method.md) method may be called to get the uninstantiated type for a generic type; otherwise, do not call `ICorDebugType::GetClass`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c667c-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c667c-109">Requirements</span></span>  
 <span data-ttu-id="c667c-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c667c-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c667c-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c667c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c667c-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c667c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c667c-113">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c667c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
