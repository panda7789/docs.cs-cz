---
title: ICorDebugVariableHome::GetArgumentIndex – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetArgumentIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetArgumentIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetArgumentiIndex method [.NET Framework debugging]
- GetArgumentIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: e86fcc72-388d-4009-ab21-8f9c3323e9a3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 163704bf9a71ceda04bdfd73f9ca676c19d8a62c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54526637"
---
# <a name="icordebugvariablehomegetargumentindex-method"></a><span data-ttu-id="63949-102">ICorDebugVariableHome::GetArgumentIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="63949-102">ICorDebugVariableHome::GetArgumentIndex Method</span></span>
<span data-ttu-id="63949-103">Získá index argumentu funkce.</span><span class="sxs-lookup"><span data-stu-id="63949-103">Gets the index of a function argument.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63949-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63949-104">Syntax</span></span>  
  
```  
HRESULT GetArgumentIndex(  
    [out] ULONG32* pArgumentIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="63949-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="63949-105">Parameters</span></span>  
 `pArgumentIndex`  
 <span data-ttu-id="63949-106">[out] Ukazatel na index argumentu.</span><span class="sxs-lookup"><span data-stu-id="63949-106">[out] A pointer to the argument index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="63949-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="63949-107">Return Value</span></span>  
 <span data-ttu-id="63949-108">Metoda vrátí následující hodnoty.</span><span class="sxs-lookup"><span data-stu-id="63949-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="63949-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="63949-109">Value</span></span>|<span data-ttu-id="63949-110">Popis</span><span class="sxs-lookup"><span data-stu-id="63949-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="63949-111">Volání metody, které vrátí index platný argument.</span><span class="sxs-lookup"><span data-stu-id="63949-111">The method call returned a valid argument index.</span></span>|  
|`E_FAIL`|<span data-ttu-id="63949-112">Aktuální [icordebugvariablehome –](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance představuje místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="63949-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a local variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63949-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="63949-113">Remarks</span></span>  
 <span data-ttu-id="63949-114">Argument index je možné načíst metadata pro tento argument.</span><span class="sxs-lookup"><span data-stu-id="63949-114">The argument index can be used to retrieve metadata for this argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63949-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="63949-115">Requirements</span></span>  
 <span data-ttu-id="63949-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63949-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63949-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="63949-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63949-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63949-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63949-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63949-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63949-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="63949-120">See also</span></span>
- [<span data-ttu-id="63949-121">ICorDebugVariableHome – rozhraní</span><span class="sxs-lookup"><span data-stu-id="63949-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
