---
title: ClrCreateManagedInstance – funkce
ms.date: 03/30/2017
api_name:
- ClrCreateManagedInstance
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- ClrCreateManagedInstance
helpviewer_keywords:
- ClrCreateManagedInstance function [.NET Framework hosting]
ms.assetid: 58ba42c0-4857-43bf-a039-73a4dc6544c2
topic_type:
- apiref
ms.openlocfilehash: ecd618ecf08836ea5e38ce738f97fc91ee6426f4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616809"
---
# <a name="clrcreatemanagedinstance-function"></a>ClrCreateManagedInstance – funkce
Vytvoří instanci zadaného spravovaného typu.  
  
 Tato funkce se už nepoužívá v .NET Framework 4. Použijte aktivaci COM k vytvoření instance spravovaného typu nebo použijte hostování (viz [rozhraní pro hostování CLR přidaná v .NET Framework 4 a 4,5](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,
    [in]  REFIID   riid,
    [out] void     **ppObject  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pTypeName`  
 pro Ukazatel na název požadovaného typu instance.  
  
 `riid`  
 pro Požadovaný `IID` typ instance.  
  
 `ppObject`  
 mimo Ukazatel na ukazatel na instanci spravovaného typu, který požadoval volající.  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR (Common Language Runtime) by již měl být načten do procesu. Například může být načten pomocí volání funkce [CorBindToRuntimeEx –](corbindtoruntimeex-function.md) před `ClrCreateManagedInstance` voláním funkce. Pokud modul runtime není načtený, `ClrCreateManagedInstance` nejprve se pokusí načíst v 1.0.3705 modulu runtime. Pokud se to nepovede, pokusí se načíst nejnovější verzi modulu runtime.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Zastaralé funkce hostování CLR](deprecated-clr-hosting-functions.md)
- [Hostování](index.md)
