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
ms.openlocfilehash: 7e201b9a350c030da59e2b6ed27f84f570c8e621
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59126656"
---
# <a name="efngetmanagedexcepstack-function"></a><span data-ttu-id="0831e-102">_EFN_GetManagedExcepStack – funkce</span><span class="sxs-lookup"><span data-stu-id="0831e-102">_EFN_GetManagedExcepStack Function</span></span>
<span data-ttu-id="0831e-103">Zadaný objekt na spravované výjimky adresu vrátí řetězec verzi obsažena v trasování zásobníku.</span><span class="sxs-lookup"><span data-stu-id="0831e-103">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0831e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0831e-104">Syntax</span></span>  
  
```  
HRESULT _EFN_GetManagedExcepStack(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       StackObjAddr,  
    [out] __out_ecount(cbString) PSTR szStackString,  
    [out] ULONG         cbString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0831e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0831e-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="0831e-106">[in] Klient, který se právě ladí.</span><span class="sxs-lookup"><span data-stu-id="0831e-106">[in] The client being debugged.</span></span>  
  
 `StackObjAddr`  
 <span data-ttu-id="0831e-107">[in] Ukazatel spravovaný objekt, odvozený z <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="0831e-107">[in] A managed object pointer, derived from <xref:System.Exception>.</span></span>  
  
 <span data-ttu-id="0831e-108">szStackString</span><span class="sxs-lookup"><span data-stu-id="0831e-108">szStackString</span></span>  
 <span data-ttu-id="0831e-109">[out] Vrácený řetězec.</span><span class="sxs-lookup"><span data-stu-id="0831e-109">[out] The returned string.</span></span>  
  
 `cbString`  
 <span data-ttu-id="0831e-110">[out] Počet znaků, které jsou k dispozici ve vyrovnávací paměti řetězce.</span><span class="sxs-lookup"><span data-stu-id="0831e-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0831e-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0831e-111">Remarks</span></span>  
 <span data-ttu-id="0831e-112">Pokud neexistuje žádný spravovaný kód ve vlákně aktuálně v kontextu, funkce vrátí HRESULT SOS_E_NOMANAGEDCODE s hodnotou zařízení 0xa0 a 0x1000 kód chyby.</span><span class="sxs-lookup"><span data-stu-id="0831e-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0831e-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0831e-113">Requirements</span></span>  
 <span data-ttu-id="0831e-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0831e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0831e-115">**Záhlaví:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="0831e-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 **<span data-ttu-id="0831e-116">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="0831e-116">.NET Framework Version:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0831e-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0831e-117">See also</span></span>

- [<span data-ttu-id="0831e-118">Globální statické funkce ladění</span><span class="sxs-lookup"><span data-stu-id="0831e-118">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
