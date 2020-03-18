---
title: Pojmenované a volitelné argumenty – programovací příručka jazyka C#
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
ms.openlocfilehash: 15b685248730c1f742035612a201d97d180bbc41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399810"
---
# <a name="named-and-optional-arguments-c-programming-guide"></a>Pojmenované a nepovinné argumenty (Průvodce programováním v C#)
C# 4 zavádí pojmenované a volitelné argumenty. *Pojmenované argumenty* umožňují zadat argument pro určitý parametr tak, že argument připojujete k názvu parametru, nikoli k umístění parametru v seznamu parametrů. *Volitelné argumenty* umožňují vynechat argumenty pro některé parametry. Obě techniky lze použít s metodami, indexery, konstruktory a delegáty.  
  
 Při použití pojmenované a volitelné argumenty argumenty jsou vyhodnoceny v pořadí, ve kterém se zobrazí v seznamu argumentů, nikoli seznam parametrů.  
  
 Pojmenované a volitelné parametry, pokud jsou použity společně, umožňují zadat argumenty pouze pro několik parametrů ze seznamu volitelných parametrů. Tato funkce výrazně usnadňuje volání rozhraní MODELU COM, jako jsou rozhraní API automatizace sady Microsoft Office.  
  
## <a name="named-arguments"></a>Pojmenované argumenty  
 Pojmenované argumenty vás osvobozují od nutnosti pamatovat si nebo vyhledat pořadí parametrů v seznamech parametrů volaných metod. Parametr pro každý argument lze zadat podle názvu parametru. Například funkce, která tiskne podrobnosti objednávky (například jméno prodejce, číslo objednávky & název produktu), může být volána standardním způsobem odesláním argumentů podle pozice v pořadí definovaném funkcí.
  
 `PrintOrderDetails("Gift Shop", 31, "Red Mug");`
  
 Pokud si nepamatujete pořadí parametrů, ale znáte jejich názvy, můžete odeslat argumenty v libovolném pořadí.  
  
 `PrintOrderDetails(orderNum: 31, productName: "Red Mug", sellerName: "Gift Shop");`
  
 `PrintOrderDetails(productName: "Red Mug", sellerName: "Gift Shop", orderNum: 31);`
  
 Pojmenované argumenty také zlepšit čitelnost kódu určením, co každý argument představuje. V příkladu metody `sellerName` níže nemůže být null nebo prázdné místo. Jako `sellerName` oba `productName` a jsou typy řetězců, namísto odesílání argumentů podle pozice, má smysl použít pojmenované argumenty k rozdvojení dvou a snížit nejasnosti pro každého, kdo čtení kódu.
  
 Pojmenované argumenty, jsou-li použity s pozičními argumenty, jsou platné, pokud

- nejsou následovány žádnými pozičními argumenty, nebo

 `PrintOrderDetails("Gift Shop", 31, productName: "Red Mug");`

- _počínaje C# 7.2_, jsou používány ve správné poloze. V níže uvedeném `orderNum` příkladu je parametr ve správné pozici, ale není explicitně pojmenován.

 `PrintOrderDetails(sellerName: "Gift Shop", 31, productName: "Red Mug");`
  
 Poziční argumenty, které následují za všemi pojmenovaná argumenty mimo pořadí, jsou neplatné.

 ```csharp
 // This generates CS1738: Named argument specifications must appear after all fixed arguments have been specified.
 PrintOrderDetails(productName: "Red Mug", 31, "Gift Shop");
 ```
  
## <a name="example"></a>Příklad  
 Následující kód implementuje příklady z této části spolu s některé další.  
  
 [!code-csharp[csProgGuideNamedAndOptional#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/program.cs#1)]  
  
## <a name="optional-arguments"></a>Volitelné argumenty  
 Definice metody, konstruktoru, indexeru nebo delegáta může určit, že jsou požadovány jeho parametry nebo že jsou volitelné. Každé volání musí poskytnout argumenty pro všechny požadované parametry, ale může vynechat argumenty pro volitelné parametry.  
  
 Každý volitelný parametr má jako součást své definice výchozí hodnotu. Pokud pro tento parametr není odeslán žádný argument, použije se výchozí hodnota. Výchozí hodnota musí být jeden z následujících typů výrazů:  
  
- konstantní výraz;  
  
- výraz formuláře `new ValType()`, kde `ValType` je typ hodnoty, například [výčtnebo](../../language-reference/builtin-types/enum.md) [struktura](../../language-reference/builtin-types/struct.md);  
  
- výraz výchozího formuláře [(ValType),](../../language-reference/operators/default.md) `ValType` kde je typ hodnoty.  
  
 Volitelné parametry jsou definovány na konci seznamu parametrů po všech požadovaných parametrech. Pokud volající poskytuje argument pro některý z posloupnosti volitelných parametrů, musí poskytnout argumenty pro všechny předchozí volitelné parametry. Mezery oddělené čárkami v seznamu argumentů nejsou podporovány. Například v následujícím kódu je `ExampleMethod` metoda instance definována s jedním povinným a dvěma volitelnými parametry.  
  
 [!code-csharp[csProgGuideNamedAndOptional#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#15)]  
  
 Následující volání `ExampleMethod` způsobí chybu kompilátoru, protože argument je k dispozici pro třetí parametr, ale ne pro druhý.  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 Pokud však znáte název třetího parametru, můžete k provedení úkolu použít pojmenovaný argument.  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 Technologie IntelliSense používá závorky k označení volitelných parametrů, jak je znázorněno na následujícím obrázku:  
  
 ![Snímek obrazovky s rychlými informacemi intelliSense pro metodu ExampleMethod](./media/named-and-optional-arguments/optional-examplemethod-parameters.png)  
  
> [!NOTE]
> Volitelné parametry můžete také deklarovat pomocí třídy .NET. <xref:System.Runtime.InteropServices.OptionalAttribute> `OptionalAttribute`parametry nevyžadují výchozí hodnotu.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu má `ExampleClass` konstruktor pro jeden parametr, který je volitelný. Metoda `ExampleMethod` instance má jeden `required`povinný parametr a `optionalstr` dva `optionalint`volitelné parametry a . Kód v `Main` ukazuje různé způsoby, ve kterém konstruktor a metoda může být vyvolána.  
  
 [!code-csharp[csProgGuideNamedAndOptional#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#2)]  
  
## <a name="com-interfaces"></a>Rozhraní COM  
 Pojmenované a volitelné argumenty spolu s podporou dynamických objektů a dalších vylepšení výrazně zlepšují interoperabilitu s rozhraními API com, jako jsou rozhraní API pro automatizaci office.  
  
 Například <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> metoda v rozhraní aplikace <xref:Microsoft.Office.Interop.Excel.Range> Microsoft Office Excel má sedm parametrů, z nichž všechny jsou volitelné. Tyto parametry jsou znázorněny na následujícím obrázku:  
  
 ![Snímek obrazovky s rychlými informacemi technologie IntelliSense pro metodu automatického formátování](./media/named-and-optional-arguments/autoformat-method-parameters.png)  
  
 V C# 3.0 a starší verze argument je vyžadován pro každý parametr, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideNamedAndOptional#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#3)]  
  
 Však můžete výrazně zjednodušit `AutoFormat` volání pomocí pojmenované a volitelné argumenty, zavedené v C# 4.0. Pojmenované a volitelné argumenty umožňují vynechat argument pro volitelný parametr, pokud nechcete změnit výchozí hodnotu parametru. V následujícím volání je zadána hodnota pouze pro jeden ze sedmi parametrů.  
  
 [!code-csharp[csProgGuideNamedAndOptional#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#13)]  
  
 Další informace a příklady najdete [v tématu Použití pojmenovaných a volitelných argumentů v programování sady Office](./how-to-use-named-and-optional-arguments-in-office-programming.md) a Jak získat přístup k [objektům interop sady Office pomocí funkcí Jazyka C#](../interop/how-to-access-office-onterop-objects.md).  
  
## <a name="overload-resolution"></a>Rozlišení přetěžování  
 Použití pojmenovaných a volitelných argumentů ovlivňuje řešení přetížení následujícími způsoby:  
  
- Metoda, indexer nebo konstruktor je kandidátem pro spuštění, pokud je každý z jeho parametrů volitelný nebo odpovídá podle názvu nebo pozice jednomu argumentu v příkazu volání a tento argument lze převést na typ parametru.  
  
- Pokud je nalezen více než jeden kandidát, pravidla řešení přetížení pro upřednostňované převody se použijí na argumenty, které jsou explicitně zadány. Vynechané argumenty pro volitelné parametry jsou ignorovány.  
  
- Pokud jsou dva kandidáti považováni za stejně dobré, upřednostňuje se kandidát, který nemá volitelné parametry, pro které byly argumenty ve výzvě vynechány. To je důsledkem obecné preference v řešení přetížení pro kandidáty, kteří mají méně parametrů.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Použití pojmenovaných a volitelných argumentů v programování sady Office](./how-to-use-named-and-optional-arguments-in-office-programming.md)
- [Použití typu dynamic](../types/using-type-dynamic.md)
- [Použití konstruktorů](./using-constructors.md)
- [Použití indexerů](../indexers/using-indexers.md)
