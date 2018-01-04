---
title: "ICorDebugDataTarget2::GetImageFromPointer – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cfe25a90fb2084c1f58eff5b42e24b15decb0163
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a>ICorDebugDataTarget2::GetImageFromPointer – metoda
Vrátí základní adresa modulu a velikost z adresy v tomto modulu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,   
   [out] CORDB_ADDRESS *pImageBase,   
   [out] ULONG32 *pSize  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `addr`  
 A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) hodnotu, která představuje adresu v modulu.  
  
 `pImageBase`  
 [out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) hodnotu, která představuje základní adresu modulu.  
  
 `pSize`  
 Ukazatel na velikost modulu.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Tato metoda je k dispozici s .NET Native jenom.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugDataTarget2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
