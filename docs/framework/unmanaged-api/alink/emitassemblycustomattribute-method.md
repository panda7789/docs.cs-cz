---
title: EmitAssemblyCustomAttribute – metoda
ms.date: 03/30/2017
api_name:
- IALink.EmitAssemblyCustomAttribute
- EmitAssemblyCustomAttribute
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssemblyCustomAttribute
helpviewer_keywords:
- EmitAssemblyCustomAttribute method
ms.assetid: b72f5409-79af-4fa7-90a7-7630eec170f1
topic_type:
- apiref
ms.openlocfilehash: ec0a86e3396ad42152bc0a244f74ad13deba16e4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446516"
---
# <a name="emitassemblycustomattribute-method"></a>EmitAssemblyCustomAttribute – metoda
Call to set assembly-level custom attributes.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EmitAssemblyCustomAttribute(  
    mdAssembly   AssemblyID,  
    mdToken      FileToken,  
    mdToken      tkType,  
    void const*  pCustomValue,  
    DWORD        cbCustomValue,  
    BOOL         bSecurity,  
    BOOL         bAllowMulti  
) PURE;  
```  
  
## <a name="parameters"></a>Parametry  
 `AssemblyID`  
 ID of the assembly.  
  
 `FileToken`  
 File that defiles the attribute. Can be NULL if `AssemblyID` does not indicate an unbound netmodule.  
  
 `tkType`  
 Type of the custom attribute.  
  
 `pCustomValue`  
 Custom value data.  
  
 `cbCustomValue`  
 Length of custom value data.  
  
 `bSecurity`  
 TRUE if the custom attribute is related to assembly signing.  
  
 `bAllowMulti`  
 TRUE if multiple attributes are to be emitted.  
  
## <a name="return-value"></a>Návratová hodnota  
 Returns S_OK if the method succeeds.  
  
## <a name="requirements"></a>Požadavky  
 Requires alink.h  
  
## <a name="see-also"></a>Viz také:

- [IALink – rozhraní](ialink-interface.md)
- [IALink2 – rozhraní](ialink2-interface.md)
- [ALink API](index.md)
