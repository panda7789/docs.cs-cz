---
title: Atribut 'Extension' lze použít pouze v deklaracích 'Module', 'Sub' nebo 'Function'.
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: 9b8f49c498699a8f7d1c4b329e82258501aa0c47
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363095"
---
# <a name="extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations"></a>Atribut 'Extension' lze použít pouze v deklaracích 'Module', 'Sub' nebo 'Function'.

Jediným způsobem, jak rozšířit datový typ v Visual Basic, je definovat metodu rozšíření uvnitř standardního modulu. Metoda rozšíření může být `Sub` procedura nebo `Function` procedura. Všechny metody rozšíření musí být označeny atributem rozšíření, `<Extension()>` z <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> oboru názvů. Volitelně může být modul, který obsahuje metodu rozšíření, označen stejným způsobem. Žádné jiné použití atributu Extension není platné.

**ID chyby:** BC36550

## <a name="to-correct-this-error"></a>Oprava této chyby

- Odeberte atribut Extension.

- Přenavrhněte své rozšíření jako metodu definovanou v ohraničujícím modulu.

## <a name="example"></a>Příklad

Následující příklad definuje `Print` metodu pro `String` datový typ.

```vb
Imports StringUtility
Imports System.Runtime.CompilerServices
Namespace StringUtility
    <Extension()>
    Module StringExtensions
        <Extension()>
        Public Sub Print (ByVal str As String)
            Console.WriteLine(str)
        End Sub
    End Module
End Namespace
```

## <a name="see-also"></a>Viz také

- [Přehled atributů](../../programming-guide/concepts/attributes/index.md)
- [Metody rozšíření](../../programming-guide/language-features/procedures/extension-methods.md)
- [Module – příkaz](../statements/module-statement.md)
