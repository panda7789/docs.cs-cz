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
ms.openlocfilehash: e5c95423a6918da7cc043f8d46de13d166b8d895
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426182"
---
# <a name="idebugautoattachautoattach-method"></a><span data-ttu-id="accdb-102">IDebugAutoAttach::AutoAttach – metoda</span><span class="sxs-lookup"><span data-stu-id="accdb-102">IDebugAutoAttach::AutoAttach Method</span></span>
<span data-ttu-id="accdb-103">Provede server volá ladicí program automaticky připojit.</span><span class="sxs-lookup"><span data-stu-id="accdb-103">Performs server-invoked debugger auto attach.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="accdb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="accdb-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="accdb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="accdb-105">Parameters</span></span>  
 `guidPort`  
 <span data-ttu-id="accdb-106">[v] Vždy nastaven na hodnotu `GUID_NULL`.</span><span class="sxs-lookup"><span data-stu-id="accdb-106">[in] Always set to `GUID_NULL`.</span></span>  
  
 `dwPid`  
 <span data-ttu-id="accdb-107">[v] ID, obvykle načíst pomocí procesu `GetCurrentProcessId` funkce.</span><span class="sxs-lookup"><span data-stu-id="accdb-107">[in] Process ID, normally retrieved with the `GetCurrentProcessId` function.</span></span>  
  
 `dwProgramType`  
 <span data-ttu-id="accdb-108">[v] Program typu: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, nebo `AUTOATTACH_PROGRAM_UNKNOWN`.</span><span class="sxs-lookup"><span data-stu-id="accdb-108">[in] Program type: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, or `AUTOATTACH_PROGRAM_UNKNOWN`.</span></span>  
  
 `dwProgramId`  
 <span data-ttu-id="accdb-109">[v] ID programu.</span><span class="sxs-lookup"><span data-stu-id="accdb-109">[in] Program ID.</span></span>  
  
 `pszSessionId`  
 <span data-ttu-id="accdb-110">[v] Řetězec předaná příkaz debug.</span><span class="sxs-lookup"><span data-stu-id="accdb-110">[in] String passed by the debug verb.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="accdb-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="accdb-111">Return Value</span></span>  
 <span data-ttu-id="accdb-112">S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="accdb-112">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="accdb-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="accdb-113">Requirements</span></span>  
 <span data-ttu-id="accdb-114">**Záhlaví:** DbgAutoAttach.h</span><span class="sxs-lookup"><span data-stu-id="accdb-114">**Header:** DbgAutoAttach.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="accdb-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="accdb-115">See Also</span></span>  
 [<span data-ttu-id="accdb-116">IDebugAutoAttach – rozhraní</span><span class="sxs-lookup"><span data-stu-id="accdb-116">IDebugAutoAttach Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)
