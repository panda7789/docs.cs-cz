---
title: "ICorDebugThread2::GetConnectionID – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread2.GetConnectionID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread2::GetConnectionID
helpviewer_keywords:
- ICorDebugThread2::GetConnectionID method [.NET Framework debugging]
- GetConnectionID method [.NET Framework debugging]
ms.assetid: 9c76b587-f941-4fa1-8b86-f3494fb10c8e
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ae852fe91bdb15007437ea6f2c61cbaa49a6918b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthread2getconnectionid-method"></a><span data-ttu-id="73736-102">ICorDebugThread2::GetConnectionID – metoda</span><span class="sxs-lookup"><span data-stu-id="73736-102">ICorDebugThread2::GetConnectionID Method</span></span>
<span data-ttu-id="73736-103">Získá identifikátor připojení pro tento objekt icordebugthread2 –.</span><span class="sxs-lookup"><span data-stu-id="73736-103">Gets the connection identifier for this ICorDebugThread2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73736-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73736-104">Syntax</span></span>  
  
```  
HRESULT GetConnectionID (  
    [out] CONNID *pdwConnectionId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="73736-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="73736-105">Parameters</span></span>  
 `pdwConnectionId`  
 <span data-ttu-id="73736-106">[out] A `CONNID` představující identifikátor připojení.</span><span class="sxs-lookup"><span data-stu-id="73736-106">[out] A `CONNID` that represents the connection identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73736-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="73736-107">Remarks</span></span>  
 <span data-ttu-id="73736-108">`GetConnectionID` Metoda vrátí hodnotu nula v `pdwConnectionId` parametr, pokud tohoto podprocesu není součástí připojení.</span><span class="sxs-lookup"><span data-stu-id="73736-108">The `GetConnectionID` method returns zero in the `pdwConnectionId` parameter, if this thread is not part of a connection.</span></span>  
  
 <span data-ttu-id="73736-109">Pokud tento přístup z více vláken je připojen k instanci systému Microsoft SQL Server 2005 Analysis Services (SSAS), `CONNID` mapuje identifikátor procesu serveru (SPID).</span><span class="sxs-lookup"><span data-stu-id="73736-109">If this thread is connected to an instance of Microsoft SQL Server 2005 Analysis Services (SSAS), the `CONNID` maps to a server process identifier (SPID).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73736-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="73736-110">Requirements</span></span>  
 <span data-ttu-id="73736-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73736-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73736-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="73736-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73736-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73736-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73736-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73736-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
