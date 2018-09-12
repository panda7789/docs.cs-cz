---
title: Použití oboru názvů (Průvodce programováním v C#)
ms.date: 07/20/2015
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
ms.openlocfilehash: 81876d1818a6e82764e4aea0ae2b6f9e091f0ba3
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44699891"
---
# <a name="using-namespaces-c-programming-guide"></a>Použití oboru názvů (Průvodce programováním v C#)
V aplikacích jazyka C# dvě možnosti, jak se hojně používají obory názvů. Za prvé tříd rozhraní .NET Framework pomocí oborů názvů můžete organizovat jeho mnoho tříd. Za druhé deklarující vlastní obory názvů umožňují omezit rozsah třídy a metody názvy ve větších programovací projektů.  
  
## <a name="accessing-namespaces"></a>Přístup k obory názvů  
 Většina aplikací C# začínat část `using` direktivy. Tato část obsahuje seznam oborů názvů, že aplikace budou často používat a ušetří programátor zadáním plně kvalifikovaného názvu pokaždé, když se používá metodu, která je součástí.  
  
 Například přidáním řádku:  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_1.cs)]  
  
 Na začátku programu můžete použít programátor kód:  
  
 [!code-csharp[csProgGuide#31](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_2.cs)]  
  
 Namísto:  
  
 [!code-csharp[csProgGuide#30](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_3.cs)]  
  
## <a name="namespace-aliases"></a>Aliasy Namespace  
 [Direktiva using](../../../csharp/language-reference/keywords/using-directive.md) lze také použít k vytvoření zástupce pro [obor názvů](../../../csharp/language-reference/keywords/namespace.md). Pokud používáte doposud zapsán obor názvů, který obsahuje vnořené obory názvů, můžete chtít deklarování aliasu. k poskytování zjednodušený způsob odkazujete na jednu zejména, jako v následujícím příkladu:  
  
 [!code-csharp[csProgGuideNamespaces#7](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_4.cs)]  
  
## <a name="using-namespaces-to-control-scope"></a>Použití oboru názvů do oboru ovládacího prvku  
 `namespace` – Klíčové slovo se používá k deklarování oboru. Schopnost vytvářet oborů v rámci svého projektu pomáhá organizovat kód a umožňuje vytvářet globálně jedinečných typů. V následujícím příkladu třída s názvem `SampleClass` je definována v dva obory názvů, jeden vnořit do druhé. [. Operátor](../../../csharp/language-reference/operators/member-access-operator.md) se používá k rozlišení, které metoda je volána.  
  
 [!code-csharp[csProgGuideNamespaces#8](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_5.cs)]  
  
## <a name="fully-qualified-names"></a>Plně kvalifikované názvy  
 Obory názvů a typy mají jedinečné názvy popsal plně kvalifikované názvy, které indikují logické hierarchie. Například příkaz `A.B` vyplývá, že `A` je název oboru názvů nebo typ, a `B` je vnořená do ho.  
  
 V následujícím příkladu jsou vnořené třídy a obory názvů. Plně kvalifikovaný název je označen jako komentář po každé entity.  
  
 [!code-csharp[csProgGuideNamespaces#9](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_6.cs)]  
  
 V předchozí segment kódu:  
  
-   Obor názvů `N1` je členem skupiny globální obor názvů. Jeho plně kvalifikovaný název je `N1`.  
  
-   Obor názvů `N2` je členem skupiny `N1`. Jeho plně kvalifikovaný název je `N1.N2`.  
  
-   Třída `C1` je členem skupiny `N1`. Jeho plně kvalifikovaný název je `N1.C1`.  
  
-   Název třídy `C2` dvakrát se používá v tomto kódu. Plně kvalifikované názvy jsou však jedinečné. První výskyt `C2` je deklarována uvnitř `C1`, proto jeho plně kvalifikovaný název je: `N1.C1.C2`. Druhou instanci `C2` je deklarován uvnitř oboru názvů `N2`, proto jeho plně kvalifikovaný název je `N1.N2.C2`.  
  
 Pomocí předchozího segmentu kódu, můžete přidat nového člena třídy `C3`, do oboru názvů `N1.N2` následujícím způsobem:  
  
 [!code-csharp[csProgGuideNamespaces#10](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_7.cs)]  
  
 Obecně platí, `::` k odkazování aliasu oboru názvů nebo `global::` k odkazu na globální obor názvů a `.` kvalifikovat typy nebo členy.  
  
 Jedná se o chybu použití `::` s aliasem, který odkazuje na typ místo oboru názvů. Příklad:  
  
 [!code-csharp[csProgGuideNamespaces#11](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_8.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#12](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_9.cs)]  
  
 Nezapomeňte, že slovo `global` alias, proto není i předdefinovanou `global.X` nemá žádný speciální význam. Získá zvláštní význam pouze v případě, že se použije s parametrem `::`.  
  
 Kompilátor varování CS0440 se vygeneruje při definování aliasu s názvem global protože `global::` vždy odkazuje na globální obor názvů, ne na alias. Například následující řádek vygeneruje upozornění:  
  
 [!code-csharp[csProgGuideNamespaces#13](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_10.cs)]  
  
 Pomocí `::` s aliasy je vhodné a chrání před neočekávaným Úvod další typy. Představte si třeba v tomto příkladu:  
  
 [!code-csharp[csProgGuideNamespaces#14](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_11.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#15](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_12.cs)]  
  
 Tento postup funguje, ale pokud typ s názvem `Alias` bylo následně zavést `Alias.` by místo toho vázat k danému typu. Pomocí `Alias::Exception` , která díky `Alias` je považován za aliasu oboru názvů a není pro typ zaměněny.  
  
 Naleznete v tématu [postupy: použití aliasu globálního Namespace](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) Další informace týkající `global` alias.  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Obory názvů](../../../csharp/programming-guide/namespaces/index.md)  
- [Klíčová slova oboru názvů](../../../csharp/language-reference/keywords/namespace-keywords.md)  
- [. – operátor](../../../csharp/language-reference/operators/member-access-operator.md)  
- [:: – operátor](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
- [extern](../../../csharp/language-reference/keywords/extern.md)
