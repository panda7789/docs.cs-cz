---
title: Abstraktní a zapečetěné třídy a členy třídy C# – Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- abstract classes [C#]
- sealed classes [C#]
- C# language, abstract classes
- C# language, sealed
ms.assetid: 99aa52f7-b435-43f9-936e-2470af734c4e
ms.openlocfilehash: 97b367b5c3d09087541ee206a2899a7aefd95305
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971353"
---
# <a name="abstract-and-sealed-classes-and-class-members-c-programming-guide"></a>Abstraktní a uzavřené třídy a jejich členové (Průvodce programováním v C#)
Klíčové slovo [abstract](../../language-reference/keywords/abstract.md) umožňuje vytvářet třídy a členy [třídy](../../language-reference/keywords/class.md) , které jsou neúplné a které musí být implementovány v odvozené třídě.  
  
 Klíčové slovo [sealed](../../language-reference/keywords/sealed.md) umožňuje zabránit dědění třídy nebo určitých členů třídy, které byly dříve označeny jako [virtuální](../../language-reference/keywords/virtual.md).  
  
## <a name="abstract-classes-and-class-members"></a>Abstraktní třídy a členy třídy  
 Třídy lze deklarovat jako abstraktní vložením klíčového slova `abstract` před definici třídy. Příklad:  
  
 [!code-csharp[csProgGuideInheritance#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#13)]  
  
 Nelze vytvořit instanci abstraktní třídy. Účelem abstraktní třídy je poskytnutí společné definice základní třídy, kterou může sdílet více odvozených tříd. Knihovna tříd může například definovat abstraktní třídu, která se používá jako parametr pro mnoho jeho funkcí, a vyžadovat programátory, kteří používají tuto knihovnu k poskytnutí vlastní implementace třídy vytvořením odvozené třídy.  
  
 Abstraktní třídy mohou také definovat abstraktní metody. To je dosaženo přidáním klíčového slova `abstract` před návratový typ metody. Příklad:  
  
 [!code-csharp[csProgGuideInheritance#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#14)]  
  
 Abstraktní metody nemají žádnou implementaci, proto je jako definice metody následován středníkem namísto bloku normální metody. Odvozené třídy abstraktní třídy musí implementovat všechny abstraktní metody. Pokud abstraktní třída dědí virtuální metodu ze základní třídy, abstraktní třída může přepsat virtuální metodu abstraktní metodou. Příklad:  
  
 [!code-csharp[csProgGuideInheritance#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#15)]  
  
 Je-li metoda `virtual` deklarována `abstract`, je stále virtuální pro jakoukoliv třídu, která dědí z abstraktní třídy. Třída, která dědí abstraktní metodu, nemůže získat přístup k původní implementaci metody – v předchozím příkladu `DoWork` ve třídě F nemůže volat `DoWork` na třídu D. Tímto způsobem abstraktní třída může vynutit odvozené třídy, aby poskytovala nové implementace metod pro virtuální metody.  
  
## <a name="sealed-classes-and-class-members"></a>Zapečetěné třídy a členy třídy  
 Třídy lze deklarovat jako [zapečetěné](../../language-reference/keywords/sealed.md) vložením klíčového slova `sealed` před definici třídy. Příklad:  
  
 [!code-csharp[csProgGuideInheritance#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#16)]  
  
 Zapečetěná třída se nedá použít jako základní třída. Z tohoto důvodu nemůže být zároveň abstraktní třídou. Zapečetěné třídy brání odvození. Vzhledem k tomu, že je nelze nikdy použít jako základní třídu, mohou některé optimalizace za běhu volat členy zapečetěné třídy trochu rychleji.  
  
 Metoda, indexer, vlastnost nebo událost v odvozené třídě, která přepisuje virtuální člen základní třídy, může deklarovat tento člen jako zapečetěný. Tato negace je virtuální aspekt člena pro jakoukoliv další odvozenou třídu. To je dosaženo vložením klíčového slova `sealed` před klíčové slovo [override](../../language-reference/keywords/override.md) v deklaraci člena třídy. Příklad:  
  
 [!code-csharp[csProgGuideInheritance#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#17)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Třídy a struktury](./index.md)
- [Dědičnost](./inheritance.md)
- [Metody](./methods.md)
- [Pole](./fields.md)
- [Definování abstraktních vlastností](./how-to-define-abstract-properties.md)
