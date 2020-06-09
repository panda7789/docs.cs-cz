---
title: Asynchronní I/O soubory
description: Přečtěte si o asynchronních vstupně-výstupních operacích souborů v .NET. Naučte se asynchronní metody, které zjednodušují asynchronní operace, jako jsou ReadAsync, WriteAsync a další.
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
ms.openlocfilehash: 9506a366b6f1e363ec13550e5ed68c7176dd4d0a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598616"
---
# <a name="asynchronous-file-io"></a>Asynchronní I/O soubory

Asynchronní operace umožňují provádět vstupně-výstupní operace náročné na prostředky bez blokování hlavního vlákna. Toto posouzení výkonu je obzvláště důležité v aplikaci Windows 8. x nebo desktopové aplikaci, kde časově náročná operace může zablokovat vlákno uživatelského rozhraní a nastavit, aby se vaše aplikace zobrazila, jako by nefungovala.

Počínaje .NET Framework 4,5 obsahují vstupně-výstupní typy asynchronní metody pro zjednodušení asynchronních operací. Asynchronní metoda obsahuje v názvu parametr `Async`, jako například <xref:System.IO.Stream.ReadAsync%2A>, <xref:System.IO.Stream.WriteAsync%2A>, <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.TextReader.ReadLineAsync%2A> a <xref:System.IO.TextReader.ReadToEndAsync%2A>. Asynchronní metody jsou implementovány ve třídách datových proudů, jako například <xref:System.IO.Stream>, <xref:System.IO.FileStream> a <xref:System.IO.MemoryStream>, a ve třídách, které se používají pro čtení nebo zápis datových proudů, jako například <xref:System.IO.TextReader> a <xref:System.IO.TextWriter>.

V rozhraní .NET Framework 4 a předchozích verzích je pro implementaci asynchronních vstupně-výstupních operací nutné použít metody, jako jsou <xref:System.IO.Stream.BeginRead%2A> a <xref:System.IO.Stream.EndRead%2A>. Tyto metody jsou stále k dispozici v .NET Framework 4,5 pro podporu staršího kódu; asynchronní metody však umožňují snadnější implementaci asynchronních vstupně-výstupních operací.

Jazyky C# a Visual Basic mají dvě klíčová slova pro asynchronní programování:

- Modifikátor `Async` (Visual Basic) nebo `async` (jazyk C#), který se používá pro označení metody, jež obsahuje asynchronní operaci.

- Modifikátor `Await` (Visual Basic) nebo `await` (jazyk C#), který se používá pro výsledek asynchronní metody.

Pro implementaci asynchronních vstupně-výstupních operací je třeba použít klíčová slova spolu s asynchronními metodami, jak je znázorněno v následujících příkladech. Další informace naleznete v tématu [asynchronní programování s modifikátorem Async a await (C#)](../../csharp/programming-guide/concepts/async/index.md) nebo [asynchronní programování s použitím modifikátoru Async a operátoru Await (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md).

Následující příklad znázorňuje, jakým způsobem lze objekty <xref:System.IO.FileStream> použít pro asynchronní kopírování souborů z jednoho adresáře do druhého. Je třeba poznamenat, že obslužná rutina <xref:System.Web.UI.WebControls.Button.Click> pro ovládací prvek <xref:System.Windows.Controls.Button> je označena modifikátorem `async`, jelikož volá asynchronní metodu.

[!code-csharp[Asynchronous_File_IO_async#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example.cs#1)]
[!code-vb[Asynchronous_File_IO_async#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example.vb#1)]

Následující příklad se podobá předchozímu příkladu, ale pro asynchronní čtení a zápis obsahu textového souboru používá objekty <xref:System.IO.StreamReader> a <xref:System.IO.StreamWriter>.

[!code-csharp[Asynchronous_File_IO_async#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example2.cs#2)]
[!code-vb[Asynchronous_File_IO_async#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example2.vb#2)]

Následující příklad ukazuje soubor s kódem na pozadí a soubor XAML, který se používá k otevření souboru jako <xref:System.IO.Stream> v aplikaci Windows 8. x Store a ke čtení jeho obsahu pomocí instance <xref:System.IO.StreamReader> třídy. Pro otevření souboru jako datového proudu a přečtení jeho obsahu se používají asynchronní metody.

[!code-csharp[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml.cs#2)]
[!code-vb[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/vb/blankpage.xaml.vb#2)]

[!code-xaml[System.IO.WindowsRuntimeStorageExtensions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml#1)]

## <a name="see-also"></a>Viz také

- <xref:System.IO.Stream>
- [Vstupně-výstupní operace se soubory a datovým proudem](index.md)
- [Asynchronní programování s modifikátorem Async a operátoru Await (C#)](../../csharp/programming-guide/concepts/async/index.md)
- [Asynchronní programování s modifikátorem Async a operátoru Await (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md)
