---
title: "Funkce GetDemultiplexedStub (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce GetDemultiplexedStub vytvoří předávání podřízený objekt klienta jako pomůcku při přijímání asynchronní volání od Správa systému Windows."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetDemultiplexedStub
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetDemultiplexedStub
helpviewer_keywords: GetDemultiplexedStub function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6ba7ca9941dc148444a4c605fecc8aaf150e8601
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="getdemultiplexedstub-function"></a><span data-ttu-id="e9ab2-103">GetDemultiplexedStub – funkce</span><span class="sxs-lookup"><span data-stu-id="e9ab2-103">GetDemultiplexedStub function</span></span>
<span data-ttu-id="e9ab2-104">Vytvoří předávání podřízený objekt klienta jako pomůcku při přijímání asynchronní volání od Správa systému Windows.</span><span class="sxs-lookup"><span data-stu-id="e9ab2-104">Creates an object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="e9ab2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9ab2-105">Syntax</span></span>  
  
```  
HRESULT GetDemultiplexedStub (
   [in] IUnknown*    pObject, 
   [in] boolean      isLocal, 
   [out] IUnknown**  ppObject
); 
```  

## <a name="parameters"></a><span data-ttu-id="e9ab2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9ab2-106">Parameters</span></span>

`pObject`  
<span data-ttu-id="e9ab2-107">[v] Ukazatel na implementaci klienta v rámci procesu [IWbemObjectSink](https://msdn.microsoft.com/en-us/library/aa391787(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="e9ab2-107">[in] A pointer to the client's in-process implementation of [IWbemObjectSink](https://msdn.microsoft.com/en-us/library/aa391787(v=vs.85).aspx).</span></span>

`isLocal`  
<span data-ttu-id="e9ab2-108">[v] Příznak, který určuje, zda je místní události (`true`), jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="e9ab2-108">[in] A flag that indicates whether the event is local (`true`); otherwise, `false`.</span></span>

`ppObject`  
<span data-ttu-id="e9ab2-109">[out] Podřízený objekt předávání klienta jako pomůcku při přijímání asynchronní volání od Správa systému Windows.</span><span class="sxs-lookup"><span data-stu-id="e9ab2-109">[out] A object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>

## <a name="return-value"></a><span data-ttu-id="e9ab2-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e9ab2-110">Return value</span></span>

<span data-ttu-id="e9ab2-111">Pokud funkci úspěšné, je vrácenou hodnotu `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="e9ab2-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="e9ab2-112">V případě selhání funkce návratovou hodnotu je kód chyby nulová.</span><span class="sxs-lookup"><span data-stu-id="e9ab2-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="e9ab2-113">Chcete-li získat rozšířené informace o chybě, zavolejte [GetErrorInfo –](geterrorinfo.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="e9ab2-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
    
## <a name="requirements"></a><span data-ttu-id="e9ab2-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e9ab2-114">Requirements</span></span>  
 <span data-ttu-id="e9ab2-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9ab2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9ab2-116">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="e9ab2-116">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="e9ab2-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e9ab2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9ab2-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9ab2-118">See also</span></span>  
[<span data-ttu-id="e9ab2-119">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="e9ab2-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
