---
title: PFN_CLRDataCreateInstance – ukazatel na funkci
ms.date: 03/30/2017
api_name:
- PFN_CLRDataCreateInstance
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- PFN_CLRDataCreateInstance
helpviewer_keywords:
- PFN_CLRDataCreateInstance function pointer [.NET Framework debugging]
ms.assetid: 5c66ac57-d751-4de5-af9f-26ceb949af8b
topic_type:
- apiref
ms.openlocfilehash: 433f34447d3bd1a57ca1e289cb0eab3facac2c69
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790359"
---
# <a name="pfn_clrdatacreateinstance-function-pointer"></a>PFN_CLRDataCreateInstance – ukazatel na funkci
Odkazuje na funkci, která vytvoří objekt rozhraní pro zadanou cílovou položku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef HRESULT (STDAPICALLTYPE* PFN_CLRDataCreateInstance) (  
    [in]  REFIID           iid,  
    [in]  ICLRDataTarget  *target,  
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `iid`  
 pro Identifikátor rozhraní, které má být vytvořena instance.  
  
 `target`  
 pro Ukazatel na uživatelem implementovaný objekt [ICLRDataTarget](iclrdatatarget-interface.md) , který představuje cílovou položku, pro kterou chcete vytvořit objekt rozhraní.  
  
 `iface`  
 mimo Ukazatel na adresu vráceného objektu rozhraní.  
  
## <a name="remarks"></a>Poznámky  
 Objekt `ICLRDataTarget` je implementován modulem pro ladění aplikace. Implementace závisí na typu reprezentované cílové položky. Cílová položka může být proces, výpis paměti, vzdálený počítač atd.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** ClrData. idl  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Globální statické funkce pro ladění](debugging-global-static-functions.md)
