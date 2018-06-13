---
title: 'Postupy: Převádění mezi datovými proudy rozhraní .NET Framework a datovými proudy prostředí Windows Runtime'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 23a763ea-8348-4244-9f8c-a4280b870b47
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f67f88cd7f690e56664fa45878d1c9ac1f8a6b6b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33577558"
---
# <a name="how-to-convert-between-net-framework-streams-and-windows-runtime-streams"></a>Postupy: Převádění mezi datovými proudy rozhraní .NET Framework a datovými proudy prostředí Windows Runtime
Rozhraní .NET Framework pro aplikace Windows Store je podmnožinou kompletního rozhraní .NET Framework. Z důvodu bezpečnosti a vzhledem k jiným požadavkům na aplikace pro Windows Store nelze použít úplnou sadu API rozhraní .NET Framework pro otevírání a čtení souborů. Další informace najdete v tématu [přehled aplikace .NET pro Windows Store](http://msdn.microsoft.com/library/windows/apps/br230302.aspx). Rozhraní API pro .NET Framework však můžete použít pro jiné operace manipulace s datovým proudem. K manipulaci s těchto datových proudů, možná bude potřeba převádět typ datového proudu rozhraní .NET Framework, jako <xref:System.IO.MemoryStream> nebo <xref:System.IO.FileStream>a prostředí Windows Runtime datového proudu jako [IInputStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.iinputstream.aspx), [IOutputStream ](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.ioutputstream.aspx), nebo [IRandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.irandomaccessstream.aspx).  
  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions>--> `System.IO.WindowsRuntimeStreamExtensions` Třída obsahuje metody, které umožňují snadnou tyto převody. Existují však základní rozdíly mezi datovými proudy v rozhraní .NET Framework a Windows Runtime, které ovlivní výsledky použití těchto metod. Podrobnosti jsou uvedeny v následujících částech.  
  
<a name="BKMK_ConvertingfromaWindowsRuntimestreamtoaNETFrameworkstream"></a>   
## <a name="converting-from-a-windows-runtime-stream-to-a-net-framework-stream"></a>Převod z datového proudu Windows Runtime na datový proud v rozhraní .NET Framework  
 Můžete převést z prostředí Windows Runtime datový proud na datový proud, rozhraní .NET Framework pomocí jedné z následujících <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions>--> `System.IO.WindowsRuntimeStreamExtensions` metody:  
  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsStream%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsStream`  
 Převede datový proud Windows Runtime s náhodným přístupem na spravovaný datový proud v podmnožině rozhraní .NET pro aplikace Windows Store.  
  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForWrite%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsStreamForWrite`
 Převede výstupní datový proud Windows Runtime na spravovaný datový proud v podmnožině rozhraní .NET pro aplikace Windows Store.  
  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead`  
 Převede vstupní datový proud Windows Runtime na spravovaný datový proud v podmnožině rozhraní .NET pro aplikace Windows Store.  
  
 Prostředí Windows Runtime nabízí datové proudy, které podporují pouze čtení, pouze zápis, nebo čtení a zápis. Tyto možnosti jsou spravovány při převodu datového proudu Windows Runtime do datového proudu rozhraní .NET Framework. Dále platí, že pokud převedete datový proud Windows Runtime na datový proud rozhraní .NET Framework a zpět, získáte původní instanci Windows Runtime. Doporučujeme používat metodu převodu, která odpovídá možnostem datového proudu Windows Runtime, který chcete převést. Ale protože [IRandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.irandomaccessstream.aspx) je možné číst a zapisovat (obě implementuje [IOutputStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.ioutputstream.aspx) a [IInputStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.iinputstream.aspx)), můžete použít libovolnou metodu převod a Možnosti původní datového proudu jsou zachovány. Například pomocí <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead` převést [IRandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.irandomaccessstream.aspx) nebude omezit převedený datového proudu rozhraní .NET Framework k probíhá pouze čitelný; bude také s možností zápisu.  
  
#### <a name="to-convert-from-a-windows-runtime-random-access-stream-to-a-net-framework-stream"></a>Převod z datového proudu Windows Runtime s náhodným přístupem na datový proud v rozhraní .NET Framework  
  
-   Použití <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsStream%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsStream` metoda.  
  
     Následující příklad kódu znázorňuje, jakým způsobem můžete uživatele vyzvat, aby vybral konkrétní soubor, otevřel jej pomocí rozhraní API Windows Runtime a poté jej převedl na proud rozhraní .NET Framework, který je přečten a převeden do bloku textu. V tomto scénáři budete před vytvářením výsledků výstupu pracovat většinou s datovým proudem s rozhraním API .NET Framework.  
  
     Pokud chcete spustit tento příklad, musíte vytvořit aplikaci Windows Store XAML, která obsahuje bloku s názvem `TextBlock1` a tlačítko s názvem `Button1`. Klikněte na tlačítko události musí být přidružen `button1_Click` metoda ukazuje příklad.  
  
     [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#imports)]
     [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#imports)]  
    [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#1)]
    [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#1)]  
  
<a name="BKMK_ConvertingfromaNETFrameworkstreamtoaWindowsRuntimestream"></a>   
## <a name="converting-from-a-net-framework-stream-to-a-windows-runtime-stream"></a>Převod z datového proudu rozhraní .NET Framework na datový proud Windows Runtime  
 Můžete převést z datového proudu rozhraní .NET Framework na datový proud, prostředí Windows Runtime pomocí jedné z následujících <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions>--> `System.IO.WindowsRuntimeStreamExtensions` metody:  
  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsInputStream%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsInputStream`  
 Převede spravovaný datový proud v podmnožině rozhraní .NET pro aplikace Windows Store na vstupní datový proud Windows Runtime.  
  
<!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsOutputStream%2A>  --> `System.IO.WindowsRuntimeStreamExtensions.AsOutputStream`
 Převede spravovaný datový proud v podmnožině rozhraní .NET pro aplikace Windows Store na výstupní datový proud Windows Runtime.  
  
 [AsRandomAccessStream](../../../docs/standard/cross-platform/windowsruntimestreamextensions-asrandomaccessstream-method.md)  
 Převede spravovaný datový proud v podmnožině rozhraní .NET pro aplikace Windows Store na datový proud s náhodným přístupem, který lze použít pro čtení a zápis v modulu Windows Runtime.  
  
 Při převodu datového proudu rozhraní .NET Framework na datový proud v modulu Windows Runtime závisí možnosti převedeného datového proudu na původním datovém proudu. Například, pokud původní datový proud podporuje čtení i zápis a volání <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsInputStream%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsInputStream` k převedení datového proudu, bude vrácená typ `IRandomAccessStream`, který implementuje `IInputStream` a `IOutputStream`a podporuje čtení a zápis  
  
 Datové proudy .NET Framework nepodporují klonování, a to ani po dokončení převodu. To znamená, že při převodu datového proudu rozhraní .NET Framework na datový proud prostředí Windows Runtime a volání [GetInputStreamAt](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.inmemoryrandomaccessstream.getinputstreamat.aspx) nebo [GetOutputStreamAt](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.irandomaccessstream.getoutputstreamat.aspx), které volání [CloneStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.randomaccessstreamoverstream.clonestream.aspx) nebo volání [CloneStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.randomaccessstreamoverstream.clonestream.aspx) přímo, dojde k výjimce.  
  
#### <a name="to-convert-from-a-net-framework-stream-to-a-windows-runtime-random-access-stream"></a>Převod z datového proudu rozhraní .NET Framework na datový proud Windows Runtime s náhodným přístupem  
  
-   Použití [AsRandomAccessStream](../../../docs/standard/cross-platform/windowsruntimestreamextensions-asrandomaccessstream-method.md) metoda, jak je znázorněno v následujícím příkladu.  
  
    > [!IMPORTANT]
    >  Ověřte, zda požadovaný datový proud rozhraní .NET Framework podporuje vyhledávání nebo kopírování do datového proudu, který tyto operace podporuje. Můžete použít <xref:System.IO.Stream.CanSeek%2A?displayProperty=nameWithType> vlastnost to bylo možné určit.  
  
     Pokud chcete spustit tento příklad, musíte vytvořit aplikaci Windows Store XAML, která cílí rozhraní .NET Framework 4.5.1 a obsahuje bloku s názvem `TextBlock2` a tlačítko s názvem `Button2`. Klikněte na tlačítko události musí být přidružen `button2_Click` metoda uvedeno v následujícím příkladu.  
  
     [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#imports)]
     [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#imports)]  
    [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#2)]
    [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 [Rychlý úvod: Čtení a zápis do souboru (Windows)](https://msdn.microsoft.com/library/windows/apps/hh464978.aspx)  
 [Přehled aplikace .NET pro Windows Store](http://msdn.microsoft.com/library/windows/apps/br230302.aspx)  
 [Aplikace .NET pro Windows Store – podporované rozhraní API](https://msdn.microsoft.com/library/windows/apps/br230232.aspx)
