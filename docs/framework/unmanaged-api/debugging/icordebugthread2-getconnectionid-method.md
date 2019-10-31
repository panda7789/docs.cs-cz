---
title: ICorDebugThread2::GetConnectionID – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetConnectionID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetConnectionID
helpviewer_keywords:
- ICorDebugThread2::GetConnectionID method [.NET Framework debugging]
- GetConnectionID method [.NET Framework debugging]
ms.assetid: 9c76b587-f941-4fa1-8b86-f3494fb10c8e
topic_type:
- apiref
ms.openlocfilehash: a81842132769934a6f5f34e6dc462bba77b3854a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138688"
---
# <a name="icordebugthread2getconnectionid-method"></a><span data-ttu-id="722c9-102">ICorDebugThread2::GetConnectionID – metoda</span><span class="sxs-lookup"><span data-stu-id="722c9-102">ICorDebugThread2::GetConnectionID Method</span></span>
<span data-ttu-id="722c9-103">Získá identifikátor připojení pro tento objekt ICorDebugThread2.</span><span class="sxs-lookup"><span data-stu-id="722c9-103">Gets the connection identifier for this ICorDebugThread2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="722c9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="722c9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConnectionID (  
    [out] CONNID *pdwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="722c9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="722c9-105">Parameters</span></span>  
 `pdwConnectionId`  
 <span data-ttu-id="722c9-106">mimo `CONNID`, který představuje identifikátor připojení.</span><span class="sxs-lookup"><span data-stu-id="722c9-106">[out] A `CONNID` that represents the connection identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="722c9-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="722c9-107">Remarks</span></span>  
 <span data-ttu-id="722c9-108">Metoda `GetConnectionID` vrátí nulu v parametru `pdwConnectionId`, pokud toto vlákno není součástí připojení.</span><span class="sxs-lookup"><span data-stu-id="722c9-108">The `GetConnectionID` method returns zero in the `pdwConnectionId` parameter, if this thread is not part of a connection.</span></span>  
  
 <span data-ttu-id="722c9-109">Pokud je toto vlákno připojeno k instanci Microsoft SQL Server 2005 Analysis Services (SSAS), `CONNID` se mapuje na identifikátor procesu serveru (SPID).</span><span class="sxs-lookup"><span data-stu-id="722c9-109">If this thread is connected to an instance of Microsoft SQL Server 2005 Analysis Services (SSAS), the `CONNID` maps to a server process identifier (SPID).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="722c9-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="722c9-110">Requirements</span></span>  
 <span data-ttu-id="722c9-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="722c9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="722c9-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="722c9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="722c9-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="722c9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="722c9-114">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="722c9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
