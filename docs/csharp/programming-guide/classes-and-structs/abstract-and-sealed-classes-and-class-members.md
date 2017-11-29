---
title: "Abstraktní a uzavřené třídy a jejich členové (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- abstract classes [C#]
- sealed classes [C#]
- C# language, abstract classes
- C# language, sealed
ms.assetid: 99aa52f7-b435-43f9-936e-2470af734c4e
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dac7570c018bd577faac4540e4d800cc11143578
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="abstract-and-sealed-classes-and-class-members-c-programming-guide"></a>Abstraktní a uzavřené třídy a jejich členové (Průvodce programováním v C#)
[Abstraktní](../../../csharp/language-reference/keywords/abstract.md) – klíčové slovo lze vytvořit třídy a [třída](../../../csharp/language-reference/keywords/class.md) členy, kteří jsou neúplné a musí být implementován v odvozené třídě.  
  
 [Zapečetěné](../../../csharp/language-reference/keywords/sealed.md) – klíčové slovo umožňuje zabránit dědičnosti třídy nebo členy určité třídy, které byly dříve označeny [virtuální](../../../csharp/language-reference/keywords/virtual.md).  
  
## <a name="abstract-classes-and-class-members"></a>Abstraktní třídy a jejich členové  
 Třídy lze deklarovat jako abstraktní umístěním klíčové slovo `abstract` před definici třídy. Příklad:  
  
 [!code-csharp[csProgGuideInheritance#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_1.cs)]  
  
 Nelze vytvořit instanci abstraktní třídy. Účelem abstraktní třída je poskytnout společná definice, můžete sdílet více odvozené třídy základní třídy. Knihovny tříd může například definovat abstraktní třída, která se používá jako parametr pro řadu její funkce a vyžadují programátory použití této knihovny a zadejte vlastní implementaci třídy vytvořením odvozené třídy.  
  
 Abstraktní třídy může také definovat abstraktní metody. To je možné udělat přidáním klíčové slovo `abstract` před návratový typ metody. Příklad:  
  
 [!code-csharp[csProgGuideInheritance#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_2.cs)]  
  
 Abstraktní metody nemají implementaci, tak definici metody následuje středníkem místo normální metoda blok. Abstraktní třídy odvozené třídy musí implementovat všechny abstraktní metody. Když abstraktní třídy dědí virtuální metoda ze základní třídy, abstraktní třídu můžete přepsat virtuální metodu s abstraktní metodu. Příklad:  
  
 [!code-csharp[csProgGuideInheritance#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_3.cs)]  
  
 Pokud `virtual` je deklarovaná metoda `abstract`, je stále virtuální všechny třídy, která dědí z abstraktní třídy. Dědění metodu pro abstraktní třídu nelze získat přístup k původní implementace metody – v předchozím příkladu `DoWork` na třídu, nelze volat F `DoWork` na D. – Třída Tímto způsobem můžete vynutit abstraktní třídy odvozené třídy zajistit nové implementace metody pro virtuální metody.  
  
## <a name="sealed-classes-and-class-members"></a>Zapečetěné třídy a jejich členové  
 Třídy lze deklarovat jako [zapečetěné](../../../csharp/language-reference/keywords/sealed.md) umístěním klíčové slovo `sealed` před definici třídy. Příklad:  
  
 [!code-csharp[csProgGuideInheritance#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_4.cs)]  
  
 Zapečetěné třídy nelze použít jako základní třída. Z tohoto důvodu je také nemůže být abstraktní třídu. Zapečetěné třídy zabránit odvození. Protože nikdy je možné použít jako základní třída, můžete provést některé optimalizace běhu volání členy zapečetěné třídy mírně rychlejší.  
  
 Metoda, indexer, vlastnost nebo událost v odvozené třídě, která přepisují člena virtuální základní třídy lze deklarovat jako zapečetěné tohoto člena. To Neguje virtuální aspekt člena pro všechny další odvozené třídy. To lze provést vložení `sealed` – klíčové slovo před [přepsat](../../../csharp/language-reference/keywords/override.md) – klíčové slovo v deklarace člena třídy. Příklad:  
  
 [!code-csharp[csProgGuideInheritance#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_5.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Dědičnost](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
 [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [Pole](../../../csharp/programming-guide/classes-and-structs/fields.md)  
 [Postupy: definování abstraktních a vlastností](../../../csharp/programming-guide/classes-and-structs/how-to-define-abstract-properties.md)
