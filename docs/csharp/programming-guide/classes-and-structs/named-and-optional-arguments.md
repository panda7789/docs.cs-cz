---
title: Pojmenované a volitelné argumenty – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- namedParameter_CSharpKeyword
- cs_namedParameter
helpviewer_keywords:
- parameters [C#], named
- named arguments [C#]
- arguments [C#], named
- optional arguments [C#]
- arguments [C#], optional
- parameters [C#], optional
- named and optional arguments [C#]
ms.assetid: 839c960c-c2dc-4d05-af4d-ca5428e54008
ms.openlocfilehash: 74cfc6a425e82014bbcf5093f52f476ff09db130
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796556"
---
# <a name="named-and-optional-arguments-c-programming-guide"></a>Pojmenované a nepovinné argumenty (Průvodce programováním v C#)
C#4 zavádí pojmenované a volitelné argumenty. *Pojmenované argumenty* umožňují zadat argument pro konkrétní parametr přiřazením argumentu s názvem parametru, nikoli zadáním pozice parametru v seznamu parametrů. *Volitelné argumenty* umožňují vynechat argumenty pro některé parametry. Oba postupy lze použít s metodami, indexery, konstruktory a delegáty.  
  
 Při použití pojmenovaných a volitelných argumentů jsou argumenty vyhodnocovány v pořadí, v jakém jsou uvedeny v seznamu argumentů, nikoli v seznamu parametrů.  
  
 Pojmenované a volitelné parametry – při použití společně vám umožní zadat argumenty jenom pro několik parametrů ze seznamu nepovinných parametrů. Tato funkce významně usnadňuje volání rozhraní COM, jako jsou systém Microsoft Office rozhraní API pro automatizaci.  
  
## <a name="named-arguments"></a>Pojmenované argumenty  
 Pojmenované argumenty, které si zapamatujete, abyste si vyhledali pořadí parametrů v seznamech volaných metod. Parametr pro každý argument lze zadat pomocí názvu parametru. Například funkce, která tiskne podrobnosti objednávky (například, jméno prodejce, číslo objednávky & název produktu), může být volána standardním způsobem odesláním argumentů podle pozice v pořadí určeném funkcí.
  
 `PrintOrderDetails("Gift Shop", 31, "Red Mug");`
  
 Pokud si nepamatujete pořadí parametrů, ale znáte jejich názvy, můžete argumenty poslat v libovolném pořadí.  
  
 `PrintOrderDetails(orderNum: 31, productName: "Red Mug", sellerName: "Gift Shop");`
  
 `PrintOrderDetails(productName: "Red Mug", sellerName: "Gift Shop", orderNum: 31);`
  
 Pojmenované argumenty také zlepšují čitelnost kódu tím, že identifikují, co každý argument představuje. V níže uvedeném `sellerName` příkladu nemůže být null nebo prázdné místo. `sellerName` Jak a `productName` jsou typy řetězců namísto odeslání argumentů podle pozice, má smysl použít pojmenované argumenty k jednoznačnému odstranění těchto dvou a omezení nejasností pro kohokoli, kdo čte kód.
  
 Pojmenované argumenty, pokud se používají s pozičními argumenty, jsou platné, dokud 

- nejsou následovány žádnými pozičními argumenty nebo

 `PrintOrderDetails("Gift Shop", 31, productName: "Red Mug");`

- _počínaje C# 7,2_se používají ve správné pozici. V následujícím příkladu je parametr `orderNum` ve správné pozici, ale není explicitně pojmenován.

 `PrintOrderDetails(sellerName: "Gift Shop", 31, productName: "Red Mug");`
  
 Pojmenované argumenty jsou však neplatné, pokud jsou následovány pozičními argumenty.

 ```csharp
 // This generates CS1738: Named argument specifications must appear after all fixed arguments have been specified.
 PrintOrderDetails(productName: "Red Mug", 31, "Gift Shop");
 ```
  
## <a name="example"></a>Příklad  
 Následující kód implementuje příklady z této části spolu s dalšími dalšími.  
  
 [!code-csharp[csProgGuideNamedAndOptional#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/program.cs#1)]  
  
## <a name="optional-arguments"></a>Nepovinné argumenty  
 Definice metody, konstruktoru, indexeru nebo delegáta může určit, že jeho parametry jsou povinné nebo že jsou nepovinné. Jakékoli volání musí poskytnout argumenty pro všechny požadované parametry, ale může vynechat argumenty pro volitelné parametry.  
  
 Každý volitelný parametr má jako součást definice výchozí hodnotu. Pokud není pro tento parametr odeslán žádný argument, je použita výchozí hodnota. Výchozí hodnota musí být jeden z následujících typů výrazů:  
  
- konstantní výraz;  
  
- výraz formuláře `new ValType()`, kde `ValType` je hodnotový typ, jako je například [výčet](../../../csharp/language-reference/keywords/enum.md) nebo [Struktura](../../../csharp/programming-guide/classes-and-structs/structs.md);  
  
- výchozí výraz formuláře [(ValType)](../../../csharp/language-reference/operators/default.md), kde `ValType` je hodnotový typ.  
  
 Volitelné parametry jsou definovány na konci seznamu parametrů po všech požadovaných parametrech. Pokud volající poskytne argument pro jakékoli z úspěchu volitelných parametrů, musí zadat argumenty pro všechny předchozí volitelné parametry. Mezery oddělené čárkami v seznamu argumentů nejsou podporovány. Například v následujícím kódu je metoda `ExampleMethod` instance definována s jedním vyžadovaným a dvěma nepovinnými parametry.  
  
 [!code-csharp[csProgGuideNamedAndOptional#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#15)]  
  
 Následující volání `ExampleMethod` způsobí chybu kompilátoru, protože je k dispozici argument pro třetí parametr, ale ne pro druhý.  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 Pokud však znáte název třetího parametru, můžete k dokončení úkolu použít pojmenovaný argument.  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 Technologie IntelliSense používá hranaté závorky k označení volitelných parametrů, jak je znázorněno na následujícím obrázku:  
  
 ![Snímek obrazovky znázorňující rychlé informace technologie IntelliSense pro metodu ExampleMethod](./media/named-and-optional-arguments/optional-examplemethod-parameters.png)  
  
> [!NOTE]
>  Můžete také deklarovat volitelné parametry pomocí třídy .NET <xref:System.Runtime.InteropServices.OptionalAttribute> . `OptionalAttribute`Parametry nevyžadují výchozí hodnotu.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu má konstruktor pro `ExampleClass` jeden parametr, který je nepovinný. Metoda `ExampleMethod` instance má jeden povinný `required`parametr, `optionalstr` a dva volitelné parametry a `optionalint`. Kód v `Main` ukazuje různé způsoby, jak lze vyvolat konstruktor a metodu.  
  
 [!code-csharp[csProgGuideNamedAndOptional#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#2)]  
  
## <a name="com-interfaces"></a>Rozhraní COM  
 Pojmenované a nepovinné argumenty, společně s podporou pro dynamické objekty a další vylepšení, významně zlepšují interoperabilitu s rozhraními API modelu COM, jako jsou třeba rozhraní API pro automatizaci Office.  
  
 Například <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> metoda v rozhraní systém Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Range> má sedm parametrů, z nichž všechny jsou volitelné. Tyto parametry jsou uvedeny na následujícím obrázku:  
  
 ![Snímek obrazovky s rychlými informacemi technologie IntelliSense pro metodu automatického formátování](./media/named-and-optional-arguments/autoformat-method-parameters.png)  
  
 V C# 3,0 a starších verzích je pro každý parametr požadován argument, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideNamedAndOptional#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#3)]  
  
 Nicméně můžete značně zjednodušit volání `AutoFormat` pomocí pojmenovaných a nepovinných argumentů představených v C# 4,0. Pojmenované a volitelné argumenty umožňují vynechat argument pro volitelný parametr, pokud nechcete změnit výchozí hodnotu parametru. V následujícím volání je hodnota zadána pouze pro jeden ze sedmi parametrů.  
  
 [!code-csharp[csProgGuideNamedAndOptional#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#13)]  
  
 Další informace a příklady naleznete v tématu [How to: Použijte pojmenované a volitelné argumenty při programování](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) systému Office a [postup: Přístup k objektům Interop Office pomocí C# vizuálních funkcí](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
  
## <a name="overload-resolution"></a>Rozlišení přetěžování  
 Použití pojmenovaných a nepovinných argumentů má vliv na rozlišení přetížení následujícími způsoby:  
  
- Metoda, indexer nebo konstruktor je kandidátem na provedení, pokud jsou jednotlivé parametry buď volitelné, nebo odpovídají, podle názvu nebo podle pozice, k jednomu argumentu v příkazu volání a tento argument lze převést na typ parametru.  
  
- Pokud je nalezen více než jeden kandidát, budou pravidla rozlišení přetížení pro preferované převody použita na argumenty, které jsou explicitně určeny. Vynechané argumenty pro volitelné parametry jsou ignorovány.  
  
- Pokud jsou dva kandidáty odůvodněné stejně dobré, preference směřuje k kandidátovi, který nemá nepovinné parametry pro to, které argumenty byly ve volání vynechány. Jedná se o důsledek Obecné předvolby v řešení přetížení pro kandidáty, které mají méně parametrů.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Použití pojmenovaných a nepovinných argumentů v programování pro Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [Použití typu dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md)
- [Použití konstruktorů](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)
- [Použití indexerů](../../../csharp/programming-guide/indexers/using-indexers.md)
