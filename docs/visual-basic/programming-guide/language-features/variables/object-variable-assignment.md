---
title: Přiřazení proměnné objektu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], object variable assignment
- object variables [Visual Basic], initializing
- variables [Visual Basic], initializing
- objects [Visual Basic], current instance
- object variables [Visual Basic], assigning
- variables [Visual Basic], object variables
- current instance [Visual Basic], defined
- variables [Visual Basic], assigning
- assignment statements [Visual Basic], object variable assignment
- Me keyword [Visual Basic], as object variable
ms.assetid: 3706811d-fd40-44fe-8727-d692e8e55d6d
ms.openlocfilehash: f20a03c4d9a0e33203629ae066686f4c9f25c105
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="object-variable-assignment-visual-basic"></a>Přiřazení proměnné objektu (Visual Basic)
Příkaz normální přiřazení můžete použít k přiřazení objektu k proměnné objektu. Můžete přiřadit výraz objekt nebo [nic](../../../../visual-basic/language-reference/nothing.md) – klíčové slovo, jako následující příklad znázorňuje.  
  
```  
Dim thisObject As Object  
' The following statement assigns an object reference.  
thisObject = Form1  
' The following statement discontinues association with any object.  
thisObject = Nothing  
```  
  
 `Nothing` znamená, že žádný objekt aktuálně přiřazená k proměnné.  
  
## <a name="initialization"></a>Inicializace  
 Pokud váš kód zahájí spuštění, proměnné se inicializují k objektu `Nothing`. Ty, jejichž deklarace zahrnují inicializace jsou opětovně inicializovány na hodnoty, které určíte při provedení deklarační příkazy.  
  
 Inicializace můžete zahrnout do vaší deklarace pomocí [nový](../../../../visual-basic/language-reference/operators/new-operator.md) – klíčové slovo. Následující příkazy deklarace deklarace objektové proměnné `testUri` a `ver` a k nim přiřadíte konkrétní objekty. Každá používá jednu z přetížené konstruktory příslušné třídy k inicializaci objektu.  
  
```  
Dim testUri As New System.Uri("http://www.microsoft.com")  
Dim ver As New System.Version(6, 1, 0)  
```  
  
## <a name="disassociation"></a>Zrušení přidružení  
 Nastavení proměnné objektu `Nothing` ze přidružení konkrétního objektu proměnné. To brání omylem Změna objektu změnou proměnnou. Také umožňuje otestovat, zda proměnná objektu odkazuje na platný objekt, jak ukazuje následující příklad.  
  
```  
If otherObject IsNot Nothing Then  
    ' otherObject refers to a valid object, so your code can use it.  
End If  
```  
  
 Pokud objekt, který vaše proměnná odkazuje v jiné aplikaci, tento test nelze určit, zda má aplikace ukončeno, nebo jenom zrušena objekt.  
  
 Proměnné objektu s hodnotou `Nothing` se označuje taky jako *odkaz s hodnotou null*.  
  
## <a name="current-instance"></a>Aktuální Instance  
 *Aktuální instance* objektu je ten, ve kterém je aktuálně provádění kódu. Vzhledem k tomu, že veškerý kód provede uvnitř procedury, aktuální instance je ten, ve kterém byl vyvolán postupu.  
  
 `Me` – Klíčové slovo funguje jako proměnná objektu odkazuje na aktuální instanci. Pokud není procedury [sdílené](../../../../visual-basic/language-reference/modifiers/shared.md), můžete použít `Me` – klíčové slovo k získání ukazatele na aktuální instanci. Sdílené procedury nelze přidružit k určité instance třídy.  
  
 Pomocí `Me` je obzvláště užitečné pro předávání aktuální instance proceduře v jiném modulu. Předpokládejme například, máte několik dokumentů XML a chcete přidat některé standardní text pro všechny z nich. V následujícím příkladu definuje postup zajímá.  
  
```  
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)  
    XmlDoc.CreateTextNode("This text goes into every XML document.")  
End Sub  
```  
  
 Každý objekt dokumentu XML může pak voláním procedury a předat jako argument jeho aktuální instance. Následující příklad ukazuje to.  
  
```  
addStandardText(Me)  
```  
  
## <a name="see-also"></a>Viz také  
 [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Deklarace objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [Hodnoty objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [Postupy: deklarace objektové proměnné a přiřazení objektu k v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)  
 [Postupy: Nastavení objektové proměnné tak, aby neodkazovala na žádnou instanci](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md)  
 [Me, My, MyBase a MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
