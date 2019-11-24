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
Determines the portable executable type, either machine-specific or machine-agnostic.  
  
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
 ID of the assembly.  
  
 `FileToken`  
 Token of file for which the PE type is to be set. Can be NULL if `AssemblyID` does not indicate an unbound netmodule.  
  
 `dwPEKind`  
 The type of PE, as indicated by the [CorPEKind Enumeration](../metadata/corpekind-enumeration.md).  
  
 `dwMachine`  
 The target machine architecture, as indicated in the NT header.  
  
## <a name="return-value"></a>Návratová hodnota  
 Returns S_OK if the method succeeds.  
  
## <a name="requirements"></a>Požadavky  
 Requires alink.h.  
  
## <a name="see-also"></a>Viz také:

- [GetPEKind – metoda](../metadata/imetadataimport2-getpekind-method.md)
- [IALink2 – rozhraní](ialink2-interface.md)
- [IALink – rozhraní](ialink-interface.md)
- [ALink API](index.md)
