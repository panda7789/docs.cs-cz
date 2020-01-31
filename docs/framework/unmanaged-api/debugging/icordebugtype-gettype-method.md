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
ms.openlocfilehash: 25ffbf73fbefbb3c584450283c3080dfc11ee598
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791242"
---
# <a name="icordebugtypegettype-method"></a><span data-ttu-id="203b2-102">ICorDebugType::GetType – metoda</span><span class="sxs-lookup"><span data-stu-id="203b2-102">ICorDebugType::GetType Method</span></span>
<span data-ttu-id="203b2-103">Získá hodnotu CorElementType –, která popisuje nativní typ modulu CLR (Common Language Runtime) <xref:System.Type> reprezentovaného tímto ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="203b2-103">Gets a CorElementType value that describes the native type of the common language runtime (CLR) <xref:System.Type> represented by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="203b2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="203b2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="203b2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="203b2-105">Parameters</span></span>  
 `ty`  
 <span data-ttu-id="203b2-106">mimo Ukazatel na hodnotu výčtu `CorElementType`, která označuje CLR <xref:System.Type>, který tento `ICorDebugType` představuje.</span><span class="sxs-lookup"><span data-stu-id="203b2-106">[out] A pointer to a value of the `CorElementType` enumeration that indicates the CLR <xref:System.Type> that this `ICorDebugType` represents.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="203b2-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="203b2-107">Remarks</span></span>  
 <span data-ttu-id="203b2-108">Pokud je hodnota `ty` buď ELEMENT_TYPE_CLASS nebo ELEMENT_TYPE_VALUETYPE, může být volána metoda [ICorDebugType:: GetClass](icordebugtype-getclass-method.md) pro získání typu bez instance pro obecný typ; v opačném případě Nevolejte `ICorDebugType::GetClass`.</span><span class="sxs-lookup"><span data-stu-id="203b2-108">If the value of `ty` is either ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, the [ICorDebugType::GetClass](icordebugtype-getclass-method.md) method may be called to get the uninstantiated type for a generic type; otherwise, do not call `ICorDebugType::GetClass`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="203b2-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="203b2-109">Requirements</span></span>  
 <span data-ttu-id="203b2-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="203b2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="203b2-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="203b2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="203b2-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="203b2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="203b2-113">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="203b2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
