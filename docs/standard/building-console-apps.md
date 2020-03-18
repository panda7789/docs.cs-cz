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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73132869"
---
# <a name="building-console-applications-in-the-net-framework"></a>Sestavování konzolových aplikací v rozhraní .NET Framework
Aplikace v rozhraní .NET <xref:System.Console?displayProperty=nameWithType> Framework mohou třídu používat ke čtení znaků a zápisu znaků do konzoly. Data z konzoly se čtou ze standardního vstupního datového proudu, data do konzoly se zapisují do standardního výstupního datového proudu a data o chybách do konzoly se zapisují do standardního datového proudu chyb. Tyto datové proudy jsou automaticky přidruženy ke konzole <xref:System.Console.In%2A>při <xref:System.Console.Out%2A>spuštění <xref:System.Console.Error%2A> aplikace a jsou prezentovány jako , a vlastnosti.  
  
 Hodnota vlastnosti <xref:System.Console.In%2A?displayProperty=nameWithType> je <xref:System.IO.TextReader?displayProperty=nameWithType> objekt, zatímco hodnoty <xref:System.Console.Out%2A?displayProperty=nameWithType> a <xref:System.Console.Error%2A?displayProperty=nameWithType> vlastnosti <xref:System.IO.TextWriter?displayProperty=nameWithType> jsou objekty. Tyto vlastnosti můžete přidružit k datovým proudům, které nepředstavují konzolu, což umožňuje nasměrovat datový proud do jiného umístění pro vstup nebo výstup. Například můžete přesměrovat výstup do souboru <xref:System.Console.Out%2A?displayProperty=nameWithType> nastavením <xref:System.IO.StreamWriter?displayProperty=nameWithType>vlastnosti na , která <xref:System.IO.FileStream?displayProperty=nameWithType> zapouzdřuje pomocí <xref:System.Console.SetOut%2A?displayProperty=nameWithType> metody. <xref:System.Console.In%2A?displayProperty=nameWithType> Vlastnosti <xref:System.Console.Out%2A?displayProperty=nameWithType> a není nutné odkazovat na stejný datový proud.  
  
> [!NOTE]
> Další informace o vytváření konzolových aplikací, včetně příkladů v jazyce C#, Visual <xref:System.Console> Basic a C++, naleznete v dokumentaci ke třídě.  
  
 Pokud konzola neexistuje, jako v aplikaci založené na systému Windows, výstup zapsaný do standardního výstupního datového proudu nebude viditelný, protože neexistuje žádná konzola pro zápis informací. Zápis informací do nepřístupné konzoly nezpůsobí výjimku, která má být vyvolána.  
  
 Chcete-li konzolu povolit pro čtení a zápis v aplikaci založené na systému Windows, která je vyvinuta pomocí sady Visual Studio, otevřete dialogové okno **Vlastnosti** projektu, klepněte na kartu **Aplikace** a nastavte **typ aplikace** na **konzolovou aplikaci**.  
  
 Konzolové aplikace postrádají čerpadlo zpráv, které se spustí ve výchozím nastavení. Proto může dojít k selhání volání konzoly microsoft Win32 časovače.  
  
 Třída **System.Console** má metody, které mohou číst jednotlivé znaky nebo celé řádky z konzoly. Jiné metody převádějí data a formátovací řetězce a pak zapisují formátované řetězce do konzoly. Další informace o formátovacích řetězcích naleznete v [tématu Typy formátování](../../docs/standard/base-types/formatting-types.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Console?displayProperty=nameWithType>
- [Typy formátování](../../docs/standard/base-types/formatting-types.md)
