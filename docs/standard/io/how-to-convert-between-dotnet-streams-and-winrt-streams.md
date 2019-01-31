---
title: 'Postupy: Převod mezi rozhraní .NET Framework a prostředí Windows Runtime datové proudy (jenom Windows)'
ms.date: 01/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 23a763ea-8348-4244-9f8c-a4280b870b47
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dc38e69a79af7c7220b8e3b55d4cb1f4ca3695f6
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55255195"
---
# <a name="how-to-convert-between-net-framework-and-windows-runtime-streams-windows-only"></a>Postupy: Převod mezi rozhraní .NET Framework a prostředí Windows Runtime datové proudy (jenom Windows)

Rozhraní .NET Framework pro aplikace pro UPW je podmnožinou úplné rozhraní .NET Framework. Z důvodu zabezpečení a další požadavky pro aplikace pro UPW nelze použít úplnou sadu API rozhraní .NET Framework pro otevírání a čtení souborů. Další informace najdete v tématu [.NET pro aplikace UPW – přehled](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)). Rozhraní API pro .NET Framework však můžete použít pro jiné operace manipulace s datovým proudem. K práci s těmito proudy, je možné převádět mezi typem datového proudu rozhraní .NET Framework, jako <xref:System.IO.MemoryStream> nebo <xref:System.IO.FileStream>a datový proud Windows Runtime, jako <xref:Windows.Storage.Streams.IInputStream>, <xref:Windows.Storage.Streams.IOutputStream>, nebo <xref:Windows.Storage.Streams.IRandomAccessStream>.

[System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.aspx) třída obsahuje metody, které tyto převody usnadňují. Však základní rozdíly mezi proudy rozhraní .NET Framework a prostředí Windows Runtime ovlivní výsledky použití těchto metod, jak je popsáno v následujících částech:

## <a name="convert-from-a-windows-runtime-to-a-net-framework-stream"></a>Převod z modulu Windows Runtime na datový proud v rozhraní .NET Framework
Pro převod z datového proudu Windows Runtime na datový proud v rozhraní .NET Framework, použijte jednu z následujících [System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.aspx) metody:

- [System.IO.WindowsRuntimeStreamExtensions.AsStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstream.aspx) převede proud s náhodným přístupem v modulu Windows Runtime na spravovaný datový proud v rozhraní .NET pro aplikace pro UPW.
  
- [System.IO.WindowsRuntimeStreamExtensions.AsStreamForWrite](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstreamforwrite.aspx) převede výstupní datový proud Windows Runtime na spravovaný datový proud v rozhraní .NET pro aplikace pro UPW.
  
- [System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstreamforread.aspx) převede vstupní datový proud Windows Runtime na spravovaný datový proud v rozhraní .NET pro aplikace pro UPW.

Modul Windows Runtime nabízí datové proudy, které podporují pouze pro čtení, zápis, nebo čtení a zápis. Tyto možnosti jsou spravovány při převodu datového proudu Windows Runtime na datový proud v rozhraní .NET Framework. Dále platí, že pokud převedete datový proud Windows Runtime na datový proud rozhraní .NET Framework a zpět, získáte původní instanci Windows Runtime. 

Je vhodné používat metodu převodu, který odpovídá možnostem datového proudu Windows Runtime, který chcete převést. Nicméně od <xref:Windows.Storage.Streams.IRandomAccessStream> je čtení a zápisu (implementuje oba <xref:Windows.Storage.Streams.IOutputStream> a <xref:Windows.Storage.Streams.IInputStream>), metody převodu Udržovat možnosti původního datového proudu. Například použití [System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstreamforread.aspx) převést <xref:Windows.Storage.Streams.IRandomAccessStream> neomezuje převedený datový proud rozhraní .NET Framework ke. Je také zapisovat.

## <a name="example-convert-windows-runtime-random-access-to-net-framework-stream"></a>Příklad: Převést náhodného modulu Windows Runtime přístupu do datového proudu rozhraní .NET Framework
Chcete-li převést z datového proudu Windows Runtime náhodným přístupem na datový proud v rozhraní .NET Framework, použijte [System.IO.WindowsRuntimeStreamExtensions.AsStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstream.aspx) metody.

Následující příklad kódu vás vyzve k výběru souboru, otevře se rozhraní API Windows Runtime a převede ho na datový proud v rozhraní .NET Framework. Načte datový proud a uloží jej do bloku textu. Můžete pracovat většinou s datovým proudem s rozhraním API .NET Framework před vytvářením výsledků výstupu.

Chcete-li spustit tento příklad, vytvořit aplikaci UPW XAML, která obsahuje blok textu s názvem `TextBlock1` a tlačítko s názvem `Button1`. Přidružení tlačítko klikněte na událost s `button1_Click` metoda ukazuje příklad.

  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage1.xaml.cs)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage1.xaml.vb)]

## <a name="convert-from-a-net-framework-to-a-windows-runtime-stream"></a>Převést na rozhraní .NET Framework na datový proud Windows Runtime
Pro převod z datového proudu rozhraní .NET Framework na datový proud Windows Runtime, použijte jednu z následujících [System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.aspx) metody:

- [System.IO.WindowsRuntimeStreamExtensions.AsInputStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asinputstream.aspx) převede spravovaný datový proud v rozhraní .NET pro aplikace pro UPW pro vstupní datový proud Windows Runtime.
  
- [System.IO.WindowsRuntimeStreamExtensions.AsOutputStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asoutputstream.aspx) převede spravovaný datový proud v rozhraní .NET pro aplikace pro UPW do výstupního datového proudu Windows Runtime.
  
- [AsRandomAccessStream](../../../docs/standard/cross-platform/windowsruntimestreamextensions-asrandomaccessstream-method.md) převede spravovaný datový proud v rozhraní .NET pro aplikace pro UPW do datového proudu náhodný přístup, můžete použít modul Windows Runtime pro čtení nebo zápis.

Při převodu datového proudu rozhraní .NET Framework na datový proud Windows Runtime závisí možnosti převedeného datového proudu na původního datového proudu. Například, pokud původní datový proud podporuje čtení i zápis a zavoláte [System.IO.WindowsRuntimeStreamExtensions.AsInputStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asinputstream.aspx) k převedení datového proudu, je vrácený typ `IRandomAccessStream`. `IRandomAccessStream` implementuje `IInputStream` a `IOutputStream`a podporuje čtení a zápis.

Datové proudy rozhraní .NET framework nepodporují klonování, dokonce i po převodu. Pokud převedete datový proud rozhraní .NET Framework na datový proud prostředí Windows Runtime a volání <xref:Windows.Storage.Streams.InMemoryRandomAccessStream.GetInputStreamAt%2A> nebo <xref:Windows.Storage.Streams.IRandomAccessStream.GetOutputStreamAt%2A>, která volá <xref:Windows.Storage.Streams.RandomAccessStreamOverStream.CloneStream%2A>, nebo pokud zavoláte <xref:Windows.Storage.Streams.RandomAccessStreamOverStream.CloneStream%2A> přímo, dojde k výjimce.

## <a name="example-convert-net-framework-to-windows-runtime-random-access-stream"></a>Příklad: Převést rozhraní .NET Framework na datový proud Windows Runtime náhodný přístup

Chcete-li převést z datového proudu rozhraní .NET Framework na datový proud Windows Runtime náhodný přístup, použijte [AsRandomAccessStream](../../../docs/standard/cross-platform/windowsruntimestreamextensions-asrandomaccessstream-method.md) způsob, jak je znázorněno v následujícím příkladu:

> [!IMPORTANT]
> Ujistěte se, že datový proud rozhraní .NET Framework, které používáte podporuje vyhledávání nebo ho zkopírujte do datového proudu, který provede. Můžete použít <xref:System.IO.Stream.CanSeek%2A?displayProperty=nameWithType> vlastnost ke zjištění.

Chcete-li spustit tento příklad, vytvořit aplikaci UPW XAML, který cílí na .NET Framework 4.5.1 a obsahuje blok textu s názvem `TextBlock2` a tlačítko s názvem `Button2`. Přidružení tlačítko klikněte na událost s `button2_Click` metoda ukazuje příklad.

  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage2.xaml.cs)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage2.xaml.vb)]

## <a name="see-also"></a>Viz také:

- [Rychlý start: Čtení a zápis do souboru (Windows)](https://msdn.microsoft.com/library/windows/apps/hh464978.aspx)  
- [.NET pro Windows Store apps – přehled](https://msdn.microsoft.com/library/windows/apps/br230302.aspx)  
- [Aplikace .NET pro Windows Store: Podporované rozhraní API](https://msdn.microsoft.com/library/windows/apps/br230232.aspx)  
