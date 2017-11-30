---
title: "Sestavování konzolových aplikací v rozhraní .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework, building console applications
- application development [.NET Framework], console
- console applications
ms.assetid: c21fb997-9f0e-40a5-8741-f73bba376bd8
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4e0bc3f14a3d21776506f0a269a1a8c9f970cac0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="building-console-applications-in-the-net-framework"></a>Sestavování konzolových aplikací v rozhraní .NET Framework
Můžete použít aplikací v rozhraní .NET Framework <xref:System.Console?displayProperty=nameWithType> třídy ke čtení znaků z a zápis znaků do konzoly. Ze standardní vstupní proud je číst data z konzoly, data do konzoly se zapisují do standardního výstupního datového proudu a údaje o chybě do konzoly je zapsán do výstupního datového proudu standardní chyba. Tyto datové proudy jsou automaticky spojeny s konzolou při spuštění aplikace a jsou jako <xref:System.Console.In%2A>, <xref:System.Console.Out%2A>, a <xref:System.Console.Error%2A> vlastnosti, v uvedeném pořadí.  
  
 Hodnota <xref:System.Console.In%2A?displayProperty=nameWithType> vlastnost je <xref:System.IO.TextReader?displayProperty=nameWithType> objektu, zatímco hodnoty <xref:System.Console.Out%2A?displayProperty=nameWithType> a <xref:System.Console.Error%2A?displayProperty=nameWithType> vlastnosti jsou <xref:System.IO.TextWriter?displayProperty=nameWithType> objekty. Tyto vlastnosti můžete přidružit s datovými proudy, které nepředstavují konzole, což vám umožní bodu do jiného umístění pro vstup nebo výstup datového proudu. Například přesměrujte výstup do souboru nastavením <xref:System.Console.Out%2A?displayProperty=nameWithType> vlastnosti <xref:System.IO.StreamWriter?displayProperty=nameWithType>, který zapouzdřuje <xref:System.IO.FileStream?displayProperty=nameWithType> prostřednictvím <xref:System.Console.SetOut%2A?displayProperty=nameWithType> metoda. <xref:System.Console.In%2A?displayProperty=nameWithType> a <xref:System.Console.Out%2A?displayProperty=nameWithType> vlastnosti nemusíte odkazovat na stejného datového proudu.  
  
> [!NOTE]
>  Další informace o vytváření konzolových aplikací, včetně příkladů v C#, Visual Basic a C++, najdete v dokumentaci pro <xref:System.Console> třídy.  
  
 Pokud konzole neexistuje, jako v aplikaci založené na Windows nezobrazí výstup zapsán do standardního výstupního datového proudu, protože neexistuje žádné konzoly při zápisu informací do. Zápis informací do konzole nepřístupný nezpůsobí výjimku má být aktivována.  
  
 Můžete také pokud chcete povolit konzolu pro čtení a zápis v rámci aplikace systému Windows, který je vyvinuté pomocí sady Visual Studio, otevřete projektu **vlastnosti** dialogové okno, klikněte **aplikace** kartě a nastavte **typ aplikace** k **konzolové aplikace**.  
  
 Konzolové aplikace nedostatku zprávy odeslané, která se spouští ve výchozím nastavení. Proto se nemusí podařit konzoly volání časovače Microsoft Win32.  
  
 **System.Console** třída obsahuje metody, které může číst jednotlivé znaky nebo celé řádky z konzoly. Ostatní metody převod řetězců data a formát a zapište si formátované řetězce do konzoly. Další informace o formátování řetězce najdete v tématu [typy formátování](../../docs/standard/base-types/formatting-types.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Console?displayProperty=nameWithType>  
 [Typy formátování](../../docs/standard/base-types/formatting-types.md)
