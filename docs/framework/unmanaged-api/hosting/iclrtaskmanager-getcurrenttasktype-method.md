---
title: ICLRTaskManager::GetCurrentTaskType – metoda
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.GetCurrentTaskType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::GetCurrentTaskType
helpviewer_keywords:
- GetCurrentTaskType method [.NET Framework hosting]
- ICLRTaskManager::GetCurrentTaskType method [.NET Framework hosting]
ms.assetid: 6b0d9259-dbe2-45bb-b34d-990f60c73424
topic_type:
- apiref
ms.openlocfilehash: 2bf1b8b10aded8e61b9bceab0ee02b1d7c0b752a
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762809"
---
# <a name="iclrtaskmanagergetcurrenttasktype-method"></a><span data-ttu-id="51036-102">ICLRTaskManager::GetCurrentTaskType – metoda</span><span class="sxs-lookup"><span data-stu-id="51036-102">ICLRTaskManager::GetCurrentTaskType Method</span></span>
<span data-ttu-id="51036-103">Získá typ úlohy, která je právě prováděna.</span><span class="sxs-lookup"><span data-stu-id="51036-103">Gets the type of the task that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51036-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51036-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTaskType(  
    [out] ETaskType *pTaskType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51036-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="51036-105">Parameters</span></span>  
 `pTaskType`  
 <span data-ttu-id="51036-106">mimo Ukazatel na hodnotu výčtu [ETaskType –](etasktype-enumeration.md) , která určuje typ úlohy, která je právě prováděna.</span><span class="sxs-lookup"><span data-stu-id="51036-106">[out] A pointer to a value of the [ETaskType](etasktype-enumeration.md) enumeration that indicates the type of task that is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51036-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="51036-107">Requirements</span></span>  
 <span data-ttu-id="51036-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51036-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51036-109">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="51036-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="51036-110">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="51036-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="51036-111">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51036-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51036-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="51036-112">See also</span></span>

- [<span data-ttu-id="51036-113">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="51036-113">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
