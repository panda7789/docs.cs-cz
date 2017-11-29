---
title: "_EFN_GetManagedExcepStack – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _EFN_GetManagedExcepStack
api_location: mscordbi.dll
api_type: COM
f1_keywords: _EFN_GetManagedExcepStack
helpviewer_keywords: _EFN_GetManagedExcepStack function [.NET Framework debugging]
ms.assetid: 21ceed9e-62b2-4024-b027-6d095109955a
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9dabcf1d39bea44a3bd90824082a082ae9650b54
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="efngetmanagedexcepstack-function"></a><span data-ttu-id="74f31-102">_EFN_GetManagedExcepStack – funkce</span><span class="sxs-lookup"><span data-stu-id="74f31-102">_EFN_GetManagedExcepStack Function</span></span>
<span data-ttu-id="74f31-103">Zadaný objekt adresu spravovaného výjimka vrátí řetězec verzi nachází v trasování zásobníku.</span><span class="sxs-lookup"><span data-stu-id="74f31-103">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74f31-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74f31-104">Syntax</span></span>  
  
```  
HRESULT _EFN_GetManagedExcepStack(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       StackObjAddr,  
    [out] __out_ecount(cbString) PSTR szStackString,  
    [out] ULONG         cbString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="74f31-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="74f31-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="74f31-106">[v] Klient laděné.</span><span class="sxs-lookup"><span data-stu-id="74f31-106">[in] The client being debugged.</span></span>  
  
 `StackObjAddr`  
 <span data-ttu-id="74f31-107">[v] Ukazatel spravovaného objektu, odvozené od <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="74f31-107">[in] A managed object pointer, derived from <xref:System.Exception>.</span></span>  
  
 <span data-ttu-id="74f31-108">szStackString</span><span class="sxs-lookup"><span data-stu-id="74f31-108">szStackString</span></span>  
 <span data-ttu-id="74f31-109">[out] Vrácený řetězec.</span><span class="sxs-lookup"><span data-stu-id="74f31-109">[out] The returned string.</span></span>  
  
 `cbString`  
 <span data-ttu-id="74f31-110">[out] Počet znaků, které jsou k dispozici ve vyrovnávací paměti řetězců.</span><span class="sxs-lookup"><span data-stu-id="74f31-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74f31-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="74f31-111">Remarks</span></span>  
 <span data-ttu-id="74f31-112">Pokud neexistuje žádný spravovaný kód ve vlákně aktuálně v kontextu, funkce vrátí HRESULT SOS_E_NOMANAGEDCODE s hodnotou zařízení 0xa0 a chybový kód 0x1000.</span><span class="sxs-lookup"><span data-stu-id="74f31-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74f31-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="74f31-113">Requirements</span></span>  
 <span data-ttu-id="74f31-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74f31-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74f31-115">**Záhlaví:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="74f31-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="74f31-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74f31-116">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74f31-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="74f31-117">See Also</span></span>  
 [<span data-ttu-id="74f31-118">Globální statické funkce ladění</span><span class="sxs-lookup"><span data-stu-id="74f31-118">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
