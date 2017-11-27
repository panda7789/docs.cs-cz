---
title: "Vytváření vlastních atributů (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7a24553ae4cc2186e805d76ddb37f38c0322aeac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="creating-custom-attributes-visual-basic"></a>Vytváření vlastních atributů (Visual Basic)
Můžete vytvořit vlastní atributy definováním třídy atributu, třídu odvozenou z přímo nebo nepřímo <xref:System.Attribute>, které díky Identifikace definice atributu v metadatech rychlé a snadné. Předpokládejme, že chcete typy značky s názvem programátory, kteří napsali typu. Můžete třeba definovat vlastní `Author` třídy atributů:  
  
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
  
 Název třídy je název atributu, `Author`. Je odvozený od `System.Attribute`, takže je třídu vlastního atributu. V konstruktoru parametry jsou vlastní atribut poziční parametry. V tomto příkladu `name` je parametr poziční. Všechny vlastnosti nebo veřejná pole pro čtení a zápis jsou pojmenované parametry. V takovém případě `version` je jediným s názvem parametru. Všimněte si použití `AttributeUsage` atribut, aby `Author` atribut platná pouze pro třídy a `Structure` deklarace.  
  
 Tento nový atribut můžete použít takto:  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 `AttributeUsage`má parametr s názvem `AllowMultiple`, pomocí kterého můžete nastavit vlastní atribut jedno použití nebo multiuse. V následujícím příkladu kódu je vytvořen multiuse atribut.  
  
```vb  
' multiuse attribute  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct,   
                       AllowMultiple:=True)>   
Public Class Author  
    Inherits System.Attribute  
```  
  
 V následujícím příkladu kódu je na třídu použít víc atributů stejného typu.  
  
```vb  
<Author("P. Ackerman", Version:=1.1),   
Author("R. Koch", Version:=1.2)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
    ' R. Koch's code goes here...  
End Class  
```  
  
> [!NOTE]
>  Pokud vaše třídy atributů obsahuje vlastnost, vlastnosti musí být pro čtení a zápis.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Reflection>  
 [Průvodce programováním v jazyce Visual Basic](../../../../visual-basic/programming-guide/index.md)  
 [Zápis vlastních atributů](../../../../standard/attributes/writing-custom-attributes.md)  
 [Reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [Atributy (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)  
 [Přístup k atributům pomocí reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
 [AttributeUsage (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
