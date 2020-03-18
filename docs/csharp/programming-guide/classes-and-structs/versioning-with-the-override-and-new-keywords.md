---
title: Správa verzí s přepsáním a novými klíčovými slovy – programovací příručka jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, versioning
- C# language, override and new
ms.assetid: 88247d07-bd0d-49e9-a619-45ccbbfdf0c5
ms.openlocfilehash: 089d5d7c7a95e2de4629f53255d9d9790fd5508a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705389"
---
# <a name="versioning-with-the-override-and-new-keywords-c-programming-guide"></a>Správa verzí pomocí klíčových slov override a new (Průvodce programováním v C#)
Jazyk C# je navržen tak, aby správa verzí mezi [základní](../../language-reference/keywords/base.md) a odvozené třídy v různých knihovnách můžete vyvíjet a udržovat zpětnou kompatibilitu. To například znamená, že zavedení nového člena v základní [třídě](../../language-reference/keywords/class.md) se stejným názvem jako člen v odvozené třídě je zcela podporováno c# a nevede k neočekávanému chování. To také znamená, že třída musí explicitně uvést, zda je metoda určena k přepsání zděděné metody nebo zda je metoda novou metodou, která skryje podobně pojmenovanou zděděnou metodu.  
  
 V C# odvozené třídy mohou obsahovat metody se stejným názvem jako metody základní třídy.  
  
- Metoda základní třídy musí být definována [jako virtuální](../../language-reference/keywords/virtual.md).  
  
- Pokud metoda v odvozené třídě není předchází [nové](../../language-reference/keywords/new-modifier.md) nebo [přepsat](../../language-reference/keywords/override.md) klíčová slova, kompilátor vydá upozornění `new` a metoda se bude chovat, jako by klíčové slovo byly přítomny.  
  
- Pokud metoda v odvozené třídě předchází `new` klíčové slovo, metoda je definována jako nezávislá na metodě v základní třídě.  
  
- Pokud metoda v odvozené třídě předchází `override` klíčové slovo, objekty odvozené třídy bude volat tuto metodu namísto metody základní třídy.  
  
- Metoda základní třídy může být volána z `base` odvozené třídy pomocí klíčového slova.  
  
- Klíčové `override` `virtual`slova `new` , a lze použít také na vlastnosti, indexery a události.  
  
 Ve výchozím nastavení nejsou metody Jazyka C# virtuální. Pokud je metoda deklarována jako virtuální, může jakákoli třída, která tuto metodu dědí, implementovat vlastní verzi. Chcete-li metodu `virtual` virtuální, modifikátor se používá v deklaraci metody základní třídy. Odvozená třída pak může přepsat základní virtuální `override` metodu pomocí klíčového slova nebo skrýt `new` virtuální metodu v základní třídě pomocí klíčového slova. Pokud není `override` zadáno `new` klíčové slovo ani klíčové slovo, kompilátor vydá upozornění a metoda v odvozené třídě skryje metodu v základní třídě.  
  
 Chcete-li to prokázat v praxi, předpokládejme na `GraphicsClass`chvíli, že společnost A vytvořila třídu s názvem , kterou program používá. Toto `GraphicsClass`je:  
  
 [!code-csharp[csProgGuideInheritance#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#27)]  
  
 Vaše společnost používá tuto třídu a vy ji používáte k odvození vlastní třídy přidáním nové metody:  
  
 [!code-csharp[csProgGuideInheritance#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#28)]  
  
 Aplikace se používá bez problémů, dokud společnost A `GraphicsClass`nevydá novou verzi aplikace , která se podobá následujícímu kódu:  
  
 [!code-csharp[csProgGuideInheritance#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#29)]  
  
 Nová verze `GraphicsClass` nyní obsahuje metodu s názvem `DrawRectangle`. Zpočátku se nic neděje. Nová verze je stále binární kompatibilní se starou verzí. Veškerý software, který jste nasadili, bude nadále fungovat, a to i v případě, že je v těchto počítačových systémech nainstalována nová třída. Všechny existující volání `DrawRectangle` metody bude i nadále odkazovat na verzi v odvozené třídě.  
  
 Však jakmile překompilujete aplikaci pomocí `GraphicsClass`nové verze aplikace , obdržíte upozornění od kompilátoru CS0108. Toto upozornění vás informuje, že je `DrawRectangle` třeba zvážit, jak chcete, aby se vaše metoda chovala ve vaší aplikaci.  
  
 Pokud chcete, aby vaše metoda přepsat novou metodu základní třídy, použijte `override` klíčové slovo:  
  
 [!code-csharp[csProgGuideInheritance#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#30)]  
  
 Klíčové `override` slovo zajišťuje, že všechny `YourDerivedGraphicsClass` objekty odvozené z `DrawRectangle`bude používat odvozené třídy verze . Objekty odvozené z `YourDerivedGraphicsClass` můžete stále `DrawRectangle` přístup k verzi základní třídy pomocí základní klíčové slovo:  
  
 [!code-csharp[csProgGuideInheritance#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#44)]  
  
 Pokud nechcete, aby vaše metoda přepsat novou metodu základní třídy, platí následující aspekty. Chcete-li se vyhnout záměně mezi těmito dvěma metodami, můžete přejmenovat metodu. To může být časově náročné a náchylné k chybám, a prostě není praktické v některých případech. Pokud je však váš projekt relativně malý, můžete metodu přejmenovat pomocí možností refaktoringu sady Visual Studio. Další informace naleznete [v tématu Refactoring Třídy a typy (Návrhář tříd)](/visualstudio/ide/class-designer/refactoring-classes-and-types).  
  
 Případně můžete zabránit upozornění pomocí klíčového `new` slova v definici odvozené třídy:  
  
 [!code-csharp[csProgGuideInheritance#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#31)]  
  
 Pomocí `new` klíčového slova říká kompilátoru, že vaše definice skryje definici, která je obsažena v základní třídě. Toto je výchozí chování.  
  
## <a name="override-and-method-selection"></a>Přepsání a výběr metody  
 Pokud je metoda pojmenována ve třídě, kompilátor Jazyka C# vybere nejlepší metodu pro volání, pokud je s voláním kompatibilní více než jedna metoda, například když existují dvě metody se stejným názvem a parametry, které jsou kompatibilní s předaným parametrem. Byly by kompatibilní následující metody:  
  
 [!code-csharp[csProgGuideInheritance#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#32)]  
  
 Když `DoWork` je volána `Derived`na instanci , kompilátor Jazyka C# se `DoWork` nejprve pokusí `Derived`o kompatibilitu volání s verzemi původně deklarované na . Přepsat metody nejsou považovány za deklarované na třídu, jsou nové implementace metody deklarované na základní třídy. Pouze v případě, že kompilátor Jazyka C# `Derived` nemůže odpovídat volání metody na se pokusí shodovat volání přepsané metody se stejným názvem a kompatibilní parametry. Například:  
  
 [!code-csharp[csProgGuideInheritance#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#33)]  
  
 Vzhledem `val` k tomu, že proměnná může být převedena `DoWork(double)` na `DoWork(int)`double implicitně, c# kompilátor volání namísto . Existují dva způsoby, jak se tomu vyhnout. Nejprve se vyhněte deklarování nových metod se stejným názvem jako virtuální metody. Za druhé můžete pokyn kompilátoru Jazyka C# volat virtuální metodu tím, že `Derived` `Base`jej prohledávat seznam metod základní třídy přetypováním instance do . Vzhledem k tomu, že `DoWork(int)` `Derived` metoda je virtuální, bude volána implementace on. Například:  
  
 [!code-csharp[csProgGuideInheritance#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#34)]  
  
 Další příklady `new` a `override`, viz [Vědět, kdy použít přepsat a nová klíčová slova](./knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Třídy a struky](./index.md)
- [Metody](./methods.md)
- [Dědičnost](./inheritance.md)
