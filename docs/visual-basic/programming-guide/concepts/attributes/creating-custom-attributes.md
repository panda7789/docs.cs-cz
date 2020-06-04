---
title: Vytváření vlastních atributů
ms.date: 07/20/2015
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
ms.openlocfilehash: 84b400c2fa1b2d4019eec32092f954d680e64978
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400691"
---
# <a name="creating-custom-attributes-visual-basic"></a>Vytváření vlastních atributů (Visual Basic)

Můžete vytvořit vlastní atributy definováním třídy atributů, třídy, která je odvozena přímo nebo nepřímo z <xref:System.Attribute> , což umožňuje rychlou a jednoduchou identifikaci definic atributů v metadatech. Předpokládejme, že chcete označit typy s názvem programátora, který typ napsal. Je možné definovat vlastní `Author` třídu atributu:

```vb
<System.AttributeUsage(System.AttributeTargets.Class Or
                       System.AttributeTargets.Struct)>
Public Class Author
    Inherits System.Attribute
    Private name As String
    Public version As Double
    Sub New(ByVal authorName As String)
        name = authorName
        version = 1.0
    End Sub
End Class
```

Název třídy je název atributu, `Author` . Je odvozen z `System.Attribute` , takže se jedná o vlastní třídu atributu. Parametry konstruktoru jsou poziční parametry vlastního atributu. V tomto příkladu `name` je poziční parametr. Všechna veřejná pole nebo vlastnosti pro čtení i zápis se nazývají parametry. V tomto případě `version` je jediným pojmenovaným parametrem. Všimněte si, že použití `AttributeUsage` atributu pro nastavení `Author` atributu je platné pouze pro třídu a `Structure` deklarace.

Tento nový atribut můžete použít následujícím způsobem:

```vb
<Author("P. Ackerman", Version:=1.1)>
Class SampleClass
    ' P. Ackerman's code goes here...
End Class
```

`AttributeUsage`má pojmenovaný parametr, `AllowMultiple` pomocí kterého můžete vytvořit vlastní atribut s jedním použitím nebo Multiuse. V následujícím příkladu kódu je vytvořen atribut Multiuse.

```vb
' multiuse attribute
<System.AttributeUsage(System.AttributeTargets.Class Or
                       System.AttributeTargets.Struct,
                       AllowMultiple:=True)>
Public Class Author
    Inherits System.Attribute
```

V následujícím příkladu kódu je pro třídu použito více atributů stejného typu.

```vb
<Author("P. Ackerman", Version:=1.1),
Author("R. Koch", Version:=1.2)>
Class SampleClass
    ' P. Ackerman's code goes here...
    ' R. Koch's code goes here...
End Class
```

> [!NOTE]
> Pokud vaše třída atributu obsahuje vlastnost, musí být tato vlastnost pro čtení i zápis.

## <a name="see-also"></a>Viz také

- <xref:System.Reflection>
- [Příručka k programování v jazyce Visual Basic](../../index.md)
- [Zápis vlastních atributů](../../../../standard/attributes/writing-custom-attributes.md)
- [Reflexe (Visual Basic)](../reflection.md)
- [Atributy (Visual Basic)](../../../language-reference/attributes.md)
- [Přístup k atributům pomocí reflexe (Visual Basic)](accessing-attributes-by-using-reflection.md)
- [AttributeUsage (Visual Basic)](attributeusage.md)
