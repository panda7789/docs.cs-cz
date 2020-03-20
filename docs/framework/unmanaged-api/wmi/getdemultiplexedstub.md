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
# <a name="getdemultiplexedstub-function"></a>GetDemultiplexedStub
Vytvoří jímku pro předávání objektů, která pomáhá klientovi přijímat asynchronní volání ze správy systému Windows.
  
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
[v] Ukazatel na inprocesní implementaci [iWbemObjectSink klienta](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink).

`isLocal`  
[v] Příznak označující, zda je`true`událost místní ( ); v `false`opačném případě .

`ppObject`  
[out] Jímka pro předávání objektů, která pomáhá klientovi přijímat asynchronní volání ze správy systému Windows.

## <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, `S_OK` vrácená hodnota je (0).

Pokud funkce selže, vrácená hodnota je nenulový kód chyby. Chcete-li získat rozšířené informace o chybě, zavolejte funkci [GetErrorInfo.](geterrorinfo.md)

## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také

- [Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)](index.md)
