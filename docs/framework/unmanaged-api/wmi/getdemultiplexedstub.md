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
ms.openlocfilehash: 9cc028b3300b43f8a0fb3e29f8b5ac6e1817b8c1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127474"
---
# <a name="getdemultiplexedstub-function"></a><span data-ttu-id="2e6ad-103">GetDemultiplexedStub – funkce</span><span class="sxs-lookup"><span data-stu-id="2e6ad-103">GetDemultiplexedStub function</span></span>
<span data-ttu-id="2e6ad-104">Vytvoří jímku objektu pro překládání objektů, která klientovi pomůže přijímat asynchronní volání ze správy systému Windows.</span><span class="sxs-lookup"><span data-stu-id="2e6ad-104">Creates an object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="2e6ad-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e6ad-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDemultiplexedStub (
   [in] IUnknown*    pObject, 
   [in] boolean      isLocal, 
   [out] IUnknown**  ppObject
); 
```  

## <a name="parameters"></a><span data-ttu-id="2e6ad-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2e6ad-106">Parameters</span></span>

`pObject`  
<span data-ttu-id="2e6ad-107">pro Ukazatel na implementaci [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink)v rámci procesu klienta.</span><span class="sxs-lookup"><span data-stu-id="2e6ad-107">[in] A pointer to the client's in-process implementation of [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink).</span></span>

`isLocal`  
<span data-ttu-id="2e6ad-108">pro Příznak, který označuje, zda je událost místní (`true`); v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="2e6ad-108">[in] A flag that indicates whether the event is local (`true`); otherwise, `false`.</span></span>

`ppObject`  
<span data-ttu-id="2e6ad-109">mimo Jímka pro překládání objektů pomáhající klientovi při přijímání asynchronních volání ze správy systému Windows.</span><span class="sxs-lookup"><span data-stu-id="2e6ad-109">[out] A object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>

## <a name="return-value"></a><span data-ttu-id="2e6ad-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2e6ad-110">Return value</span></span>

<span data-ttu-id="2e6ad-111">Pokud je funkce úspěšná, návratová hodnota je `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="2e6ad-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="2e6ad-112">Pokud dojde k chybě funkce, vrácená hodnota je nenulový kód chyby.</span><span class="sxs-lookup"><span data-stu-id="2e6ad-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="2e6ad-113">Chcete-li získat rozšířené informace o chybě, zavolejte funkci [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="2e6ad-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
    
## <a name="requirements"></a><span data-ttu-id="2e6ad-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2e6ad-114">Requirements</span></span>  
 <span data-ttu-id="2e6ad-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e6ad-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e6ad-116">**Hlavička:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="2e6ad-116">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="2e6ad-117">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2e6ad-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e6ad-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2e6ad-118">See also</span></span>

- [<span data-ttu-id="2e6ad-119">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="2e6ad-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
