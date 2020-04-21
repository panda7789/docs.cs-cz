---
title: Použití oborů názvů – programovací příručka jazyka C#
ms.date: 07/20/2015
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
ms.openlocfilehash: b4326be8c9e299a96477096ec21864ec69037abe
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738248"
---
# <a name="using-namespaces-c-programming-guide"></a>Použití oborů názvů (Programovací příručka Jazyka C#)

Obory názvů jsou v rámci programů jazyka C# používány dvěma způsoby. Za prvé, třídy rozhraní .NET Framework používají prostory názvů k uspořádání mnoha tříd. Za druhé deklarování vlastní chodů názvů může pomoci řídit rozsah názvů tříd a metod ve větších programovacích projektech.  
  
## <a name="accessing-namespaces"></a>Přístup k oborům názvů

 Většina aplikací Jazyka C# `using` začíná částí direktiv. V této části jsou uvedeny obory názvů, které bude aplikace často používat, a programátor ovi ušetří zadání plně kvalifikovaného názvu při každém použití metody, která je obsažena v aplikaci.  
  
 Například zahrnutím řádku:  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 Na začátku programu může programátor použít kód:  
  
 [!code-csharp[csProgGuide#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#31)]  
  
 Namísto:  
  
 [!code-csharp[csProgGuide#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#30)]  
  
## <a name="namespace-aliases"></a>Aliasy oboru názvů

 [ `using` Direktivu](../../language-reference/keywords/using-directive.md) můžete také použít k vytvoření aliasu pro obor názvů. [Kvalifikátor `::` aliasu oboru názvů](../../language-reference/operators/namespace-alias-qualifier.md) použijte pro přístup k členům aliasového oboru názvů. Následující příklad ukazuje, jak vytvořit a použít alias oboru názvů:
  
[!code-csharp[csProgGuideNamespaces#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#5)]
  
## <a name="using-namespaces-to-control-scope"></a>Použití oborů názvů k řízení oboru

 Klíčové `namespace` slovo se používá k deklarování oboru. Možnost vytvářet obory v rámci projektu pomáhá organizovat kód a umožňuje vytvářet globálně jedinečné typy. V následujícím příkladu je `SampleClass` třída s názvem definována ve dvou oborech názvů, jeden vnořený uvnitř druhého. [ `.` Token](../../language-reference/operators/member-access-operators.md#member-access-expression-) se používá k rozlišení, která metoda se nazývá.  
  
 [!code-csharp[csProgGuideNamespaces#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#8)]  
  
## <a name="fully-qualified-names"></a>Plně kvalifikované názvy

 Obory názvů a typy mají jedinečné názvy popsané plně kvalifikovanými názvy, které označují logickou hierarchii. Například příkaz `A.B` znamená, `A` že je název oboru názvů `B` nebo typu a je vnořen uvnitř něj.  
  
 V následujícím příkladu jsou vnořené třídy a obory názvů. Plně kvalifikovaný název je uveden jako komentář za každou entitou.  
  
 [!code-csharp[csProgGuideNamespaces#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#9)]  
  
 V předchozím segmentu kódu:  
  
- Obor názvů `N1` je členem globálního oboru názvů. Jeho plně kvalifikovaný `N1`název je .  
  
- Obor názvů `N2` je členem `N1`společnosti . Jeho plně kvalifikovaný `N1.N2`název je .  
  
- Třída `C1` je členem `N1`. Jeho plně kvalifikovaný `N1.C1`název je .  
  
- Název `C2` třídy se používá dvakrát v tomto kódu. Plně kvalifikované názvy jsou však jedinečné. První instance `C2` je deklarována uvnitř `C1`; proto je jeho plně `N1.C1.C2`kvalifikovaný název: . Druhá instance `C2` je deklarována uvnitř oboru názvů `N2`; proto je `N1.N2.C2`jeho plně kvalifikovaný název .  
  
 Pomocí předchozího segmentu kódu můžete do `C3`oboru `N1.N2` názvů přidat nového člena třídy:  
  
 [!code-csharp[csProgGuideNamespaces#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#10)]  
  
 Obecně použijte [kvalifikátor `::` aliasu oboru názvů](../../language-reference/operators/namespace-alias-qualifier.md) k odkazování na `.` alias oboru názvů nebo `global::` k odkazování na globální obor názvů a ke kvalifikaci typů nebo členů.  
  
 Je chyba použít `::` s alias, který odkazuje na typ namísto oboru názvů. Příklad:  
  
 [!code-csharp[csProgGuideNamespaces#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#11)]  
  
 [!code-csharp[csProgGuideNamespaces#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#12)]  
  
 Nezapomeňte, že `global` slovo není předdefinovaný alias; `global.X` proto nemá žádný zvláštní význam. Zvláštní význam získává pouze v případě, `::`že se používá s .  
  
 Upozornění kompilátoru CS0440 je generováno, `global::` pokud definujete alias s názvem global, protože vždy odkazuje na globální obor názvů a nikoli na alias. Například následující řádek generuje upozornění:  
  
 [!code-csharp[csProgGuideNamespaces#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#13)]  
  
 Použití `::` s aliasy je dobrý nápad a chrání před neočekávaným zavedením dalších typů. Zvažte například tento příklad:  
  
 [!code-csharp[csProgGuideNamespaces#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#14)]  
  
 [!code-csharp[csProgGuideNamespaces#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#15)]  
  
 To funguje, ale pokud `Alias` typ s názvem byly `Alias.` následně zavedeny, by se vázat na tento typ místo. Použití `Alias::Exception` zajišťuje, `Alias` že je považován za alias oboru názvů a není zaměněn za typ.  

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Jmenné prostory](./index.md)
- [Výraz přístupu člena](../../language-reference/operators/member-access-operators.md#member-access-expression-)
- [:: – operátor](../../language-reference/operators/namespace-alias-qualifier.md)
- [externí alias](../../language-reference/keywords/extern-alias.md)
