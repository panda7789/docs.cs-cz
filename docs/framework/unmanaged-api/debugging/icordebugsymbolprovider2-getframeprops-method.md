---
title: 'ICorDebugSymbolProvider2:: GetFrameProps – metoda'
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
ms.openlocfilehash: dc64152938c46945978715251286ecb6c6d8983c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791513"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a>ICorDebugSymbolProvider2:: GetFrameProps – metoda
Vrátí metodu, která spouští relativní virtuální adresu metody a nadřazený rámec pro relativní virtuální adresu kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `codeRva`  
 pro Relativní virtuální adresa pro kód.  
  
 `pCodeStartRva`  
 mimo Ukazatel na počáteční relativní virtuální adresu metody.  
  
 `pParentFrameStartRva`  
 mimo Ukazatel na počáteční relativní virtuální adresu rámce.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugSymbolProvider2 – rozhraní](icordebugsymbolprovider2-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
