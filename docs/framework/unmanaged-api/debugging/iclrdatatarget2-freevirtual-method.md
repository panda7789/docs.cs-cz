---
title: "ICLRDataTarget2::FreeVirtual – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c6c52291d08af4c9537de6ca17d80f28870a6bc8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatarget2freevirtual-method"></a>ICLRDataTarget2::FreeVirtual – metoda
Voláno rozhraním common language runtime (CLR) služby přístupu k datům volné paměti, které již bylo přiděleno v adresním prostoru tento cílový proces.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `addr`  
 [v] A `CLRDATA_ADDRESS` hodnotu, která určuje počáteční adresa paměti na uvolnění.  
  
 `size`  
 [v] Velikost v bajtech, na uvolnění paměti.  
  
 `typeFlags`  
 [v] Příznaky, které řídí uvolnění paměti. V tématu Win32 `VirtualFree` funkce.  
  
## <a name="remarks"></a>Poznámky  
 `FreeVirtual` Metoda slouží jako logické obálku pro Win32 `VirtualFree` funkce.  
  
 Tato metoda je implementována zapisovačem ladění aplikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** ClrData.idl, ClrData.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRDataTarget2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [AllocVirtual – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)
