---
title: Sestavování konzolových aplikací v rozhraní .NET Framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET Framework, building console applications
- application development [.NET Framework], console
- console applications
ms.assetid: c21fb997-9f0e-40a5-8741-f73bba376bd8
ms.openlocfilehash: 1ec65795a7f3d706b2878dd8a8397ae42b61ce7e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132869"
---
# <a name="building-console-applications-in-the-net-framework"></a>Sestavování konzolových aplikací v rozhraní .NET Framework
Aplikace v .NET Framework mohou použít třídu <xref:System.Console?displayProperty=nameWithType> ke čtení znaků z a zápis znaků do konzoly. Data z konzoly se čtou ze standardního vstupního datového proudu, data do konzoly se zapisují do standardního výstupního proudu a data do konzoly se zapisují do standardního výstupního proudu chyb. Tyto datové proudy jsou automaticky spojeny s konzolou při spuštění aplikace a jsou prezentovány jako <xref:System.Console.In%2A>, <xref:System.Console.Out%2A>a <xref:System.Console.Error%2A> vlastnosti v uvedeném pořadí.  
  
 Hodnota vlastnosti <xref:System.Console.In%2A?displayProperty=nameWithType> je objekt <xref:System.IO.TextReader?displayProperty=nameWithType>, zatímco hodnoty <xref:System.Console.Out%2A?displayProperty=nameWithType> a <xref:System.Console.Error%2A?displayProperty=nameWithType>ch vlastností jsou <xref:System.IO.TextWriter?displayProperty=nameWithType> objekty. Tyto vlastnosti můžete přidružit k datovým proudům, které nepředstavuje konzolu, což vám umožní nasměrovat datový proud na jiné místo pro vstup nebo výstup. Můžete například přesměrovat výstup do souboru nastavením vlastnosti <xref:System.Console.Out%2A?displayProperty=nameWithType> na <xref:System.IO.StreamWriter?displayProperty=nameWithType>, která zapouzdřuje <xref:System.IO.FileStream?displayProperty=nameWithType> prostřednictvím metody <xref:System.Console.SetOut%2A?displayProperty=nameWithType>. Vlastnosti <xref:System.Console.In%2A?displayProperty=nameWithType> a <xref:System.Console.Out%2A?displayProperty=nameWithType> nemusí odkazovat na stejný datový proud.  
  
> [!NOTE]
> Další informace o vytváření konzolových aplikací, včetně příkladů v C#, Visual Basic a C++naleznete v dokumentaci ke třídě <xref:System.Console>.  
  
 Pokud konzola neexistuje, stejně jako v aplikaci pro systém Windows, výstup zapsaný do standardního výstupního datového proudu nebude viditelný, protože není k dispozici žádná konzola pro zápis informací do. Zápis informací do nepřístupné konzoly nezpůsobí vyvolání výjimky.  
  
 Alternativně, pokud chcete povolit konzolu pro čtení a zápis v rámci aplikace založené na systému Windows, která je vyvíjena pomocí sady Visual Studio, otevřete dialogové okno **vlastnosti** projektu, klikněte na kartu **aplikace** a nastavte **Typ aplikace** . do **konzolové aplikace**.  
  
 Konzolové aplikace chybí pumpa zpráv, která se spouští ve výchozím nastavení. Proto se může stát, že volání konzoly Microsoft Win32 časovače selže.  
  
 Třída **System. Console** obsahuje metody, které mohou číst jednotlivé znaky nebo celé řádky z konzoly. Jiné metody převádějí data a formátuje řetězce a pak zapisují formátované řetězce do konzoly. Další informace o formátování řetězců naleznete v tématu [Formatting Types](../../docs/standard/base-types/formatting-types.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Console?displayProperty=nameWithType>
- [Typy formátování](../../docs/standard/base-types/formatting-types.md)
