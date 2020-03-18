---
title: Použití konstruktorů – programovací příručka Jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: 7c227b61c6d5b4ead00fced0dba046b90683fde1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626409"
---
# <a name="using-constructors-c-programming-guide"></a>Použití konstruktorů (Průvodce programováním v C#)

Při vytvoření [třídy](../../language-reference/keywords/class.md) nebo [struktury](../../language-reference/builtin-types/struct.md) je volána její konstruktor. Konstruktory mají stejný název jako třída nebo struktura a obvykle inicializují datové členy nového objektu.  
  
 V následujícím příkladu je `Taxi` třída s názvem definována pomocí jednoduchého konstruktoru. Tato třída je pak vytvořena s [novým](../../language-reference/operators/new-operator.md) operátorem. Konstruktor `Taxi` je vyvolán operátorem `new` ihned po přidělení paměti pro nový objekt.  
  
 [!code-csharp[csProgGuideObjects#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#53)]  
  
 Konstruktor, který nepřijímá žádné parametry, se nazývá *konstruktor bez parametrů*. Konstruktory bez parametrů jsou vyvolány vždy, když je `new` objekt vytvořen pomocí operátoru `new`a žádné argumenty jsou k dispozici . Další informace naleznete v tématu [Instance Constructors](./instance-constructors.md).  
  
 Pokud třída není [statická](../../language-reference/keywords/static.md), třídy bez konstruktorů jsou uvedeny veřejné konstruktor bez parametrů kompilátorem C# za účelem povolení instance třídy. Další informace naleznete [v tématu Statické třídy a statické členy třídy](./static-classes-and-static-class-members.md).  
  
 Můžete zabránit vytvoření instance třídy tím, že konstruktor uvažuje takto:  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 Další informace naleznete [v tématu Private Constructors](./private-constructors.md).  
  
 Konstruktory pro [typy struktury](../../language-reference/builtin-types/struct.md) se podobají konstruktorům třídy, ale `structs` nemohou obsahovat explicitní konstruktor bez parametrů, protože je automaticky poskytován kompilátorem. Tento konstruktor inicializuje každé `struct` pole v [na výchozí hodnotu](../../language-reference/builtin-types/default-values.md). Tento konstruktor bez parametrů je však `struct` vyvolána pouze `new`v případě, že je vytvořena instance s . Například tento kód používá konstruktor <xref:System.Int32>bez parametrů pro , takže máte jistotu, že celé číslo je inicializováno:  
  
```csharp  
int i = new int();  
Console.WriteLine(i);  
```  
  
 Následující kód však způsobí chybu kompilátoru, `new`protože nepoužívá , a protože se pokusí použít objekt, který nebyl inicializován:  
  
```csharp  
int i;  
Console.WriteLine(i);  
```  
  
 Alternativně objekty `structs` založené na (včetně všech vestavěných číselných typů) mohou být inicializovány nebo přiřazeny a poté použity jako v následujícím příkladu:  
  
```csharp  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 Takže volání konstruktoru bez parametrů pro typ hodnoty není vyžadováno.  
  
 Obě třídy a `structs` můžete definovat konstruktory, které berou parametry. Konstruktory, které berou parametry, `new` musí být volány prostřednictvím příkazu nebo [základního](../../language-reference/keywords/base.md) příkazu. Třídy `structs` a můžete také definovat více konstruktorů a ani je nutné definovat konstruktor bez parametrů. Například:  
  
 [!code-csharp[csProgGuideObjects#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#54)]  
  
 Tuto třídu lze vytvořit pomocí některého z následujících příkazů:  
  
 [!code-csharp[csProgGuideObjects#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#55)]  
  
 Konstruktor můžete použít `base` klíčové slovo volat konstruktor základní třídy. Například:  
  
 [!code-csharp[csProgGuideObjects#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#56)]  
  
 V tomto příkladu je konstruktor pro základní třídu volán před spuštěním bloku pro konstruktor. Klíčové `base` slovo lze použít s parametry nebo bez něj. Všechny parametry konstruktoru lze použít jako `base`parametry pro nebo jako součást výrazu. Další informace naleznete v [tématu base](../../language-reference/keywords/base.md).  
  
 V odvozené třídě, pokud konstruktor základní třídy není `base` explicitně volána pomocí klíčového slova, konstruktor bez parametrů, pokud existuje, je volán implicitně. To znamená, že následující deklarace konstruktoru jsou účinně stejné:  
  
 [!code-csharp[csProgGuideObjects#58](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#58)]  
  
 [!code-csharp[csProgGuideObjects#57](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#57)]  
  
 Pokud základní třída nenabízí konstruktor bez parametrů, odvozené třídy musí explicitní volání `base`základní konstruktor pomocí .  
  
 Konstruktor může vyvolat jiný konstruktor ve stejném objektu pomocí klíčového slova [This.](../../language-reference/keywords/this.md) Stejně jako `base`, `this` lze použít s nebo bez parametrů a všechny parametry `this`v konstruktoru jsou k dispozici jako parametry pro , nebo jako součást výrazu. Například druhý konstruktor v předchozím příkladu lze `this`přepsat pomocí :  
  
 [!code-csharp[csProgGuideObjects#59](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#59)]  
  
 Použití klíčového `this` slova v předchozím příkladu způsobí, že tento konstruktor se nazývá:  
  
 [!code-csharp[csProgGuideObjects#60](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#60)]  
  
 Konstruktory mohou být označeny jako [veřejné](../../language-reference/keywords/public.md), [soukromé](../../language-reference/keywords/private.md), [chráněné](../../language-reference/keywords/protected.md), [interní](../../language-reference/keywords/internal.md), [chráněné vnitřní](../../language-reference/keywords/protected-internal.md) nebo soukromé [chráněné](../../language-reference/keywords/private-protected.md). Tyto modifikátory přístupu definují, jak mohou uživatelé třídy vytvořit třídu. Další informace naleznete [v tématu Access Modifiers](./access-modifiers.md).  
  
 Konstruktor lze deklarovat statické pomocí [statické](../../language-reference/keywords/static.md) klíčové slovo. Statické konstruktory jsou volány automaticky, bezprostředně před všechny statická pole jsou přístupné a obecně se používají k inicializaci statické členy třídy. Další informace naleznete [v tématu Statické konstruktory](./static-constructors.md).  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  

Další informace naleznete [v tématu instance konstruktory](~/_csharplang/spec/classes.md#instance-constructors) a [statické konstruktory](~/_csharplang/spec/classes.md#static-constructors) ve [specifikaci jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Třídy a struky](./index.md)
- [Konstruktory](./constructors.md)
- [Finalizační metody](./destructors.md)
