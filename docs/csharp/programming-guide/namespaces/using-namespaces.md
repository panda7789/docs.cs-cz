---
title: Používání oborů názvů C# – Průvodce programováním
ms.date: 07/20/2015
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
ms.openlocfilehash: 5193fc7aaae83cbc0c75e81835244eaaaece69a5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75700195"
---
# <a name="using-namespaces-c-programming-guide"></a>Používání oborů názvůC# (Průvodce programováním)

Obory názvů jsou v C# rámci programů silně používány dvěma způsoby. Nejprve třídy .NET Framework používají obory názvů k uspořádání svých mnoha tříd. Následně deklarace vlastních oborů názvů vám může pomáhat řídit obor názvů tříd a metod ve větších programovacích projektech.  
  
## <a name="accessing-namespaces"></a>Přístup k oborům názvů

 Většina C# aplikací začíná oddílem direktiv `using`. V této části jsou uvedeny obory názvů, které aplikace často používá, a uloží programátora z určení plně kvalifikovaného názvu pokaždé, když se použije metoda, která je obsažena v rámci.  
  
 Například zahrnutím řádku:  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 Na začátku programu může programátor použít kód:  
  
 [!code-csharp[csProgGuide#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#31)]  
  
 Namísto:  
  
 [!code-csharp[csProgGuide#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#30)]  
  
## <a name="namespace-aliases"></a>Aliasy oboru názvů

 Můžete také použít [direktivu`using`](../../language-reference/keywords/using-directive.md) pro vytvoření aliasu pro obor názvů. Pro přístup ke členům oboru názvů s aliasy použijte [kvalifikátor aliasu oboru názvů `::`](../../language-reference/operators/namespace-alias-qualifier.md) . Následující příklad ukazuje, jak vytvořit a použít alias oboru názvů:
  
[!code-csharp[csProgGuideNamespaces#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#5)]
  
## <a name="using-namespaces-to-control-scope"></a>Použití oborů názvů k řízení oboru

 Klíčové slovo `namespace` slouží k deklaraci oboru. Schopnost vytvářet obory v rámci projektu pomáhá organizovat kód a umožňuje vytvářet globálně jedinečné typy. V následujícím příkladu je třída s názvem `SampleClass` definovaná ve dvou oborech názvů, jedna vnořená uvnitř druhé. [Operátor přístupu členů `.`](../../language-reference/operators/member-access-operators.md#member-access-operator-) slouží k odlišení, která metoda se volá.  
  
 [!code-csharp[csProgGuideNamespaces#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#8)]  
  
## <a name="fully-qualified-names"></a>Plně kvalifikované názvy

 Obory názvů a typy mají jedinečné názvy, které popisují plně kvalifikované názvy, které označují logickou hierarchii. Například příkaz `A.B` znamená, že `A` je název oboru názvů nebo typu a `B` je vnořen uvnitř něj.  
  
 V následujícím příkladu jsou vnořené třídy a obory názvů. Plně kvalifikovaný název je označen jako komentář za každou entitou.  
  
 [!code-csharp[csProgGuideNamespaces#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#9)]  
  
 V předchozím segmentu kódu:  
  
- Obor názvů `N1` je členem globálního oboru názvů. Jeho plně kvalifikovaný název je `N1`.  
  
- Obor názvů `N2` je členem `N1`. Jeho plně kvalifikovaný název je `N1.N2`.  
  
- `C1` třídy je členem `N1`. Jeho plně kvalifikovaný název je `N1.C1`.  
  
- Název třídy `C2` se v tomto kódu používá dvakrát. Plně kvalifikované názvy jsou ale jedinečné. První instance `C2` je deklarována uvnitř `C1`; Proto je jeho plně kvalifikovaný název: `N1.C1.C2`. Druhá instance `C2` je deklarována uvnitř oboru názvů `N2`; Proto je jeho plně kvalifikovaný název `N1.N2.C2`.  
  
 Pomocí předchozího segmentu kódu můžete přidat nový člen třídy `C3`do oboru názvů `N1.N2` následujícím způsobem:  
  
 [!code-csharp[csProgGuideNamespaces#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#10)]  
  
 Obecně použijte [kvalifikátor aliasu oboru názvů `::`](../../language-reference/operators/namespace-alias-qualifier.md) pro odkazování na alias oboru názvů nebo `global::` pro odkazování na globální obor názvů a `.` k zařazování typů nebo členů.  
  
 Použití `::` s aliasem, který odkazuje na typ namísto oboru názvů, je chyba. Příklad:  
  
 [!code-csharp[csProgGuideNamespaces#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#11)]  
  
 [!code-csharp[csProgGuideNamespaces#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#12)]  
  
 Pamatujte, že slovo `global` není předdefinovaným aliasem. Proto `global.X` nemá žádný zvláštní význam. Získá zvláštní význam pouze v případě, že se používá s `::`.  
  
 Při definování aliasu s názvem Global se vygeneruje upozornění kompilátoru CS0440, protože `global::` vždycky odkazuje na globální obor názvů, ne na alias. Například následující řádek vygeneruje upozornění:  
  
 [!code-csharp[csProgGuideNamespaces#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#13)]  
  
 Použití `::` s aliasy je dobrý nápad a chrání proti neočekávanému zavedení dalších typů. Zvažte například tento příklad:  
  
 [!code-csharp[csProgGuideNamespaces#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#14)]  
  
 [!code-csharp[csProgGuideNamespaces#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#15)]  
  
 Tento postup funguje, ale pokud byl následně zaveden typ s názvem `Alias`, `Alias.` by se místo toho naváže k tomuto typu. Pomocí `Alias::Exception` zajistí, že `Alias` je považován za alias oboru názvů a nemusíte ho označit pro typ.  

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Obory názvů](./index.md)
- [. podnikatel](../../language-reference/operators/member-access-operators.md#member-access-operator-)
- [:: – operátor](../../language-reference/operators/namespace-alias-qualifier.md)
- [extern alias](../../language-reference/keywords/extern-alias.md)
