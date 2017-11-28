---
title: "Date – datový typ (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Date
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
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 190b40888dc4a42075b7b6b27bdb1bd403a7efb5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="date-data-type-visual-basic"></a>Date – datový typ (Visual Basic)
Obsahuje hodnoty IEEE 64-bit (8 bajtů), které reprezentují rozsahu od 1. ledna roku 0001 až 31. prosince 9999 roku datum a čas od 12:00:00: 00 (půlnoc) prostřednictvím 11:59:59.9999999 PM. Každý přírůstek představuje 100 nanosekundách uplynulý čas od začátku 1. ledna roku 1 v gregoriánském kalendáři. Maximální hodnota 100 nanosekundách představuje před začátkem 1. ledna roku 10000.  
  
## <a name="remarks"></a>Poznámky  
 Použití `Date` datový typ obsahovat hodnoty data, času hodnoty nebo hodnoty data a času.  
  
 Výchozí hodnota `Date` je 0:00:00 (půlnoc) na 1. ledna 0001.  
  
 Můžete získat aktuální datum a čas z <xref:Microsoft.VisualBasic.DateAndTime> třídy.  
  
## <a name="format-requirements"></a>Požadavky na formát  
 Je nutné uzavřít `Date` literálu v rámci znaky (`# #`). Zadejte hodnoty date ve formátu M/d/rrrr, například `#5/31/1993#`, nebo RRRR MM-dd, například `#1993-5-31#`. Lomítka můžete použít při zadávání nejprve v roce.  Tento požadavek je nezávislý na národním prostředí, data počítače a nastavení formátu času.  
  
 Důvod tohoto omezení je, že význam kódu by nikdy změnit v závislosti na národním prostředí, ve kterém je aplikace spuštěna. Předpokládejme, pevné kódu `Date` literálu z `#3/4/1998#` a chcete-li znamenat 4. března 1998. V národním prostředí, která používá mm/dd/rrrr 3 nebo 4 nebo 1998 zkompiluje jako, který chcete. Ale Předpokládejme, že nasazení aplikace v mnoha zemích. V národním prostředí, která používá dd/mm/rrrr by do 3. dubna 1998 zkompilovat vaší pevně literál. V národním prostředí, která používá rrrr/mm/dd, by byl neplatný literál (duben 1998 0003) a způsobit chyby kompilátoru.  
  
## <a name="workarounds"></a>Alternativní řešení  
 Převést `Date` literál formát národní prostředí, nebo vlastní formát, zadejte literál k <xref:Microsoft.VisualBasic.Strings.Format%2A> funkce, zadání buď formátu předdefinovaných nebo uživatelsky definovaných data. Následující příklad ukazuje to.  
  
```  
MsgBox("The formatted date is " & Format(#5/31/1993#, "dddd, d MMM yyyy"))  
```  
  
 Alternativně můžete použít jednu z přetížené konstruktory <xref:System.DateTime> struktura ke kompilaci hodnota data a času. Následující příklad vytvoří hodnotu představující 31 může 1993 na 12:14 odpoledne.  
  
```  
Dim dateInMay As New System.DateTime(1993, 5, 31, 12, 14, 0)  
```  
  
## <a name="hour-format"></a>H formátu  
 Hodnota času ve formátu 12 hodin nebo 24 hodin, můžete zadat například `#1:15:30 PM#` nebo `#13:15:30#`. Ale pokud nezadáte dobu nebo do sekund, zadejte dop.  
  
## <a name="date-and-time-defaults"></a>Datum a čas výchozích hodnot  
 Pokud nebudou obsahovat datum v literálu datum/čas, Visual Basic nastaví datum součástí hodnotu 1. ledna 0001. Pokud nezadáte čas v literál datum a čas, Visual Basic nastaví časovou část hodnoty na začátek dne, který je půlnoc (0: 00:00).  
  
## <a name="type-conversions"></a>Převody typu  
 Pokud převedete `Date` hodnotu `String` typu, vykreslí datum podle formát krátkého data určeného národní prostředí runtime jazyka Visual Basic a vykreslí čas podle formát času (12 hodin nebo 24 hodin) určeného národní prostředí runtime.  
  
## <a name="programming-tips"></a>Tipy k programování  
  
-   **Spolupráce aspekty.** Pokud jsou během propojení s součásti, které nejsou určeny pro rozhraní .NET Framework pro příklad objekty automatizace nebo COM, mějte na paměti, která data a času typy v jiných prostředích nejsou kompatibilní s jazykem Visual Basic `Date` typu. Pokud tyto součásti jsou předány argumentem datum a čas, deklarujte ji jako `Double` místo `Date` v jazyce Visual Basic kód a použít metody převod <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> a <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>.  
  
-   **Znaky typu.** `Date`nemá žádnou – znak typu literálu nebo – znak typu identifikátoru. Ale kompilátor zpracovává literály uzavřené v rámci znaky (`# #`) jako `Date`.  
  
-   **Typ Framework.** Typ odpovídající v rozhraní .NET Framework je <xref:System.DateTime?displayProperty=nameWithType> struktura.  
  
## <a name="example"></a>Příklad  
 Proměnnou nebo konstantu `Date` obsahuje datový typ datum a čas. Toto dokládá následující příklad.  
  
```  
Dim someDateAndTime As Date = #8/13/2002 12:14 PM#  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.DateTime?displayProperty=nameWithType>  
 [Datové typy](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Řetězce formátu standardní hodnoty data a času](../../../standard/base-types/standard-date-and-time-format-strings.md)  
 [Řetězce formátu vlastní hodnota data a času](../../../standard/base-types/custom-date-and-time-format-strings.md)  
 [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Souhrn konverze](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
