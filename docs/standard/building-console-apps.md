---
title: Sestavování konzolových aplikací v rozhraní .NET Framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET Framework, building console applications
- application development [.NET Framework], console
- console applications
ms.assetid: c21fb997-9f0e-40a5-8741-f73bba376bd8
ms.openlocfilehash: 3c2031e2d038f32f6392a2eb734e4f8851d7b936
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291627"
---
# <a name="building-console-applications-in-the-net-framework"></a>Sestavování konzolových aplikací v rozhraní .NET Framework
Aplikace v .NET Framework mohou <xref:System.Console?displayProperty=nameWithType> třídu používat ke čtení znaků a k zápisu znaků do konzoly. Data z konzoly se čtou ze standardního vstupního datového proudu, data do konzoly se zapisují do standardního výstupního proudu a data do konzoly se zapisují do standardního výstupního proudu chyb. Tyto streamy jsou automaticky spojeny s konzolou při spuštění aplikace a jsou prezentovány <xref:System.Console.In%2A> jako <xref:System.Console.Out%2A> vlastnosti, a v <xref:System.Console.Error%2A> uvedeném pořadí.  
  
 Hodnota <xref:System.Console.In%2A?displayProperty=nameWithType> vlastnosti je <xref:System.IO.TextReader?displayProperty=nameWithType> objekt, zatímco hodnoty <xref:System.Console.Out%2A?displayProperty=nameWithType> <xref:System.Console.Error%2A?displayProperty=nameWithType> vlastností a jsou <xref:System.IO.TextWriter?displayProperty=nameWithType> objekty. Tyto vlastnosti můžete přidružit k datovým proudům, které nepředstavuje konzolu, což vám umožní nasměrovat datový proud na jiné místo pro vstup nebo výstup. Můžete například přesměrovat výstup do souboru nastavením <xref:System.Console.Out%2A?displayProperty=nameWithType> vlastnosti na <xref:System.IO.StreamWriter?displayProperty=nameWithType> , který zapouzdřuje <xref:System.IO.FileStream?displayProperty=nameWithType> pomocí <xref:System.Console.SetOut%2A?displayProperty=nameWithType> metody. <xref:System.Console.In%2A?displayProperty=nameWithType>Vlastnosti a nemusí <xref:System.Console.Out%2A?displayProperty=nameWithType> odkazovat na stejný datový proud.  
  
> [!NOTE]
> Další informace o vytváření konzolových aplikací, včetně příkladů v jazycích C#, Visual Basic a C++, naleznete v dokumentaci ke <xref:System.Console> třídě.  
  
 Pokud konzola neexistuje, stejně jako v aplikaci pro systém Windows, výstup zapsaný do standardního výstupního datového proudu nebude viditelný, protože není k dispozici žádná konzola pro zápis informací do. Zápis informací do nepřístupné konzoly nezpůsobí vyvolání výjimky.  
  
 Alternativně, pokud chcete povolit konzolu pro čtení a zápis v rámci aplikace založené na systému Windows, která je vyvíjena pomocí sady Visual Studio, otevřete dialogové okno **vlastnosti** projektu, klikněte na kartu **aplikace** a nastavte **Typ aplikace** na **Konzolová aplikace**.  
  
 Konzolové aplikace chybí pumpa zpráv, která se spouští ve výchozím nastavení. Proto se může stát, že volání konzoly Microsoft Win32 časovače selže.  
  
 Třída **System. Console** obsahuje metody, které mohou číst jednotlivé znaky nebo celé řádky z konzoly. Jiné metody převádějí data a formátuje řetězce a pak zapisují formátované řetězce do konzoly. Další informace o formátování řetězců naleznete v tématu [Formatting Types](base-types/formatting-types.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Console?displayProperty=nameWithType>
- [Typy formátování](base-types/formatting-types.md)
