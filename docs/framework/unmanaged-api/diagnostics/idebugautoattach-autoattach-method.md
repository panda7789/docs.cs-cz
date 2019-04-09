---
title: IDebugAutoAttach::AutoAttach – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5064e66708044d82e3a097c8235b5b28a3412200
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077131"
---
# <a name="idebugautoattachautoattach-method"></a><span data-ttu-id="e8457-102">IDebugAutoAttach::AutoAttach – metoda</span><span class="sxs-lookup"><span data-stu-id="e8457-102">IDebugAutoAttach::AutoAttach Method</span></span>
<span data-ttu-id="e8457-103">Provede automaticky serveru vyvolá ladicí program připojit.</span><span class="sxs-lookup"><span data-stu-id="e8457-103">Performs server-invoked debugger auto attach.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8457-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8457-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="e8457-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e8457-105">Parameters</span></span>  
 `guidPort`  
 <span data-ttu-id="e8457-106">[in] Vždy nastaven na hodnotu `GUID_NULL`.</span><span class="sxs-lookup"><span data-stu-id="e8457-106">[in] Always set to `GUID_NULL`.</span></span>  
  
 `dwPid`  
 <span data-ttu-id="e8457-107">[in] ID, obvykle načteno pomocí procesu `GetCurrentProcessId` funkce.</span><span class="sxs-lookup"><span data-stu-id="e8457-107">[in] Process ID, normally retrieved with the `GetCurrentProcessId` function.</span></span>  
  
 `dwProgramType`  
 <span data-ttu-id="e8457-108">[in] Typ programu: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, nebo `AUTOATTACH_PROGRAM_UNKNOWN`.</span><span class="sxs-lookup"><span data-stu-id="e8457-108">[in] Program type: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, or `AUTOATTACH_PROGRAM_UNKNOWN`.</span></span>  
  
 `dwProgramId`  
 <span data-ttu-id="e8457-109">[in] ID programu.</span><span class="sxs-lookup"><span data-stu-id="e8457-109">[in] Program ID.</span></span>  
  
 `pszSessionId`  
 <span data-ttu-id="e8457-110">[in] Řetězec předaný příkaz debug.</span><span class="sxs-lookup"><span data-stu-id="e8457-110">[in] String passed by the debug verb.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8457-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e8457-111">Return Value</span></span>  
 <span data-ttu-id="e8457-112">S_OK, pokud metoda uspěje.</span><span class="sxs-lookup"><span data-stu-id="e8457-112">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8457-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e8457-113">Requirements</span></span>  
 <span data-ttu-id="e8457-114">**Záhlaví:** DbgAutoAttach.h</span><span class="sxs-lookup"><span data-stu-id="e8457-114">**Header:** DbgAutoAttach.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8457-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e8457-115">See also</span></span>

- [<span data-ttu-id="e8457-116">IDebugAutoAttach – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e8457-116">IDebugAutoAttach Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)
