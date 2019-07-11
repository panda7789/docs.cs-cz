---
title: INotifySink2::OnSyncCallReturn – metoda
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallReturn
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallReturn
helpviewer_keywords:
- OnSyncCallReturn method [.NET Framework debugging]
- INotifySink2::OnSyncCallReturn method [.NET Framework debugging]
ms.assetid: c1bda761-6292-4750-a14b-7d5db8f33456
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 84fd40dbecf9a866a4ec0889cbb62c475c063475
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736218"
---
# <a name="inotifysink2onsynccallreturn-method"></a><span data-ttu-id="08f44-102">INotifySink2::OnSyncCallReturn – metoda</span><span class="sxs-lookup"><span data-stu-id="08f44-102">INotifySink2::OnSyncCallReturn Method</span></span>
<span data-ttu-id="08f44-103">Získá vyvolán při volání vrátí.</span><span class="sxs-lookup"><span data-stu-id="08f44-103">Gets invoked when a call returns.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08f44-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08f44-104">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallReturn  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08f44-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="08f44-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="08f44-106">[in] Identifikátor hovoru vráceného z.</span><span class="sxs-lookup"><span data-stu-id="08f44-106">[in] ID of the call being returned from.</span></span> <span data-ttu-id="08f44-107">Zobrazit [call_id – struktura](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="08f44-107">See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `in_pBuffer`  
 <span data-ttu-id="08f44-108">[in] Volání vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="08f44-108">[in] Call buffer.</span></span>  
  
 `in_BufferSize`  
 <span data-ttu-id="08f44-109">[in] Velikost vyrovnávací paměti volání, v bajtech.</span><span class="sxs-lookup"><span data-stu-id="08f44-109">[in] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="08f44-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="08f44-110">Return Value</span></span>  
 <span data-ttu-id="08f44-111">S_OK, pokud metoda uspěje.</span><span class="sxs-lookup"><span data-stu-id="08f44-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08f44-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="08f44-112">Requirements</span></span>  
 <span data-ttu-id="08f44-113">**Záhlaví:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="08f44-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08f44-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="08f44-114">See also</span></span>

- [<span data-ttu-id="08f44-115">INotifySink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="08f44-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="08f44-116">INotifySource2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="08f44-116">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="08f44-117">INotifyConnection2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="08f44-117">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
