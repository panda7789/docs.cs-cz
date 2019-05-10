---
title: Správa verzí pomocí přepsání a nových klíčových slov - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, versioning
- C# language, override and new
ms.assetid: 88247d07-bd0d-49e9-a619-45ccbbfdf0c5
ms.openlocfilehash: ec6040081d44a389bd42bb50cdd81ac0634abf91
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64583129"
---
# <a name="versioning-with-the-override-and-new-keywords-c-programming-guide"></a>Správa verzí pomocí klíčových slov override a new (Průvodce programováním v C#)
Jazyk C# je navržený tak, aby Správa verzí mezi [základní](../../../csharp/language-reference/keywords/base.md) a odvozené třídy v jiných knihovnách můžete vyvíjet a udržovat zpětnou kompatibilitu. To znamená, například, že zavedení nového člena v základní třídě [třída](../../../csharp/language-reference/keywords/class.md) se stejným názvem jako člena v odvozené třídě je plně podporován v jazyce C# a nevede k neočekávanému chování. Také znamená, že třída musí explicitně uvést, zda metoda je určena k přepsání zděděné metody nebo určuje, zda je metoda novou metodu, která skrývá podobně pojmenovaných zděděné metody.  
  
 V jazyce C# odvozené třídy mohou obsahovat metody se stejným názvem jako metody základní třídy.  
  
- Metoda základní třídy musí být definován [virtuální](../../../csharp/language-reference/keywords/virtual.md).  
  
- Pokud metoda v odvozené třídě není předcházen [nové](../../../csharp/language-reference/keywords/new.md) nebo [přepsat](../../../csharp/language-reference/keywords/override.md) klíčová slova, kompilátor vygeneruje upozornění a metodu se bude chovat jako `new` – klíčové slovo nebyly nalezeny.  
  
- Pokud je metoda v odvozené třídě začínající `new` – klíčové slovo, metoda je definována jako nezávislé na metodu v základní třídě.  
  
- Pokud je metoda v odvozené třídě začínající `override` – klíčové slovo, objekty odvozené třídy zavolá tato metoda namísto metody základní třídy.  
  
- Metoda základní třídy lze volat z v rámci odvozené třídy pomocí `base` – klíčové slovo.  
  
- `override`, `virtual`, A `new` klíčová slova lze také použít u vlastnosti, indexery a události.  
  
 Ve výchozím nastavení nejsou virtuální metody jazyka C#. Pokud metoda deklarována jako virtuální, všechny třídu, která dědí metodu můžete implementovat vlastní verzi. Virtuální, aby metoda `virtual` modifikátor se používá v deklaraci metody základní třídy. Odvozená třída může přepsat základní metodu virtuální pak pomocí `override` – klíčové slovo nebo skrýt virtuální metodu v základní třídě pomocí `new` – klíčové slovo. Pokud ani `override` – klíčové slovo ani `new` zadáno klíčové slovo, kompilátor vygeneruje upozornění a metodu v odvozené třídě budou skrývat metodu v základní třídě.  
  
 Abychom si předvedli v praxi, předpokládají na chvíli zastavíme, firmy A vytvořil třídu s názvem `GraphicsClass`, který program používá. Tady je `GraphicsClass`:  
  
 [!code-csharp[csProgGuideInheritance#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#27)]  
  
 Vaše společnost používá ochranu této třídy a můžete ji použít k odvodit vlastní třídu, přidání nové metody:  
  
 [!code-csharp[csProgGuideInheritance#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#28)]  
  
 Vaše aplikace se používá bez problémů, dokud nové verze aktualizací společnosti A `GraphicsClass`, který vypadá podobně jako následující kód:  
  
 [!code-csharp[csProgGuideInheritance#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#29)]  
  
 Nová verze `GraphicsClass` nyní obsahuje metodu s názvem `DrawRectangle`. Na začátku nedojde k žádné akci. Nová verze je stále binární kompatibilní s předchozí verzi aplikace. Veškerý software, který jste nasadili se budou nadále fungovat, i v případě nové třídy je nainstalována v těchto počítačích. Všechna existující volání do metody `DrawRectangle` budou i nadále odkazují na vaši verzi, a to v odvozené třídě.  
  
 Ale co nejdříve aplikaci znovu zkompilujete pomocí nové verze `GraphicsClass`, zobrazí se upozornění z kompilátoru CS0108. Toto upozornění vás informuje, že budete muset zvážit, jak chcete vaši `DrawRectangle` metoda chovat ve vaší aplikaci.  
  
 Pokud chcete metodu pro přepsání novou metodu základní třídy, použijte `override` – klíčové slovo:  
  
 [!code-csharp[csProgGuideInheritance#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#30)]  
  
 `override` – Klíčové slovo zajišťuje, že všechny objekty odvozené z `YourDerivedGraphicsClass` budou používat verzi odvozené třídy `DrawRectangle`. Objekty odvozené z `YourDerivedGraphicsClass` pořád přístup k verzi základní třídy `DrawRectangle` pomocí klíčového slova base:  
  
 [!code-csharp[csProgGuideInheritance#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#44)]  
  
 Pokud nechcete, aby vaše metoda k přepsání novou metodu základní třídy, platí následující aspekty. Aby nedocházelo k záměně mezi těmito dvěma metodami, můžete přejmenovat metodu. To může být časově náročné a náchylné k chybě a v některých případech stačí není praktické. Pokud váš projekt je poměrně malý, můžete přejmenovat metodu můžete použít možnosti aplikace Visual Studio refaktoringu. Další informace najdete v tématu [refaktoring tříd a typů (návrhář tříd)](/visualstudio/ide/refactoring-classes-and-types-class-designer).  
  
 Alternativně můžete zabránit upozornění pomocí klíčového slova `new` v definici odvozené třídy:  
  
 [!code-csharp[csProgGuideInheritance#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#31)]  
  
 Použití `new` – klíčové slovo sděluje kompilátoru, že vaše definice skryje definici, která je obsažena v základní třídě. Toto je výchozí chování.  
  
## <a name="override-and-method-selection"></a>Přepsání a výběr metody  
 Při názvem metodu na třídu, kompilátor jazyka C# vybere nejlepší metody volat, pokud více než jedním ze způsobů je kompatibilní s voláním, například když existují dvě metody se stejným názvem a parametry, které jsou kompatibilní s parametrem předán. Následující metody by měly kompatibilní:  
  
 [!code-csharp[csProgGuideInheritance#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#32)]  
  
 Když `DoWork` je volán na instanci `Derived`, kompilátor jazyka C# se nejdřív pokusí použít, provede volání kompatibilní s verzemi `DoWork` původně deklarovaná na `Derived`. Přepsání metody nepovažují, protože deklaruje se na třídu, nové implementace metody deklarované pro základní třídu. Pouze v případě, že kompilátor jazyka C# se nemůže shodovat volání metody na původní metodu na `Derived` se pokusit porovnat volání přepsané metody se stejným názvem a kompatibilní parametry. Příklad:  
  
 [!code-csharp[csProgGuideInheritance#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#33)]  
  
 Protože proměnné `val` lze implicitně převést na dvojitou hodnotu volání kompilátor jazyka C# `DoWork(double)` místo `DoWork(int)`. Existují dva způsoby, abyste tomu předešli. Vyhněte se nejprve deklaraci nových metod se stejným názvem jako virtuální metody. Za druhé, můžete dát pokyn kompilátoru C# pro volání virtuální metody tím, že metoda základní třídy v seznamu vyhledejte přetypováním instanci `Derived` k `Base`. Protože metoda je virtuální, provádění `DoWork(int)` na `Derived` , zavolá se. Příklad:  
  
 [!code-csharp[csProgGuideInheritance#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#34)]  
  
 Další příklady `new` a `override`, naleznete v tématu [vědět, když pro použití přepsání a nových klíčových slov](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)
- [Dědičnost](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
