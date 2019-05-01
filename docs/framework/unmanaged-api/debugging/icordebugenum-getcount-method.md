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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b4af328c537fbc3b64eb1a2ac3df3a4e4224789e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61996018"
---
# <a name="icordebugenumgetcount-method"></a><span data-ttu-id="74f86-102">ICorDebugEnum::GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="74f86-102">ICorDebugEnum::GetCount Method</span></span>
<span data-ttu-id="74f86-103">Získá počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="74f86-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74f86-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74f86-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74f86-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="74f86-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="74f86-106">[out] Ukazatel na počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="74f86-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74f86-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="74f86-107">Requirements</span></span>  
 <span data-ttu-id="74f86-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74f86-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74f86-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="74f86-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="74f86-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74f86-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74f86-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74f86-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
