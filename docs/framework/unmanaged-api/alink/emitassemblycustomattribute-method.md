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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 77d54f6c8f67dda5132518d1fbd579a91ce82071
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777438"
---
# <a name="emitassemblycustomattribute-method"></a>EmitAssemblyCustomAttribute – metoda
Volání pro nastavení vlastních atributů na úrovni sestavení.  
  
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
 ID sestavení  
  
 `FileToken`  
 Soubor, který tento atribut odfile. Může mít hodnotu null `AssemblyID` , pokud neoznačuje nevázaný netmodule.  
  
 `tkType`  
 Typ vlastního atributu  
  
 `pCustomValue`  
 Vlastní data hodnoty.  
  
 `cbCustomValue`  
 Délka dat vlastních hodnot  
  
 `bSecurity`  
 TRUE, pokud vlastní atribut souvisí s podepisováním sestavení.  
  
 `bAllowMulti`  
 TRUE, pokud má být vygenerováno více atributů.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrací S_OK, pokud je metoda úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje ALink. h  
  
## <a name="see-also"></a>Viz také:

- [IALink – rozhraní](ialink-interface.md)
- [IALink2 – rozhraní](ialink2-interface.md)
- [Rozhraní API ALink](index.md)
