---
title: ICorDebugType::GetRank – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetRank
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetRank
helpviewer_keywords:
- GetRank method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::GetRank method [.NET Framework debugging]
ms.assetid: 72d3d927-f590-4f2d-8f60-448f3dfb96af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 134fe55de71e3d6a9a68249febc4c70f11d4f36f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993860"
---
# <a name="icordebugtypegetrank-method"></a><span data-ttu-id="9a3f8-102">ICorDebugType::GetRank – metoda</span><span class="sxs-lookup"><span data-stu-id="9a3f8-102">ICorDebugType::GetRank Method</span></span>
<span data-ttu-id="9a3f8-103">Získá počet dimenzí v typu pole.</span><span class="sxs-lookup"><span data-stu-id="9a3f8-103">Gets the number of dimensions in an array type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a3f8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9a3f8-104">Syntax</span></span>  
  
```  
HRESULT GetRank (  
    [out] ULONG32   *pnRank  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a3f8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9a3f8-105">Parameters</span></span>  
 `pnRank`  
 <span data-ttu-id="9a3f8-106">[out] Ukazatel na počet rozměrů.</span><span class="sxs-lookup"><span data-stu-id="9a3f8-106">[out] A pointer to the number of dimensions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a3f8-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9a3f8-107">Requirements</span></span>  
 <span data-ttu-id="9a3f8-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a3f8-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a3f8-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9a3f8-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9a3f8-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a3f8-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a3f8-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a3f8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
