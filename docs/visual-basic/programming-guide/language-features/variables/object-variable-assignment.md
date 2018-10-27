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
ms.openlocfilehash: 571b09a0783ec0dfd09970b000faec39dca682b3
ms.sourcegitcommit: 4621e67f69e7a9503ea93313ff60d69683207889
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2018
ms.locfileid: "49995360"
---
# <a name="object-variable-assignment-visual-basic"></a>Přiřazení proměnné objektu (Visual Basic)
Normální přiřazovací příkaz použijete k přiřazení objektu k proměnné objektu. Můžete přiřadit výrazu objektu nebo [nic](../../../../visual-basic/language-reference/nothing.md) – klíčové slovo, jako následující příklad ukazuje.  
  
```  
Dim thisObject As Object  
' The following statement assigns an object reference.  
thisObject = Form1  
' The following statement discontinues association with any object.  
thisObject = Nothing  
```  
  
 `Nothing` znamená, že neexistuje žádný objekt aktuálně přiřazená k proměnné.  
  
## <a name="initialization"></a>Inicializace  
 Pokud váš kód zahájí spuštění, proměnné jsou inicializovány na hodnotu objektu `Nothing`. Ty, jejichž deklarace zahrnují inicializace jsou opětovně inicializovány na hodnoty, které určíte při spuštění příkazů deklarace.  
  
 Můžete zahrnout inicializace vaší deklarace pomocí [nový](../../../../visual-basic/language-reference/operators/new-operator.md) – klíčové slovo. Následující příkazy deklarace deklarovat objekt proměnné `testUri` a `ver` a přiřadit jim konkrétní objekty. Každá používá jednu z přetížených konstruktorů z příslušné třídy k inicializaci objektu.  
  
```  
Dim testUri As New System.Uri("https://www.microsoft.com")  
Dim ver As New System.Version(6, 1, 0)  
```  
  
## <a name="disassociation"></a>Zrušení přidružení  
 Nastavení proměnné objektu na `Nothing` navrátí přidružení konkrétního objektu proměnné. Předchází se tak nechtěných úpravách objektu tak, že změníte proměnné. Také umožňuje otestovat, zda proměnná objektu odkazuje na platný objekt, jak ukazuje následující příklad.  
  
```  
If otherObject IsNot Nothing Then  
    ' otherObject refers to a valid object, so your code can use it.  
End If  
```  
  
 Pokud je vaše proměnná odkazuje na objekt v jiné aplikaci, tento test nelze určit, jestli tato aplikace má ukončily nebo které právě zneplatněny objektu.  
  
 Proměnné objektu s hodnotou `Nothing` se také nazývá *nulový odkaz*.  
  
## <a name="current-instance"></a>Aktuální Instance  
 *Aktuální instance* objektu, je ten, ve kterém právě spouští kód. Vzhledem k tomu, že veškerý kód provede uvnitř procedury, je ten, ve kterém byla vyvolána procedura aktuální instance.  
  
 `Me` – Klíčové slovo funguje jako proměnná objektu odkazuje na aktuální instanci. Pokud procedura není [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), můžete použít `Me` – klíčové slovo k získání ukazatele na aktuální instanci. Sdílené postupy nemůže být přidružena k určité instanci třídy.  
  
 Pomocí `Me` je obzvláště užitečné pro předávání aktuální instanci v jiném modulu proceduře. Předpokládejme například, máte několik dokumentů XML a chcete přidat některé standardní text pro všechny z nich. Následující příklad definuje proceduru provedete to tak.  
  
```  
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)  
    XmlDoc.CreateTextNode("This text goes into every XML document.")  
End Sub  
```  
  
 Každý objekt dokumentu XML může potom zavolejte proceduru a předejte svoji aktuální instanci jako argument. Následující příklad ukazuje to.  
  
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
