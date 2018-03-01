---
title: Key (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.AnonymousKey
helpviewer_keywords:
- anonymous types [Visual Basic], key
- Key [Visual Basic]
- Key keyword [Visual Basic]
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 20dbe4e67fb3e415ba0202555ace7fd5afed68d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="key-visual-basic"></a>Key (Visual Basic)
`Key` – Klíčové slovo můžete určit chování pro vlastnosti anonymní typy. Pouze vlastnosti, které označíte jako vlastnosti klíče účastnit testy rovnosti mezi anonymní typ instance nebo výpočtu hodnoty hash. Hodnoty vlastnosti klíče nelze změnit.  
  
 Vlastnost anonymní typ určíte jako vlastnosti klíče, tím, že umístíte klíčové slovo `Key` před jeho deklaraci v seznamu inicializace. V následujícím příkladu `Airline` a `FlightNo` jsou klíčové vlastnosti, ale `Gate` není.  
  
 [!code-vb[VbVbalrAnonymousTypes#26](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_1.vb)]  
  
 Když je vytvořen nový anonymní typ, dědí přímo z <xref:System.Object>. Kompilátor přepsání tři zděděné členy: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, a <xref:System.Object.ToString%2A>. Kód přepsání, která je vytvořena pro <xref:System.Object.Equals%2A> a <xref:System.Object.GetHashCode%2A> je založena na klíčové vlastnosti. Pokud nejsou žádné klíčové vlastnosti v typu, <xref:System.Object.GetHashCode%2A> a <xref:System.Object.Equals%2A> nepřepíše.  
  
## <a name="equality"></a>Rovnost  
 Dvě instance anonymního typu jsou stejné, pokud jsou instance stejného typu a hodnoty jejich klíčové vlastnosti jsou stejné. V následujících příkladech `flight2` rovná `flight1` z předchozího příkladu protože jsou instance anonymní stejného typu a mají odpovídající hodnoty pro jejich vlastnosti klíče. Ale `flight3` se nerovná `flight1` protože má jinou hodnotu pro klíčovou vlastnost `FlightNo`. Instance `flight4` není stejného typu jako `flight1` vzhledem k tomu, že určit různé vlastnosti jako vlastnosti klíče.  
  
 [!code-vb[VbVbalrAnonymousTypes#27](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_2.vb)]  
  
 Pokud jsou dvě instance deklarovat s pouze neklíčovými vlastnostmi, stejná název, typ, pořadí a hodnoty, nejsou dvě instance stejné. Instance bez vlastnosti klíče je rovna pouze na sebe sama.  
  
 Další informace o podmínkách, pod kterým jsou dvě instance anonymní typ instance stejného typu anonymní najdete v tématu [anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
## <a name="hash-code-calculation"></a>Výpočet hodnoty hash kódu  
 Jako <xref:System.Object.Equals%2A>, funkce algoritmu hash, která je definována v <xref:System.Object.GetHashCode%2A> pro anonymní typ je založena na klíčové vlastnosti typu. Následující příklady ukazují interakce mezi klíčové vlastnosti a hodnotu hash hodnoty kódu.  
  
 Instance anonymního typu, které mají stejné hodnoty pro všechny vlastnosti klíče mají stejnou hodnotu hash kód, i když neklíčovými vlastnostmi nemají odpovídající hodnoty. Následující příkaz vrátí `True`.  
  
 [!code-vb[VbVbalrAnonymousTypes#37](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_3.vb)]  
  
 Anonymní typ instancí, které mají různé hodnoty pro jeden nebo více klíčové vlastnosti mít hodnoty různých hash. Následující příkaz vrátí `False`.  
  
 [!code-vb[VbVbalrAnonymousTypes#38](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_4.vb)]  
  
 Instance anonymní typy, které určit různé vlastnosti jako vlastnosti klíče nejsou instance stejného typu. Hodnoty hash různých mají i v případě, že názvy a hodnoty všech vlastností jsou stejné. Následující příkaz vrátí `False`.  
  
 [!code-vb[VbVbalrAnonymousTypes#39](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_5.vb)]  
  
## <a name="read-only-values"></a>Jen pro čtení hodnoty  
 Hodnoty vlastnosti klíče nelze změnit. Například v `flight1` v předchozích příkladech `Airline` a `FlightNo` pole jsou jen pro čtení, ale `Gate` lze změnit.  
  
 [!code-vb[VbVbalrAnonymousTypes#28](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_6.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Definice autonomního typu](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)  
 [Postupy: odvození názvů a typů v deklaracích anonymního typu vlastností](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 [Anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
