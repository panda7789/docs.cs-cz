---
title: Obecné třídy (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic classes
- generics [C#], classes
ms.assetid: 27d6f256-cd61-41e3-bc6e-b990a53b0224
ms.openlocfilehash: 65c5f376bce44e6120c17638076d2edfc38c734e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33338283"
---
# <a name="generic-classes-c-programming-guide"></a>Obecné třídy (Průvodce programováním v C#)
Obecné třídy zapouzdřovat operace, které nejsou specifické pro určitý datový typ. Nejčastěji používá pro obecné třídy je ke kolekcím, jako jsou propojené seznamy, zatřiďovacích tabulkách, zásobníky, fronty, stromy a tak dále. Operace, jako je například přidávání a odebírání položek z kolekce se provádějí v bez ohledu na typ uložení dat v podstatě stejným způsobem.  
  
 Doporučený postup pro většinu scénářů, které vyžadují třídy kolekce, je použití těm, které jsou uvedené v knihovně tříd rozhraní .NET. Další informace o použití těchto tříd naleznete v tématu [obecné kolekce v rozhraní .NET](../../../standard/generics/collections.md).  
  
 Obecné třídy obvykle vytvoříte tak, že počínaje existující konkrétní třídy a změna typy parametrů typu jeden v době, dokud se nedostanete optimální rovnováha mezi počtem Generalizace a použitelnost. Při vytváření vlastní obecné třídy, je důležité zvážit zahrnují následující:  
  
-   Jaké typy generalize do parametrů typu.  
  
     Jako pravidlo, další typy, které můžete parametrizovat, více flexibilní a opakovaně použitelný kód změní. Příliš mnoho generalizace však můžete vytvořit kód, který je složité jiné vývojářům pro čtení nebo pochopit.  
  
-   Jaké omezení, pokud existuje, které chcete použít pro parametry typu (viz [omezení parametrů typů](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)).  
  
     Doporučujeme použít maximální možné omezení, která bude stále umožňují zpracování typy, které je nutné zpracovat. Například pokud jste si jisti, že obecná třída je určena pro použití jenom s typy odkazů, platí omezení třídy. Který zabrání neúmyslnému použití třídě s typy hodnot a budete moci použít `as` operátor na `T`a zkontrolujte hodnoty null.  
  
-   Určuje, zda zohlednit obecné chování do základní třídy a podtřídy.  
  
     Protože obecné třídy může sloužit jako základní třídy, stejné aspekty návrhu zde platí stejně jako u neobecné třídy. Najdete v části pravidla o tom, která dědí z obecné základní třídy později v tomto tématu.  
  
-   Určuje, zda implementovat jednu nebo více obecná rozhraní.  
  
     Například pokud navrhujete třídu, která se použije k vytvoření položek v kolekci na základě obecné typy, budete muset implementovat rozhraní, jako <xref:System.IComparable%601> kde `T` je typ třídě.  
  
 Příklad jednoduchého obecné třídy, naleznete v části [Úvod do obecných typů](../../../csharp/programming-guide/generics/introduction-to-generics.md).  
  
 Pravidla pro parametry typu a omezení mají několik vliv na chování obecná třída, zejména pokud jde o dědičnosti a člen usnadnění. Než budete pokračovat, měli byste pochopit některé podmínky. Pro obecné třídy `Node<T>,` kód klienta může odkazovat na třídu buď tak, že zadáte argument typu, k vytvoření typu uzavřené vytvořený (`Node<int>`). Případně ho můžete nechat parametr typu Tento parametr nezadáte, například když zadáte obecné základní třídy, k vytvoření otevřenou sestavený typu (`Node<T>`). Obecné třídy může dědit vlastnosti z konkrétní, uzavřené vytvořený nebo otevřené sestavené základní třídy:  
  
 [!code-csharp[csProgGuideGenerics#16](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_1.cs)]  
  
 Jinými slovy, konkrétní non Obecné, třídy můžete dědění z uzavřených vytvořený základní třídy, ale není z otevřené sestavené třídy nebo z parametrů typu, protože neexistuje žádný způsob v době běhu kódu klienta zadat argument typu potřebné k vytváření instancí Základní třída.  
  
 [!code-csharp[csProgGuideGenerics#17](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_2.cs)]  
  
 Obecné třídy, které dědí od otevřené sestavené typy musíte zadat argumenty typu pro všechny parametry typu základní třídy, které nejsou sdíleny dědičných třídu, jak je ukázáno v následujícím kódu:  
  
 [!code-csharp[csProgGuideGenerics#18](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_3.cs)]  
  
 Obecné třídy, které dědí od otevřené sestavené typy musíte zadat omezení, která je nadmnožinou nebo implikují omezení u základního typu:  
  
 [!code-csharp[csProgGuideGenerics#19](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_4.cs)]  
  
 Obecné typy můžete použít několik parametrů typu a omezení, následujícím způsobem:  
  
 [!code-csharp[csProgGuideGenerics#20](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_5.cs)]  
  
 Otevřené sestavené typy vytvořený a uzavřené lze použít jako parametry metody:  
  
 [!code-csharp[csProgGuideGenerics#21](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_6.cs)]  
  
 Pokud obecná třída implementuje rozhraní, všechny instance této třídy lze převést na tomto rozhraní.  
  
 Obecné třídy jsou neutrální. Jinými slovy Pokud určuje vstupní parametr `List<BaseClass>`, kompilaci chyba se zobrazí, pokud se pokusíte poskytují `List<DerivedClass>`.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.Generic>  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Obecné typy](../../../csharp/programming-guide/generics/index.md)  
 [Uložení stavu výčty](https://blogs.msdn.microsoft.com/wesdyer/2006/01/13/saving-the-state-of-enumerators/)  
 [Stavebnice dědičnosti první část](https://blogs.msdn.microsoft.com/ericlippert/2007/07/27/an-inheritance-puzzle-part-one/)
