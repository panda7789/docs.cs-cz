---
title: Pojmenované a nepovinné argumenty (Průvodce programováním v C#)
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
ms.openlocfilehash: b0963457e22bf0c3fc92d33c5ed0eb699be27cf7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="named-and-optional-arguments-c-programming-guide"></a>Pojmenované a nepovinné argumenty (Průvodce programováním v C#)
[!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] představuje pojmenované a nepovinné argumenty. *Pojmenované argumenty* vám umožní zadat argument pro konkrétní parametr tím, že přidružíte argument s názvem parametru a nikoli s parametru pozici v seznamu parametrů. *Nepovinné argumenty* umožňují vynechejte argumenty pro některé parametry. Obě tyto metody lze pomocí metody, indexery, konstruktory a delegáti.  
  
 Při použití pojmenovaných a nepovinných argumentů argumenty, které jsou vyhodnocovány v pořadí, v jakém jsou uvedeny v seznamu argumentů není seznam parametrů.  
  
 Pojmenované a nepovinné parametry, při použití společně, umožňují zadat argumenty pro pouze několik parametrů ze seznamu volitelné parametry. Tato funkce výrazně usnadňuje volání do rozhraní COM, jako je například rozhraní API automatizace Microsoft Office.  
  
## <a name="named-arguments"></a>Pojmenované argumenty  
 Pojmenované argumenty vás zbaví nutnosti mějte na paměti, nebo k vyhledání pořadí parametrů v seznamu parametrů vyvolání metod. Parametr pro každý argument může být určena název parametru. Například funkci, která zobrazí podrobnosti o pořadí (jako je třeba název prodejce, název pořadí číslo & produktu) může být volán v standardním způsobem odesláním argumentů podle pozice v pořadí definované funkce.
  
 `PrintOrderDetails("Gift Shop", 31, "Red Mug");`
  
 Pokud pořadí parametrů nepamatujete, ale znáte jejich názvy, můžete odeslat argumenty v libovolném pořadí.  
  
 `PrintOrderDetails(orderNum: 31, productName: "Red Mug", sellerName: "Gift Shop");`
  
 `PrintOrderDetails(productName: "Red Mug", sellerName: "Gift Shop", orderNum: 31);`
  
 Pojmenované argumenty taky aby zlepšila čitelnost kódu tím, že určíte, co představuje všechny argumenty. V metodě v příkladu níže `sellerName` nesmí být null ani prázdné znaky. Jako obě `sellerName` a `productName` jsou typy řetězce, místo abyste odesílali argumentů podle pozice, má smysl pojmenované argumenty použít k rozlišení dvou a snížit nedorozuměním pro každý, kdo čtení kódu.
  
 Pojmenované argumenty, pokud se používá s poziční parametry, jsou platné, dokud 

- nejsou následuje argumentů podle pozice, nebo

 `PrintOrderDetails("Gift Shop", 31, productName: "Red Mug");`

- _od verze jazyka C# 7.2_, jejich použití ve správné pozici. V příkladu níže parametr `orderNum` je ve správné pozici, ale není explicitně s názvem.

 `PrintOrderDetails(sellerName: "Gift Shop", 31, productName: "Red Mug");`
  
 Pojmenované argumenty pořadí se na více systémů jsou však neplatný, pokud jste postupovali podle poziční argumenty.

 ```csharp
 // This generates CS1738: Named argument specifications must appear after all fixed arguments have been specified.
 PrintOrderDetails(productName: "Red Mug", 31, "Gift Shop");
 ```
  
## <a name="example"></a>Příklad  
 Následující kód implementuje příklady z této části společně s ty, které jsou některé další.  
  
 [!code-csharp[csProgGuideNamedAndOptional#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_1.cs)]  
  
## <a name="optional-arguments"></a>Nepovinné argumenty  
 Definice metoda, konstruktor, indexer nebo delegáta můžete určit, že jeho parametry jsou povinné a že jsou volitelné. Žádném volání, musíte zadat argumenty pro všechny požadované parametry, ale můžete vynechat argumenty pro volitelné parametry.  
  
 Každý volitelný parametr má výchozí hodnotu v rámci jeho definice. Pokud se pro tento parametr je odeslat žádný argument, je použita výchozí hodnota. Výchozí hodnota musí být jedna z následujících typů výrazů:  
  
-   konstantní výraz;  
  
-   výraz ve tvaru `new ValType()`, kde `ValType` je hodnota typu, například [výčtu](../../../csharp/language-reference/keywords/enum.md) nebo [struktura](../../../csharp/programming-guide/classes-and-structs/structs.md);  
  
-   výraz, který formulář [default(ValType)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md), kde `ValType` je typ hodnoty.  
  
 Volitelné parametry jsou definovány na konci seznamu parametrů po požadované parametry. Pokud má volající poskytuje argument pro každý z postupným volitelné parametry, je nutné zadat argumenty pro všechny předchozí volitelné parametry. Textový soubor s oddělovači mezery v seznamu argumentů nejsou podporovány. Například v následujícím kódu metodu instance `ExampleMethod` je definovaná pomocí jednu požadované a volitelné dva parametry.  
  
 [!code-csharp[csProgGuideNamedAndOptional#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_2.cs)]  
  
 Následující volání do `ExampleMethod` způsobí chybu kompilátoru, protože argument je k dispozici pro třetí parametr, ale ne pro druhý.  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 Ale pokud znáte název třetí parametr, můžete s názvem argument provedení úkolu.  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 IntelliSense pomocí závorek označuje volitelné parametry, jak je znázorněno na následujícím obrázku.  
  
 ![Rychlé informace technologie IntelliSense pro metodu ExampleMethod. ] (../../../csharp/programming-guide/classes-and-structs/media/optional_parameters.png "Optional_Parameters")  
Volitelné parametry v ExampleMethod  
  
> [!NOTE]
>  Volitelné parametry můžete také deklarovat s použitím .NET <xref:System.Runtime.InteropServices.OptionalAttribute> třídy. `OptionalAttribute` Parametry nevyžadují výchozí hodnotu.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu v konstruktoru pro `ExampleClass` má jeden parametr, který je volitelné. Metodu instance `ExampleMethod` má jeden požadovaný parametr `required`a dva volitelné parametry, `optionalstr` a `optionalint`. Kód v `Main` ukazuje různé způsoby, ve kterém můžete vyvolat konstruktor a metoda.  
  
 [!code-csharp[csProgGuideNamedAndOptional#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_3.cs)]  
  
## <a name="com-interfaces"></a>COM – rozhraní  
 Pojmenované a nepovinné argumenty, společně s podporou pro dynamické objekty a další rozšíření dojít k výraznému zlepšení spolupráce se rozhraní API modelu COM, jako je například Office automatizace rozhraní API.  
  
 Například [automatický formát](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.autoformat(v=office.15).aspx) metoda v aplikaci Microsoft Office Excel [rozsah](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range(v=office.15).aspx) rozhraní má sedm parametry, které jsou volitelné. Tyto parametry se zobrazí na následujícím obrázku.  
  
 ![Rychlé informace technologie IntelliSense pro metodu automatické formátování. ] (../../../csharp/programming-guide/classes-and-structs/media/autoformat_parameters.png "AutoFormat_Parameters")  
Automatický formát parametrů  
  
 V C# 3.0 a starší verze je potřebná pro každý parametr argument, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideNamedAndOptional#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_4.cs)]  
  
 Však může výrazně zjednodušit volání `AutoFormat` pomocí pojmenovaných a nepovinných argumentů, zavedená v C# 4.0. Pojmenované a nepovinné argumenty umožňují vynechejte argument pro volitelný parametr, pokud nechcete změnit výchozí hodnoty parametru. V následující volání je zadaná hodnota jenom pro jednu ze sedmi parametry.  
  
 [!code-csharp[csProgGuideNamedAndOptional#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_5.cs)]  
  
 Další informace a příklady naleznete v tématu [postup: pomocí pojmenovaných a nepovinných argumentů v programování Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) a [postupy: přístup k objektům zprostředkovatel komunikace s objekty Office pomocí Visual C# funkce](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).  
  
## <a name="overload-resolution"></a>Rozlišení přetěžování  
 Použití pojmenovaných a nepovinných argumentů ovlivňuje rozlišení přetížení následujícími způsoby:  
  
-   Metoda, indexer nebo konstruktor je kandidátem na spuštění, pokud všechny její parametry je volitelný nebo odpovídá podle názvu nebo podle pozici, na jeden argument příkazu volání a který argument lze převést na typ parametru.  
  
-   Pokud je nalezen více než jeden candidate, přetížení řešení pro upřednostňované převody pravidla argumenty, které jsou explicitně určena. Vynechání argumenty pro volitelné parametry jsou ignorovány.  
  
-   Pokud dva kandidáty jsou považovány za být stejně dobrý, předvoleb přejde na candidate, který nemá volitelné parametry, pro které byly vynechány argumenty ve volání. Toto je důsledkem Obecné předvolby rozlišení přetížení pro kandidáty, které mají méně parametry.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Použití pojmenovaných a nepovinných argumentů v programování pro sadu Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)  
 [Použití typu dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md)  
 [Použití konstruktorů](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)  
 [Použití indexerů](../../../csharp/programming-guide/indexers/using-indexers.md)
