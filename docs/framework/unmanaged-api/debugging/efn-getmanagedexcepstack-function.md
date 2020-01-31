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
ms.openlocfilehash: 824be4a401d265575b48f66045dd944d521e64a4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789150"
---
# <a name="_efn_getmanagedexcepstack-function"></a><span data-ttu-id="b870e-102">\_EFN\_GetManagedExcepStack Function</span><span class="sxs-lookup"><span data-stu-id="b870e-102">\_EFN\_GetManagedExcepStack Function</span></span>
<span data-ttu-id="b870e-103">Pokud je zadána adresa spravovaného objektu výjimky, vrátí verzi řetězce trasování zásobníku obsaženého v rámci.</span><span class="sxs-lookup"><span data-stu-id="b870e-103">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b870e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b870e-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedExcepStack(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       StackObjAddr,  
    [out] __out_ecount(cbString) PSTR szStackString,  
    [out] ULONG         cbString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b870e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b870e-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="b870e-106">pro Probíhá ladění klienta.</span><span class="sxs-lookup"><span data-stu-id="b870e-106">[in] The client being debugged.</span></span>  
  
 `StackObjAddr`  
 <span data-ttu-id="b870e-107">pro Ukazatel spravovaného objektu odvozený z <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="b870e-107">[in] A managed object pointer, derived from <xref:System.Exception>.</span></span>  
  
 <span data-ttu-id="b870e-108">szStackString</span><span class="sxs-lookup"><span data-stu-id="b870e-108">szStackString</span></span>  
 <span data-ttu-id="b870e-109">mimo Vrácený řetězec.</span><span class="sxs-lookup"><span data-stu-id="b870e-109">[out] The returned string.</span></span>  
  
 `cbString`  
 <span data-ttu-id="b870e-110">mimo Počet znaků, které jsou k dispozici v bufferu řetězce.</span><span class="sxs-lookup"><span data-stu-id="b870e-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b870e-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b870e-111">Remarks</span></span>  
 <span data-ttu-id="b870e-112">Pokud ve vlákně, který je aktuálně v kontextu, není žádný spravovaný kód, funkce vrátí hodnotu HRESULT SOS_E_NOMANAGEDCODE s hodnotou zařízení 0xa0 a kódem chyby 0x1000.</span><span class="sxs-lookup"><span data-stu-id="b870e-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b870e-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b870e-113">Requirements</span></span>  
 <span data-ttu-id="b870e-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b870e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b870e-115">**Hlavička:** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="b870e-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="b870e-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b870e-116">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b870e-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b870e-117">See also</span></span>

- [<span data-ttu-id="b870e-118">Globální statické funkce pro ladění</span><span class="sxs-lookup"><span data-stu-id="b870e-118">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
