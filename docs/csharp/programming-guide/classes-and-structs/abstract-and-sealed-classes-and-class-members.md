---
title: Abstraktní a uzavřené třídy a členové - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- abstract classes [C#]
- sealed classes [C#]
- C# language, abstract classes
- C# language, sealed
ms.assetid: 99aa52f7-b435-43f9-936e-2470af734c4e
ms.openlocfilehash: 3257d365bb9816f4cb41d354f78c88ad4fa0f567
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54523828"
---
# <a name="abstract-and-sealed-classes-and-class-members-c-programming-guide"></a>Abstraktní a uzavřené třídy a jejich členové (Průvodce programováním v C#)
[Abstraktní](../../../csharp/language-reference/keywords/abstract.md) – klíčové slovo umožňuje vytvářet třídy a [třídy](../../../csharp/language-reference/keywords/class.md) členy, kteří jsou nekompletní a které musí být implementované v odvozené třídě.  
  
 [Zapečetěné](../../../csharp/language-reference/keywords/sealed.md) – klíčové slovo umožňuje zabránit dědění třídy nebo členů určité třídy, které byly dříve označeny [virtuální](../../../csharp/language-reference/keywords/virtual.md).  
  
## <a name="abstract-classes-and-class-members"></a>Abstraktní třídy a jejich členové  
 Třídy lze deklarovat jako abstraktní vložením klíčového slova `abstract` před definici třídy. Příklad:  
  
 [!code-csharp[csProgGuideInheritance#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_1.cs)]  
  
 Nelze vytvořit instanci abstraktní třídy. Účelem abstraktní třídy je stanovit společnou definici základní třídy, která může sdílet více odvozených tříd. Knihovna tříd může například definovat abstraktní třídu, která se používá jako parametr pro většinu jeho funkcí a vyžaduje, aby programátoři využívající tuto knihovnu poskytli vlastní implementaci třídy vytvořením odvozené třídy.  
  
 Abstraktní třídy mohou také definovat abstraktní metody. To lze provést přidáním klíčového slova `abstract` před návratovým typem metody. Příklad:  
  
 [!code-csharp[csProgGuideInheritance#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_2.cs)]  
  
 Abstraktní metody nemají implementaci, takže definice metody následuje středníkem místo bloku normální metody. Odvozené třídy abstraktní třídy musí implementovat všechny abstraktní metody. Když abstraktní třída dědí ze základní třídy virtuální metody, abstraktní třída může přepsat virtuální metodu pomocí abstraktní metody. Příklad:  
  
 [!code-csharp[csProgGuideInheritance#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_3.cs)]  
  
 Pokud `virtual` metoda deklarována `abstract`, je stále virtuální pro jakoukoli třídu, která dědí z abstraktní třídy. Třída dědící abstraktní metodu nemůže získat přístup k původní implementaci metody – v předchozím příkladu `DoWork` u třídy F nemůže volat `DoWork` u třídy D. Tímto způsobem abstraktní třída může vynutit odvozené třídy pro poskytování implementací nových metod pro virtuální metody.  
  
## <a name="sealed-classes-and-class-members"></a>Zapečetěné třídy a členy třídy  
 Třídy lze deklarovat jako [zapečetěné](../../../csharp/language-reference/keywords/sealed.md) vložením klíčového slova `sealed` před definici třídy. Příklad:  
  
 [!code-csharp[csProgGuideInheritance#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_4.cs)]  
  
 Zapečetěnou třídu nelze použít jako základní třídu. Z tohoto důvodu to nemůže být také abstraktní třídu. Zapečetěné třídy zabraňují odvození. Protože nemohou být nikdy použity jako základní třída, některé optimalizace za běhu můžete provést volání zapouzdřených členů mírně rychleji.  
  
 Metoda, indexer, vlastnost nebo událost odvozené třídy, které přepisují virtuálního člena základní třídy lze deklarovat tento člen je zapečetěn. To Neguje virtuální aspekt člena pro jakékoli další odvozené třídy. To lze provést vložením `sealed` – klíčové slovo před [přepsat](../../../csharp/language-reference/keywords/override.md) – klíčové slovo v deklaraci třídy člena. Příklad:  
  
 [!code-csharp[csProgGuideInheritance#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_5.cs)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Dědičnost](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
- [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)
- [Pole](../../../csharp/programming-guide/classes-and-structs/fields.md)
- [Postupy: Definování abstraktních a vlastností](../../../csharp/programming-guide/classes-and-structs/how-to-define-abstract-properties.md)
