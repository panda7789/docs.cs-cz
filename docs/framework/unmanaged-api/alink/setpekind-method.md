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
ms.openlocfilehash: dfbc10bdbe633450dee2e27524c29ead21fb739e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445531"
---
# <a name="setpekind-method"></a>SetPEKind – metoda
Určuje typ přenositelného spustitelného souboru, který je specifický pro konkrétní počítač nebo Machine-nezávislá.  
  
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
 ID sestavení  
  
 `FileToken`  
 Token souboru, pro který má být nastaven typ PE. Může mít hodnotu NULL, pokud `AssemblyID` neindikuje nevázaný netmodule.  
  
 `dwPEKind`  
 Typ PE, jak je uvedeno ve [výčtu CorPEKind –](../metadata/corpekind-enumeration.md).  
  
 `dwMachine`  
 Architektura cílového počítače, jak je uvedeno v hlavičce NT.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK, pokud je metoda úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje ALink. h.  
  
## <a name="see-also"></a>Viz také:

- [GetPEKind – metoda](../metadata/imetadataimport2-getpekind-method.md)
- [IALink2 – rozhraní](ialink2-interface.md)
- [IALink – rozhraní](ialink-interface.md)
- [Rozhraní API ALink](index.md)
