---
title: Asynchronní I/O soubory
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- streams, synchronous streams
- asynchronous I/O
- synchronous I/O
- streams, asynchronous streams
- I/O [.NET Framework], asynchronous I/O
- Stream class, synchronous I/O
- data streams, asynchronous streams
- Stream class, asynchronous I/O
- multiple I/O requests
- data streams, synchronous streams
ms.assetid: dbdd55e7-d6b9-4f9e-8abb-ab0edd4457f7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cf253ff4a25ba902c16c6d00a8be4bf291166774
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44097651"
---
# <a name="asynchronous-file-io"></a>Asynchronní I/O soubory
Asynchronní operace umožňují provádět vstupně-výstupní operace náročné na prostředky bez blokování hlavního vlákna. Toto posouzení výkonu je důležité především v případě aplikací pro [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] nebo [!INCLUDE[desktop_appname](../../../includes/desktop-appname-md.md)], kde časově náročná operace může zablokovat vlákno uživatelského rozhraní a aplikace se pak jeví jako nefunkční.  
  
 Počínaje verzí [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] obsahují vstupně-výstupní typy asynchronní metody pro zjednodušení asynchronních operací. Asynchronní metoda obsahuje v názvu parametr `Async`, jako například <xref:System.IO.Stream.ReadAsync%2A>, <xref:System.IO.Stream.WriteAsync%2A>, <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.TextReader.ReadLineAsync%2A> a <xref:System.IO.TextReader.ReadToEndAsync%2A>. Asynchronní metody jsou implementovány ve třídách datových proudů, jako například <xref:System.IO.Stream>, <xref:System.IO.FileStream> a <xref:System.IO.MemoryStream>, a ve třídách, které se používají pro čtení nebo zápis datových proudů, jako například <xref:System.IO.TextReader> a <xref:System.IO.TextWriter>.  
  
 V rozhraní .NET Framework 4 a předchozích verzích je pro implementaci asynchronních vstupně-výstupních operací nutné použít metody, jako jsou <xref:System.IO.Stream.BeginRead%2A> a <xref:System.IO.Stream.EndRead%2A>. Tyto metody jsou i nadále k dispozici v rozhraní [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] z důvodu podpory původního kódu. Přesto však asynchronní metody umožňují snadnější implementaci asynchronních vstupně-výstupních operací.  
  
 Počínaje verzí [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] poskytuje sada Visual Studio dvě klíčová slova pro asynchronní programování:  
  
 Modifikátor `Async` (Visual Basic) nebo `async` (jazyk C#), který se používá pro označení metody, jež obsahuje asynchronní operaci.  
  
 Modifikátor `Await` (Visual Basic) nebo `await` (jazyk C#), který se používá pro výsledek asynchronní metody.  
  
 Pro implementaci asynchronních vstupně-výstupních operací je třeba použít klíčová slova spolu s asynchronními metodami, jak je znázorněno v následujících příkladech. Další informace najdete v tématu [Asynchronous Programming with Async and Await](https://msdn.microsoft.com/library/db854f91-ccef-4035-ae4d-0911fde808c7).  
  
 Následující příklad znázorňuje, jakým způsobem lze objekty <xref:System.IO.FileStream> použít pro asynchronní kopírování souborů z jednoho adresáře do druhého. Je třeba poznamenat, že obslužná rutina <xref:System.Web.UI.WebControls.Button.Click> pro ovládací prvek <xref:System.Windows.Controls.Button> je označena modifikátorem `async`, jelikož volá asynchronní metodu.  
  
 [!code-csharp[Asynchronous_File_IO_async#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example.cs#1)]
 [!code-vb[Asynchronous_File_IO_async#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example.vb#1)]  
  
 Následující příklad se podobá předchozímu příkladu, ale pro asynchronní čtení a zápis obsahu textového souboru používá objekty <xref:System.IO.StreamReader> a <xref:System.IO.StreamWriter>.  
  
 [!code-csharp[Asynchronous_File_IO_async#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example2.cs#2)]
 [!code-vb[Asynchronous_File_IO_async#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example2.vb#2)]  
  
 Následující příklad znázorňuje soubor kódu na pozadí a soubor XAML, které se používají pro otevření souboru jako <xref:System.IO.Stream> v aplikaci pro [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] a jehož obsah se přečte pomocí instance třídy <xref:System.IO.StreamReader>. Pro otevření souboru jako datového proudu a přečtení jeho obsahu se používají asynchronní metody.  
  
 [!code-csharp[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml.cs#2)]
 [!code-vb[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/vb/blankpage.xaml.vb#2)]  
  
 [!code-xaml[System.IO.WindowsRuntimeStorageExtensions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO.Stream>  
- [Vstup/výstup souborů a streamů](../../../docs/standard/io/index.md)  
- [Asynchronní programování pomocí modifikátoru Async a operátoru Await](https://msdn.microsoft.com/library/db854f91-ccef-4035-ae4d-0911fde808c7)
