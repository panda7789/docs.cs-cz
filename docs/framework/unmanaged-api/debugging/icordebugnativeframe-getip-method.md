---
title: ICorDebugNativeFrame::GetIP – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
- ICorDebugNativeFrame::GetIP method [.NET Framework debugging]
ms.assetid: 99f693f3-d3b9-4fd8-9d09-b8efd03f7b67
topic_type:
- apiref
ms.openlocfilehash: 53576ca938074fb7e5974a96bb53a84cb6ed67ab
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213592"
---
# <a name="icordebugnativeframegetip-method"></a><span data-ttu-id="24e89-102">ICorDebugNativeFrame::GetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="24e89-102">ICorDebugNativeFrame::GetIP Method</span></span>
<span data-ttu-id="24e89-103">Získá umístění posunutí nativního kódu, na který je aktuálně nastaven ukazatel na instrukci.</span><span class="sxs-lookup"><span data-stu-id="24e89-103">Gets the native code offset location to which the instruction pointer is currently set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24e89-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="24e89-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32           *pnOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24e89-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="24e89-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="24e89-106">mimo Ukazatel na umístění posunu v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="24e89-106">[out] A pointer to the offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24e89-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="24e89-107">Remarks</span></span>  
 <span data-ttu-id="24e89-108">Pokud je aktivní rámec zásobníku, který je reprezentován tímto "ICorDebugNativeFrame", posunem je adresa dalšího pokynu, který má být proveden.</span><span class="sxs-lookup"><span data-stu-id="24e89-108">If the stack frame that is represented by this "ICorDebugNativeFrame" is active, the offset is the address of the next instruction to be executed.</span></span> <span data-ttu-id="24e89-109">Pokud tento rámec zásobníku není aktivní, posun je adresa další instrukce, která se má provést, když se znovu aktivuje rámec zásobníku.</span><span class="sxs-lookup"><span data-stu-id="24e89-109">If this stack frame is not active, the offset is the address of the next instruction to be executed when the stack frame is reactivated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24e89-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="24e89-110">Requirements</span></span>  
 <span data-ttu-id="24e89-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24e89-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24e89-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="24e89-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="24e89-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="24e89-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24e89-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24e89-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24e89-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="24e89-115">See also</span></span>
