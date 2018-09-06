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
ms.openlocfilehash: 979989c3e1f90f3de47473aa1bd8bc5268520e57
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43872803"
---
# <a name="building-console-applications-in-the-net-framework"></a>Sestavování konzolových aplikací v rozhraní .NET Framework
Aplikace v rozhraní .NET Framework lze používat <xref:System.Console?displayProperty=nameWithType> třídy znaků z čtení a zápis znaků do konzoly. Ze standardního vstupního proudu je číst data z konzoly, data do konzoly se zapisují do standardního výstupního datového proudu a chyba data do konzoly se zapisují do výstupního datového proudu standardní chybu. Tyto datové proudy jsou automaticky spojeny s konzolou při spuštění aplikace a jsou uvedené jako <xref:System.Console.In%2A>, <xref:System.Console.Out%2A>, a <xref:System.Console.Error%2A> vlastnosti, v uvedeném pořadí.  
  
 Hodnota <xref:System.Console.In%2A?displayProperty=nameWithType> je vlastnost <xref:System.IO.TextReader?displayProperty=nameWithType> objektu, zatímco hodnoty <xref:System.Console.Out%2A?displayProperty=nameWithType> a <xref:System.Console.Error%2A?displayProperty=nameWithType> vlastnosti jsou <xref:System.IO.TextWriter?displayProperty=nameWithType> objekty. Tyto vlastnosti můžete přidružit s datovými proudy, které nereprezentují konzole umožňuje odkazovat na jiné umístění pro vstup nebo výstup datového proudu. Například přesměrujte výstup do souboru tak, že nastavíte <xref:System.Console.Out%2A?displayProperty=nameWithType> vlastnost <xref:System.IO.StreamWriter?displayProperty=nameWithType>, což zapouzdřuje <xref:System.IO.FileStream?displayProperty=nameWithType> prostřednictvím <xref:System.Console.SetOut%2A?displayProperty=nameWithType> metoda. <xref:System.Console.In%2A?displayProperty=nameWithType> a <xref:System.Console.Out%2A?displayProperty=nameWithType> vlastnosti nemusí odkazovat na stejný datový proud.  
  
> [!NOTE]
>  Další informace o vytváření konzolových aplikací, včetně příkladů v jazyce C#, Visual Basic a C++, naleznete v dokumentaci pro <xref:System.Console> třídy.  
  
 Pokud konzole neexistuje, stejně jako v případě aplikace založené na Windows nezobrazí výstup zapsány do standardního výstupního datového proudu, protože neexistuje žádný konzoly při zápisu informací do. Zápis informací do nedostupný konzoly nezpůsobí výjimku vyvolána.  
  
 Můžete také povolit konzolu pro čtení a zápis v rámci aplikace založené na Windows, která je vytvořena pomocí sady Visual Studio, otevřete v projektu **vlastnosti** dialogové okno, klikněte na tlačítko **aplikace** kartu a nastavit **typ aplikace** k **konzolovou aplikaci**.  
  
 Aplikace konzoly nemají pumpu zpráv, který se spustí ve výchozím nastavení. Proto se nemusí podařit konzoly volání časovače Microsoft Win32.  
  
 **System.Console** třída obsahuje metody, které může číst jednotlivé znaky nebo celé řádky z konzoly. Jiné metody převodu dat a formát řetězce a pak napište formátovaných řetězců do konzoly. Další informace o formátovacích řetězcích naleznete v tématu [Formatting Types](../../docs/standard/base-types/formatting-types.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Console?displayProperty=nameWithType>  
- [Typy formátování](../../docs/standard/base-types/formatting-types.md)
