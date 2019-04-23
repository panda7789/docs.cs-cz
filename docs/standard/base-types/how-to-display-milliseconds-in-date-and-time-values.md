---
title: 'Postupy: Zobrazení milisekund v hodnotách data a času'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DateTime.ToString method
- displaying date and time data
- time [.NET Framework], milliseconds
- dates [.NET Framework], milliseconds
- milliseconds [.NET Framework]
ms.assetid: ae1a0610-90b9-4877-8eb6-4e30bc5e00cf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3950b7a8cf107fc06240f56e5f95eca4e6882251
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59314929"
---
# <a name="how-to-display-milliseconds-in-date-and-time-values"></a>Postupy: Zobrazení milisekund v hodnotách data a času
Výchozí metody pro formátování hodnot data a času, jako například <xref:System.DateTime.ToString?displayProperty=nameWithType>, zahrnují hodiny, minuty a sekundy příslušné časové hodnoty, ale neobsahují komponentu milisekund. Toto téma popisuje způsob začlenění komponenty milisekund do příslušné hodnoty data a času ve formátovaných řetězcích data a času.  
  
### <a name="to-display-the-millisecond-component-of-a-datetime-value"></a>Zobrazení komponenty milisekund hodnoty DateTime  
  
1. Při práci s řetězcovou reprezentací data je třeba ji převést na hodnotu <xref:System.DateTime> nebo <xref:System.DateTimeOffset> pomocí statické metody <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.Parse%28System.String%29?displayProperty=nameWithType>.  
  
2. Chcete-li extrahovat řetězcovou reprezentaci komponenty milisekund, zavolejte metodu hodnot data a času <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.ToString%2A> a předejte vzor vlastního formátu `fff` nebo `FFF` buď samostatně, nebo s dalšími specifikátory vlastního formátu jako parametr `format`.  
  
## <a name="example"></a>Příklad  
 Příklad zobrazí komponentu milisekund hodnot <xref:System.DateTime> a <xref:System.DateTimeOffset> do konzoly samostatně i jako součást delšího řetězce data a času.  
  
 [!code-csharp[Formatting.HowTo.Millisecond#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#1)]
 [!code-vb[Formatting.HowTo.Millisecond#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#1)]  
  
 Vzor formátu `fff` zahrnuje všechny koncové nuly v hodnotě milisekund. Vzor formátu `FFF` je potlačí. Rozdíl je znázorněn v následujícím příkladu.  
  
 [!code-csharp[Formatting.HowTo.Millisecond#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#2)]
 [!code-vb[Formatting.HowTo.Millisecond#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#2)]  
  
 Problém s definováním kompletního specifikátoru vlastního formátu, který zahrnuje komponentu milisekund příslušného data a času, spočívá v tom, že definuje pevně zakódovaný formát, který nemusí odpovídat uspořádání prvků času v aktuální jazykové verzi aplikace. Lepší alternativou je načíst jeden ze vzorů zobrazení data a času, které jsou definovány v objektu aktuální jazykové verze <xref:System.Globalization.DateTimeFormatInfo>, a upravit je tak, aby milisekundy obsahovaly. Tento příklad znázorňuje také tento přístup. Načte úplný vzor data a času pro aktuální jazykovou verzi z vlastnosti <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> a poté za vzor sekund vloží vlastní vzor `.ffff`. Příklad používá pro provedení této operace v rámci jednoho volání metody regulární výraz.  
  
 Pro zobrazení jiné části sekundového údaje než milisekund lze použít také specifikátor vlastního formátu. Například specifikátor vlastního formátu `f` nebo `F` zobrazí desetiny sekundy, specifikátor vlastního formátu `ff` nebo `FF` zobrazí setiny sekundy a specifikátor vlastního formátu `ffff` nebo `FFFF` zobrazí desetitisíciny sekundy. Zlomkové části milisekundy jsou ve vráceném řetězci namísto zaokrouhlení zkráceny. Tyto specifikátory formátu se používají v následujícím příkladu.  
  
 [!code-csharp[Formatting.HowTo.Millisecond#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#3)]
 [!code-vb[Formatting.HowTo.Millisecond#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#3)]  
  
> [!NOTE]
>  Je možné zobrazit velmi malé zlomkové jednotky sekundy, jako například desetitisíciny sekundy nebo stotisíciny sekundy. Tyto hodnoty však nemusí být smysluplné. Přesnost hodnot data a času závisí na rozlišení systémových hodin. V systému Windows NT 3.5 a novějších verzích a v operačním systému [!INCLUDE[windowsver](../../../includes/windowsver-md.md)] je rozlišení hodin přibližně 10–15 milisekund.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Je možné zkompilovat kód v příkazovém řádku pomocí souboru csc.exe nebo vb.exe. Chcete-li zkompilovat kód v sadě Visual Studio, vložte ho do šablony projektu konzolové aplikace.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Globalization.DateTimeFormatInfo>
- [Vlastní řetězce formátu data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
