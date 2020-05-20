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
ms.openlocfilehash: ff1dabcfc366607639cd98be4392f8dd59dc83a1
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442004"
---
# <a name="inotifysink2onsynccallreturn-method"></a><span data-ttu-id="20882-102">INotifySink2::OnSyncCallReturn – metoda</span><span class="sxs-lookup"><span data-stu-id="20882-102">INotifySink2::OnSyncCallReturn Method</span></span>
<span data-ttu-id="20882-103">Vyvolá se, když se volání vrátí.</span><span class="sxs-lookup"><span data-stu-id="20882-103">Gets invoked when a call returns.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20882-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20882-104">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallReturn  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20882-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="20882-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="20882-106">pro ID volání, ze kterého se vrací.</span><span class="sxs-lookup"><span data-stu-id="20882-106">[in] ID of the call being returned from.</span></span> <span data-ttu-id="20882-107">Viz [struktura CALL_ID](call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="20882-107">See [CALL_ID Structure](call-id-structure.md).</span></span>  
  
 `in_pBuffer`  
 <span data-ttu-id="20882-108">pro Vyrovnávací paměť volání.</span><span class="sxs-lookup"><span data-stu-id="20882-108">[in] Call buffer.</span></span>  
  
 `in_BufferSize`  
 <span data-ttu-id="20882-109">pro Velikost vyrovnávací paměti volání (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="20882-109">[in] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20882-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="20882-110">Return Value</span></span>  
 <span data-ttu-id="20882-111">S_OK, zda je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="20882-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20882-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="20882-112">Requirements</span></span>  
 <span data-ttu-id="20882-113">**Hlavička:** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="20882-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20882-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="20882-114">See also</span></span>

- [<span data-ttu-id="20882-115">INotifySink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="20882-115">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="20882-116">INotifySource2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="20882-116">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="20882-117">INotifyConnection2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="20882-117">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
