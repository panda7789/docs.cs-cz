---
title: ICorDebugThread::GetObject – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetObject
helpviewer_keywords:
- GetObject method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetObject method [.NET Framework debugging]
ms.assetid: 1590febe-96c2-4046-97db-d81d81d67e01
topic_type:
- apiref
ms.openlocfilehash: 624469ca1ae4c96b4143f8768b4c5ff9c2601a2f
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378874"
---
# <a name="icordebugthreadgetobject-method"></a><span data-ttu-id="71dbb-102">ICorDebugThread::GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="71dbb-102">ICorDebugThread::GetObject Method</span></span>
<span data-ttu-id="71dbb-103">Načte ukazatel rozhraní do vlákna modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="71dbb-103">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71dbb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="71dbb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71dbb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="71dbb-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="71dbb-106">mimo Ukazatel na adresu objektu rozhraní ICorDebugValue, který představuje vlákno CLR.</span><span class="sxs-lookup"><span data-stu-id="71dbb-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71dbb-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="71dbb-107">Requirements</span></span>  
 <span data-ttu-id="71dbb-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71dbb-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71dbb-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="71dbb-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="71dbb-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="71dbb-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71dbb-111">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71dbb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71dbb-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="71dbb-112">See also</span></span>

- <xref:System.Threading.Thread>
