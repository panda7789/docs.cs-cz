---
title: Použití oboru názvů (Průvodce programováním v C#)
ms.date: 07/20/2015
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
ms.openlocfilehash: 773add221317a2154ac620acf766607ec22c629d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="using-namespaces-c-programming-guide"></a>Použití oboru názvů (Průvodce programováním v C#)
Obory názvů jsou nejčastěji používá v rámci programy C# dvěma způsoby. Za prvé tříd rozhraní .NET Framework použít obory názvů k uspořádání jeho mnoho tříd. Za druhé deklarace vlastní oborů názvů umožňují omezit rozsah třídy a metody názvy v projektech větší programování.  
  
## <a name="accessing-namespaces"></a>Přístup k obory názvů  
 Většina aplikací v C# začínat oddíl `using` direktivy. Tato část uvádí obory názvů, že aplikace budou často používat a uloží programátorů zadat pokaždé, když se používá metoda, která je obsažená v plně kvalifikovaný název.  
  
 Například zahrnutím řádku:  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_1.cs)]  
  
 Při spuštění programu můžete použít programátorů kód:  
  
 [!code-csharp[csProgGuide#31](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_2.cs)]  
  
 Namísto:  
  
 [!code-csharp[csProgGuide#30](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_3.cs)]  
  
## <a name="namespace-aliases"></a>Namespace aliasy  
 [Using – direktiva](../../../csharp/language-reference/keywords/using-directive.md) lze také použít k vytvoření zástupce pro [obor názvů](../../../csharp/language-reference/keywords/namespace.md). Pokud používáte dříve napsané obor názvů, který obsahuje vnořené obory názvů, můžete chtít deklarovat alias zajistit zjednodušený způsob jeden odkazující na konkrétní jako v následujícím příkladu:  
  
 [!code-csharp[csProgGuideNamespaces#7](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_4.cs)]  
  
## <a name="using-namespaces-to-control-scope"></a>Použití oboru názvů do oboru ovládacího prvku  
 `namespace` – Klíčové slovo se používá k deklaraci oboru. Schopnost vytvářet oborů v rámci projektu pomáhá uspořádat kódu a umožňuje vytvořit globálně jedinečné typy. V následujícím příkladu třída s názvem `SampleClass` je definována v dva obory názvů, jeden vnořený do druhého. [. Operátor](../../../csharp/language-reference/operators/member-access-operator.md) se používá k rozlišení, které metoda je volána.  
  
 [!code-csharp[csProgGuideNamespaces#8](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_5.cs)]  
  
## <a name="fully-qualified-names"></a>Plně kvalifikované názvy  
 Obory názvů a typy mít jedinečné názvy, které jsou popsané ve plně kvalifikované názvy, které označují logické hierarchie. Například příkaz `A.B` vyplývá, že `A` je název oboru názvů nebo typu, a `B` je vnořit.  
  
 V následujícím příkladu jsou vnořené třídy a obory názvů. Plně kvalifikovaný název je označen jako komentář následující každé entity.  
  
 [!code-csharp[csProgGuideNamespaces#9](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_6.cs)]  
  
 V předchozí segment kódu:  
  
-   Obor názvů `N1` je členem globální obor názvů. Je plně kvalifikovaným názvem `N1`.  
  
-   Obor názvů `N2` je členem `N1`. Je plně kvalifikovaným názvem `N1.N2`.  
  
-   Třída `C1` je členem `N1`. Je plně kvalifikovaným názvem `N1.C1`.  
  
-   Název třídy `C2` dvakrát se používá v tomto kódu. Plně kvalifikované názvy jsou však jedinečný. První instance `C2` je deklarovaná uvnitř `C1`; proto je plně kvalifikovaným názvem: `N1.C1.C2`. Druhou instanci `C2` je deklarovaná uvnitř oboru názvů `N2`; proto je plně kvalifikovaným názvem `N1.N2.C2`.  
  
 Pomocí předchozího segmentu kódu, můžete přidat nového člena třídy `C3`, do oboru názvů `N1.N2` následujícím způsobem:  
  
 [!code-csharp[csProgGuideNamespaces#10](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_7.cs)]  
  
 Obecně platí, použijte `::` tak, aby odkazovaly alias oboru názvů nebo `global::` tak, aby odkazovaly na globální obor názvů a `.` ke kvalifikaci typy nebo členy.  
  
 Jedná se o chybu používat `::` s alias, který odkazuje na typ místo obor názvů. Příklad:  
  
 [!code-csharp[csProgGuideNamespaces#11](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_8.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#12](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_9.cs)]  
  
 Nezapomeňte, že slovo `global` není i předdefinovanou alias; proto `global.X` nemá žádný speciální význam. Operace čtení, zvláštní význam jenom v případě, že se používá s `::`.  
  
 Kompilátoru upozornění CS0440 se vygeneruje, pokud definujete alias s názvem globální protože `global::` vždy odkazuje na obor názvů globální a není alias. Například následující řádek vygeneruje upozornění:  
  
 [!code-csharp[csProgGuideNamespaces#13](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_10.cs)]  
  
 Pomocí `::` s aliasy je vhodné a chrání před neočekávané zavedení další typy. Představte si třeba v tomto příkladu:  
  
 [!code-csharp[csProgGuideNamespaces#14](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_11.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#15](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_12.cs)]  
  
 Tento postup funguje, ale pokud typu s názvem `Alias` měla být následně zavést, `Alias.` by navázat na daný typ místo. Pomocí `Alias::Exception` , tomu se budou `Alias` je považován za alias oboru názvů a není pro typ zaměněny.  
  
 Podívejte se na téma [postupy: použití aliasu globálního Namespace](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) Další informace ohledně `global` alias.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Obory názvů](../../../csharp/programming-guide/namespaces/index.md)  
 [Klíčová slova oboru názvů](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [. – operátor](../../../csharp/language-reference/operators/member-access-operator.md)  
 [:: – operátor](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [extern](../../../csharp/language-reference/keywords/extern.md)
