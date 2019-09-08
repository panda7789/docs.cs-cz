---
title: GetDemultiplexedStub – funkce (Reference nespravovaného rozhraní API)
description: Funkce GetDemultiplexedStub vytvoří jímku objektu pro překládání objektů, která pomůže klientovi při přijímání asynchronních volání ze správy systému Windows.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a2d3885a4a9e54950909053ba18de5b1891e7edf
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798609"
---
# <a name="getdemultiplexedstub-function"></a><span data-ttu-id="a96a7-103">GetDemultiplexedStub – funkce</span><span class="sxs-lookup"><span data-stu-id="a96a7-103">GetDemultiplexedStub function</span></span>
<span data-ttu-id="a96a7-104">Vytvoří jímku objektu pro překládání objektů, která klientovi pomůže přijímat asynchronní volání ze správy systému Windows.</span><span class="sxs-lookup"><span data-stu-id="a96a7-104">Creates an object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="a96a7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a96a7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDemultiplexedStub (
   [in] IUnknown*    pObject, 
   [in] boolean      isLocal, 
   [out] IUnknown**  ppObject
); 
```  

## <a name="parameters"></a><span data-ttu-id="a96a7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a96a7-106">Parameters</span></span>

`pObject`  
<span data-ttu-id="a96a7-107">pro Ukazatel na implementaci [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink)v rámci procesu klienta.</span><span class="sxs-lookup"><span data-stu-id="a96a7-107">[in] A pointer to the client's in-process implementation of [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink).</span></span>

`isLocal`  
<span data-ttu-id="a96a7-108">pro Příznak, který označuje, zda je událost místní (`true`); `false`v opačném případě.</span><span class="sxs-lookup"><span data-stu-id="a96a7-108">[in] A flag that indicates whether the event is local (`true`); otherwise, `false`.</span></span>

`ppObject`  
<span data-ttu-id="a96a7-109">mimo Jímka pro překládání objektů pomáhající klientovi při přijímání asynchronních volání ze správy systému Windows.</span><span class="sxs-lookup"><span data-stu-id="a96a7-109">[out] A object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>

## <a name="return-value"></a><span data-ttu-id="a96a7-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a96a7-110">Return value</span></span>

<span data-ttu-id="a96a7-111">Pokud je funkce úspěšná, vrácená hodnota je `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="a96a7-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="a96a7-112">Pokud dojde k chybě funkce, vrácená hodnota je nenulový kód chyby.</span><span class="sxs-lookup"><span data-stu-id="a96a7-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="a96a7-113">Chcete-li získat rozšířené informace o chybě, zavolejte funkci [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="a96a7-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
    
## <a name="requirements"></a><span data-ttu-id="a96a7-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a96a7-114">Requirements</span></span>  
 <span data-ttu-id="a96a7-115">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a96a7-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a96a7-116">**Hlaviček** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="a96a7-116">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="a96a7-117">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a96a7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a96a7-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a96a7-118">See also</span></span>

- [<span data-ttu-id="a96a7-119">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="a96a7-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
