---
title: SetPEKind – metoda
ms.date: 03/30/2017
api_name:
- IALink2.SetPEKind
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetPEKind
helpviewer_keywords:
- SetPEKind method
ms.assetid: 050e77ee-3014-45c0-9e29-2ebe29347b0d
topic_type:
- apiref
ms.openlocfilehash: 5a8442b1f0869e1592a05dfeeb0f5e6d583f3ea8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179386"
---
# <a name="setpekind-method"></a>SetPEKind – metoda
Určuje přenosný spustitelný typ, buď specifický pro počítač nebo nezávislá na počítači.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;
```  
  
## <a name="parameters"></a>Parametry  
 `AssemblyID`  
 ID sestavení.  
  
 `FileToken`  
 Token souboru, pro který má být nastaven typ PE. Může být `AssemblyID` NULL, pokud neoznačuje nevázaný netmodule.  
  
 `dwPEKind`  
 Typ PE, jak je uvedeno ve [výčtu CorPEKind](../metadata/corpekind-enumeration.md).  
  
 `dwMachine`  
 Architektura cílového počítače, jak je uvedeno v záhlaví NT.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK, pokud je metoda úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje alink.h.  
  
## <a name="see-also"></a>Viz také

- [GetPEKind – metoda](../metadata/imetadataimport2-getpekind-method.md)
- [IALink2 – rozhraní](ialink2-interface.md)
- [IALink – rozhraní](ialink-interface.md)
- [ALink API](index.md)
