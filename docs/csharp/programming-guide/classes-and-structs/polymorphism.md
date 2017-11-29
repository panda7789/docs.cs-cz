---
title: "Polymorfismus (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, polymorphism
- polymorphism [C#]
ms.assetid: 086af969-29a5-4ce8-a993-0b7d53839dab
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 601c8cf626c846ca6c5d6bc2338e271e6b93544a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="polymorphism-c-programming-guide"></a>Polymorfismus (Průvodce programováním v C#)
Polymorfismus se často označuje jako třetím pilíře objektově orientované programování po zapouzdření a dědičnost. Polymorfismus je řecké slovo, které znamená "mnoho ve tvaru" a má dva jedinečné aspekty:  
  
-   V době běhu objekty odvozené třídy mohou být považovány za objekty základní třídy na místech, jako je například parametry metody a kolekce nebo pole. V takovém případě deklarovaného typu objektu již není stejný jako její typ spuštění.  
  
-   Třídy Base může definovat a implementovat [virtuální](../../../csharp/language-reference/keywords/virtual.md) *metody*, a odvozené třídy mohou [přepsat](../../../csharp/language-reference/keywords/override.md) sebou, což znamená, poskytují vlastní definice a implementace. Při spuštění když kód klienta volá metodu, modulu CLR běhového typu objektu, a, vyvolá tento přepsání virtuální metody. Proto ve zdrojovém kódu můžete volat metodu pro základní třídu a způsobit, že do odvozené třídy verzi metody spouštění.  
  
 Virtuální metody umožňují pracovat s skupiny související objekty jednotným způsobem. Předpokládejme například, že máte kreslení aplikaci, která umožňuje uživateli vytvořit různé druhy tvarů na kreslicí plochy. Neznáte v době kompilace jaké konkrétní typy tvarů uživatel vytvoří. Ale aplikace má ke sledování všech různé typy tvarů, které jsou vytvořené a má je aktualizovat v odpovědi na akce myši uživatele. Polymorfismus můžete použít k vyřešení tohoto problému v dva základní kroky:  
  
1.  Vytvořte hierarchie tříd, ve kterém každá třída konkrétní tvaru odvozená z obecná základní třída.  
  
2.  Použijte virtuální metoda k vyvolání metody odpovídající na všechny odvozené třídy prostřednictvím jednoho volání metody základní třídy.  
  
 Nejprve vytvořte základní třídu s názvem `Shape`a jsou odvozené třídy, jako `Rectangle`, `Circle`, a `Triangle`. Poskytnout `Shape` třídy virtuální metodu s názvem `Draw`, a představuje přepsání, v každém odvozené třídy za účelem kreslení konkrétní utvářejí třídy. Vytvoření `List<Shape>` objektu a přidejte do ní kruh, trojúhelníček a rámečku. Chcete-li aktualizovat kreslicí plochy, použijte [foreach](../../../csharp/language-reference/keywords/foreach-in.md) smyčky k iteraci v rámci seznamu a volání `Draw` metoda na každém `Shape` objektu v seznamu. I když každý objekt v seznamu má deklarovaný typ `Shape`, je běhového typu (přepsané verze metodu každý odvozené třídy), která bude volána.  
  
 [!code-csharp[csProgGuideInheritance#50](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_1.cs)]  
  
 V jazyce C#, každý typ je polymorfní, protože dědí všechny typy, včetně uživatelem definované typy <xref:System.Object>.  
  
## <a name="polymorphism-overview"></a>Polymorfismus – přehled  
  
### <a name="virtual-members"></a>Virtuální členové  
 Když do odvozené třídy dědí vlastnosti ze základní třídy, získá všechny metody, pole, vlastnosti a události základní třídy. Můžete zvolit návrháře odvozené třídy, jestli se má  
  
-   přepsat virtuální členy v základní třídě.  
  
-   Zdědit nejbližší metoda základní třídy bez jeho přepsání  
  
-   Definujte nové nevirtuálních implementace členů, které skrýt implementace třídy base  
  
 Odvozené třídy můžete přepsat člena základní třídy, pouze v případě, že je člen základní třídy je deklarován jako [virtuální](../../../csharp/language-reference/keywords/virtual.md) nebo [abstraktní](../../../csharp/language-reference/keywords/abstract.md). Odvozené člen musí používat [přepsat](../../../csharp/language-reference/keywords/override.md) – klíčové slovo explicitně indikující, že metoda je určena k účasti v virtuální volání. Následující kód představuje příklad:  
  
 [!code-csharp[csProgGuideInheritance#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_2.cs)]  
  
 Pole nemůže být virtuální; pouze metody, vlastnosti, události a indexery může být virtuální. Tento člen odvozené třídě přepsání člena virtuální, se nazývá i v případě, že instance této třídy je přistupuje jako instance základní třídy. Následující kód představuje příklad:  
  
 [!code-csharp[csProgGuideInheritance#21](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_3.cs)]  
  
 Virtuální metody a vlastnosti, povolte odvozené třídy rozšíření základní třídy bez nutnosti použít implementace základní třídy metody. Další informace najdete v tématu [Správa verzí pomocí nové klíčových slov Override a](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md). Rozhraní poskytuje jiný způsob, jak definovat metody nebo sadu metod, jejichž implementace je ponechán do odvozených tříd. Další informace najdete v tématu [rozhraní](../../../csharp/programming-guide/interfaces/index.md).  
  
### <a name="hiding-base-class-members-with-new-members"></a>Skrytí členy základní třídy se nové členy  
 Pokud chcete, aby vaše odvozené člena do mají stejný název jako člen v základní třídě, ale nechcete, aby mohla účastnit virtuální volání, můžete použít [nové](../../../csharp/language-reference/keywords/new.md) – klíčové slovo. `new` Je před návratový typ člena třídy, který se nahrazuje uveďte – klíčové slovo. Následující kód představuje příklad:  
  
 [!code-csharp[csProgGuideInheritance#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_4.cs)]  
  
 Členy skrytá základní třídy můžete dál dostat z kódu klienta podle přetypování instanci odvozené třídy do instance základní třídy. Příklad:  
  
 [!code-csharp[csProgGuideInheritance#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_5.cs)]  
  
### <a name="preventing-derived-classes-from-overriding-virtual-members"></a>Odvozené třídy brání přepisování virtuální členové  
 Virtuální členové zůstat virtuální dobu neurčitou, bez ohledu na tom, kolik třídy byli deklarováni mezi člena virtuální a třídu, která ho původně deklarovány. Pokud třídy A deklaruje člena virtuální třídy B je odvozena z A a b je odvozena třída C, třída C dědí člena virtuální a má možnost přepsat, bez ohledu na tom, jestli třídy B deklarovat přepsání pro tohoto člena. Následující kód představuje příklad:  
  
 [!code-csharp[csProgGuideInheritance#22](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_6.cs)]  
  
 Odvozené třídy můžete zastavit virtuální dědičnost deklarováním přepsání jako [zapečetěné](../../../csharp/language-reference/keywords/sealed.md). To vyžaduje uvedení `sealed` – klíčové slovo před `override` – klíčové slovo v deklarace člena třídy. Následující kód představuje příklad:  
  
 [!code-csharp[csProgGuideInheritance#24](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_7.cs)]  
  
 V předchozím příkladu metoda `DoWork` již není virtuálních a všechny třídy odvozené od C. Je stále virtuální pro instance C, i když jsou přetypovat na typ nebo typ B A. zapečetěné metody lze nahradit odvozené třídy pomocí `new` – klíčové slovo, jak ukazuje následující příklad:  
  
 [!code-csharp[csProgGuideInheritance#25](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_8.cs)]  
  
 V takovém případě pokud `DoWork` je volána v D pomocí proměnné typu D, nové `DoWork` je volána. Pokud proměnná typu C, B nebo A slouží k přístupu k instanci D, volání `DoWork` bude postupovat podle pravidla virtuální dědičnost, směrování těchto volání na implementaci `DoWork` u třídy C.  
  
### <a name="accessing-base-class-virtual-members-from-derived-classes"></a>Přístup k virtuální členy základní třídy z odvozené třídy  
 Odvozené třídy, která má nahradit nebo přepsání metody nebo vlastnosti můžete pořád přístup k metody nebo vlastnosti na základní třídy pomocí base – klíčové slovo. Následující kód představuje příklad:  
  
 [!code-csharp[csProgGuideInheritance#26](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_9.cs)]  
  
 Další informace najdete v tématu [základní](../../../csharp/language-reference/keywords/base.md).  
  
> [!NOTE]
>  Je doporučeno, použít virtuální členové `base` volat základní třída implementace tohoto člena v jejich vlastní implementaci. Když necháte dojít umožňuje soustředit se na odvozené třídy základní třída chování implementace chování, které jsou specifické pro odvozené třídy. Pokud není volán implementaci základní třídy, je až odvozené třídy, aby jejich chování kompatibilní s chováním základní třídy.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
-   [Správa verzí pomocí nové klíčových slov Override a](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)  
  
-   [Znalost, kdy použít nové klíčových slov Override a](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)  
  
-   [Postupy: potlačení metody ToString](../../../csharp/programming-guide/classes-and-structs/how-to-override-the-tostring-method.md)  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Dědičnost](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
 [Abstraktní a uzavřené třídy a jejich členové](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
 [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [Události](../../../csharp/programming-guide/events/index.md)  
 [Vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Indexery](../../../csharp/programming-guide/indexers/index.md)  
 [Typy](../../../csharp/programming-guide/types/index.md)
