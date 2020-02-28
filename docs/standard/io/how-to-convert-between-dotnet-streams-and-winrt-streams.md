---
title: 'Postupy: převod mezi datovými proudy .NET Framework a prostředí Windows Runtime (pouze Windows)'
ms.date: 01/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 23a763ea-8348-4244-9f8c-a4280b870b47
ms.openlocfilehash: 7413c3fae7d7189ec8dca43b0c77f6b56158f416
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159465"
---
# <a name="how-to-convert-between-net-framework-and-windows-runtime-streams-windows-only"></a>Postupy: převod mezi datovými proudy .NET Framework a prostředí Windows Runtime (pouze Windows)

.NET Framework pro aplikace UWP je podmnožinou úplných .NET Framework. Z důvodu zabezpečení a dalších požadavků pro aplikace pro UWP nemůžete použít úplnou sadu .NET Framework rozhraní API k otevírání a čtení souborů. Další informace najdete v tématu [Přehled aplikací .NET pro UWP](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)). Rozhraní API pro .NET Framework však můžete použít pro jiné operace manipulace s datovým proudem. Pokud chcete manipulovat s těmito datovými proudy, můžete převádět mezi .NET Frameworkm datovým proudem typu <xref:System.IO.MemoryStream> nebo <xref:System.IO.FileStream>, a prostředí Windows Runtime datovým proudem, jako je například <xref:Windows.Storage.Streams.IInputStream>, <xref:Windows.Storage.Streams.IOutputStream>nebo <xref:Windows.Storage.Streams.IRandomAccessStream>.

Třída <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=nameWithType> obsahuje metody, které usnadňují tyto převody. Základní rozdíly mezi .NET Framework a datovými proudy prostředí Windows Runtime ale ovlivňují výsledky používání těchto metod, jak je popsáno v následujících částech:

## <a name="convert-from-a-windows-runtime-to-a-net-framework-stream"></a>Převod z prostředí Windows Runtime na datový proud .NET Framework
Chcete-li převést datový proud z prostředí Windows Runtime na datový proud .NET Framework, použijte jednu z následujících metod <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=nameWithType>:

- <xref:System.IO.WindowsRuntimeStreamExtensions.AsStream%2A?displayProperty=nameWithType> převede datový proud s náhodným přístupem v prostředí Windows Runtime na spravovaný datový proud v rozhraní .NET pro aplikace UWP.
  
- <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForWrite%2A?displayProperty=nameWithType> převede výstupní datový proud v prostředí Windows Runtime na spravovaný datový proud v rozhraní .NET pro aplikace UWP.
  
- <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead%2A?displayProperty=nameWithType> převede vstupní datový proud v prostředí Windows Runtime na spravovaný datový proud v rozhraní .NET pro aplikace UWP.

Prostředí Windows Runtime nabízí typy streamů, které podporují jenom čtení, jenom zápis nebo čtení a zápis. Tyto možnosti jsou zachovány, když převedete prostředí Windows Runtime datový proud na datový proud .NET Framework. Dále platí, že pokud převedete datový proud Windows Runtime na datový proud rozhraní .NET Framework a zpět, získáte původní instanci Windows Runtime.

Osvědčeným postupem je použít metodu převodu, která odpovídá schopnostem prostředí Windows Runtimeho datového proudu, který chcete převést. Vzhledem k tomu, že <xref:Windows.Storage.Streams.IRandomAccessStream> je čitelný a zapisovatelný (implementuje <xref:Windows.Storage.Streams.IOutputStream> i <xref:Windows.Storage.Streams.IInputStream>), metody převodu udržují možnosti původního datového proudu. Například použití <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead%2A?displayProperty=nameWithType> k převodu <xref:Windows.Storage.Streams.IRandomAccessStream> neomezuje převedený .NET Framework datový proud na čitelné. Je také možné zapisovat.

## <a name="example-convert-windows-runtime-random-access-to-net-framework-stream"></a>Příklad: převod prostředí Windows Runtime náhodným přístupem na datový proud .NET Framework
K převodu z prostředí Windows Runtime datového proudu s náhodným přístupem do datového proudu .NET Framework použijte metodu <xref:System.IO.WindowsRuntimeStreamExtensions.AsStream%2A?displayProperty=nameWithType>.

Následující příklad kódu vás vyzve k výběru souboru, otevře ho pomocí prostředí Windows Runtime rozhraní API a pak ho převede na datový proud .NET Framework. Přečte stream a zapíše ho do textového bloku. Před výstupem výsledků byste obvykle měli datový proud s .NET Framework API pracovat.

Chcete-li spustit tento příklad, vytvořte aplikaci XAML pro UWP obsahující textový blok s názvem `TextBlock1` a tlačítko s názvem `Button1`. Přidružte událost kliknutí na tlačítko s metodou `button1_Click` zobrazenou v příkladu.

  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage1.xaml.cs)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage1.xaml.vb)]

## <a name="convert-from-a-net-framework-to-a-windows-runtime-stream"></a>Převod z .NET Framework na datový proud prostředí Windows Runtime
Chcete-li převést datový proud z .NET Framework na datový proud prostředí Windows Runtime, použijte jednu z následujících metod <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=nameWithType>:

- <xref:System.IO.WindowsRuntimeStreamExtensions.AsInputStream%2A?displayProperty=nameWithType> převede spravovaný datový proud v rozhraní .NET pro aplikace UWP na vstupní datový proud v prostředí Windows Runtime.
  
- <xref:System.IO.WindowsRuntimeStreamExtensions.AsOutputStream%2A?displayProperty=nameWithType> převede spravovaný datový proud v rozhraní .NET pro aplikace UWP na výstupní datový proud v prostředí Windows Runtime.
  
- <xref:System.IO.WindowsRuntimeStreamExtensions.AsRandomAccessStream%2A?displayProperty=nameWithType> převede spravovaný datový proud v rozhraní .NET pro aplikace UWP na datový proud s náhodným přístupem, který může prostředí Windows Runtime použít pro čtení nebo zápis.

Když převedete .NET Framework datový proud na datový proud prostředí Windows Runtime, funkce převedeného datového proudu závisí na původním datovém proudu. Například pokud původní datový proud podporuje čtení i zápis a zavoláte <xref:System.IO.WindowsRuntimeStreamExtensions.AsInputStream%2A?displayProperty=nameWithType> k převodu datového proudu, vrácený typ je `IRandomAccessStream`. `IRandomAccessStream` implementuje `IInputStream` a `IOutputStream`a podporuje čtení a zápis.

.NET Framework datové proudy nepodporují klonování, ani po převodu. Pokud převedete .NET Framework datový proud na datový proud prostředí Windows Runtime a zavoláte <xref:Windows.Storage.Streams.InMemoryRandomAccessStream.GetInputStreamAt%2A> nebo <xref:Windows.Storage.Streams.IRandomAccessStream.GetOutputStreamAt%2A>, které volají <xref:Windows.Storage.Streams.RandomAccessStreamOverStream.CloneStream%2A>, nebo pokud voláte <xref:Windows.Storage.Streams.RandomAccessStreamOverStream.CloneStream%2A> přímo, dojde k výjimce.

## <a name="example-convert-net-framework-to-windows-runtime-random-access-stream"></a>Příklad: převod .NET Framework na prostředí Windows Runtime datový proud s náhodným přístupem

Chcete-li převést datový proud z .NET Framework na prostředí Windows Runtime datový proud s náhodným přístupem, použijte metodu <xref:System.IO.WindowsRuntimeStreamExtensions.AsRandomAccessStream%2A>, jak je znázorněno v následujícím příkladu:

> [!IMPORTANT]
> Ujistěte se, že .NET Framework datový proud, který používáte, podporuje hledání nebo kopírování do datového proudu, který dělá. K určení této vlastnosti můžete použít vlastnost <xref:System.IO.Stream.CanSeek%2A?displayProperty=nameWithType>.

Chcete-li spustit tento příklad, vytvořte aplikaci XAML pro UWP, která cílí na .NET Framework 4.5.1 a obsahuje textový blok s názvem `TextBlock2` a tlačítko s názvem `Button2`. Přidružte událost kliknutí na tlačítko s metodou `button2_Click` zobrazenou v příkladu.

  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage2.xaml.cs)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage2.xaml.vb)]

## <a name="see-also"></a>Viz také

- [Rychlý Start: čtení a zápis souboru (Windows)](https://docs.microsoft.com/previous-versions/windows/apps/hh464978(v=win.10))  
- [Přehled aplikace .NET pro Windows Store](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140))  
- [Rozhraní API pro rozhraní .NET pro aplikace pro Windows Store](https://docs.microsoft.com/previous-versions/br230232(v=vs.120))  
