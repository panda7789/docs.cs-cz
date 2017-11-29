---
title: "Použití konstruktorů (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
caps.latest.revision: "26"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: eb9fcd1e4090da300de17c7fd808669ba51767c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="using-constructors-c-programming-guide"></a>Použití konstruktorů (Průvodce programováním v C#)
Když [– třída](../../../csharp/language-reference/keywords/class.md) nebo [struktura](../../../csharp/language-reference/keywords/struct.md) je vytvořen, se nazývá jeho konstruktoru. Konstruktory mít stejný název jako třídě nebo struktuře a obvykle inicializují datových členů nového objektu.  
  
 V následujícím příkladu třída s názvem `Taxi` se definuje pomocí jednoduchého konstruktor. Tato třída je pak vytvořena s [nové](../../../csharp/language-reference/keywords/new.md) operátor. `Taxi` Se vyvolat konstruktor `new` operátor ihned po paměti je přidělen pro nový objekt.  
  
 [!code-csharp[csProgGuideObjects#53](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_1.cs)]  
  
 Volání konstruktoru, které nepřijímá žádné parametry *výchozí konstruktor*. Výchozí konstruktory jsou vyvolány při každém vytvoření instance objektu pomocí `new` operátor a odpovídající žádné argumenty `new`. Další informace najdete v tématu [konstruktory instancí](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  
  
 Pokud je třída [statické](../../../csharp/language-reference/keywords/static.md), tříd bez konstruktory jsou uvedeny výchozí veřejný konstruktor kompilátorem C#, chcete-li povolit vytváření instance třídy. Další informace najdete v tématu [statické třídy a statické členy třídy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Třídu můžete zabránit ve vytváření instancí tím, že konstruktoru privátní, následujícím způsobem:  
  
 [!code-csharp[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_2.cs)]  
  
 Další informace najdete v tématu [soukromé konstruktory](../../../csharp/programming-guide/classes-and-structs/private-constructors.md).  
  
 Konstruktory pro [struktura](../../../csharp/language-reference/keywords/struct.md) typy vypadat třída konstruktory, ale `structs` nemůže obsahovat explicitní výchozí konstruktor, protože je zadáno automaticky kompilátorem. Tento konstruktor inicializuje každé pole v `struct` na výchozí hodnoty. Další informace najdete v tématu [výchozí hodnoty tabulky](../../../csharp/language-reference/keywords/default-values-table.md). Však tato výchozí konstruktor je volána, pouze pokud `struct` je vytvořena s `new`. Například tento kód používá výchozí konstruktor pro <xref:System.Int32>, takže budete mít jistotu, že je inicializován na celé číslo:  
  
```  
int i = new int();  
Console.WriteLine(i);  
```  
  
 Následující kód, ale způsobí chybu kompilátoru, protože nepoužívá `new`, a protože se pokusí použít objekt, který není inicializovaný.:  
  
```  
int i;  
Console.WriteLine(i);  
```  
  
 Případně na základě objektů `structs` (včetně všech předdefinovaných číselnými typy) může být inicializován nebo přiřadit a pak se použije jako v následujícím příkladu:  
  
```  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 Proto volání výchozí konstruktor pro typ hodnoty se nevyžaduje.  
  
 Obě třídy a `structs` můžete definovat konstruktory, které nepřijímají parametry. Konstruktory, které nepřijímají parametry musí být voláno prostřednictvím `new` příkaz nebo [základní](../../../csharp/language-reference/keywords/base.md) příkaz. Třídy a `structs` můžete také definovat více konstruktory a ani jeden z nich je potřeba definovat výchozí konstruktor. Příklad:  
  
 [!code-csharp[csProgGuideObjects#54](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_3.cs)]  
  
 Tato třída lze vytvořit pomocí některé z následujících příkazů:  
  
 [!code-csharp[csProgGuideObjects#55](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_4.cs)]  
  
 Můžete použít konstruktor `base` – klíčové slovo volat konstruktor základní třídy. Příklad:  
  
 [!code-csharp[csProgGuideObjects#56](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_5.cs)]  
  
 V tomto příkladu v konstruktoru pro základní třídy je volána před provedením blok pro konstruktor. `base` – Klíčové slovo lze použít s nebo bez parametrů. Žádné parametry konstruktoru lze použít jako parametry, které `base`, nebo jako součást výrazu. Další informace najdete v tématu [základní](../../../csharp/language-reference/keywords/base.md).  
  
 V odvozené třídě, pokud konstruktor základní třída není explicitně volána pomocí `base` – klíčové slovo, výchozí konstruktor, pokud existuje, nazývá implicitně. To znamená, že následující konstruktor deklarace jsou efektivně stejné:  
  
 [!code-csharp[csProgGuideObjects#58](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_6.cs)]  
  
 [!code-csharp[csProgGuideObjects#57](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_7.cs)]  
  
 Pokud základní třídu nenabízí výchozí konstruktor, odvozené třídy musí být být explicitní volání konstruktoru základní pomocí `base`.  
  
 Konstruktor můžete vyvolat jiný konstruktor pro stejný objekt pomocí [to](../../../csharp/language-reference/keywords/this.md) – klíčové slovo. Jako `base`, `this` lze použít s nebo bez parametrů, a jsou k dispozici jako parametry pro všechny parametry v konstruktoru `this`, nebo jako součást výrazu. Druhý konstruktor v předchozím příkladu může být například přepsán pomocí `this`:  
  
 [!code-csharp[csProgGuideObjects#59](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_8.cs)]  
  
 Použití `this` – klíčové slovo v předchozím příkladu způsobí, že tento konstruktor k volání:  
  
 [!code-csharp[csProgGuideObjects#60](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_9.cs)]  
  
 Může být konstruktory označený jako [veřejné](../../../csharp/language-reference/keywords/public.md), [privátní](../../../csharp/language-reference/keywords/private.md), [chráněné](../../../csharp/language-reference/keywords/protected.md), [interní](../../../csharp/language-reference/keywords/internal.md), [chráněné interní](../../../csharp/language-reference/keywords/protected-internal.md)nebo [privátní chráněné](../../../csharp/language-reference/keywords/private-protected.md). Tyto modifikátory přístupu definovat, jak uživatelé třídy můžete vytvořit třídu. Další informace najdete v tématu [modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Konstruktor lze deklarovat statickou pomocí [statické](../../../csharp/language-reference/keywords/static.md) – klíčové slovo. Statické konstruktory jsou automaticky, volá se bezprostředně před všechny statická pole ke kterým se přistupuje a jsou obecně používány k chybě při inicializaci členové statické třídy. Další informace najdete v tématu [statické konstruktory](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [Finalizační metody](../../../csharp/programming-guide/classes-and-structs/destructors.md)
