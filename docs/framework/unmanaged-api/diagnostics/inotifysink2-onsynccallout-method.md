---
title: INotifySink2::OnSyncCallOut – metoda
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallOut
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallOut
helpviewer_keywords:
- INotifySink2::OnSyncCallOut method [.NET Framework debugging]
- OnSyncCallOut method [.NET Framework debugging]
ms.assetid: 97f15656-8677-4079-8553-a1d8603355d6
topic_type:
- apiref
ms.openlocfilehash: ce0e192a9d7d5abf56a55f844cf886c386f1c563
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441991"
---
# <a name="inotifysink2onsynccallout-method"></a><span data-ttu-id="13a7b-102">INotifySink2::OnSyncCallOut – metoda</span><span class="sxs-lookup"><span data-stu-id="13a7b-102">INotifySink2::OnSyncCallOut Method</span></span>
<span data-ttu-id="13a7b-103">Vyvolá se, když je volání ven.</span><span class="sxs-lookup"><span data-stu-id="13a7b-103">Gets invoked when a call is out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13a7b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13a7b-104">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallOut  
(  
    [in]  CALL_ID  in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*   out_pBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13a7b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="13a7b-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="13a7b-106">pro ID volání, které je mimo. Viz [struktura CALL_ID](call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="13a7b-106">[in] ID of the call that is out. See [CALL_ID Structure](call-id-structure.md).</span></span>  
  
 `out_ppBuffer`  
 <span data-ttu-id="13a7b-107">mimo Vyrovnávací paměť volání.</span><span class="sxs-lookup"><span data-stu-id="13a7b-107">[out] Call buffer.</span></span>  
  
 `out_pBufferSize`  
 <span data-ttu-id="13a7b-108">mimo Velikost vyrovnávací paměti volání (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="13a7b-108">[out] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13a7b-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="13a7b-109">Return Value</span></span>  
 <span data-ttu-id="13a7b-110">S_OK, zda je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="13a7b-110">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13a7b-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="13a7b-111">Requirements</span></span>  
 <span data-ttu-id="13a7b-112">**Hlavička:** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="13a7b-112">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13a7b-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="13a7b-113">See also</span></span>

- [<span data-ttu-id="13a7b-114">INotifySink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="13a7b-114">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="13a7b-115">INotifySource2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="13a7b-115">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="13a7b-116">INotifyConnection2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="13a7b-116">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
