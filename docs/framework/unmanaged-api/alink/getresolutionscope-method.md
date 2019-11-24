---
title: GetResolutionScope – metoda
ms.date: 03/30/2017
api_name:
- IALink.GetResolutionScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetResolutionScope
helpviewer_keywords:
- GetResolutionScope method
ms.assetid: 5b48ca60-dacd-44b2-9979-4a5122f00812
topic_type:
- apiref
ms.openlocfilehash: f2b78b35db6306c82e389955c4824875bcf25334
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447222"
---
# <a name="getresolutionscope-method"></a>GetResolutionScope – metoda
Retrieves the scope of a given type.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetResolutionScope(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    mdToken     TargetFile,  
    mdToken*    pScope  
) PURE;  
```  
  
## <a name="parameters"></a>Parametry  
 `AssemblyID`  
 ID of the assembly.  
  
 `FileToken`  
 File that is in need of a reference.  
  
 `TargetFile`  
 Token of file that type is defined in, usually retrieved with [ImportFile Method](importfile-method.md).  
  
 `pScope`  
 Receives the assembly or module reference.  
  
## <a name="return-value"></a>Návratová hodnota  
 Returns S_OK if the method succeeds.  
  
## <a name="requirements"></a>Požadavky  
 Requires alink.h.  
  
## <a name="see-also"></a>Viz také:

- [IALink – rozhraní](ialink-interface.md)
- [IALink2 – rozhraní](ialink2-interface.md)
- [ALink API](index.md)
