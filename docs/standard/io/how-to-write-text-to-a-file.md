---
title: 'Postup: Zápis textu do souboru'
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
ms.openlocfilehash: ba1c1815f0e49c02d1f0ee3c48ba01b7c2f5e727
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160245"
---
# <a name="how-to-write-text-to-a-file"></a>Postup: Zápis textu do souboru
Toto téma ukazuje různé způsoby zápisu textu do souboru aplikace .NET.

Následující třídy a metody se obvykle používají k zápisu textu do souboru:  
  
- <xref:System.IO.StreamWriter>obsahuje metody pro zápis do souboru<xref:System.IO.StreamWriter.Write%2A> <xref:System.IO.TextWriter.WriteLine%2A>synchronně ( a )<xref:System.IO.StreamWriter.WriteAsync%2A> <xref:System.IO.StreamWriter.WriteLineAsync%2A>nebo asynchronně ( a ).  
  
- <xref:System.IO.File>Poskytuje statické metody pro zápis textu <xref:System.IO.File.WriteAllLines%2A> do <xref:System.IO.File.WriteAllText%2A>souboru, například a , <xref:System.IO.File.AppendAllLines%2A>nebo <xref:System.IO.File.AppendAllText%2A>pro <xref:System.IO.File.AppendText%2A>připojení textu k souboru, například , a .  
  
- <xref:System.IO.Path>je pro řetězce, které mají informace o cestě k souboru nebo adresáři. Obsahuje metodu <xref:System.IO.Path.Combine%2A> a v rozhraní .NET Core 2.1 a novější metody <xref:System.IO.Path.Join%2A> a, <xref:System.IO.Path.TryJoin%2A> které umožňují zřetězení řetězců k vytvoření cesty k souboru nebo adresáři.

> [!NOTE]
> Následující příklady ukazují pouze minimální množství kódu potřebné. Aplikace reálného světa obvykle poskytuje robustnější kontrolu chyb a zpracování výjimek.  
  
## <a name="example-synchronously-write-text-with-streamwriter"></a>Příklad: Synchronně psát text s StreamWriter

Následující příklad ukazuje, jak <xref:System.IO.StreamWriter> použít třídu synchronně psát text do nového souboru po jednom řádku. Vzhledem <xref:System.IO.StreamWriter> k tomu, že objekt `using` je deklarován a instancivaci v příkazu, <xref:System.IO.StreamWriter.Dispose%2A> metoda je vyvolána, která automaticky vyprázdní a zavře datový proud.  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/write.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/write.vb)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="example-synchronously-append-text-with-streamwriter"></a>Příklad: Synchronně připojit text s StreamWriter

Následující příklad ukazuje, jak <xref:System.IO.StreamWriter> použít třídu synchronně připojit text do textového souboru vytvořeného v prvním příkladu.

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/append.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/append.vb)]  

## <a name="example-asynchronously-write-text-with-streamwriter"></a>Příklad: Asynchronně psát text s StreamWriter

Následující příklad ukazuje, jak asynchronně zapisovat text <xref:System.IO.StreamWriter> do nového souboru pomocí třídy. Chcete-li <xref:System.IO.StreamWriter.WriteAsync%2A> vyvolat metodu, volání `async` metody musí být v rámci metody. Příklad Jazyka C# vyžaduje c# 7.1 nebo `async` novější, který přidává podporu pro modifikátor na vstupní bod programu.

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/async.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/async.vb)]  

## <a name="example-write-and-append-text-with-the-file-class"></a>Příklad: Zápis a připojení textu s třídou File

Následující příklad ukazuje, jak psát text do nového souboru a připojit <xref:System.IO.File> nové řádky textu do stejného souboru pomocí třídy. Metody <xref:System.IO.File.WriteAllText%2A> <xref:System.IO.File.AppendAllLines%2A> a automaticky otevírají a zavírají soubor. Pokud cesta, kterou <xref:System.IO.File.WriteAllText%2A> zadáte k metodě již existuje, soubor je přepsán.  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/file.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/file.vb)]  

## <a name="see-also"></a>Viz také

- <xref:System.IO.StreamWriter>
- <xref:System.IO.Path>
- <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>
- [Postup: Výčet adresářů a souborů](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)
- [Postup: Čtení a zápis do nově vytvořeného datového souboru](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)
- [Postup: Otevření a připojení k souboru protokolu](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)
- [Postup: Čtení textu ze souboru](../../../docs/standard/io/how-to-read-text-from-a-file.md)
- [Vstupně-tono-videa](../../../docs/standard/io/index.md)
