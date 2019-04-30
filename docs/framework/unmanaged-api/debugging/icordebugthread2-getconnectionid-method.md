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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7d51e21eab4ac1edc81b58171e5382ada170a57f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946331"
---
# <a name="icordebugthread2getconnectionid-method"></a><span data-ttu-id="d51e6-102">ICorDebugThread2::GetConnectionID – metoda</span><span class="sxs-lookup"><span data-stu-id="d51e6-102">ICorDebugThread2::GetConnectionID Method</span></span>
<span data-ttu-id="d51e6-103">Získá identifikátor připojení pro tento objekt icordebugthread2 –.</span><span class="sxs-lookup"><span data-stu-id="d51e6-103">Gets the connection identifier for this ICorDebugThread2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d51e6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d51e6-104">Syntax</span></span>  
  
```  
HRESULT GetConnectionID (  
    [out] CONNID *pdwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d51e6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d51e6-105">Parameters</span></span>  
 `pdwConnectionId`  
 <span data-ttu-id="d51e6-106">[out] A `CONNID` , která představuje identifikátor připojení.</span><span class="sxs-lookup"><span data-stu-id="d51e6-106">[out] A `CONNID` that represents the connection identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d51e6-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d51e6-107">Remarks</span></span>  
 <span data-ttu-id="d51e6-108">`GetConnectionID` Metoda vrátí nulu v `pdwConnectionId` parametr, pokud toto vlákno není součástí připojení.</span><span class="sxs-lookup"><span data-stu-id="d51e6-108">The `GetConnectionID` method returns zero in the `pdwConnectionId` parameter, if this thread is not part of a connection.</span></span>  
  
 <span data-ttu-id="d51e6-109">Pokud toto vlákno je připojen k instanci systému Microsoft SQL Server 2005 Analysis Services (SSAS), `CONNID` mapuje na identifikátor procesu serveru (SPID).</span><span class="sxs-lookup"><span data-stu-id="d51e6-109">If this thread is connected to an instance of Microsoft SQL Server 2005 Analysis Services (SSAS), the `CONNID` maps to a server process identifier (SPID).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d51e6-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d51e6-110">Requirements</span></span>  
 <span data-ttu-id="d51e6-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d51e6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d51e6-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d51e6-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d51e6-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d51e6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d51e6-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d51e6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
