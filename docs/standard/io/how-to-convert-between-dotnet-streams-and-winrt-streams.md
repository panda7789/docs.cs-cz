---
title: 'Postup: Převod mezi datovými proudy rozhraní .NET Framework a Windows Runtime (pouze systém Windows)'
ms.date: 01/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 23a763ea-8348-4244-9f8c-a4280b870b47
ms.openlocfilehash: 7413c3fae7d7189ec8dca43b0c77f6b56158f416
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159465"
---
# <a name="how-to-convert-between-net-framework-and-windows-runtime-streams-windows-only"></a>Postup: Převod mezi datovými proudy rozhraní .NET Framework a Windows Runtime (pouze systém Windows)

Rozhraní .NET Framework pro aplikace UPW je podmnožinou úplného rozhraní .NET Framework. Z důvodu zabezpečení a dalších požadavků na aplikace UPW nelze k otevírání a čtení souborů použít úplnou sadu rozhraní API rozhraní .NET Framework. Další informace naleznete v tématu [.NET pro přehled aplikací UPW](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)). Rozhraní API pro .NET Framework však můžete použít pro jiné operace manipulace s datovým proudem. Chcete-li manipulovat s těmito datovými proudy, můžete <xref:System.IO.MemoryStream> <xref:System.IO.FileStream>převést mezi typem datového proudu rozhraní .NET Framework, například nebo , a datovým proudem prostředí Windows Runtime, například <xref:Windows.Storage.Streams.IInputStream>, <xref:Windows.Storage.Streams.IOutputStream>nebo <xref:Windows.Storage.Streams.IRandomAccessStream>.

Třída <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=nameWithType> obsahuje metody, které tyto převody usnadňují. Základní rozdíly mezi datovými proudy rozhraní .NET Framework a Windows Runtime však ovlivňují výsledky použití těchto metod, jak je popsáno v následujících částech:

## <a name="convert-from-a-windows-runtime-to-a-net-framework-stream"></a>Převod z prostředí Windows Runtime na datový proud rozhraní .NET Framework
Chcete-li převést z datového proudu prostředí Windows Runtime <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=nameWithType> na datový proud rozhraní .NET Framework, použijte jednu z následujících metod:

- <xref:System.IO.WindowsRuntimeStreamExtensions.AsStream%2A?displayProperty=nameWithType>převede datový proud s náhodným přístupem v prostředí Windows Runtime na spravovaný datový proud v rozhraní .NET pro aplikace UPW.
  
- <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForWrite%2A?displayProperty=nameWithType>převede výstupní datový proud v prostředí Windows Runtime na spravovaný datový proud v rozhraní .NET pro aplikace UPW.
  
- <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead%2A?displayProperty=nameWithType>převede vstupní datový proud v prostředí Windows Runtime na spravovaný datový proud v rozhraní .NET pro aplikace UPW.

Prostředí Windows Runtime nabízí typy datových proudů, které podporují pouze čtení, zápis nebo čtení a zápis. Tyto možnosti jsou udržovány při převodu datového proudu prostředí Windows Runtime na datový proud rozhraní .NET Framework. Dále platí, že pokud převedete datový proud Windows Runtime na datový proud rozhraní .NET Framework a zpět, získáte původní instanci Windows Runtime.

Doporučujeme použít metodu převodu, která odpovídá možnostem datového proudu prostředí Windows Runtime, který chcete převést. Však <xref:Windows.Storage.Streams.IRandomAccessStream> vzhledem k tomu, že je <xref:Windows.Storage.Streams.IOutputStream> <xref:Windows.Storage.Streams.IInputStream>čitelný a zapisovatelný (implementuje oba a ), metody převodu zachovat možnosti původního datového proudu. Například pomocí <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead%2A?displayProperty=nameWithType> převést <xref:Windows.Storage.Streams.IRandomAccessStream> neomezuje převedený datový proud rozhraní .NET Framework na čitelné. Je to také zapisovatelné.

## <a name="example-convert-windows-runtime-random-access-to-net-framework-stream"></a>Příklad: Převod náhodného přístupu prostředí Windows Runtime na datový proud rozhraní .NET Framework
Chcete-li převést z datového proudu s náhodným přístupem <xref:System.IO.WindowsRuntimeStreamExtensions.AsStream%2A?displayProperty=nameWithType> prostředí Windows Runtime na datový proud rozhraní .NET Framework, použijte metodu.

Následující příklad kódu vás vyzve k výběru souboru, otevře jej pomocí rozhraní API prostředí Windows Runtime a převede jej na datový proud rozhraní .NET Framework. Přečte datový proud a výstupy do textového bloku. Obvykle byste manipulovat datový proud s rozhraní API rozhraní .NET Framework před vyčtením výsledků.

Chcete-li spustit tento příklad, vytvořte aplikaci UWP `TextBlock1` XAML, která obsahuje textový blok s názvem a tlačítko s názvem `Button1`. Přidružte událost `button1_Click` kliknutí na tlačítko k metodě uvedené v příkladu.

  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage1.xaml.cs)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage1.xaml.vb)]

## <a name="convert-from-a-net-framework-to-a-windows-runtime-stream"></a>Převod z rozhraní .NET Framework na datový proud prostředí Windows Runtime
Chcete-li převést z datového proudu rozhraní .NET Framework <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=nameWithType> na datový proud prostředí Windows Runtime, použijte jednu z následujících metod:

- <xref:System.IO.WindowsRuntimeStreamExtensions.AsInputStream%2A?displayProperty=nameWithType>převede spravovaný datový proud v rozhraní .NET pro aplikace UPW na vstupní datový proud v prostředí Windows Runtime.
  
- <xref:System.IO.WindowsRuntimeStreamExtensions.AsOutputStream%2A?displayProperty=nameWithType>převede spravovaný datový proud v rozhraní .NET pro aplikace UPW na výstupní datový proud v prostředí Windows Runtime.
  
- <xref:System.IO.WindowsRuntimeStreamExtensions.AsRandomAccessStream%2A?displayProperty=nameWithType>převede spravovaný datový proud v rozhraní .NET pro aplikace UPW na datový proud s náhodným přístupem, který může prostředí Windows Runtime použít pro čtení nebo zápis.

Při převodu datového proudu rozhraní .NET Framework na datový proud prostředí Windows Runtime závisí možnosti převedeného datového proudu na původním datovém proudu. Například pokud původní datový proud podporuje čtení i <xref:System.IO.WindowsRuntimeStreamExtensions.AsInputStream%2A?displayProperty=nameWithType> zápis a volání převést `IRandomAccessStream`datový proud, vrácený typ je . `IRandomAccessStream`a `IInputStream` , `IOutputStream`a podporuje čtení a zápis.

Datové proudy rozhraní .NET Framework nepodporují klonování, a to ani po převodu. Pokud převedete datový proud rozhraní .NET Framework <xref:Windows.Storage.Streams.InMemoryRandomAccessStream.GetInputStreamAt%2A> <xref:Windows.Storage.Streams.IRandomAccessStream.GetOutputStreamAt%2A>na datový <xref:Windows.Storage.Streams.RandomAccessStreamOverStream.CloneStream%2A>proud prostředí <xref:Windows.Storage.Streams.RandomAccessStreamOverStream.CloneStream%2A> Windows Runtime a volání nebo , které volají , nebo pokud voláte přímo, dojde k výjimce.

## <a name="example-convert-net-framework-to-windows-runtime-random-access-stream"></a>Příklad: Převod rozhraní .NET Framework na datový proud s náhodným přístupem prostředí Windows Runtime

Chcete-li převést z datového proudu rozhraní .NET Framework <xref:System.IO.WindowsRuntimeStreamExtensions.AsRandomAccessStream%2A> na datový proud s náhodným přístupem prostředí Windows Runtime, použijte metodu, jak je znázorněno v následujícím příkladu:

> [!IMPORTANT]
> Ujistěte se, že datový proud rozhraní .NET Framework, který používáte, podporuje hledání, nebo jej zkopírujte do datového proudu, který jej používá. Vlastnost můžete <xref:System.IO.Stream.CanSeek%2A?displayProperty=nameWithType> použít k určení tohoto.

Chcete-li spustit tento příklad, vytvořte aplikaci UWP XAML, která cílí `TextBlock2` na rozhraní `Button2`.NET Framework 4.5.1 a obsahuje textový blok s názvem a tlačítko s názvem . Přidružte událost `button2_Click` kliknutí na tlačítko k metodě uvedené v příkladu.

  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage2.xaml.cs)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage2.xaml.vb)]

## <a name="see-also"></a>Viz také

- [Úvodní příručka: Čtení a zápis souboru (Windows)](https://docs.microsoft.com/previous-versions/windows/apps/hh464978(v=win.10))  
- [Přehled rozhraní .NET pro aplikace pro Windows Store](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140))  
- [Rozhraní API aplikací pro Windows Store](https://docs.microsoft.com/previous-versions/br230232(v=vs.120))  
