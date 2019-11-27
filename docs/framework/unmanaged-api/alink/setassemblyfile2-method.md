---
title: SetAssemblyFile2 – metoda
ms.date: 03/30/2017
api_name:
- IALink2.SetAssemblyFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile2
helpviewer_keywords:
- SetAssemblyFile2 method
ms.assetid: eedb9125-1ef1-4000-abfc-7de86e5a1f17
topic_type:
- apiref
ms.openlocfilehash: 4f710ef9741869a2b4fd8473ed3ecf379cfcc56d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445585"
---
# <a name="setassemblyfile2-method"></a>SetAssemblyFile2 – metoda
Nastaví název a možnosti pro nové sestavení. Nevolejte tuto metodu, když vytváříte nevázané moduly.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a>Parametry  
 `pszFilename`  
 Název souboru manifestu  
  
 `pEmitter`  
 Rozhraní [IMetaDataEmit2 rozhraní](../metadata/imetadataemit2-interface.md) pro tento soubor.  
  
 `afFlags`  
 Možnosti reprezentované [výčtem AssemblyFlags –](../metadata/assemblyflags-enumeration.md)  
  
 `pAssemblyID`  
 Získá jedinečné ID sestavení, které je sestaveno.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK, pokud je metoda úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje ALink. h.  
  
## <a name="see-also"></a>Viz také:

- [IALink2 – rozhraní](ialink2-interface.md)
- [IALink – rozhraní](ialink-interface.md)
- [Rozhraní API ALink](index.md)
