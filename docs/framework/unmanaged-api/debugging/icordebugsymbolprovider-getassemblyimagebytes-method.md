---
title: 'ICorDebugSymbolProvider:: GetAssemblyImageBytes – metoda'
ms.date: 03/30/2017
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
ms.openlocfilehash: 3184ba116704df8945b53766e62435a4252eaa11
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138937"
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a>ICorDebugSymbolProvider:: GetAssemblyImageBytes – metoda
Načte data ze sloučeného sestavení s ohledem na relativní virtuální adresu (RVA) ve sloučeném sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,   
   [in] ULONG32 length,   
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `rva`  
 pro Relativní virtuální adresa (RVA) ve sloučeném sestavení.  
  
 `length`  
 Počet bajtů, které mají být čteny ze sloučeného sestavení.  
  
 `ppMemoryBuffer`  
 Ukazatel na adresu objektu [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) , který obsahuje informace o vyrovnávací paměti pro Sloučená metadata sestavení.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugSymbolProvider – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
