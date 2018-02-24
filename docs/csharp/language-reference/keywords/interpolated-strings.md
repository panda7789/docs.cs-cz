---
title: "Interpolované řetězce (C#)"
ms.date: 10/18/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 324f267e-1c61-431a-97ed-852c1530742d
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0569636bde875d2d0d8921a544273f3214d05188
ms.sourcegitcommit: cec0525b2121c36198379525e69aa5388266db5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="interpolated-strings-c-reference"></a>Interpolované řetězce (referenční dokumentace jazyka C#)

Umožňuje vytvářet řetězce.  Interpolované řetězec vypadá jako řetězec šablony, která obsahuje *interpolované výrazy*.  Interpolované řetězce vrátí řetězec, který nahradí jejich řetězcové vyjádření interpolované výrazy, které obsahuje. Tato funkce je k dispozici v C# 6 a novější verze.

Argumenty interpolované řetězce jsou srozumitelnější než [složený formátovací řetězec](../../../standard/base-types/composite-formatting.md#composite-format-string).  Například interpolované řetězce  
  
```csharp  
Console.WriteLine($"Name = {name}, hours = {hours:hh}");
```  
obsahuje dva interpolované výrazy {name}' a '{hodin: hh}'. Je ekvivalentní složený formátovací řetězec:

```csharp
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours); 
```  

Struktura interpolované řetězce je:  
  
```  
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."  
```  

kde: 

- *Šířka pole* se znaménkem, která určuje počet znaků v poli. Pokud je kladné, je pole vpravo zarovnaný; záporná, zarovnaný doleva. 

- *řetězec formátu* je vhodný pro typ objektu, který je formátován řetězec formátu. Například <xref:System.DateTime> hodnotu, může to být standardní hodnoty data a řetězec formátu času, například "D" nebo "d".

> [!IMPORTANT]
> Nemůže mít žádné mezery mezi `$` a `"` , začíná řetězec. To způsobí, že chybu v době kompilace.

 Interpolované řetězce můžete použít kdekoli můžete řetězcový literál.  Interpolované řetězce je vyhodnocován pokaždé, když spustí kód s interpolované řetězce. To umožňuje oddělit definice a vyhodnocení interpolované řetězce.  
  
 Zahrnout složené závorky ("{" nebo "}") v interpolované řetězce, pomocí dvou složené závorky, "{{" nebo "}}".  Implicitní převody části Další podrobnosti.  

Pokud interpolované řetězec obsahuje jiné znaky s zvláštní význam interpolované řetězce, jako je například uvozovky ("), dvojtečkou (:) ani čárky (,), že by měly být ukončeny Pokud se vyskytují v literálu text, nebo by měl být součástí výrazu oddělená závorky, pokud jsou součástí interpolované výrazu prvků jazyka. Následující příklad řídicí sekvence znaky uvozovek pro zahrnutí ve výsledném řetězci a používá kulaté závorky a tím vymezit výraz `(age == 1 ? "" : "s")` tak, aby dvojtečkou není interpretována jako od řetězec formátu.

[!code-csharp[interpolated-strings4](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings4.cs#1)]  

Doslovné interpolované řetězce použití `$` následuje znak `@` znak. Další informace o typu verbatim řetězců najdete v tématu [řetězec](string.md) tématu. Následující kód je upravenou verzi fragmentu předchozí pomocí typu verbatim interpolované řetězce:

[!code-csharp[interpolated-strings4](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings5.cs#1)]  

Změny formátování jsou nutné, protože není orientují typu verbatim řetězce `\` řídicí sekvence.

> [!IMPORTANT]
> `$` Token musí být před `@` tokenu typu verbatim interpolované řetězce.


## <a name="implicit-conversions"></a>Implicitní převody  

Existují tři typu implicitní převody z interpolované řetězce:  

1. Interpolované řetězce pro převod <xref:System.String>. Následující příklad vrátí řetězec, jehož interpolované řetězce výrazy nahradil jejich řetězcové vyjádření. Příklad:

   [!code-csharp[interpolated-strings1](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings1.cs#1)]  

   Toto je poslední výsledek interpretace řetězec. Všechny výskyty dvojité složené závorky ("{{" a "}}") se převedou na jednom složených závorek. 

2. Interpolované řetězce pro převod <xref:System.IFormattable> proměnné, která umožňuje vytvořit více výsledek řetězce s obsahem specifické pro jazykovou verzi z jedné <xref:System.IFormattable> instance. To je užitečné pro jako jsou správné číselné a číselné formáty pro jednotlivé jazykové verze.  Všechny výskyty dvojité složené závorky ("{{" a "}}") zůstanou jako dvojité složené závorky, dokud se naformátovat řetězec voláním explicitně nebo implicitně <xref:System.Object.ToString> metoda.  Všechny obsažené interpolace výrazy se převedou na {0}, {1} a tak dále.  

   Následující příklad používá reflexe k zobrazení členů, jakož i pole a vlastnosti hodnoty <xref:System.IFormattable> proměnné, která je vytvořena z interpolované řetězce. Také předá <xref:System.IFormattable> proměnnou <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metoda.

   [!code-csharp[interpolated-strings2](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings2.cs#1)]  

   Všimněte si, že může být prověřovány interpolované řetězce pouze pomocí reflexe. Pokud je předán řetězec formátování metoda, jako například <xref:System.Console.WriteLine(System.String)>, jeho položky formátu jsou vyřešeny a vrátí výsledný řetězec. 

3. Interpolované řetězce pro převod <xref:System.FormattableString> proměnné, která představuje složený formátovací řetězec. Probíhá kontrola složený formátovací řetězec a jak se vykreslí v důsledku řetězec, například vám můžou pomoct chránit před útoky, vkládání, pokud vytváříte dotazu. <xref:System.FormattableString> také zahrnuje <xref:System.FormattableString.ToString> přetížení, které vám umožní vytvořit výsledek řetězce pro <xref:System.Globalization.CultureInfo.InvariantCulture> a <xref:System.Globalization.CultureInfo.CurrentCulture>.  Všechny výskyty dvojité složené závorky ("{{" a "}}") zůstanou jako dvojité složené závorky, dokud formátovat.  Všechny obsažené interpolace výrazy se převedou na {0}, {1} a tak dále.  

   [!code-csharp[interpolated-strings3](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings3.cs#1)]  

## <a name="language-specification"></a>Specifikace jazyka  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
