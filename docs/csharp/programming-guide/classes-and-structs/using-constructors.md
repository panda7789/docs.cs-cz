---
title: Použití konstruktorů – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: 6825fbc571d8b08808f14a3f69ffc6f8a1ef048c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596188"
---
# <a name="using-constructors-c-programming-guide"></a>Použití konstruktorů (Průvodce programováním v C#)

Při vytvoření [třídy](../../language-reference/keywords/class.md) nebo [struktury](../../language-reference/keywords/struct.md) se zavolá její konstruktor. Konstruktory mají stejný název jako třída nebo struktura a obvykle inicializují datové členy nového objektu.  
  
 V následujícím příkladu je třída s názvem `Taxi` definována pomocí jednoduchého konstruktoru. Tato třída se pak vytvoří s operátorem [New](../../language-reference/operators/new-operator.md) . Konstruktor je vyvolán `new` operátorem ihned po přidělení paměti pro nový objekt. `Taxi`  
  
 [!code-csharp[csProgGuideObjects#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#53)]  
  
 Konstruktor, který nepřijímá žádné parametry, se nazývá *konstruktor bez parametrů*. Konstruktory bez parametrů jsou vyvolány pokaždé, když je vytvořena instance `new` objektu pomocí operátoru a nejsou k `new`dispozici žádné argumenty. Další informace naleznete v tématu [konstruktory instancí](./instance-constructors.md).  
  
 Pokud třída není [statická](../../language-reference/keywords/static.md), třídy bez konstruktorů mají za účelem povolení vytváření instancí třídy veřejný konstruktor C# bez parametrů. Další informace naleznete v tématu [statické třídy a statické členy třídy](./static-classes-and-static-class-members.md).  
  
 Instanci třídy lze zabránit vytvořením konstruktoru jako soukromého pomocí následujícího postupu:  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 Další informace naleznete v tématu [Soukromé konstruktory](./private-constructors.md).  
  
 Konstruktory pro typy [struktury](../../language-reference/keywords/struct.md) připomínají konstruktory třídy, ale `structs` nemůžou obsahovat explicitní konstruktor bez parametrů, protože jeden je k dispozici automaticky kompilátorem. Tento konstruktor inicializuje každé pole v oblasti `struct` na výchozí hodnoty. Další informace najdete v tématu [Tabulka výchozích hodnot](../../language-reference/keywords/default-values-table.md). Tento konstruktor bez parametrů je však vyvolána pouze v `struct` `new`případě, že je vytvořena instance. Například tento kód používá konstruktor bez parametrů pro <xref:System.Int32>, takže máte jistotu, že je inicializováno celé číslo:  
  
```csharp  
int i = new int();  
Console.WriteLine(i);  
```  
  
 Následující kód ale způsobí chybu kompilátoru, protože nepoužívá `new`a protože se pokouší použít objekt, který nebyl inicializován:  
  
```  
int i;  
Console.WriteLine(i);  
```  
  
 Alternativně lze objekty založené `structs` na (včetně všech předdefinovaných číselných typů) inicializovat nebo přiřadit a pak použít jako v následujícím příkladu:  
  
```  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 Proto není požadováno volání konstruktoru bez parametrů pro typ hodnoty.  
  
 Obě třídy i `structs` mohou definovat konstruktory, které přijímají parametry. Konstruktory, které přijímají parametry, musí být `new` volány prostřednictvím příkazu nebo [základního](../../language-reference/keywords/base.md) příkazu. Třídy a `structs` mohou také definovat více konstruktorů a není ani nutné definovat konstruktor bez parametrů. Příklad:  
  
 [!code-csharp[csProgGuideObjects#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#54)]  
  
 Tuto třídu lze vytvořit pomocí některého z následujících příkazů:  
  
 [!code-csharp[csProgGuideObjects#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#55)]  
  
 Konstruktor může použít `base` klíčové slovo pro volání konstruktoru základní třídy. Příklad:  
  
 [!code-csharp[csProgGuideObjects#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#56)]  
  
 V tomto příkladu je konstruktor pro základní třídu volán před provedením bloku pro konstruktor. `base` Klíčové slovo lze použít s parametry nebo bez nich. Jakékoli parametry konstruktoru lze použít jako parametry `base`nebo jako součást výrazu. Další informace naleznete v tématu [Base](../../language-reference/keywords/base.md).  
  
 V odvozené třídě, pokud konstruktor základní třídy není volán explicitně pomocí `base` klíčového slova, konstruktor bez parametrů, pokud existuje, je volán implicitně. To znamená, že následující deklarace konstruktoru jsou efektivně stejné:  
  
 [!code-csharp[csProgGuideObjects#58](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#58)]  
  
 [!code-csharp[csProgGuideObjects#57](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#57)]  
  
 Pokud základní třída nenabízí konstruktor bez parametrů, musí odvozená třída vytvořit explicitní volání základního konstruktoru pomocí `base`.  
  
 Konstruktor může vyvolat jiný konstruktor ve stejném objektu pomocí klíčového slova [This](../../language-reference/keywords/this.md) . Podobně `base`jako `this` , lze použít s parametry nebo bez parametrů a jakékoli parametry v konstruktoru `this`jsou k dispozici jako parametry, nebo jako součást výrazu. Například druhý konstruktor v předchozím příkladu lze přepsat pomocí `this`:  
  
 [!code-csharp[csProgGuideObjects#59](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#59)]  
  
 Použití `this` klíčového slova v předchozím příkladu způsobí volání tohoto konstruktoru:  
  
 [!code-csharp[csProgGuideObjects#60](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#60)]  
  
 Konstruktory mohou být označeny jako [veřejné](../../language-reference/keywords/public.md), [privátní](../../language-reference/keywords/private.md), [chráněné](../../language-reference/keywords/protected.md), [interní](../../language-reference/keywords/internal.md), [chráněné interní](../../language-reference/keywords/protected-internal.md) nebo [soukromé chráněné](../../language-reference/keywords/private-protected.md). Tyto modifikátory přístupu definují, jak mohou uživatelé třídy vytvořit třídu. Další informace najdete v tématu [modifikátory přístupu](./access-modifiers.md).  
  
 Konstruktor lze deklarovat staticky pomocí klíčového slova [static](../../language-reference/keywords/static.md) . Statické konstruktory jsou volány automaticky, bezprostředně před tím, než jsou k dispozici statická pole a jsou obecně použity pro inicializaci statických členů třídy. Další informace naleznete v tématu [statické konstruktory](./static-constructors.md).  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  

Další informace naleznete v tématu [konstruktory instancí](~/_csharplang/spec/classes.md#instance-constructors) a [statické konstruktory](~/_csharplang/spec/classes.md#static-constructors) ve [ C# specifikaci jazyka](../../language-reference/language-specification/index.md). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Třídy a struktury](./index.md)
- [Konstruktory](./constructors.md)
- [Finalizační metody](./destructors.md)
