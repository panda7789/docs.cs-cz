---
title: 'ICorDebugSymbolProvider:: GetCodeRange – metoda'
ms.date: 03/30/2017
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
ms.openlocfilehash: a9c1a4a625196d7430e365916cc7c2b67bf94127
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83376093"
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a>ICorDebugSymbolProvider:: GetCodeRange – metoda
Získá počáteční adresu a velikost metody dané relativní virtuální adresy (RVA) v metodě.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,
   [out] ULONG32* pCodeStartAddress,
   [out] ULONG32* pCodeSize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `codeRva`  
 pro Relativní virtuální adresa (RVA) v metodě.  
  
 `pCodeStartAddress`  
 mimo Ukazatel na počáteční adresu metody.  
  
 `pCodeSize`  
 Ukazatel na velikost kódu metody (počet bajtů kódu metody).  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugSymbolProvider – rozhraní](icordebugsymbolprovider-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
