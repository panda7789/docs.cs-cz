---
title: Funkce GetDemultiplexedStub (Nespravovaný odkaz na rozhraní API)
description: Funkce GetDemultiplexedStub vytvoří jímku pro předávání objektů, která klientovi pomáhá přijímat asynchronní volání ze správy systému Windows.
ms.date: 11/06/2017
api_name:
- GetDemultiplexedStub
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetDemultiplexedStub
helpviewer_keywords:
- GetDemultiplexedStub function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: d15fed261db2ca2cda6dbf824dc9cb0d5c56eed3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174963"
---
# <a name="getdemultiplexedstub-function"></a><span data-ttu-id="8526f-103">GetDemultiplexedStub</span><span class="sxs-lookup"><span data-stu-id="8526f-103">GetDemultiplexedStub function</span></span>
<span data-ttu-id="8526f-104">Vytvoří jímku pro předávání objektů, která pomáhá klientovi přijímat asynchronní volání ze správy systému Windows.</span><span class="sxs-lookup"><span data-stu-id="8526f-104">Creates an object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="8526f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8526f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDemultiplexedStub (
   [in] IUnknown*    pObject,
   [in] boolean      isLocal,
   [out] IUnknown**  ppObject
);
```  

## <a name="parameters"></a><span data-ttu-id="8526f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8526f-106">Parameters</span></span>

`pObject`  
<span data-ttu-id="8526f-107">[v] Ukazatel na inprocesní implementaci [iWbemObjectSink klienta](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink).</span><span class="sxs-lookup"><span data-stu-id="8526f-107">[in] A pointer to the client's in-process implementation of [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink).</span></span>

`isLocal`  
<span data-ttu-id="8526f-108">[v] Příznak označující, zda je`true`událost místní ( ); v `false`opačném případě .</span><span class="sxs-lookup"><span data-stu-id="8526f-108">[in] A flag that indicates whether the event is local (`true`); otherwise, `false`.</span></span>

`ppObject`  
<span data-ttu-id="8526f-109">[out] Jímka pro předávání objektů, která pomáhá klientovi přijímat asynchronní volání ze správy systému Windows.</span><span class="sxs-lookup"><span data-stu-id="8526f-109">[out] A object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>

## <a name="return-value"></a><span data-ttu-id="8526f-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8526f-110">Return value</span></span>

<span data-ttu-id="8526f-111">Pokud je funkce úspěšná, `S_OK` vrácená hodnota je (0).</span><span class="sxs-lookup"><span data-stu-id="8526f-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="8526f-112">Pokud funkce selže, vrácená hodnota je nenulový kód chyby.</span><span class="sxs-lookup"><span data-stu-id="8526f-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="8526f-113">Chcete-li získat rozšířené informace o chybě, zavolejte funkci [GetErrorInfo.](geterrorinfo.md)</span><span class="sxs-lookup"><span data-stu-id="8526f-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="8526f-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8526f-114">Requirements</span></span>  
 <span data-ttu-id="8526f-115">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8526f-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8526f-116">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="8526f-116">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="8526f-117">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8526f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8526f-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="8526f-118">See also</span></span>

- [<span data-ttu-id="8526f-119">Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="8526f-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
