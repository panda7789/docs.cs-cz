---
title: "IDebugAutoAttach::AutoAttach – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IDebugAutoAttach.AutoAttach
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IDebugAutoAttach::AutoAttach
helpviewer_keywords:
- AutoAttach method [.NET Framework debugging]
- IDebugAutoAttach::AutoAttach method [.NET Framework debugging]
ms.assetid: 3cf3bd9c-7d88-4afa-a476-94cdc7609aa6
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3b875fec2fdb6ecaeaccf8e58030b2fccbb8653b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="idebugautoattachautoattach-method"></a><span data-ttu-id="9f2e6-102">IDebugAutoAttach::AutoAttach – metoda</span><span class="sxs-lookup"><span data-stu-id="9f2e6-102">IDebugAutoAttach::AutoAttach Method</span></span>
<span data-ttu-id="9f2e6-103">Provede server volá ladicí program automaticky připojit.</span><span class="sxs-lookup"><span data-stu-id="9f2e6-103">Performs server-invoked debugger auto attach.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f2e6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f2e6-104">Syntax</span></span>  
  
```  
HRESULT AutoAttach  
(  
    [in]  REFGUID   guidPort,  
    [in]  DWORD     dwPid,  
    [in]  AUTOATTACH_PROGRAM_TYPE dwProgramType,  
    [in]  DWORD     dwProgramId,  
    [in]  LPCWSTR   pszSessionId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9f2e6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9f2e6-105">Parameters</span></span>  
 `guidPort`  
 <span data-ttu-id="9f2e6-106">[v] Vždy nastaven na hodnotu `GUID_NULL`.</span><span class="sxs-lookup"><span data-stu-id="9f2e6-106">[in] Always set to `GUID_NULL`.</span></span>  
  
 `dwPid`  
 <span data-ttu-id="9f2e6-107">[v] ID, obvykle načíst pomocí procesu `GetCurrentProcessId` funkce.</span><span class="sxs-lookup"><span data-stu-id="9f2e6-107">[in] Process ID, normally retrieved with the `GetCurrentProcessId` function.</span></span>  
  
 `dwProgramType`  
 <span data-ttu-id="9f2e6-108">[v] Program typu: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, nebo `AUTOATTACH_PROGRAM_UNKNOWN`.</span><span class="sxs-lookup"><span data-stu-id="9f2e6-108">[in] Program type: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, or `AUTOATTACH_PROGRAM_UNKNOWN`.</span></span>  
  
 `dwProgramId`  
 <span data-ttu-id="9f2e6-109">[v] ID programu.</span><span class="sxs-lookup"><span data-stu-id="9f2e6-109">[in] Program ID.</span></span>  
  
 `pszSessionId`  
 <span data-ttu-id="9f2e6-110">[v] Řetězec předaná příkaz debug.</span><span class="sxs-lookup"><span data-stu-id="9f2e6-110">[in] String passed by the debug verb.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9f2e6-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9f2e6-111">Return Value</span></span>  
 <span data-ttu-id="9f2e6-112">S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="9f2e6-112">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f2e6-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9f2e6-113">Requirements</span></span>  
 <span data-ttu-id="9f2e6-114">**Záhlaví:** DbgAutoAttach.h</span><span class="sxs-lookup"><span data-stu-id="9f2e6-114">**Header:** DbgAutoAttach.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f2e6-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="9f2e6-115">See Also</span></span>  
 [<span data-ttu-id="9f2e6-116">IDebugAutoAttach – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9f2e6-116">IDebugAutoAttach Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)
