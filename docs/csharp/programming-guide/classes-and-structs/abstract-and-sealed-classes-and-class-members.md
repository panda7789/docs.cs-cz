---
title: Abstraktní a zapečetěné třídy a členové třídy - C# Programovací průvodce
ms.date: 07/20/2015
helpviewer_keywords:
- abstract classes [C#]
- sealed classes [C#]
- C# language, abstract classes
- C# language, sealed
ms.assetid: 99aa52f7-b435-43f9-936e-2470af734c4e
ms.openlocfilehash: 07738031f1dec05424f7c3756f49a8f1f9a2c44b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714998"
---
# <a name="abstract-and-sealed-classes-and-class-members-c-programming-guide"></a>Abstraktní a uzavřené třídy a jejich členové (Průvodce programováním v C#)
Klíčové slovo [abstract](../../language-reference/keywords/abstract.md) umožňuje vytvářet třídy a členy [třídy,](../../language-reference/keywords/class.md) které jsou neúplné a musí být implementovány v odvozené třídě.  
  
 Klíčové slovo [sealed](../../language-reference/keywords/sealed.md) umožňuje zabránit dědičnosti třídy nebo určitých členů třídy, které byly dříve označeny [jako virtuální](../../language-reference/keywords/virtual.md).  
  
## <a name="abstract-classes-and-class-members"></a>Abstraktní třídy a členové třídy  
 Třídy mohou být deklarovány jako abstraktní umístěním klíčového slova `abstract` před definici třídy. Například:  
  
 [!code-csharp[csProgGuideInheritance#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#13)]  
  
 Abstraktní třídu nelze vytvořit instanci. Účelem abstraktní třídy je poskytnout společnou definici základní třídy, kterou může sdílet více odvozených tříd. Knihovna tříd může například definovat abstraktní třídu, která se používá jako parametr pro mnoho jeho funkcí a vyžadovat, aby programátoři používající tuto knihovnu poskytovali vlastní implementaci třídy vytvořením odvozené třídy.  
  
 Abstraktní třídy mohou také definovat abstraktní metody. Toho lze dosáhnout přidáním `abstract` klíčového slova před návratový typ metody. Například:  
  
 [!code-csharp[csProgGuideInheritance#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#14)]  
  
 Abstraktní metody nemají žádnou implementaci, takže za definicí metody následuje středník namísto bloku normální metody. Odvozené třídy abstraktní třídy musí implementovat všechny abstraktní metody. Když abstraktní třída zdědí virtuální metodu ze základní třídy, abstraktní třída může přepsat virtuální metodu abstraktní metodou. Například:  
  
 [!code-csharp[csProgGuideInheritance#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#15)]  
  
 Pokud `virtual` je deklarována `abstract`metoda , je stále virtuální pro všechny třídy dědí z abstraktní třídy. Třída dědění abstraktní metody nemůže získat přístup k původní implementaci `DoWork` metody – `DoWork` v předchozím příkladu ve třídě F nelze volat třídu D. Tímto způsobem abstraktní třídy můžete vynutit odvozené třídy poskytnout nové implementace metody pro virtuální metody.  
  
## <a name="sealed-classes-and-class-members"></a>Zapečetěné třídy a členové třídy  
 Třídy mohou být deklarovány jako [zapečetěné](../../language-reference/keywords/sealed.md) umístěním klíčového slova `sealed` před definici třídy. Například:  
  
 [!code-csharp[csProgGuideInheritance#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#16)]  
  
 Zapečetěnou třídu nelze použít jako základní třídu. Z tohoto důvodu nemůže být také abstraktní třídy. Uzavřené třídy zabraňují odvození. Vzhledem k tomu, že je nelze nikdy použít jako základní třídu, některé optimalizace běhu mohou volat členy zapečetěné třídy o něco rychleji.  
  
 Metoda, indexer, vlastnost nebo událost na odvozené třídy, která je přepsání virtuální člen základní třídy můžete deklarovat, že člen jako zapečetěné. To neguje virtuální aspekt člena pro všechny další odvozené třídy. Toho lze dosáhnout umístěním klíčového `sealed` slova před klíčové slovo [přepsání](../../language-reference/keywords/override.md) v deklaraci člena třídy. Například:  
  
 [!code-csharp[csProgGuideInheritance#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#17)]  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Třídy a struky](./index.md)
- [Dědičnost](./inheritance.md)
- [Metody](./methods.md)
- [Pole](./fields.md)
- [Jak definovat abstraktní vlastnosti](./how-to-define-abstract-properties.md)
