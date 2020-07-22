---
title: Správa verzí pomocí klíčových slov override a New – Průvodce programováním v C#
description: Přečtěte si o verzích pro základní a odvozené třídy v jazyce C# a o tom, jak určit, zda je metoda určena k přepsání nebo skrytí zděděné metody.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, versioning
- C# language, override and new
ms.assetid: 88247d07-bd0d-49e9-a619-45ccbbfdf0c5
ms.openlocfilehash: c2630741e1055a14dd5b9e4445d660cfd68891b0
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86863861"
---
# <a name="versioning-with-the-override-and-new-keywords-c-programming-guide"></a>Správa verzí pomocí klíčových slov override a new (Průvodce programováním v C#)
Jazyk C# je navržen tak, aby bylo možné vyvíjet a udržovat zpětnou kompatibilitu verzí mezi [základními](../../language-reference/keywords/base.md) a odvozenými třídami v různých knihovnách. To například znamená, že zavedení nového člena v základní [třídě](../../language-reference/keywords/class.md) se stejným názvem jako člen v odvozené třídě je zcela podporováno jazykem C# a nevede k neočekávanému chování. Také to znamená, že třída musí explicitně určit, zda je metoda určena k přepsání zděděné metody, nebo zda je metoda novou metodou, která skrývá obdobně pojmenovanou zděděnou metodu.  
  
 V jazyce C# odvozené třídy mohou obsahovat metody se stejným názvem jako metody základní třídy.  

- Pokud metoda v odvozené třídě nepředchází klíčové slovo [New](../../language-reference/keywords/new-modifier.md) nebo [override](../../language-reference/keywords/override.md) , kompilátor vydá upozornění a metoda se bude chovat, jako kdyby `new` bylo klíčové slovo přítomno.  
  
- Je-li metoda v odvozené třídě uvozena `new` klíčovým slovem, je metoda definována jako nezávislá na metodě v základní třídě.  
  
- Pokud metoda v odvozené třídě předchází `override` klíčové slovo, objekty odvozené třídy budou volat tuto metodu namísto metody základní třídy.  

- Aby bylo možné použít `override` klíčové slovo pro metodu v odvozené třídě, musí být metoda základní třídy definovaná jako [virtuální](../../language-reference/keywords/virtual.md).
  
- Metoda základní třídy může být volána v rámci odvozené třídy pomocí `base` klíčového slova.  
  
- `override` `virtual` `new` Klíčová slova, a lze také použít pro vlastnosti, indexery a události.  
  
 Ve výchozím nastavení nejsou metody jazyka C# virtuální. Pokud je metoda deklarována jako Virtual, jakákoliv třída, která dědí metodu, může implementovat svou vlastní verzi. Chcete-li vytvořit metodu Virtual, `virtual` je použit modifikátor v deklaraci metody základní třídy. Odvozená třída pak může přepsat základní virtuální metodu pomocí `override` klíčového slova nebo skrýt virtuální metodu v základní třídě pomocí `new` klíčového slova. Pokud `override` není zadáno klíčové slovo ani `new` klíčové slovo, kompilátor vydá upozornění a metoda v odvozené třídě skryje metodu v základní třídě.  
  
 K tomu je potřeba předpokládat, že společnost A vytvořila třídu s názvem `GraphicsClass` , kterou program používá. Následující `GraphicsClass` :  
  
 [!code-csharp[csProgGuideInheritance#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#27)]  
  
 Vaše společnost tuto třídu používá a použijete ji k odvození vlastní třídy a přidání nové metody:  
  
 [!code-csharp[csProgGuideInheritance#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#28)]  
  
 Vaše aplikace se používá bez problémů, dokud společnost A neuvolní novou verzi nástroje `GraphicsClass` , která se podobá následujícímu kódu:  
  
 [!code-csharp[csProgGuideInheritance#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#29)]  
  
 Nová verze `GraphicsClass` nyní obsahuje metodu s názvem `DrawRectangle` . Zpočátku nedojde k žádnému výskytu. Nová verze je stále binární kompatibilní se starou verzí. Veškerý software, který jste nasadili, bude fungovat i v případě, že je nová třída nainstalovaná na těchto počítačových systémech. Všechna existující volání metody `DrawRectangle` budou v odvozené třídě nadále odkazovat na vaši verzi.  
  
 Jakmile však aplikaci znovu zkompilujete pomocí nové verze nástroje `GraphicsClass` , obdržíte upozornění od kompilátoru, CS0108. Toto upozornění vás informuje o tom, že je nutné vzít v úvahu, jak se má vaše `DrawRectangle` Metoda chovat ve vaší aplikaci.  
  
 Chcete-li, aby metoda přepsala novou metodu základní třídy, použijte `override` klíčové slovo:  
  
 [!code-csharp[csProgGuideInheritance#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#30)]  
  
 `override`Klíčové slovo zajistí, že všechny objekty odvozené z `YourDerivedGraphicsClass` budou používat odvozenou třídu verze `DrawRectangle` . Objekty odvozené od `YourDerivedGraphicsClass` mají stále přístup k verzi základní třídy `DrawRectangle` pomocí klíčového slova Base:  
  
 [!code-csharp[csProgGuideInheritance#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#44)]  
  
 Pokud nechcete, aby metoda přepsala novou metodu základní třídy, platí následující požadavky. Chcete-li se vyhnout nejasnostem mezi těmito dvěma metodami, můžete přejmenovat metodu. To může být časově náročné a náchylné k chybám a v některých případech to není prakticky praktické. Pokud je však projekt relativně malý, můžete k přejmenování metody použít možnosti refaktoringu sady Visual Studio. Další informace naleznete v tématu [Refaktoring tříd a typů (návrhář tříd)](/visualstudio/ide/class-designer/refactoring-classes-and-types).  
  
 Alternativně můžete zabránit upozornění pomocí klíčového slova `new` v definici odvozené třídy:  
  
 [!code-csharp[csProgGuideInheritance#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#31)]  
  
 Použití `new` klíčového slova dává kompilátoru pokyn, že definice skrývá definici, která je obsažena v základní třídě. Toto je výchozí chování.  
  
## <a name="override-and-method-selection"></a>Přepsání a výběr metody  
 Pokud je metoda pojmenována na třídě, kompilátor jazyka C# vybere nejlepší metodu pro volání, pokud je více než jedna metoda kompatibilní se voláním, například pokud existují dvě metody se stejným názvem a parametry, které jsou kompatibilní s předaným parametrem. Následující metody by byly kompatibilní:  
  
 [!code-csharp[csProgGuideInheritance#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#32)]  
  
 Když `DoWork` je volána na instanci `Derived` , kompilátor jazyka C# se nejprve pokusí provést volání kompatibilní s verzemi `DoWork` deklarovanými původně na `Derived` . Metody přepsání nejsou považovány za deklarované u třídy, jsou to nové implementace metody deklarované u základní třídy. Pouze v případě, že kompilátor jazyka C# nemůže souhlasit s voláním metody původní metody, se `Derived` pokusí porovnat volání přepsané metody se stejným názvem a kompatibilními parametry. Příklad:  
  
 [!code-csharp[csProgGuideInheritance#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#33)]  
  
 Vzhledem k tomu `val` , že proměnnou lze převést na typ Double implicitně, kompilátor jazyka C# `DoWork(double)` místo `DoWork(int)` . Neexistují dva způsoby, jak se tomu vyhnout. Nejprve Vyhněte deklaraci nových metod se stejným názvem jako virtuální metody. Za druhé můžete instruovat kompilátor jazyka C#, aby vyvolal virtuální metodu tím, že prohledá seznam metod základní třídy přetypováním instance `Derived` na `Base` . Vzhledem k tomu, že metoda je virtuální, `DoWork(int)` bude `Derived` volána implementace on. Příklad:  
  
 [!code-csharp[csProgGuideInheritance#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#34)]  
  
 Další příklady a najdete `new` `override` v tématu [znalost, kdy použít klíčová slova override a New](./knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Třídy a struktury](./index.md)
- [Metody](./methods.md)
- [Dědičnost](./inheritance.md)
