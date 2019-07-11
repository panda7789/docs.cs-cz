---
title: ICLRDataTarget2::AllocVirtual – metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2.AllocVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2::AllocVirtual
helpviewer_keywords:
- ICLRDataTarget2::AllocVirtual method [.NET Framework debugging]
- AllocVirtual method [.NET Framework debugging]
ms.assetid: e3226230-964b-47fb-9f53-d6fdbeda1e9e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 92eff65078f05557f542c64c1be7d4f6eca43eb5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738469"
---
# <a name="iclrdatatarget2allocvirtual-method"></a>ICLRDataTarget2::AllocVirtual – metoda
Je voláno common language runtime (CLR) data access services přidělení paměti v adresním prostoru cílového procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT AllocVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags,  
    [in] ULONG32 protectFlags,  
    [out] CLRDATA_ADDRESS* virt  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `addr`  
 [in] A `CLRDATA_ADDRESS` hodnota, která určuje požadovanou počáteční adresu paměti, která bude přidělena.  
  
 `size`  
 [in] Velikost v bajtech, která bude přidělena paměť.  
  
 `typeFlags`  
 [in] Příznaky, které řídí přidělení paměti. Zobrazit Win32 `VirtualAlloc` funkce.  
  
 `protectFlags`  
 [in] Atributy ochrany pro přidělené paměti. Zobrazit Win32 `VirtualAlloc` funkce.  
  
 `virt`  
 [out] Ukazatel `CLRDATA_ADDRESS` hodnota, která určuje skutečné počáteční adresa přidělené paměti.  
  
## <a name="remarks"></a>Poznámky  
 `AllocVirtual` Metody slouží jako logické obálku pro Win32 `VirtualAlloc` funkce.  
  
 Tato metoda je implementováno tvůrci ladění aplikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** ClrData.idl, ClrData.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRDataTarget2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [FreeVirtual – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)
