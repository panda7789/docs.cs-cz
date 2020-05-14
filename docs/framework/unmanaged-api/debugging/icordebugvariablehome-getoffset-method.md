---
title: 'ICorDebugVariableHome:: GetOffset – metoda'
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
ms.openlocfilehash: 75a165e2fd517f36d779a934a5bdd9c41956411a
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396766"
---
# <a name="icordebugvariablehomegetoffset-method"></a><span data-ttu-id="5aeca-102">ICorDebugVariableHome:: GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="5aeca-102">ICorDebugVariableHome::GetOffset Method</span></span>
<span data-ttu-id="5aeca-103">Získá posun od základního registru pro proměnnou.</span><span class="sxs-lookup"><span data-stu-id="5aeca-103">Gets the offset from the base register for a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5aeca-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5aeca-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5aeca-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5aeca-105">Parameters</span></span>  
 `pOffset`  
 <span data-ttu-id="5aeca-106">mimo Posun základního registru.</span><span class="sxs-lookup"><span data-stu-id="5aeca-106">[out] The offset from the base register.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5aeca-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5aeca-107">Return Value</span></span>  
 <span data-ttu-id="5aeca-108">Metoda vrací následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="5aeca-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="5aeca-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5aeca-109">Value</span></span>|<span data-ttu-id="5aeca-110">Popis</span><span class="sxs-lookup"><span data-stu-id="5aeca-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="5aeca-111">Proměnná je v umístění relativní paměti pro registraci.</span><span class="sxs-lookup"><span data-stu-id="5aeca-111">The variable is in a register-relative memory location.</span></span>|  
|`E_FAIL`|<span data-ttu-id="5aeca-112">Proměnná není v umístění relativní paměti registru.</span><span class="sxs-lookup"><span data-stu-id="5aeca-112">The variable is not in a register-relative memory location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5aeca-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5aeca-113">Requirements</span></span>  
 <span data-ttu-id="5aeca-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5aeca-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5aeca-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5aeca-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5aeca-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5aeca-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5aeca-117">**Verze .NET Framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5aeca-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5aeca-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="5aeca-118">See also</span></span>

- [<span data-ttu-id="5aeca-119">ICorDebugVariableHome – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5aeca-119">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
