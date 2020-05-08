---
title: ICorDebugEnum::GetCount – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEnum.GetCount
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum::GetCount
helpviewer_keywords:
- ICorDebugEnum::GetCount method [.NET Framework debugging]
- GetCount method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: d8a74304-1cb2-4977-a21d-e1af48c563ff
topic_type:
- apiref
ms.openlocfilehash: 90ba690897abced2d4f6282eedef91712d8ceeca
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976340"
---
# <a name="icordebugenumgetcount-method"></a><span data-ttu-id="af763-102">ICorDebugEnum::GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="af763-102">ICorDebugEnum::GetCount Method</span></span>
<span data-ttu-id="af763-103">Získá počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="af763-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af763-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af763-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af763-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="af763-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="af763-106">mimo Ukazatel na počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="af763-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af763-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="af763-107">Requirements</span></span>  
 <span data-ttu-id="af763-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af763-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af763-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="af763-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="af763-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="af763-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af763-111">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af763-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
