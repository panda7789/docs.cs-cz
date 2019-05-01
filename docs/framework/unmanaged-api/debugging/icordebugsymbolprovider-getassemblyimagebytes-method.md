---
title: ICorDebugSymbolProvider::GetAssemblyImageBytes – metoda
ms.date: 03/30/2017
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 103e724c37ae356729dd5bba3ff66c0f443f6eaa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61953520"
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a>ICorDebugSymbolProvider::GetAssemblyImageBytes – metoda
Přečte data ze sloučeného sestavení sloučeného sestavení podle relativní virtuální adresu (RVA).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,   
   [in] ULONG32 length,   
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `rva`  
 [in] Relativní virtuální adresu (RVA) ve sloučené sestavení.  
  
 `length`  
 Počet bajtů ke čtení ze sloučeného sestavení.  
  
 `ppMemoryBuffer`  
 Ukazatel na adresu [icordebugmemorybuffer –](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) objekt, který obsahuje informace o vyrovnávací paměti s metadaty sloučené sestavení.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Tato metoda je pouze k dispozici s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugSymbolProvider – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
