---
title: ICorDebugProcess::IsOSSuspended – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsOSSuspended
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsOSSuspended
helpviewer_keywords:
- IsOSSuspended method [.NET Framework debugging]
- ICorDebugProcess::IsOSSuspended method [.NET Framework debugging]
ms.assetid: 83406cb2-5797-4402-872d-89c9516aefec
topic_type:
- apiref
ms.openlocfilehash: 9452f238bd84c9c185ca8e007acac563474d29df
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212058"
---
# <a name="icordebugprocessisossuspended-method"></a><span data-ttu-id="288a7-102">ICorDebugProcess::IsOSSuspended – metoda</span><span class="sxs-lookup"><span data-stu-id="288a7-102">ICorDebugProcess::IsOSSuspended Method</span></span>
<span data-ttu-id="288a7-103">Získá hodnotu, která označuje, zda bylo zadané vlákno pozastaveno v důsledku zastavení tohoto procesu v rámci ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="288a7-103">Gets a value that indicates whether the specified thread has been suspended as a result of the debugger stopping this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="288a7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="288a7-104">Syntax</span></span>  
  
```cpp  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
## <a name="parameters"></a><span data-ttu-id="288a7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="288a7-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="288a7-106">pro ID daného vlákna.</span><span class="sxs-lookup"><span data-stu-id="288a7-106">[in] The ID of thread in question.</span></span>  
  
 `pbSuspended`  
 <span data-ttu-id="288a7-107">mimo Ukazatel na logickou hodnotu, která je `true` v případě pozastavení zadaného vlákna; v opačném případě \* `pbSuspended` je `false` .</span><span class="sxs-lookup"><span data-stu-id="288a7-107">[out] A pointer to a Boolean value that is `true` if the specified thread has been suspended; otherwise \*`pbSuspended` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="288a7-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="288a7-108">Remarks</span></span>  
 <span data-ttu-id="288a7-109">Pokud bylo zadané vlákno pozastaveno v důsledku zastavení tohoto procesu ladicím programem, je počet pozastavených vláken v systému Win32 zvýšen o jednu.</span><span class="sxs-lookup"><span data-stu-id="288a7-109">When the specified thread has been suspended as a result of the debugger stopping this process, the specified thread's Win32 suspend count is incremented by one.</span></span> <span data-ttu-id="288a7-110">Uživatelské rozhraní (UI) ladicího programu může chtít tyto informace vzít v úvahu, pokud zobrazuje počet pozastavených vláken v operačním systému na uživatele.</span><span class="sxs-lookup"><span data-stu-id="288a7-110">The debugger user interface (UI) may want to take this information into account if it displays the operating system (OS) suspend count of the thread to the user.</span></span>  
  
 <span data-ttu-id="288a7-111">`IsOSSuspended`Metoda dává smysl pouze v kontextu nespravovaného ladění.</span><span class="sxs-lookup"><span data-stu-id="288a7-111">The `IsOSSuspended` method makes sense only in the context of unmanaged debugging.</span></span> <span data-ttu-id="288a7-112">Během spravovaného ladění jsou vlákna v pozastaveném operačním systému spíše pozastavena.</span><span class="sxs-lookup"><span data-stu-id="288a7-112">During managed debugging, threads are cooperatively suspended rather than OS-suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="288a7-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="288a7-113">Requirements</span></span>  
 <span data-ttu-id="288a7-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="288a7-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="288a7-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="288a7-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="288a7-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="288a7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="288a7-117">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="288a7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
