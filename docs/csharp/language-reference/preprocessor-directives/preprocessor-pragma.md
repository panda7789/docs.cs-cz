---
title: '#pragma - C# Reference'
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 3bd62364aeae0f21715711324655ef7d00d88afc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712452"
---
# <a name="pragma-c-reference"></a>#pragma (referenční dokumentace jazyka C#)
`#pragma`poskytuje kompilátoru zvláštní pokyny pro kompilaci souboru, ve kterém se objeví. Pokyny musí být podporovány kompilátorem. Jinými slovy nelze `#pragma` použít k vytvoření vlastních pokynů pro předběžné zpracování. Kompilátor Microsoft C# podporuje `#pragma` následující dva pokyny:  
  
 [#pragma varování](./preprocessor-pragma-warning.md)  
  
 [#pragma checksum](./preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
## <a name="parameters"></a>Parametry  
 `pragma-name`  
 Jméno uznávaného pragma.  
  
 `pragma-arguments`  
 Pragma-specifické argumenty.  
  
## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [Direktivy preprocesoru jazyka C#](./index.md)
- [#pragma varování](./preprocessor-pragma-warning.md)
- [#pragma checksum](./preprocessor-pragma-checksum.md)
