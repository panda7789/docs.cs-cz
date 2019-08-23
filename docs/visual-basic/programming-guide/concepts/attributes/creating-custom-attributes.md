---
title: Vytváření vlastních atributů (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
ms.openlocfilehash: e4b55f92466fde47011937d08c946c9c75ca07b7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966334"
---
# <a name="creating-custom-attributes-visual-basic"></a>Vytváření vlastních atributů (Visual Basic)
Můžete vytvořit vlastní atributy definováním třídy atributů, třídy, která je odvozena přímo nebo nepřímo z <xref:System.Attribute>, což umožňuje rychlou a jednoduchou identifikaci definic atributů v metadatech. Předpokládejme, že chcete označit typy s názvem programátora, který typ napsal. Je možné definovat vlastní `Author` třídu atributu:  
  
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
  
 Název třídy je název atributu, `Author`. Je odvozen z `System.Attribute`, takže se jedná o vlastní třídu atributu. Parametry konstruktoru jsou poziční parametry vlastního atributu. V tomto příkladu `name` je poziční parametr. Všechna veřejná pole nebo vlastnosti pro čtení i zápis se nazývají parametry. V tomto případě `version` je jediným pojmenovaným parametrem. Všimněte si, že použití `AttributeUsage` atributu pro nastavení atributu `Author` je platné pouze pro třídu a `Structure` deklarace.  
  
 Tento nový atribut můžete použít následujícím způsobem:  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 `AttributeUsage`má pojmenovaný parametr, `AllowMultiple`pomocí kterého můžete vytvořit vlastní atribut s jedním použitím nebo Multiuse. V následujícím příkladu kódu je vytvořen atribut Multiuse.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Reflection>
- [Průvodce programováním Visual Basic](../../../../visual-basic/programming-guide/index.md)
- [Zápis vlastních atributů](../../../../standard/attributes/writing-custom-attributes.md)
- [Reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [Atributy (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)
- [Přístup k atributům pomocí reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
- [AttributeUsage (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
