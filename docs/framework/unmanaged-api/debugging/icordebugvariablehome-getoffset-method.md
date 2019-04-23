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
ms.openlocfilehash: 864cb893511bceabd61ce0064065b3866ce01dfe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59212593"
---
# <a name="icordebugvariablehomegetoffset-method"></a><span data-ttu-id="3567f-102">ICorDebugVariableHome::GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="3567f-102">ICorDebugVariableHome::GetOffset Method</span></span>
<span data-ttu-id="3567f-103">Získá posun od základní registrace pro proměnnou.</span><span class="sxs-lookup"><span data-stu-id="3567f-103">Gets the offset from the base register for a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3567f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3567f-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3567f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3567f-105">Parameters</span></span>  
 `pOffset`  
 <span data-ttu-id="3567f-106">[out] Posun od základní registrace.</span><span class="sxs-lookup"><span data-stu-id="3567f-106">[out] The offset from the base register.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3567f-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3567f-107">Return Value</span></span>  
 <span data-ttu-id="3567f-108">Metoda vrátí následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="3567f-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="3567f-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="3567f-109">Value</span></span>|<span data-ttu-id="3567f-110">Popis</span><span class="sxs-lookup"><span data-stu-id="3567f-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="3567f-111">Proměnná se nachází v umístění paměti register relativní.</span><span class="sxs-lookup"><span data-stu-id="3567f-111">The variable is in a register-relative memory location.</span></span>|  
|`E_FAIL`|<span data-ttu-id="3567f-112">Proměnná se nenachází v paměti register relativní umístění.</span><span class="sxs-lookup"><span data-stu-id="3567f-112">The variable is not in a register-relative memory location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3567f-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3567f-113">Requirements</span></span>  
 <span data-ttu-id="3567f-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3567f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3567f-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3567f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3567f-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3567f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3567f-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3567f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3567f-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3567f-118">See also</span></span>

- [<span data-ttu-id="3567f-119">ICorDebugVariableHome – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3567f-119">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
