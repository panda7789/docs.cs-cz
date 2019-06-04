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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67bd6e8a0519d35b867cb525d5ff7730c0459016
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490677"
---
# <a name="clrcreatemanagedinstance-function"></a>ClrCreateManagedInstance – funkce
Vytvoří instanci určeného spravovaného typu.  
  
 Tato funkce se již nepoužívá v rozhraní .NET Framework 4. Použít aktivaci modelu COM. k vytvoření instance spravovaného typu, nebo použít hostování (viz [CLR hostování rozhraní přidaná v rozhraní .NET Framework 4 a 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,   
    [in]  REFIID   riid,   
    [out] void     **ppObject  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pTypeName`  
 [in] Ukazatel na název požadovaného typu instance.  
  
 `riid`  
 [in] `IID` Typu instanci požaduje.  
  
 `ppObject`  
 [out] Ukazatel na ukazatel na instanci spravovaného typu, který byl vyžádán volajícím.  
  
## <a name="remarks"></a>Poznámky  
 Modul common language runtime by již načten do procesu. Například můžete načíst pomocí volání [CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) fungovaly před `ClrCreateManagedInstance` funkce je volána. Pokud není načten modul runtime, `ClrCreateManagedInstance` poprvé pokusí se načíst v1.0.3705 modulu runtime. Pokud selže, pokusí se načíst nejnovější verzi modulu runtime.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Zastaralé funkce pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
