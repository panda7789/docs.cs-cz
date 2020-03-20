---
title: ICorDebugSymbolProvider::Metoda GetAssemblyImageBytes
ms.date: 03/30/2017
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
ms.openlocfilehash: 6361b12802876ef480acbe1cc13f32b77ba0be49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178490"
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a>ICorDebugSymbolProvider::Metoda GetAssemblyImageBytes
Čte data ze sloučeného sestavení dané relativní virtuální adresu (RVA) ve sloučeném sestavení.  
  
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
 [v] Relativní virtuální adresa (RVA) ve sloučeném sestavení.  
  
 `length`  
 Počet bajtů číst ze sloučeného sestavení.  
  
 `ppMemoryBuffer`  
 Ukazatel na adresu objektu [ICorDebugMemoryBuffer,](icordebugmemorybuffer-interface.md) který obsahuje informace o vyrovnávací paměti se sloučenými metadaty sestavení.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s nativní .NET.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugSymbolProvider – rozhraní](icordebugsymbolprovider-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
