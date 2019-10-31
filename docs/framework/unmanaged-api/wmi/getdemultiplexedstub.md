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
pro Příznak, který označuje, zda je událost místní (`true`); v opačném případě `false`.

`ppObject`  
mimo Jímka pro překládání objektů pomáhající klientovi při přijímání asynchronních volání ze správy systému Windows.

## <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, návratová hodnota je `S_OK` (0).

Pokud dojde k chybě funkce, vrácená hodnota je nenulový kód chyby. Chcete-li získat rozšířené informace o chybě, zavolejte funkci [GetErrorInfo](geterrorinfo.md) .
    
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** WMINet_Utils. idl  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
