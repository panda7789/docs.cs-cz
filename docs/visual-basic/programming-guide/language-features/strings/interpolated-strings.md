---
title: Interpolované řetězce (Visual Basic)
ms.date: 10/31/2017
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9501c052f387a522226e957193a8866083aa4233
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2018
---
# <a name="interpolated-strings-visual-basic-reference"></a>Interpolované řetězce (referenční dokumentace jazyka Visual Basic)

Umožňuje vytvářet řetězce.  Interpolované řetězec vypadá jako řetězec šablony, která obsahuje *interpolované výrazy*.  Interpolované řetězce vrátí řetězec, který nahradí jejich řetězcové vyjádření interpolované výrazy, které obsahuje. Tato funkce je dostupná v jazyce Visual Basic 14 a novějších verzích.

Argumenty interpolované řetězce jsou srozumitelnější než [složený formátovací řetězec](../../../../standard/base-types/composite-formatting.md#composite-format-string).  Například interpolované řetězce  
  
```vb  
Console.WriteLine($"Name = {name}, hours = {hours:hh}")
```  
obsahuje dva interpolované výrazy {name}' a '{hodin: hh}'. Je ekvivalentní složený formátovací řetězec:

```vb
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours); 
```  

Struktura interpolované řetězce je:  
  
```vb  
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."  
```  

kde: 

- *Šířka pole* se znaménkem, která určuje počet znaků v poli. Pokud je kladné, je pole vpravo zarovnaný; záporná, zarovnaný doleva. 

- *řetězec formátu* je vhodný pro typ objektu, který je formátován řetězec formátu. Například <xref:System.DateTime> hodnotu, může to být [řetězec formátu standardní hodnoty data a času](~/docs/standard/base-types/standard-date-and-time-format-strings.md) jako je například "D" nebo "d".

> [!IMPORTANT]
> Nemůže mít žádné mezery mezi `$` a `"` , začíná řetězec. Chyba kompilátoru při restartování.

 Interpolované řetězce můžete použít kdekoli můžete řetězcový literál.  Interpolované řetězce je vyhodnocován pokaždé, když spustí kód s interpolované řetězce. To umožňuje oddělit definice a vyhodnocení interpolované řetězce.  
  
 Zahrnout složené závorky ("{" nebo "}") v interpolované řetězce, pomocí dvou složené závorky, "{{" nebo "}}".  Implicitní převody části Další podrobnosti.  

Pokud interpolované řetězec obsahuje jiné znaky s zvláštní význam interpolované řetězce, jako je například uvozovky ("), dvojtečkou (:) ani čárky (,), že by měly být ukončeny Pokud se vyskytují v literálu text, nebo by měl být součástí výrazu oddělená závorky, pokud jsou součástí interpolované výrazu prvků jazyka. Následující příklad řídicí sekvence znaky uvozovek pro zahrnutí ve výsledném řetězci a používá kulaté závorky a tím vymezit výraz `(age == 1 ? "" : "s")` tak, aby dvojtečkou není interpretována jako od řetězec formátu.

[!code-vb[interpolated-strings](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings4.vb)]  

## <a name="implicit-conversions"></a>Implicitní převody  

Existují tři typu implicitní převody z interpolované řetězce:  

1. Interpolované řetězce pro převod <xref:System.String>. Následující příklad vrátí řetězec, jehož interpolované řetězce výrazy nahradil jejich řetězcové vyjádření. Příklad:

   [!code-vb[interpolated-strings1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings1.vb)]  

   Toto je poslední výsledek interpretace řetězec. Všechny výskyty dvojité složené závorky ("{{" a "}}") se převedou na jednom složených závorek. 

2. Interpolované řetězce pro převod <xref:System.IFormattable> proměnné, která umožňuje vytvořit více výsledek řetězce s obsahem specifické pro jazykovou verzi z jedné <xref:System.IFormattable> instance. To je užitečné pro jako jsou správné číselné a číselné formáty pro jednotlivé jazykové verze.  Všechny výskyty dvojité složené závorky ("{{" a "}}") zůstanou jako dvojité složené závorky, dokud se naformátovat řetězec voláním explicitně nebo implicitně <xref:System.Object.ToString> metoda.  Všechny obsažené interpolace výrazy se převedou na {0}, {1} a tak dále.  

   Následující příklad používá reflexe k zobrazení členů, jakož i pole a vlastnosti hodnoty <xref:System.IFormattable> proměnné, která je vytvořena z interpolované řetězce. Také předá <xref:System.IFormattable> proměnnou <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metoda.

   [!code-vb[interpolated-strings2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings2.vb)]  

   Všimněte si, že může být prověřovány interpolované řetězce pouze pomocí reflexe. Pokud je předán řetězec formátování metoda, jako například <xref:System.Console.WriteLine(System.String)>, jeho položky formátu jsou vyřešeny a vrátí výsledný řetězec. 

3. Interpolované řetězce pro převod <xref:System.FormattableString> proměnné, která představuje složený formátovací řetězec. Probíhá kontrola složený formátovací řetězec a jak se vykreslí v důsledku řetězec, například vám můžou pomoct chránit před útoky, vkládání, pokud vytváříte dotazu. A <xref:System.FormattableString> také zahrnuje:

      - A <xref:System.FormattableString.ToString> přetížení, které vytváří výsledný řetězec pro <xref:System.Globalization.CultureInfo.CurrentCulture>.
      
      - A <xref:System.FormattableString.Invariant%2A> metoda, která vytvoří řetězec pro <xref:System.Globalization.CultureInfo.InvariantCulture>.
      
      - A <xref:System.FormattableString.ToString(System.IFormatProvider)> metoda, která vytváří výsledný řetězec pro zadanou jazykovou verzi. 
  
    Všechny výskyty dvojité složené závorky ("{{" a "}}") zůstanou jako dvojité složené závorky, dokud formátovat.  Všechny obsažené interpolace výrazy se převedou na {0}, {1} a tak dále.  

   [!code-vb[interpolated-strings3](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings3.vb)]  

## <a name="see-also"></a>Viz také  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 [Referenční dokumentace jazyka Visual Basic](index.md)  
 