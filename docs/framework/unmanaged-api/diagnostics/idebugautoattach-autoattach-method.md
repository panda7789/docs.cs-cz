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
ms.openlocfilehash: aae03b0dc76639c50f4615d41eef73990226b5f7
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442121"
---
# <a name="idebugautoattachautoattach-method"></a><span data-ttu-id="067e4-102">IDebugAutoAttach::AutoAttach – metoda</span><span class="sxs-lookup"><span data-stu-id="067e4-102">IDebugAutoAttach::AutoAttach Method</span></span>
<span data-ttu-id="067e4-103">Provede automatické připojování ladicího programu vyvolaného serverem.</span><span class="sxs-lookup"><span data-stu-id="067e4-103">Performs server-invoked debugger auto attach.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="067e4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="067e4-104">Syntax</span></span>  
  
```cpp  
HRESULT AutoAttach  
(  
    [in]  REFGUID   guidPort,  
    [in]  DWORD     dwPid,  
    [in]  AUTOATTACH_PROGRAM_TYPE dwProgramType,  
    [in]  DWORD     dwProgramId,  
    [in]  LPCWSTR   pszSessionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="067e4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="067e4-105">Parameters</span></span>  
 `guidPort`  
 <span data-ttu-id="067e4-106">pro Vždy nastavte na `GUID_NULL` .</span><span class="sxs-lookup"><span data-stu-id="067e4-106">[in] Always set to `GUID_NULL`.</span></span>  
  
 `dwPid`  
 <span data-ttu-id="067e4-107">pro ID procesu, obvykle načteno pomocí `GetCurrentProcessId` funkce.</span><span class="sxs-lookup"><span data-stu-id="067e4-107">[in] Process ID, normally retrieved with the `GetCurrentProcessId` function.</span></span>  
  
 `dwProgramType`  
 <span data-ttu-id="067e4-108">pro Typ programu: `AUTOATTACH_PROGRAM_WIN32` , `AUTOATTACH_PROGRAM_COMPLUS` , nebo `AUTOATTACH_PROGRAM_UNKNOWN` .</span><span class="sxs-lookup"><span data-stu-id="067e4-108">[in] Program type: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, or `AUTOATTACH_PROGRAM_UNKNOWN`.</span></span>  
  
 `dwProgramId`  
 <span data-ttu-id="067e4-109">pro ID programu</span><span class="sxs-lookup"><span data-stu-id="067e4-109">[in] Program ID.</span></span>  
  
 `pszSessionId`  
 <span data-ttu-id="067e4-110">pro Řetězec předaný příkazem ladění</span><span class="sxs-lookup"><span data-stu-id="067e4-110">[in] String passed by the debug verb.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="067e4-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="067e4-111">Return Value</span></span>  
 <span data-ttu-id="067e4-112">S_OK, zda je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="067e4-112">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="067e4-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="067e4-113">Requirements</span></span>  
 <span data-ttu-id="067e4-114">**Hlavička:** DbgAutoAttach. h</span><span class="sxs-lookup"><span data-stu-id="067e4-114">**Header:** DbgAutoAttach.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="067e4-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="067e4-115">See also</span></span>

- [<span data-ttu-id="067e4-116">IDebugAutoAttach – rozhraní</span><span class="sxs-lookup"><span data-stu-id="067e4-116">IDebugAutoAttach Interface</span></span>](idebugautoattach-interface.md)
