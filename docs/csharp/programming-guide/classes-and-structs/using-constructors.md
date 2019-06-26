---
title: Použití konstruktorů - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: 14ff272fe940c265dc8984d6b20985bb2d2ba12d
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2019
ms.locfileid: "67398254"
---
# <a name="using-constructors-c-programming-guide"></a>Použití konstruktorů (Průvodce programováním v C#)

Při [třídy](../../../csharp/language-reference/keywords/class.md) nebo [struktura](../../../csharp/language-reference/keywords/struct.md) je vytvořen, se nazývá konstruktoru. Konstruktory mají stejný název jako třídy nebo struktury a obvykle inicializují datové členy nového objektu.  
  
 V následujícím příkladu třída s názvem `Taxi` je definován pomocí jednoduchého konstruktoru. Tato třída je pak vytvořena s [nové](../../../csharp/language-reference/operators/new-operator.md) operátor. `Taxi` Konstruktor vyvolá `new` je operátor ihned po paměti přidělené pro nový objekt.  
  
 [!code-csharp[csProgGuideObjects#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#53)]  
  
 Je volána konstruktor, který nepřijímá žádné parametry *konstruktor bez parametrů*. Výchozí konstruktory jsou vyvolány při každém objektu je vytvořena instance s použitím `new` operátor a bez argumentů `new`. Další informace najdete v tématu [konstruktory instancí](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  
  
 Pokud je třída [statické](../../../csharp/language-reference/keywords/static.md), třídy bez konstruktory jsou uvedeny veřejný konstruktor bez parametrů podle C# kompilátoru Chcete-li povolit vytváření instance třídy. Další informace najdete v tématu [statické třídy a statické členy třídy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Třída může zabránit před tím, že konstruktor soukromý, následujícím způsobem:  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 Další informace najdete v tématu [soukromé konstruktory](../../../csharp/programming-guide/classes-and-structs/private-constructors.md).  
  
 Konstruktory pro [struktura](../../../csharp/language-reference/keywords/struct.md) typy vypadat podobně jako konstruktor třídy, ale `structs` nemůžou obsahovat explicitní konstruktor bez parametrů, protože je automaticky zadáno kompilátorem. Tento konstruktor inicializuje každé pole v `struct` na výchozí hodnoty. Další informace najdete v tématu [výchozí hodnoty tabulky](../../../csharp/language-reference/keywords/default-values-table.md). Nicméně, tento konstruktor je vyvolána pouze v případě `struct` je vytvořena instance s `new`. Například tento kód používá konstruktor bez parametrů <xref:System.Int32>, takže budete mít jistotu, že je inicializován na celé číslo:  
  
```csharp  
int i = new int();  
Console.WriteLine(i);  
```  
  
 Následující kód, ale způsobí chybu kompilátoru, protože nepoužívá `new`, a protože se pokusí použít objekt, který není inicializovaná:  
  
```  
int i;  
Console.WriteLine(i);  
```  
  
 Můžete také na základě objektů `structs` (včetně všech předdefinovaných číselných typů) může být inicializována nebo přiřazena a pak použít jako v následujícím příkladu:  
  
```  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 Proto volání konstruktoru bez parametrů typu hodnoty se nevyžaduje.  
  
 Obě třídy a `structs` můžete definovat konstruktory, které přijímají parametry. Konstruktory, které přijímají parametry musí být volána až `new` příkaz nebo [základní](../../../csharp/language-reference/keywords/base.md) příkazu. Třídy a `structs` můžete také definovat víc konstruktorů a ani je potřeba definovat konstruktor bez parametrů. Příklad:  
  
 [!code-csharp[csProgGuideObjects#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#54)]  
  
 Tuto třídu lze vytvořit pomocí některého z následujících příkazů:  
  
 [!code-csharp[csProgGuideObjects#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#55)]  
  
 Můžete použít konstruktor `base` – klíčové slovo volat konstruktor základní třídy. Příklad:  
  
 [!code-csharp[csProgGuideObjects#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#56)]  
  
 V tomto příkladu je volána konstruktor základní třídy před provedením blok pro konstruktor. `base` – Klíčové slovo lze použít s nebo bez parametrů. Žádné parametry pro konstruktor může sloužit jako parametry pro `base`, nebo jako součást výrazu. Další informace najdete v tématu [základní](../../../csharp/language-reference/keywords/base.md).  
  
 V odvozené třídě, pokud není explicitně volána konstruktor základní třídy pomocí `base` – klíčové slovo, konstruktor bez parametrů, pokud existuje, nazývá implicitně. To znamená, že následující deklarace konstruktoru se prakticky neliší:  
  
 [!code-csharp[csProgGuideObjects#58](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#58)]  
  
 [!code-csharp[csProgGuideObjects#57](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#57)]  
  
 Pokud základní třída se nebude poskytovat konstruktor bez parametrů, odvozené třídy musí provést explicitní volání konstruktoru základní konstruktor pomocí `base`.  
  
 Konstruktor může vyvolat jiný konstruktor ve stejném objektu pomocí [to](../../../csharp/language-reference/keywords/this.md) – klíčové slovo. Stejně jako `base`, `this` lze použít s nebo bez parametrů, a jsou k dispozici jako parametry pro všechny parametry v konstruktoru `this`, nebo jako součást výrazu. Například, druhý konstruktor v předchozím příkladu může být přepsán pomocí `this`:  
  
 [!code-csharp[csProgGuideObjects#59](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#59)]  
  
 Použití `this` – klíčové slovo v předchozím příkladu způsobí, že tento konstruktor k volání:  
  
 [!code-csharp[csProgGuideObjects#60](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#60)]  
  
 Konstruktory mohou být označeny jako [veřejné](../../../csharp/language-reference/keywords/public.md), [privátní](../../../csharp/language-reference/keywords/private.md), [chráněné](../../../csharp/language-reference/keywords/protected.md), [interní](../../../csharp/language-reference/keywords/internal.md), [chráněné vnitřní](../../../csharp/language-reference/keywords/protected-internal.md)nebo [private, protected](../../../csharp/language-reference/keywords/private-protected.md). Tyto modifikátory přístupu definují, jak uživatelé třídy můžete vytvořit třídu. Další informace najdete v tématu [modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Konstruktor může být deklarované jako statické pomocí [statické](../../../csharp/language-reference/keywords/static.md) – klíčové slovo. Statické konstruktory jsou automaticky, volá se bezprostředně před všechny statické pole jsou přístupné a obvykle slouží k inicializaci statické členy třídy. Další informace najdete v tématu [statické konstruktory](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  

Další informace najdete v tématu [Instance konstruktory](~/_csharplang/spec/classes.md#instance-constructors) a [statické konstruktory](~/_csharplang/spec/classes.md#static-constructors) v [ C# specifikace jazyka](../../language-reference/language-specification/index.md). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [Finalizační metody](../../../csharp/programming-guide/classes-and-structs/destructors.md)
