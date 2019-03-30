---
title: Pojmenované a nepovinné argumenty - C# Průvodce programováním
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
ms.openlocfilehash: 751f8a0745322e7e8573d392a504ea02cb18572e
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654026"
---
# <a name="named-and-optional-arguments-c-programming-guide"></a>Pojmenované a nepovinné argumenty (Průvodce programováním v C#)
[!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] představuje pojmenované a nepovinné argumenty. *Pojmenované argumenty* vám umožní zadat argument pro parametr konkrétní tím, že přidružíte argument s názvem parametru místo parametru pozice v seznamu parametrů. *Volitelné argumenty* umožňují vynechejte argumenty pro některé parametry. Obě tyto metody lze pomocí metody, indexery, konstruktory a delegáti.  
  
 Při použití pojmenované a nepovinné argumenty jsou argumenty se vyhodnocují v pořadí, v jakém jsou uvedeny v seznamu argumentů, ne seznam parametrů.  
  
 Pojmenované a nepovinné parametry, pokud se použijí společně, umožňují zadat argumenty pouze několik parametrů ze seznamu nepovinných parametrů. Tato funkce výrazně usnadňuje volání do rozhraní COM, jako je například rozhraní API automatizace Microsoft Office.  
  
## <a name="named-arguments"></a>Pojmenované argumenty  
 Pojmenované argumenty vás zbaví nutnosti mějte na paměti, nebo k vyhledání pořadí parametrů v seznamech parametrů volané metody. Parametr pro každý argument může být určeno název parametru. Například funkce, která vytiskne OrderDetails (jako jsou například prodejce název, číslo & product název objednávky) mohou být volány v standardní způsob odesílání argumentů podle pozice v pořadí určeném parametrem funkce.
  
 `PrintOrderDetails("Gift Shop", 31, "Red Mug");`
  
 Pokud nepamatujete pořadí parametrů, ale znáte jejich názvy, můžete odeslat argumenty v libovolném pořadí.  
  
 `PrintOrderDetails(orderNum: 31, productName: "Red Mug", sellerName: "Gift Shop");`
  
 `PrintOrderDetails(productName: "Red Mug", sellerName: "Gift Shop", orderNum: 31);`
  
 Pojmenované argumenty také zlepšit čitelnost kódu díky identifikaci, co každý argument představuje. V následujícím příkladu metoda `sellerName` nesmí být null ani prázdné znaky. Obě `sellerName` a `productName` jsou typy řetězce, místo abyste odesílali argumentů podle pozice, je vhodné použít pojmenované argumenty k rozlišení dvou a redukovat nejasnosti pro každého, kdo čte kód.
  
 Pojmenované argumenty, při použití s poziční argumenty, jsou platné jako 

- nejsou následovány poziční argumenty, nebo

 `PrintOrderDetails("Gift Shop", 31, productName: "Red Mug");`

- _od verze C# 7.2_, jejich použití ve správné pozici. V příkladu níže parametr `orderNum` je ve správné pozici, ale není explicitně s názvem.

 `PrintOrderDetails(sellerName: "Gift Shop", 31, productName: "Red Mug");`
  
 Mimo pořadí pojmenované argumenty jsou však neplatná, pokud jste postupovali podle poziční argumenty.

 ```csharp
 // This generates CS1738: Named argument specifications must appear after all fixed arguments have been specified.
 PrintOrderDetails(productName: "Red Mug", 31, "Gift Shop");
 ```
  
## <a name="example"></a>Příklad  
 Následující kód implementuje příklady v této části spolu s některé další značky.  
  
 [!code-csharp[csProgGuideNamedAndOptional#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/program.cs#1)]  
  
## <a name="optional-arguments"></a>Nepovinné argumenty.  
 Definice metody, konstruktoru, indexeru nebo delegáta můžete určit, že její parametry jsou povinné a že jsou volitelné. Každé volání musí zadat argumenty pro všechny požadované parametry, ale lze vynechat argumenty pro volitelné parametry.  
  
 Každý volitelný parametr má výchozí hodnotu jako součást jeho definici. Pokud pro tento parametr je odeslán žádný argument, je použita výchozí hodnota. Výchozí hodnota musí být jedna z následujících typů výrazů:  
  
-   konstantní výraz;  
  
-   výraz ve tvaru `new ValType()`, kde `ValType` , jako je typ hodnoty, [výčtu](../../../csharp/language-reference/keywords/enum.md) nebo [struktury](../../../csharp/programming-guide/classes-and-structs/structs.md);  
  
-   výraz ve tvaru [default(ValType)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md), kde `ValType` je typ hodnoty.  
  
 Volitelné parametry jsou definované na konci seznamu parametrů po požadované parametry. Pokud volající zadá argument pro každý z sledu očekávání volitelné parametry, je nutné zadat argumenty pro všechny předchozí volitelné parametry. Exportovaná mezery v seznamu argumentů nejsou podporovány. Například následující kód metodu instance `ExampleMethod` je definována s vyžadovaný a dva volitelné parametry.  
  
 [!code-csharp[csProgGuideNamedAndOptional#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#15)]  
  
 Následující volání `ExampleMethod` způsobí chybu kompilátoru, protože argument je k dispozici pro třetí parametr, ale ne pro druhý.  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 Pokud znáte název třetí parametr, můžete ke splnění úkolu můžete použít pojmenovaný argument.  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 Technologie IntelliSense pomocí závorek k označení volitelné parametry, jak je znázorněno na následujícím obrázku:  
  
 ![Snímek obrazovky zobrazující rychlé informace technologie IntelliSense pro metodu ExampleMethod.](./media/named-and-optional-arguments/optional-examplemethod-parameters.png)  
  
> [!NOTE]
>  Volitelné parametry můžete také deklarovat s použitím .NET <xref:System.Runtime.InteropServices.OptionalAttribute> třídy. `OptionalAttribute` Parametry nevyžadují, aby výchozí hodnota.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu se v konstruktoru pro `ExampleClass` má jeden parametr, který je volitelný. Metodu instance `ExampleMethod` má jeden povinný parametr, `required`a dva volitelné parametry, `optionalstr` a `optionalint`. Kód v `Main` ukazuje různé způsoby, ve kterém lze vyvolat konstruktor a metody.  
  
 [!code-csharp[csProgGuideNamedAndOptional#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#2)]  
  
## <a name="com-interfaces"></a>Com – rozhraní  
 Pojmenované a nepovinné argumenty společně s podporou dynamických objektů a dalších vylepšení, výrazně zlepšit vzájemná funkční spolupráce s rozhraními API modelu COM, jako je například rozhraní API Office automatizace.  
  
 Například <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> metodu v aplikaci Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Range> rozhraní obsahuje sedm parametry, z nichž všechny jsou volitelné. Tyto parametry můžete vidět na následujícím obrázku:  
  
 ![Snímek obrazovky zobrazující rychlé informace technologie IntelliSense pro metodu automatické formátování.](./media/named-and-optional-arguments/autoformat-method-parameters.png)  
  
 V jazyce C# 3.0 a starší verze je argument se vyžaduje pro každý parametr, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideNamedAndOptional#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#3)]  
  
 Však může výrazně zjednodušit volání `AutoFormat` pomocí pojmenovaných a nepovinných argumentů zavedené v C# 4.0. Pojmenované a nepovinné argumenty umožňují argument pro nepovinný parametr vynechat, pokud nechcete změnit výchozí hodnotu parametru. V následujícím volání je zadána hodnota jenom pro jednu ze sedmi parametry.  
  
 [!code-csharp[csProgGuideNamedAndOptional#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#13)]  
  
 Další informace a příklady najdete v tématu [jak: Použití pojmenovaných a nepovinných argumentů v programování pro Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) a [jak: Přístup k objektům Interop sady Office pomocí Vizuálu C# funkce](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).  
  
## <a name="overload-resolution"></a>Rozlišení přetěžování  
 Použití pojmenovaných a nepovinných argumentů řešení přetížení ovlivňuje následujícími způsoby:  
  
-   Metoda, indexer nebo konstruktor je kandidátem pro spuštění, pokud každý ze svých parametrů je nepovinný nebo odpovídá podle názvu nebo podle pozice jediný argument ve volání příkazu, a že argument lze převést na typ parametru.  
  
-   Pokud je nalezen více než jeden Release candidate, pravidla rozlišení přetížení pro upřednostňované převody se aplikují na argumenty, které jsou explicitně zadány. Vynechaný argumenty pro volitelné parametry jsou ignorovány.  
  
-   Pokud dvě kandidáty jsou považovány za stejnou měrou bezproblémový, předvoleb přejde na Release candidate, který nemá žádné volitelné parametry, které byly vynechány argumenty ve volání. Toto je důsledkem obecné předvoleb v rozlišení přetížení pro kandidáty, které mají méně parametrů.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Použití pojmenovaných a nepovinných argumentů v programování pro Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [Použití typu dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md)
- [Použití konstruktorů](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)
- [Použití indexerů](../../../csharp/programming-guide/indexers/using-indexers.md)
