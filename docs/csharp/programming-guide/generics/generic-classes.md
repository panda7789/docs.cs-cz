---
title: Obecné třídy – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic classes
- generics [C#], classes
ms.assetid: 27d6f256-cd61-41e3-bc6e-b990a53b0224
ms.openlocfilehash: 141da196869d3867a9a85087a073dbec095d5118
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244398"
---
# <a name="generic-classes-c-programming-guide"></a>Obecné třídy (Průvodce programováním v C#)
Obecné třídy zapouzdření operace, které nejsou specifické pro konkrétní data typu. Nejběžnějším využitím obecných tříd je s kolekcí jako propojené seznamy zatřiďovacích tabulek, zásobníků, front, stromy a tak dále. Operace, jako jsou přidávání a odebírání položek z kolekce jsou prováděny v podstatě stejným způsobem bez ohledu na typ data ukládat.  
  
 Doporučený postup pro většinu scénářů, které vyžadují třídy kolekcí, je použít dotazy k dispozici v knihovně tříd rozhraní .NET. Další informace o použití těchto tříd naleznete v tématu [obecné kolekce na platformě .NET](../../../standard/generics/collections.md).  
  
 Obvykle vytvoříte obecných tříd od existující konkrétní třídy a změnou typy do parametry typu jeden po druhém, dokud se nedostanete optimální rovnováhu mezi Generalizace a použitelnost. Při vytváření vlastní obecných tříd, důležité informace patří:  
  
-   Jaké typy generalize do parametrů typu.  
  
     Váš kód bude jako pravidlo, další typy, které můžete parametrizovat, více flexibilní a opakovaně použitelné. Příliš mnoho generalizace však můžete vytvořit kód, který je obtížné pro jiné vývojáře pro čtení nebo pochopit.  
  
-   Jaká omezení, pokud chcete použít pro parametry typu (viz [omezení parametrů typů](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)).  
  
     Pravidlo vhodné je použít maximální možné omezení, která bude stále umožňují zpracovat typy, které je třeba ošetřit. Například pokud víte, že obecné třídy je určena pro použití pouze s typy odkazů, platí omezení třídy. Který bude zabránit neúmyslnému použití třídy s typy hodnot a vám umožní používat `as` operátoru u `T`a kontrola hodnot null.  
  
-   Určuje, zda faktor obecné chování do základních tříd a podtříd.  
  
     Protože obecné třídy může sloužit jako základní třídy, platí zde stejné aspekty návrhu stejně jako u neobecných třídách. Zobrazit pravidla o dědění z obecné základní třídy dále v tomto tématu.  
  
-   Určuje, zda implementovat jednu nebo více obecných rozhraní.  
  
     Například pokud navrhujete třídu, která se použije k vytvoření položek v kolekci na základě obecných typů, budete muset implementovat rozhraní jako <xref:System.IComparable%601> kde `T` je typ třídy.  
  
 Příklad jednoduchou obecnou třídu, naleznete v tématu [Úvod do obecných typů](../../../csharp/programming-guide/generics/introduction-to-generics.md).  
  
 Pravidla pro parametry typu a omezení mají několik důsledky pro obecnou třídu chování, zejména pokud jde o dědičnosti a člen usnadnění. Než budete pokračovat, měli byste pochopit některé podmínky. Pro obecnou třídu `Node<T>,` klientský kód může odkazovat na třídu buď tak, že zadáte argument typu, chcete-li vytvořit uzavřený konstruovaný typ. (`Node<int>`). Případně ho můžete nechat parametr typu, který je tento parametr zadán, například když zadáte obecné základní třídy, chcete-li vytvořit otevřenou konstruovaný typ. (`Node<T>`). Obecné třídy můžete dědit z konkrétní, uzavřený konstruovaný nebo otevřít konstruované základní třídy:  
  
 [!code-csharp[csProgGuideGenerics#16](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_1.cs)]  
  
 Neobecné, jinými slovy, konkrétní, třídy mohou dědit z uzavřených konstruované základní třídy, ale není otevřené konstruovaný třídy nebo parametry typu, protože neexistuje žádný způsob v době běhu pro klientský kód zadáte argument typu vyžaduje vytvoření instance Základní třída.  
  
 [!code-csharp[csProgGuideGenerics#17](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_2.cs)]  
  
 Obecné třídy, které dědí z otevřené sestavené typy musíte zadat argumenty typu pro všechny parametry typu základní třídy, které nejsou sdíleny dědičné třídě, jak je ukázáno v následujícím kódu:  
  
 [!code-csharp[csProgGuideGenerics#18](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_3.cs)]  
  
 Obecné třídy, které dědí z otevřené sestavené typy musíte zadat omezení, která je nadstavbou jazyka nebo implikovat, omezení u základního typu:  
  
 [!code-csharp[csProgGuideGenerics#19](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_4.cs)]  
  
 Obecné typy můžete použít více parametry typu a omezení, následujícím způsobem:  
  
 [!code-csharp[csProgGuideGenerics#20](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_5.cs)]  
  
 Otevřené sestavené typy vytvořený a uzavřených může sloužit jako parametry metody:  
  
 [!code-csharp[csProgGuideGenerics#21](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_6.cs)]  
  
 Pokud obecná třída implementuje rozhraní, všechny instance této třídy lze převést na rozhraní.  
  
 Obecné třídy se nebudou měnit. Jinými slovy Pokud určuje vstupní parametr `List<BaseClass>`, Chyba kompilace se zobrazí, když se pokusíte k poskytování `List<DerivedClass>`.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Collections.Generic>  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Obecné typy](../../../csharp/programming-guide/generics/index.md)  
- [Ukládání stavu čítače](https://blogs.msdn.microsoft.com/wesdyer/2006/01/13/saving-the-state-of-enumerators/)  
- [Díl stavebnice dědičnosti, část 1](https://blogs.msdn.microsoft.com/ericlippert/2007/07/27/an-inheritance-puzzle-part-one/)
