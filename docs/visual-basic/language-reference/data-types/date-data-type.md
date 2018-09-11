---
title: Date – datový typ (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Date
helpviewer_keywords:
- Date data type
- dates [Visual Basic], Visual Basic data types
- times [Visual Basic], Date data type
- Date literals [Visual Basic]
- data values [Visual Basic]
- times [Visual Basic], Visual Basic data types
- dates [Visual Basic], Date data type
- data types [Visual Basic], assigning
- literals [Visual Basic], Date
- '# specifier for Date literals'
ms.assetid: d9edf5b0-e85e-438b-a1cf-1f321e7c831b
ms.openlocfilehash: 32bd0912b0bae3340cffed010fc67431d0efb376
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2018
ms.locfileid: "44368484"
---
# <a name="date-data-type-visual-basic"></a>Date – datový typ (Visual Basic)
IEEE – 64bitová (8 bajtů) hodnoty, které představují data od 1. ledna 0001 roku do 31. prosince 9999 roku a časy od 12:00:00: 00 (půlnoc) obsahuje prostřednictvím 11:59:59.9999999 PM. Každý přírůstek představuje 100 nanosekund uplynulý čas od začátku 1. ledna roku 1 v gregoriánském kalendáři. Maximální hodnota představuje 100 nanosekund před začátkem 1. ledna roku 10000.  
  
## <a name="remarks"></a>Poznámky  
 Použití `Date` datový typ obsahující hodnoty data, času hodnoty nebo hodnoty data a času.  
  
 Výchozí hodnota `Date` je 0:00:00 (půlnoc) na 1. ledna 0001.  
  
 Můžete získat aktuální datum a čas <xref:Microsoft.VisualBasic.DateAndTime> třídy.  
  
## <a name="format-requirements"></a>Požadavky na formát  
 Je nutné uzavřít `Date` literálu v rámci symboly čísla (`# #`). Hodnota kalendářního data ve formátu M/d/rrrr, musíte zadat například `#5/31/1993#`, nebo RRRR MM-dd, například `#1993-5-31#`. Při zadávání první rok, můžete použít lomítka.  Tento požadavek je nezávislé na národní prostředí a počítače nastavení data a času formátu.  
  
 Důvodem tohoto omezení je, že by měl význam kódu nikdy nezmění v závislosti na národním prostředí, ve kterém je aplikace spuštěna. Předpokládejme pevně zakódovat `Date` literál o `#3/4/1998#` a chcete-li znamenat 4. března 1998. V národním prostředí, která používá mm/dd/rrrr zkompiluje 3/4/1998 tak, jak zamýšlíte. Ale Předpokládejme, že nasadíte svou aplikaci v mnoha zemích. V národním prostředí, která používá dd/mm/rrrr by vaše pevně zakódované literál zkompilovat do 3. dubna 1998. V národním prostředí, která používá rrrr/mm/dd, by byl literál neplatný (1998. dubna, 0003) a způsobí chybu kompilátoru.  
  
## <a name="workarounds"></a>Alternativní řešení  
 Převést `Date` zadat literál na literál na formát národní prostředí nebo na vlastní formát, <xref:Microsoft.VisualBasic.Strings.Format%2A> funkce určující formát předdefinovaných nebo uživatelem definovaný datum. Následující příklad ukazuje to.  
  
```  
MsgBox("The formatted date is " & Format(#5/31/1993#, "dddd, d MMM yyyy"))  
```  
  
 Alternativně můžete použít jednu z přetížených konstruktorů z <xref:System.DateTime> struktura sestavení hodnoty data a času. Následující příklad vytvoří hodnotu představující 31. května 1993 ve 12:14 odpoledne.  
  
```  
Dim dateInMay As New System.DateTime(1993, 5, 31, 12, 14, 0)  
```  
  
## <a name="hour-format"></a>H formátu  
 Hodnota času ve formátu 12 hodin nebo 24 hodin, můžete zadat například `#1:15:30 PM#` nebo `#13:15:30#`. Nicméně pokud nezadáte, minuty nebo sekundy, musíte zadat dop.  
  
## <a name="date-and-time-defaults"></a>Datum a čas výchozích hodnot  
 Pokud literál datum/čas neobsahují datum, Visual Basic nastaví datum část hodnoty 1. ledna 0001. Pokud literál datum a čas nezahrnují čas, Visual Basic nastaví časovou část hodnoty na začátek dne, tedy půlnoci (0: 00:00).  
  
## <a name="type-conversions"></a>Převody typu  
 Při převodu `Date` hodnota, která se `String` typu, vykreslí datum podle používaného formátu krátkého data určené národní prostředí runtime jazyka Visual Basic a vykreslí podle formátu času (12 hodin nebo 24 hodin) časový limit určený parametrem národní prostředí runtime.  
  
## <a name="programming-tips"></a>Tipy k programování  
  
-   **Spolupráce aspekty.** Při vzájemném propojování součástí, které nejsou napsané pro rozhraní .NET Framework, například objekty automatizace nebo COM, uvědomte si, že datum a čas v jiných prostředích typy nejsou kompatibilní s jazykem Visual Basic `Date` typu. Pokud takové součásti předáváte data a času argument, deklarujte ho jako `Double` místo `Date` v jazyce Visual Basic code a použít metody převodu <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> a <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>.  
  
-   **Znaky typu.** `Date` nemá žádný – znak typu literálu nebo – znak typu identifikátoru. Ale kompilátor zpracovává literály, které jsou uzavřeny v rámci symboly čísla (`# #`) jako `Date`.  
  
-   **Typ architektury.** Odpovídajícím typem v rozhraní .NET Framework je <xref:System.DateTime?displayProperty=nameWithType> struktury.  
  
## <a name="example"></a>Příklad  
 Proměnnou nebo konstantu `Date` obsahuje datový typ datum a čas. Toto dokládá následující příklad.  
  
```  
Dim someDateAndTime As Date = #8/13/2002 12:14 PM#  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.DateTime?displayProperty=nameWithType>  
 [Datové typy](../../../visual-basic/language-reference/data-types/index.md)  
 [Standardní řetězce formátu data a času](../../../standard/base-types/standard-date-and-time-format-strings.md)  
 [Vlastní řetězce formátu data a času](../../../standard/base-types/custom-date-and-time-format-strings.md)  
 [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
