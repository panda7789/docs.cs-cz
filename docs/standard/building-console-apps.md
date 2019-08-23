---
title: Sestavování konzolových aplikací v rozhraní .NET Framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET Framework, building console applications
- application development [.NET Framework], console
- console applications
ms.assetid: c21fb997-9f0e-40a5-8741-f73bba376bd8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5c1658f27b66d9447d191d23801eba2d659ce9c2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933889"
---
# <a name="building-console-applications-in-the-net-framework"></a>Sestavování konzolových aplikací v rozhraní .NET Framework
Aplikace v .NET Framework mohou <xref:System.Console?displayProperty=nameWithType> třídu používat ke čtení znaků a k zápisu znaků do konzoly. Data z konzoly se čtou ze standardního vstupního datového proudu, data do konzoly se zapisují do standardního výstupního proudu a data do konzoly se zapisují do standardního výstupního proudu chyb. Tyto streamy jsou automaticky spojeny s konzolou při spuštění aplikace a jsou prezentovány <xref:System.Console.In%2A>jako <xref:System.Console.Out%2A>vlastnosti, <xref:System.Console.Error%2A> a v uvedeném pořadí.  
  
 <xref:System.Console.In%2A?displayProperty=nameWithType> Hodnota vlastnosti <xref:System.Console.Out%2A?displayProperty=nameWithType> <xref:System.IO.TextWriter?displayProperty=nameWithType> je objekt, zatímco hodnoty vlastností a <xref:System.Console.Error%2A?displayProperty=nameWithType> jsou objekty. <xref:System.IO.TextReader?displayProperty=nameWithType> Tyto vlastnosti můžete přidružit k datovým proudům, které nepředstavuje konzolu, což vám umožní nasměrovat datový proud na jiné místo pro vstup nebo výstup. Můžete například přesměrovat <xref:System.Console.Out%2A?displayProperty=nameWithType> výstup do souboru nastavením vlastnosti <xref:System.IO.StreamWriter?displayProperty=nameWithType>na <xref:System.IO.FileStream?displayProperty=nameWithType> , který zapouzdřuje pomocí <xref:System.Console.SetOut%2A?displayProperty=nameWithType> metody. Vlastnosti <xref:System.Console.In%2A?displayProperty=nameWithType> a<xref:System.Console.Out%2A?displayProperty=nameWithType> nemusí odkazovat na stejný datový proud.  
  
> [!NOTE]
> Další informace o vytváření konzolových aplikací, včetně příkladů v C#, Visual Basic a C++naleznete v <xref:System.Console> dokumentaci ke třídě.  
  
 Pokud konzola neexistuje, stejně jako v aplikaci pro systém Windows, výstup zapsaný do standardního výstupního datového proudu nebude viditelný, protože není k dispozici žádná konzola pro zápis informací do. Zápis informací do nepřístupné konzoly nezpůsobí vyvolání výjimky.  
  
 Alternativně, pokud chcete povolit konzolu pro čtení a zápis v rámci aplikace založené na systému Windows, která je vyvíjena pomocí sady Visual Studio, otevřete dialogové okno **vlastnosti** projektu, klikněte na kartu **aplikace** a nastavte **Typ aplikace** . do **konzolové aplikace**.  
  
 Konzolové aplikace chybí pumpa zpráv, která se spouští ve výchozím nastavení. Proto se může stát, že volání konzoly Microsoft Win32 časovače selže.  
  
 Třída **System. Console** obsahuje metody, které mohou číst jednotlivé znaky nebo celé řádky z konzoly. Jiné metody převádějí data a formátuje řetězce a pak zapisují formátované řetězce do konzoly. Další informace o formátování řetězců naleznete v tématu [Formatting Types](../../docs/standard/base-types/formatting-types.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Console?displayProperty=nameWithType>
- [Typy formátování](../../docs/standard/base-types/formatting-types.md)
