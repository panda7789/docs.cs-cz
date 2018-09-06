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
ms.openlocfilehash: 96067ab6c8e13417158e4ebf7fae0e08cb9fbea4
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43867995"
---
# <a name="how-to-convert-between-net-framework-streams-and-windows-runtime-streams"></a>Postupy: Převádění mezi datovými proudy rozhraní .NET Framework a datovými proudy prostředí Windows Runtime

Rozhraní .NET Framework pro aplikace Windows Store je podmnožinou kompletního rozhraní .NET Framework. Z důvodu bezpečnosti a vzhledem k jiným požadavkům na aplikace pro Windows Store nelze použít úplnou sadu API rozhraní .NET Framework pro otevírání a čtení souborů. Další informace najdete v tématu [.NET pro Windows Store apps – přehled](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)). Rozhraní API pro .NET Framework však můžete použít pro jiné operace manipulace s datovým proudem. K práci s těmito proudy, možná bude nutné převést mezi typem datového proudu rozhraní .NET Framework, jako <xref:System.IO.MemoryStream> nebo <xref:System.IO.FileStream>a datový proud Windows Runtime, jako <xref:Windows.Storage.Streams.IInputStream>, <xref:Windows.Storage.Streams.IOutputStream>, nebo <xref:Windows.Storage.Streams.IRandomAccessStream>.

[System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.aspx) třída obsahuje metody, které tyto převody usnadňují. Existují však základní rozdíly mezi datovými proudy v rozhraní .NET Framework a Windows Runtime, které ovlivní výsledky použití těchto metod. Podrobnosti jsou uvedeny v následujících částech.

## <a name="converting-from-a-windows-runtime-stream-to-a-net-framework-stream"></a>Převod z datového proudu Windows Runtime na datový proud v rozhraní .NET Framework

Můžete převést z datového proudu Windows Runtime na datový proud v rozhraní .NET Framework pomocí jedné z následujících [System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.aspx) metody:

[System.IO.WindowsRuntimeStreamExtensions.AsStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstream.aspx)  
Převede datový proud Windows Runtime s náhodným přístupem na spravovaný datový proud v podmnožině rozhraní .NET pro aplikace Windows Store.

[System.IO.WindowsRuntimeStreamExtensions.AsStreamForWrite](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstreamforwrite.aspx)  
Převede výstupní datový proud Windows Runtime na spravovaný datový proud v podmnožině rozhraní .NET pro aplikace Windows Store.

[System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstreamforread.aspx)  
Převede vstupní datový proud Windows Runtime na spravovaný datový proud v podmnožině rozhraní .NET pro aplikace Windows Store.

Prostředí Windows Runtime nabízí datové proudy, které podporují pouze čtení, pouze zápis, nebo čtení a zápis. Tyto možnosti jsou spravovány při převodu datového proudu Windows Runtime do datového proudu rozhraní .NET Framework. Dále platí, že pokud převedete datový proud Windows Runtime na datový proud rozhraní .NET Framework a zpět, získáte původní instanci Windows Runtime. Doporučujeme používat metodu převodu, která odpovídá možnostem datového proudu Windows Runtime, který chcete převést. Nicméně od <xref:Windows.Storage.Streams.IRandomAccessStream> je čtení a zápisu (implementuje oba <xref:Windows.Storage.Streams.IOutputStream> a <xref:Windows.Storage.Streams.IInputStream>, můžete použít libovolnou metodu převodu a možnosti původního datového proudu jsou spravovány. Například použití [System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstreamforread.aspx) převést <xref:Windows.Storage.Streams.IRandomAccessStream> neomezí převedený datový proud rozhraní .NET Framework pouze ke; bude také zapisovat.

### <a name="to-convert-from-a-windows-runtime-random-access-stream-to-a-net-framework-stream"></a>Převod z datového proudu Windows Runtime s náhodným přístupem na datový proud v rozhraní .NET Framework

- Použití [System.IO.WindowsRuntimeStreamExtensions.AsStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstream.aspx) metody.

  Následující příklad kódu znázorňuje, jakým způsobem můžete uživatele vyzvat, aby vybral konkrétní soubor, otevřel jej pomocí rozhraní API Windows Runtime a poté jej převedl na proud rozhraní .NET Framework, který je přečten a převeden do bloku textu. V tomto scénáři budete před vytvářením výsledků výstupu pracovat většinou s datovým proudem s rozhraním API .NET Framework.

  Chcete-li spustit tento příklad, musíte vytvořit aplikaci Windows Store XAML, která obsahuje blok textu s názvem `TextBlock1` a tlačítko s názvem `Button1`. Kliknutí na tlačítko musí být přidružené k události `button1_Click` metoda ukazuje příklad.

  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#imports)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#imports)]
  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#1](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#1)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#1](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#1)]

## <a name="converting-from-a-net-framework-stream-to-a-windows-runtime-stream"></a>Převod z datového proudu rozhraní .NET Framework na datový proud Windows Runtime

Můžete převést z datového proudu rozhraní .NET Framework na datový proud Windows Runtime pomocí jedné z následujících [System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.aspx) metody:

[System.IO.WindowsRuntimeStreamExtensions.AsInputStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asinputstream.aspx) převede spravovaný datový proud v podmnožině rozhraní aplikace .NET pro Windows Store na vstupní datový proud Windows Runtime.

[System.IO.WindowsRuntimeStreamExtensions.AsOutputStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asoutputstream.aspx) převede spravovaný datový proud v podmnožině rozhraní aplikace .NET pro Windows Store na výstupní datový proud Windows Runtime.

[AsRandomAccessStream](../../../docs/standard/cross-platform/windowsruntimestreamextensions-asrandomaccessstream-method.md) převede spravovaný datový proud v podmnožině rozhraní .NET pro Windows Store aplikace proud s náhodným přístupem, který lze použít pro čtení nebo zápis v modulu Windows Runtime.

Při převodu datového proudu rozhraní .NET Framework na datový proud v modulu Windows Runtime závisí možnosti převedeného datového proudu na původním datovém proudu. Například, pokud původní datový proud podporuje čtení i zápis a zavoláte[System.IO.WindowsRuntimeStreamExtensions.AsInputStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asinputstream.aspx) pro převod datového proudu, vrácený typ bude `IRandomAccessStream`, která implementuje `IInputStream` a `IOutputStream`a podporuje čtení a zápis.

Datové proudy .NET Framework nepodporují klonování, a to ani po dokončení převodu. To znamená, že pokud převedete datový proud rozhraní .NET Framework na datový proud prostředí Windows Runtime a volání <xref:Windows.Storage.Streams.InMemoryRandomAccessStream.GetInputStreamAt%2A> nebo <xref:Windows.Storage.Streams.IRandomAccessStream.GetOutputStreamAt%2A>, která volá <xref:Windows.Storage.Streams.RandomAccessStreamOverStream.CloneStream%2A> nebo volání <xref:Windows.Storage.Streams.RandomAccessStreamOverStream.CloneStream%2A> přímo, dojde k výjimce.

### <a name="to-convert-from-a-net-framework-stream-to-a-windows-runtime-random-access-stream"></a>Převod z datového proudu rozhraní .NET Framework na datový proud Windows Runtime s náhodným přístupem

- Použití [AsRandomAccessStream](../../../docs/standard/cross-platform/windowsruntimestreamextensions-asrandomaccessstream-method.md) způsob, jak je znázorněno v následujícím příkladu:

  > [!IMPORTANT]
  > Ověřte, zda požadovaný datový proud rozhraní .NET Framework podporuje vyhledávání nebo kopírování do datového proudu, který tyto operace podporuje. Můžete použít <xref:System.IO.Stream.CanSeek%2A?displayProperty=nameWithType> vlastnost ke zjištění.

  Chcete-li spustit tento příklad, musíte vytvořit aplikaci Windows Store XAML, který cílí na .NET Framework 4.5.1 a obsahuje blok textu s názvem `TextBlock2` a tlačítko s názvem `Button2`. Kliknutí na tlačítko musí být přidružené k události `button2_Click` metodu uvedenou v tomto příkladu.

  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#imports)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#imports)]
  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#2](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#2)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#2](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#2)]

## <a name="see-also"></a>Viz také:

- [Rychlý start: Čtení a zápis do souboru (Windows)](https://msdn.microsoft.com/library/windows/apps/hh464978.aspx)  
- [.NET pro Windows Store apps – přehled](https://msdn.microsoft.com/library/windows/apps/br230302.aspx)  
- [Aplikace .NET pro Windows Store – podporována rozhraní API](https://msdn.microsoft.com/library/windows/apps/br230232.aspx)  