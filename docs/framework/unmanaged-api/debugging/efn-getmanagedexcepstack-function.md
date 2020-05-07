---
title: _EFN_GetManagedExcepStack – funkce
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedExcepStack
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedExcepStack
helpviewer_keywords:
- _EFN_GetManagedExcepStack function [.NET Framework debugging]
ms.assetid: 21ceed9e-62b2-4024-b027-6d095109955a
topic_type:
- apiref
ms.openlocfilehash: c50fe09648793ba7340960654811ff31187269d8
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860784"
---
# <a name="_efn_getmanagedexcepstack-function"></a><span data-ttu-id="8674d-102">\_EFN\_– funkce GetManagedExcepStack</span><span class="sxs-lookup"><span data-stu-id="8674d-102">\_EFN\_GetManagedExcepStack Function</span></span>
<span data-ttu-id="8674d-103">Pokud je zadána adresa spravovaného objektu výjimky, vrátí verzi řetězce trasování zásobníku obsaženého v rámci.</span><span class="sxs-lookup"><span data-stu-id="8674d-103">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8674d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8674d-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedExcepStack(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       StackObjAddr,  
    [out] __out_ecount(cbString) PSTR szStackString,  
    [out] ULONG         cbString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8674d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8674d-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="8674d-106">pro Probíhá ladění klienta.</span><span class="sxs-lookup"><span data-stu-id="8674d-106">[in] The client being debugged.</span></span>  
  
 `StackObjAddr`  
 <span data-ttu-id="8674d-107">pro Ukazatel spravovaného objektu odvozený z <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="8674d-107">[in] A managed object pointer, derived from <xref:System.Exception>.</span></span>  
  
 <span data-ttu-id="8674d-108">szStackString</span><span class="sxs-lookup"><span data-stu-id="8674d-108">szStackString</span></span>  
 <span data-ttu-id="8674d-109">mimo Vrácený řetězec.</span><span class="sxs-lookup"><span data-stu-id="8674d-109">[out] The returned string.</span></span>  
  
 `cbString`  
 <span data-ttu-id="8674d-110">mimo Počet znaků, které jsou k dispozici v bufferu řetězce.</span><span class="sxs-lookup"><span data-stu-id="8674d-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8674d-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8674d-111">Remarks</span></span>  
 <span data-ttu-id="8674d-112">Pokud ve vlákně, který je aktuálně v kontextu, není žádný spravovaný kód, funkce vrátí hodnotu HRESULT SOS_E_NOMANAGEDCODE s hodnotou zařízení 0xa0 a kódem chyby 0x1000.</span><span class="sxs-lookup"><span data-stu-id="8674d-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8674d-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8674d-113">Requirements</span></span>  
 <span data-ttu-id="8674d-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8674d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8674d-115">**Hlavička:** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="8674d-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="8674d-116">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8674d-116">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8674d-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="8674d-117">See also</span></span>

- [<span data-ttu-id="8674d-118">Globální statické funkce ladění</span><span class="sxs-lookup"><span data-stu-id="8674d-118">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
