---
title: 'Postupy: zápis textu do souboru'
ms.date: 01/04/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- writing text to files
- I/O [.NET Framework], writing text to files
- streams, writing text to files
- data streams, writing text to files
ms.assetid: 060cbe06-2adf-4337-9e7b-961a5c840208
ms.openlocfilehash: db0b7719105c9f6d42633df6c029a7a94f940908
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627978"
---
# <a name="how-to-write-text-to-a-file"></a>Postupy: zápis textu do souboru
V tomto tématu se dozvíte o různých způsobech zápisu textu do souboru pro aplikaci .NET. 

Následující třídy a metody se obvykle používají k zápisu textu do souboru:  
  
- <xref:System.IO.StreamWriter> obsahuje metody pro synchronně zapisování do souboru (<xref:System.IO.StreamWriter.Write%2A> a <xref:System.IO.TextWriter.WriteLine%2A>) nebo asynchronně (<xref:System.IO.StreamWriter.WriteAsync%2A> a <xref:System.IO.StreamWriter.WriteLineAsync%2A>).  
  
- <xref:System.IO.File> poskytuje statické metody pro zápis textu do souboru, například <xref:System.IO.File.WriteAllLines%2A> a <xref:System.IO.File.WriteAllText%2A>, nebo pro přidání textu do souboru, například <xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A>a <xref:System.IO.File.AppendText%2A>.  
  
- <xref:System.IO.Path> je pro řetězce, které obsahují informace o cestě k souboru nebo adresáři. Obsahuje metodu <xref:System.IO.Path.Combine%2A> a v .NET Core 2,1 a novějších metodách <xref:System.IO.Path.Join%2A> a <xref:System.IO.Path.TryJoin%2A>, které umožňují zřetězení řetězců k sestavení cesty k souboru nebo adresáři.

> [!NOTE]
> Následující příklady znázorňují pouze minimální požadovaný kód. Reálné aplikace obvykle poskytují robustnější kontrolu chyb a zpracování výjimek.  
  
## <a name="example-synchronously-write-text-with-streamwriter"></a>Příklad: synchronní zápis textu pomocí StreamWriter

Následující příklad ukazuje, jak použít třídu <xref:System.IO.StreamWriter> k synchronnímu zápisu textu do nového souboru po jednom řádku. Vzhledem k tomu, že objekt <xref:System.IO.StreamWriter> je deklarován a vytvořen v příkazu `using`, je vyvolána metoda <xref:System.IO.StreamWriter.Dispose%2A>, která automaticky vyprázdní a uzavře datový proud.  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/write.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/write.vb)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="example-synchronously-append-text-with-streamwriter"></a>Příklad: synchronní připojení textu pomocí StreamWriter

Následující příklad ukazuje, jak použít třídu <xref:System.IO.StreamWriter> k synchronnímu připojení textu k textovému souboru vytvořenému v prvním příkladu.   

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/append.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/append.vb)]  

## <a name="example-asynchronously-write-text-with-streamwriter"></a>Příklad: asynchronní zápis textu pomocí StreamWriter

Následující příklad ukazuje, jak asynchronně zapisovat text do nového souboru pomocí třídy <xref:System.IO.StreamWriter>. Chcete-li vyvolat metodu <xref:System.IO.StreamWriter.WriteAsync%2A>, musí být volání metody v rámci metody `async`. C# Příklad vyžaduje C# 7,1 nebo novější, který přidává podporu modifikátoru `async` v vstupním bodě programu. 

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/async.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/async.vb)]  

## <a name="example-write-and-append-text-with-the-file-class"></a>Příklad: zápis a přidávání textu pomocí třídy File

Následující příklad ukazuje, jak napsat text do nového souboru a připojit nové řádky textu ke stejnému souboru pomocí třídy <xref:System.IO.File>. Metody <xref:System.IO.File.WriteAllText%2A> a <xref:System.IO.File.AppendAllLines%2A> otevřou a zavřou soubor automaticky. Pokud cesta, kterou zadáte do metody <xref:System.IO.File.WriteAllText%2A>, již existuje, soubor bude přepsán.  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/file.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/file.vb)]  

## <a name="see-also"></a>Viz také

- <xref:System.IO.StreamWriter>
- <xref:System.IO.Path>
- <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>
- [Postupy: zobrazení výčtu adresářů a souborů](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)
- [Postupy: čtení a zápis do nově vytvořeného datového souboru](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)
- [Postupy: otevření a připojení k souboru protokolu](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)
- [Postupy: čtení textu ze souboru](../../../docs/standard/io/how-to-read-text-from-a-file.md)
- [Vstupně-výstupní operace se soubory a datovým proudem](../../../docs/standard/io/index.md)
