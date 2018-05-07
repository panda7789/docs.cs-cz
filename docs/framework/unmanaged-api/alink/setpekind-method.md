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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4b985aeb97621e552e9e97581e67cae029d019ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="setpekind-method"></a>SetPEKind – metoda
Určuje konkrétní počítač nebo počítače bez ohledu na typ přenosné spustitelný soubor.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;   
```  
  
#### <a name="parameters"></a>Parametry  
 `AssemblyID`  
 ID sestavení.  
  
 `FileToken`  
 Token souboru, pro kterou má být nastavena typ PE. Může mít hodnotu NULL, pokud `AssemblyID` neindikuje nevázaný netmodule.  
  
 `dwPEKind`  
 Typ PE, jak [CorPEKind – výčet](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md).  
  
 `dwMachine`  
 Architektury cílového počítače, jak je uvedeno v hlavičce NT.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK, pokud metoda bude úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje alink.h.  
  
## <a name="see-also"></a>Viz také  
 [GetPEKind – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)  
 [IALink2 – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [IALink – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [Rozhraní API ALink](../../../../docs/framework/unmanaged-api/alink/index.md)
