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
# <a name="getdemultiplexedstub-function"></a>GetDemultiplexedStub – funkce
Vytvoří jímku objektu pro překládání objektů, která klientovi pomůže přijímat asynchronní volání ze správy systému Windows.
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetDemultiplexedStub (
   [in] IUnknown*    pObject, 
   [in] boolean      isLocal, 
   [out] IUnknown**  ppObject
); 
```  

## <a name="parameters"></a>Parametry

`pObject`  
pro Ukazatel na implementaci [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink)v rámci procesu klienta.

`isLocal`  
pro Příznak, který označuje, zda je událost místní (`true`); `false`v opačném případě.

`ppObject`  
mimo Jímka pro překládání objektů pomáhající klientovi při přijímání asynchronních volání ze správy systému Windows.

## <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, vrácená hodnota je `S_OK` (0).

Pokud dojde k chybě funkce, vrácená hodnota je nenulový kód chyby. Chcete-li získat rozšířené informace o chybě, zavolejte funkci [GetErrorInfo](geterrorinfo.md) .
    
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** WMINet_Utils.idl  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
