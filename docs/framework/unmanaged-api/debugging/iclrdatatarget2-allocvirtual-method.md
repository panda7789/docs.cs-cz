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
ms.openlocfilehash: 51c06a7f8ea22fc73236131954781d8755274041
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789090"
---
# <a name="iclrdatatarget2allocvirtual-method"></a>ICLRDataTarget2::AllocVirtual – metoda
Volá se službami CLR (Common Language Runtime) k přidělení paměti v adresním prostoru tohoto cílového procesu.  
  
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
 pro Hodnota `CLRDATA_ADDRESS`, která určuje požadovanou počáteční adresu paměti, která má být přidělena.  
  
 `size`  
 pro Velikost paměti, která se má přidělit (v bajtech)  
  
 `typeFlags`  
 pro Příznaky, které řídí přidělení paměti. Podívejte se na funkci Win32 `VirtualAlloc`.  
  
 `protectFlags`  
 pro Atributy ochrany přidělené paměti. Podívejte se na funkci Win32 `VirtualAlloc`.  
  
 `virt`  
 mimo Ukazatel na hodnotu `CLRDATA_ADDRESS`, která určuje skutečnou počáteční adresu přidělené paměti.  
  
## <a name="remarks"></a>Poznámky  
 Metoda `AllocVirtual` slouží jako logická obálka funkce Win32 `VirtualAlloc`.  
  
 Tato metoda je implementována modulem pro ladění aplikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** ClrData. idl, ClrData. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRDataTarget2 – rozhraní](iclrdatatarget2-interface.md)
- [FreeVirtual – metoda](iclrdatatarget2-freevirtual-method.md)
