---
title: "ICorDebugSymbolProvider::GetAssemblyImageBytes – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 23c6dc836aefe1dd89431e003058ba2056eba3ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a>ICorDebugSymbolProvider::GetAssemblyImageBytes – metoda
Čte data z sloučené sestavení zadaný relativní virtuální adresy (RVA) v sloučené sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,   
   [in] ULONG32 length,   
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `rva`  
 [v] Relativní virtuální adresu (RVA) v sloučené sestavení.  
  
 `length`  
 Počet bajtů ke čtení z sloučené sestavení.  
  
 `ppMemoryBuffer`  
 Ukazatel na adresu [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) objekt, který obsahuje informace o vyrovnávací paměť s metadaty sloučené sestavení.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Tato metoda je k dispozici s .NET Native jenom.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugSymbolProvider – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
