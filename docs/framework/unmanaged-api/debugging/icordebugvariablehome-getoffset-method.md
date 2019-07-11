---
title: ICorDebugVariableHome::GetOffset – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetOffset
helpviewer_keywords:
- ICorDebugVariableHome::GetOffset method [.NET Framework debugging]
- GetOffset method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: f025c2e5-3f6c-4be8-9ffe-c8b214617dfe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0fdab81d499fe1508493cb0bf05a1787974a9d01
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774536"
---
# <a name="icordebugvariablehomegetoffset-method"></a><span data-ttu-id="85668-102">ICorDebugVariableHome::GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="85668-102">ICorDebugVariableHome::GetOffset Method</span></span>
<span data-ttu-id="85668-103">Získá posun od základní registrace pro proměnnou.</span><span class="sxs-lookup"><span data-stu-id="85668-103">Gets the offset from the base register for a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85668-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="85668-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85668-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="85668-105">Parameters</span></span>  
 `pOffset`  
 <span data-ttu-id="85668-106">[out] Posun od základní registrace.</span><span class="sxs-lookup"><span data-stu-id="85668-106">[out] The offset from the base register.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="85668-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="85668-107">Return Value</span></span>  
 <span data-ttu-id="85668-108">Metoda vrátí následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="85668-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="85668-109">Value</span><span class="sxs-lookup"><span data-stu-id="85668-109">Value</span></span>|<span data-ttu-id="85668-110">Popis</span><span class="sxs-lookup"><span data-stu-id="85668-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="85668-111">Proměnná se nachází v umístění paměti register relativní.</span><span class="sxs-lookup"><span data-stu-id="85668-111">The variable is in a register-relative memory location.</span></span>|  
|`E_FAIL`|<span data-ttu-id="85668-112">Proměnná se nenachází v paměti register relativní umístění.</span><span class="sxs-lookup"><span data-stu-id="85668-112">The variable is not in a register-relative memory location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="85668-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="85668-113">Requirements</span></span>  
 <span data-ttu-id="85668-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85668-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85668-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="85668-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85668-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85668-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85668-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85668-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85668-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="85668-118">See also</span></span>

- [<span data-ttu-id="85668-119">ICorDebugVariableHome – rozhraní</span><span class="sxs-lookup"><span data-stu-id="85668-119">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
