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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c1c05918965e40801757462ce53257bc36a5d8c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587710"
---
# <a name="efngetmanagedexcepstack-function"></a><span data-ttu-id="6f4c2-102">_EFN_GetManagedExcepStack – funkce</span><span class="sxs-lookup"><span data-stu-id="6f4c2-102">_EFN_GetManagedExcepStack Function</span></span>
<span data-ttu-id="6f4c2-103">Zadaný objekt na spravované výjimky adresu vrátí řetězec verzi obsažena v trasování zásobníku.</span><span class="sxs-lookup"><span data-stu-id="6f4c2-103">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f4c2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f4c2-104">Syntax</span></span>  
  
```  
HRESULT _EFN_GetManagedExcepStack(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       StackObjAddr,  
    [out] __out_ecount(cbString) PSTR szStackString,  
    [out] ULONG         cbString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6f4c2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6f4c2-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="6f4c2-106">[in] Klient, který se právě ladí.</span><span class="sxs-lookup"><span data-stu-id="6f4c2-106">[in] The client being debugged.</span></span>  
  
 `StackObjAddr`  
 <span data-ttu-id="6f4c2-107">[in] Ukazatel spravovaný objekt, odvozený z <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="6f4c2-107">[in] A managed object pointer, derived from <xref:System.Exception>.</span></span>  
  
 <span data-ttu-id="6f4c2-108">szStackString</span><span class="sxs-lookup"><span data-stu-id="6f4c2-108">szStackString</span></span>  
 <span data-ttu-id="6f4c2-109">[out] Vrácený řetězec.</span><span class="sxs-lookup"><span data-stu-id="6f4c2-109">[out] The returned string.</span></span>  
  
 `cbString`  
 <span data-ttu-id="6f4c2-110">[out] Počet znaků, které jsou k dispozici ve vyrovnávací paměti řetězce.</span><span class="sxs-lookup"><span data-stu-id="6f4c2-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f4c2-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6f4c2-111">Remarks</span></span>  
 <span data-ttu-id="6f4c2-112">Pokud neexistuje žádný spravovaný kód ve vlákně aktuálně v kontextu, funkce vrátí HRESULT SOS_E_NOMANAGEDCODE s hodnotou zařízení 0xa0 a 0x1000 kód chyby.</span><span class="sxs-lookup"><span data-stu-id="6f4c2-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f4c2-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6f4c2-113">Requirements</span></span>  
 <span data-ttu-id="6f4c2-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f4c2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f4c2-115">**Záhlaví:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="6f4c2-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="6f4c2-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f4c2-116">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f4c2-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6f4c2-117">See also</span></span>
- [<span data-ttu-id="6f4c2-118">Globální statické funkce pro ladění</span><span class="sxs-lookup"><span data-stu-id="6f4c2-118">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
