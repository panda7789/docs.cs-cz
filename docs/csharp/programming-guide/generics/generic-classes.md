---
title: Obecné třídy – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic classes
- generics [C#], classes
ms.assetid: 27d6f256-cd61-41e3-bc6e-b990a53b0224
ms.openlocfilehash: 1fdfaa833ad32428d341b6f3a61cc7f638036183
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937510"
---
# <a name="generic-classes-c-programming-guide"></a>Obecné třídy (Průvodce programováním v C#)
Obecné třídy zapouzdřují operace, které nejsou specifické pro určitý datový typ. Nejběžnější použití pro obecné třídy je s kolekcemi, jako jsou propojené seznamy, tabulky hash, zásobníky, fronty, stromy a tak dále. Operace, jako je přidávání a odebírání položek z kolekce, jsou prováděny v podstatě stejným způsobem bez ohledu na typ uložených dat.  
  
 Pro většinu scénářů, které vyžadují třídy kolekce, je doporučeným přístupem použití ty, které jsou k dispozici v knihovně tříd .NET. Další informace o použití těchto tříd naleznete [v tématu Obecné kolekce v rozhraní .NET](../../../standard/generics/collections.md).  
  
 Obvykle vytvoříte obecné třídy tak, že začnete s existující konkrétní třídou a přeřadíte typy na parametry typu jeden po druhém, dokud nedosáhnete optimální rovnováhy generalizace a použitelnosti. Při vytváření vlastníobecné třídy, důležité důležité důležité informace patří následující:  
  
- Které typy chcete generalizovat do parametrů typu.  
  
     Zpravidla platí, že čím více typů můžete parametrizovat, tím flexibilnější a opakovaně použitelný kód se stane. Příliš mnoho generalizace však můžete vytvořit kód, který je obtížné pro ostatní vývojáře číst nebo pochopit.  
  
- Jaká omezení, pokud existuje, použít na parametry typu (Viz [Omezení na parametry typu](./constraints-on-type-parameters.md)).  
  
     Dobrým pravidlem je použít maximální možná omezení, která vám stále umožní zpracovávat typy, které je nutné zpracovat. Například pokud víte, že vaše obecná třída je určena pro použití pouze s typy odkazů, použijte omezení třídy. To zabrání nechtěnému použití vaší třídy s typy hodnot `as` a `T`umožní vám použít operátor na aplikaci a zkontrolovat hodnoty null.  
  
- Určuje, zda má být obecné chování faktorováno do základních tříd a podtříd.  
  
     Vzhledem k tomu, že obecné třídy mohou sloužit jako základní třídy, platí zde stejné aspekty návrhu jako u neobecných tříd. Viz pravidla o dědit z obecných základních tříd dále v tomto tématu.  
  
- Určuje, zda má být implementováno jedno nebo více obecných rozhraní.  
  
     Například pokud navrhujete třídu, která bude použita k vytvoření položek v kolekci založené na <xref:System.IComparable%601> obecných, budete muset implementovat rozhraní, například kde `T` je typ vaší třídy.  
  
 Příklad jednoduché obecné třídy naleznete [v tématu Úvod do obecných typů](./index.md).  
  
 Pravidla pro parametry typu a omezení mají několik důsledků pro chování obecné třídy, zejména pokud jde o dědičnost a usnadnění přístupu členů. Než budete pokračovat, měli byste pochopit některé pojmy. Pro obecný `Node<T>,` kód klienta třídy můžete odkazovat na třídu buď zadáním`Node<int>`argumentu typu, chcete-li vytvořit uzavřený konstruovaný typ ( ). Alternativně může ponechat parametr typu nespecifikovaný, například když zadáte obecnou základní třídu, chcete-li vytvořit otevřený konstruovaný typ (`Node<T>`). Obecné třídy mohou dědit z betonu, uzavřené konstrukce nebo otevřené konstruované základní třídy:  
  
 [!code-csharp[csProgGuideGenerics#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#16)]  
  
 Neobecné, jinými slovy, konkrétní, třídy mohou dědit z uzavřených konstruované základní třídy, ale ne z otevřené konstruované třídy nebo z parametrů typu, protože neexistuje žádný způsob, jak za běhu pro kód klienta zadat argument typu potřebné k vytvoření instance základní třídy.  
  
 [!code-csharp[csProgGuideGenerics#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#17)]  
  
 Obecné třídy, které dědí z otevřených konstruovaných typů, musí poskytovat argumenty typu pro všechny parametry typu základní třídy, které nejsou sdíleny děvčivou třídou, jak je znázorněno v následujícím kódu:  
  
 [!code-csharp[csProgGuideGenerics#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#18)]  
  
 Obecné třídy, které dědí z otevřených konstruovaných typů, musí určit omezení, která jsou nadmnožinou nebo implikují omezení základního typu:  
  
 [!code-csharp[csProgGuideGenerics#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#19)]  
  
 Obecné typy mohou používat více parametrů typu a omezení, a to následovně:  
  
 [!code-csharp[csProgGuideGenerics#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#20)]  
  
 Jako parametry metody lze použít otevřené konstruované a uzavřené konstruované typy:  
  
 [!code-csharp[csProgGuideGenerics#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#21)]  
  
 Pokud obecná třída implementuje rozhraní, všechny instance této třídy lze přetypovat do tohoto rozhraní.  
  
 Obecné třídy jsou invariantní. Jinými slovy, pokud vstupní parametr `List<BaseClass>`určuje , zobrazí se chyba v době `List<DerivedClass>`kompilace, pokud se pokusíte poskytnout .  
  
## <a name="see-also"></a>Viz také

- <xref:System.Collections.Generic>
- [Programovací příručka jazyka C#](../index.md)
- [Obecné typy](./index.md)
- [Uložení stavu výčtů](https://docs.microsoft.com/archive/blogs/wesdyer/saving-the-state-of-enumerators)
- [Dědictví Puzzle, část první](https://docs.microsoft.com/archive/blogs/ericlippert/an-inheritance-puzzle-part-one)
