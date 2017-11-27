---
title: "Postupy: Vytvoření nové proměnné (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a6806dcbe9e00cbae77181b79d74ddb9a1e1493f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-new-variable-visual-basic"></a>Postupy: Vytvoření nové proměnné (Visual Basic)
Vytvořte proměnnou s [Dim – příkaz](../../../../visual-basic/language-reference/statements/dim-statement.md).  
  
### <a name="to-create-a-new-variable"></a>Chcete-li vytvořit nové proměnné  
  
1.  Deklarace proměnné v `Dim` příkaz.  
  
    ```  
    Dim newCustomer  
    ```  
  
2.  Zahrnout specifikace charakteristik proměnné, jako například [privátní](../../../../visual-basic/language-reference/modifiers/private.md), [statické](../../../../visual-basic/language-reference/modifiers/static.md), [stínů](../../../../visual-basic/language-reference/modifiers/shadows.md), nebo [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md). Další informace najdete v tématu [deklarované charakteristiky elementu](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).  
  
    ```  
    Public Static newCustomer  
    ```  
  
     Není nutné `Dim` – klíčové slovo, pokud používáte žádná jiná klíčová slova v deklaraci.  
  
3.  Postupujte podle specifikace s název proměnné, která musí odpovídat [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] pravidla a pravidla týkající se. Další informace najdete v tématu [deklarované názvy elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
    ```  
    Public Static newCustomer  
    ```  
  
4.  Postupujte podle názvu s [jako](../../../../visual-basic/language-reference/statements/as-clause.md) klauzule zadat datový typ proměnné.  
  
    ```  
    Public Static newCustomer As Customer  
    ```  
  
     Pokud nezadáte datový typ, použije výchozí hodnota: `Object`.  
  
5.  Postupujte podle `As` klauzule symbol rovná se (`=`) a postupujte podle pokynů rovná s počáteční hodnota proměnné.  
  
     [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]Zadaná hodnota přiřadí proměnné pokaždé, když ji spustí `Dim` příkaz. Pokud nezadáte hodnotu počáteční [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] po jej nejprve zadá kód, který obsahuje přiřadí výchozí počáteční hodnota pro datový typ proměnné `Dim` příkaz.  
  
     Pokud je proměnná typu odkazu, můžete vytvořit instanci její třídy zahrnutím [operátor New](../../../../visual-basic/language-reference/operators/new-operator.md) – klíčové slovo v `As` klauzule. Pokud nepoužijete `New`, je počáteční hodnota proměnné [nic](../../../../visual-basic/language-reference/nothing.md).  
  
    ```  
    Public Static newCustomer As New Customer  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Proměnné](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Deklarované názvy elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Deklarované charakteristiky elementu](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Příkazy](../../../../visual-basic/language-reference/statements/index.md)  
 [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Option Infer – příkaz](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
