---
title: ICLRDataTarget2::FreeVirtual – metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2.FreeVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2::FreeVirtual
helpviewer_keywords:
- ICLRDataTarget::FreeVirtual method [.NET Framework debugging]
- FreeVirtual method [.NET Framework debugging]
ms.assetid: 26fb69f8-1467-4711-bd24-cb117c63938f
topic_type:
- apiref
ms.openlocfilehash: c084a3fcbbc02504124a511c6e136be32f408d21
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73112328"
---
# <a name="iclrdatatarget2freevirtual-method"></a>ICLRDataTarget2::FreeVirtual – metoda
Volána službami CLR (Common Language Runtime) pro přístup k datům k uvolnění paměti, která byla dříve přidělena v adresním prostoru cílového procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `addr`  
 pro Hodnota `CLRDATA_ADDRESS`, která určuje počáteční adresu paměti, která má být uvolněna.  
  
 `size`  
 pro Velikost paměti, která se má uvolnit (v bajtech)  
  
 `typeFlags`  
 pro Příznaky, které řídí uvolnění paměti. Podívejte se na funkci Win32 `VirtualFree`.  
  
## <a name="remarks"></a>Poznámky  
 Metoda `FreeVirtual` slouží jako logická obálka funkce Win32 `VirtualFree`.  
  
 Tato metoda je implementována modulem pro ladění aplikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** ClrData. idl, ClrData. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRDataTarget2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [AllocVirtual – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)
