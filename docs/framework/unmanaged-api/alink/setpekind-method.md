---
title: "SetPEKind – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.SetPEKind
api_location: alink.dll
api_type: COM
f1_keywords: SetPEKind
helpviewer_keywords: SetPEKind method
ms.assetid: 050e77ee-3014-45c0-9e29-2ebe29347b0d
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3ad300d86dadd470d0a2d50d5d6deac5bd0bad71
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
