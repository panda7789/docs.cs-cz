---
title: Správa verzí pomocí klíčových slov override a new (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, versioning
- C# language, override and new
ms.assetid: 88247d07-bd0d-49e9-a619-45ccbbfdf0c5
ms.openlocfilehash: 2a6a6f59320d94cf97b1a07448000bd708d95559
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33327548"
---
# <a name="versioning-with-the-override-and-new-keywords-c-programming-guide"></a>Správa verzí pomocí klíčových slov override a new (Průvodce programováním v C#)
Jazyka C# je navržen tak, aby Správa verzí mezi [základní](../../../csharp/language-reference/keywords/base.md) a odvozené třídy v různé knihovny můžete vyvíjet a zachování zpětné kompatibility. To znamená, například, že zavedení nového člena v na základní [třída](../../../csharp/language-reference/keywords/class.md) se stejným názvem jako člen v odvozené třídě je zcela podporované v jazyce C# a nevede k neočekávanému chování. Taky to znamená, že třídu musí explicitně stavu zda metoda je určena k přepsání zděděnou metodu, nebo zda je metoda nové metodu, která skryje s podobným názvem zděděna metoda.  
  
 V jazyce C# odvozené třídy může obsahovat metody se stejným názvem jako metody třídy base.  
  
-   Metoda základní třídy musí být definován [virtuální](../../../csharp/language-reference/keywords/virtual.md).  
  
-   Pokud metoda v odvozené třídě nepředchází [nové](../../../csharp/language-reference/keywords/new.md) nebo [přepsat](../../../csharp/language-reference/keywords/override.md) klíčová slova, kompilátor vydá upozornění a metodu budou chovat jako kdyby `new` – klíčové slovo nebyly nalezeny.  
  
-   Pokud metoda v odvozené třídě předchází `new` – klíčové slovo, metoda je definován jako je nezávislé na metodu v základní třídě.  
  
-   Pokud metoda v odvozené třídě předchází `override` – klíčové slovo, objekty odvozené třídy bude volat tuto metodu místo metody třídy base.  
  
-   Základní třída metodu lze volat z v odvozené třídě pomocí `base` – klíčové slovo.  
  
-   `override`, `virtual`, A `new` klíčová slova lze použít také k vlastnostem, indexery a události.  
  
 Ve výchozím nastavení nejsou virtuální metody C#. Pokud metoda je deklarován jako virtuální, všechny třídu, která dědí metodu můžete implementovat vlastní verzi. Chcete-li metodu virtuální, `virtual` modifikátor se používá v deklaraci metoda základní třídy. Odvozené třídy lze přepsat metodu základní virtuální pak pomocí `override` – klíčové slovo nebo skrýt virtuální metody v základní třídě. pomocí `new` – klíčové slovo. Pokud `override` – klíčové slovo ani `new` je zadané klíčové slovo, kompilátor vydá upozornění a metoda v odvozené třídě skryje metodu v základní třídě.  
  
 Ukazuje to v praxi, předpokládá na chvíli společnosti A má vytvořený třídy s názvem `GraphicsClass`, který program používá. Toto je `GraphicsClass`:  
  
 [!code-csharp[csProgGuideInheritance#27](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_1.cs)]  
  
 Vaše společnost používá tuto třídu a můžete použít k odvození vlastní třídu přidání nové metody:  
  
 [!code-csharp[csProgGuideInheritance#28](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_2.cs)]  
  
 Aplikace se používá bez problémů, dokud společnosti A uvolní novou verzi `GraphicsClass`, která se podobá následující kód:  
  
 [!code-csharp[csProgGuideInheritance#29](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_3.cs)]  
  
 Nové verze `GraphicsClass` nyní obsahuje metodu s názvem `DrawRectangle`. Na začátku nedojde k žádné akci. Nová verze je stále binární kompatibilní s předchozí verzi aplikace. Veškerý software, který jste nasadili se bude nadále fungovat, i v případě, že nová třída je nainstalován na těchto počítačích. Všechny existující volání do metody `DrawRectangle` budou dál odkazovat vaší verzí v odvozené třídě.  
  
 Ale co nejdříve překompilovat vaší aplikace pomocí nové verze `GraphicsClass`, zobrazí se upozornění z kompilátoru CS0108. Toto upozornění vás upozorní, že budete muset zvážit, jakým způsobem chcete vaší `DrawRectangle` metoda chovat ve vaší aplikaci.  
  
 Pokud chcete metodu přepsat metodu nové základní třídy, použijte `override` – klíčové slovo:  
  
 [!code-csharp[csProgGuideInheritance#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_4.cs)]  
  
 `override` – Klíčové slovo zajišťuje, že všechny objekty odvozené od `YourDerivedGraphicsClass` bude používat verzi odvozené třídy `DrawRectangle`. Odvozené objekty z `YourDerivedGraphicsClass` pořád přístup k základní třída verzi `DrawRectangle` pomocí base – klíčové slovo:  
  
 [!code-csharp[csProgGuideInheritance#44](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_5.cs)]  
  
 Pokud nechcete, aby se vaše metoda přepsat metodu nové základní třídy, platí následující aspekty. Aby nedocházelo k záměně mezi tyto dvě metody, můžete přejmenovat metodu. To může být zvlášť zdlouhavé a náchylné a právě není praktické v některých případech. Pokud váš projekt je poměrně malý, můžete přejmenovat metodu můžete použít možnosti Refactoring Visual Studio. Další informace najdete v tématu [refaktoring tříd a typů (návrhář tříd)](/visualstudio/ide/refactoring-classes-and-types-class-designer).  
  
 Alternativně můžete zabránit upozornění pomocí klíčového slova `new` v definici vaší odvozené třídy:  
  
 [!code-csharp[csProgGuideInheritance#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_6.cs)]  
  
 Pomocí `new` – klíčové slovo říká kompilátoru, že vaše definice skryje definici, který je obsažen v základní třídě. Toto je výchozí chování.  
  
## <a name="override-and-method-selection"></a>Přepsání a výběr metody  
 Když metoda názvem třídy, kompilátor jazyka C# vybere nejlepší metody zavolat, když je více než jedna metoda kompatibilní s volání, jako když existují dvě metody se stejným názvem a parametry, které jsou kompatibilní s Předaný parametr. Kompatibilní by byly následující metody:  
  
 [!code-csharp[csProgGuideInheritance#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_7.cs)]  
  
 Když `DoWork` se volá na instanci `Derived`, kompilátor jazyka C# se nejdřív pokusí použít, může volat kompatibilní s verzemi systému `DoWork` původně deklarovaná u `Derived`. Přepsání metody nejsou považované za deklarovaných na třídu, jsou nové implementace metody deklarovaný na základní třídě. Pouze v případě, že kompilátor jazyka C# se nemůže shodovat volání metody pro metodu původní na `Derived` se pokusí k přiřazení volání pro metodu přepsaného se stejným názvem a kompatibilní parametry. Příklad:  
  
 [!code-csharp[csProgGuideInheritance#33](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_8.cs)]  
  
 Protože proměnnou `val` lze převést na datový typ double implicitně, volání kompilátoru C# `DoWork(double)` místo `DoWork(int)`. Existují dva způsoby, abyste tomu předešli. Vyhněte se nejprve deklarace nové metody se stejným názvem jako virtuální metody. Druhý, můžete určit, aby kompilátor jazyka C# k volání metody virtuální tím, že v seznamu metoda základní třída hledat přetypování instanci `Derived` k `Base`. Vzhledem k tomu, že je metoda virtuální, provádění `DoWork(int)` na `Derived` bude volána. Příklad:  
  
 [!code-csharp[csProgGuideInheritance#34](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_9.cs)]  
  
 Další příklady `new` a `override`, najdete v části [zároveň budete vědět, při použití přepsání a nová klíčová slova](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [Dědičnost](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
