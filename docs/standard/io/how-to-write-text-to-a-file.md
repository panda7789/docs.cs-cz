---
title: 'Postupy: Zápis textu do souboru'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 59b33c24c2821d0aef17f5feb67c1178810b939e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647786"
---
# <a name="how-to-write-text-to-a-file"></a>Postupy: Zápis textu do souboru
Toto téma ukazuje různé způsoby zápisu textu do souborů pro aplikace .NET. 

Následující třídy a metody se obvykle používají k zápisu textu do souboru:  
  
- <xref:System.IO.StreamWriter> obsahuje metody pro zápis do souboru synchronně (<xref:System.IO.StreamWriter.Write%2A> a <xref:System.IO.TextWriter.WriteLine%2A>) nebo asynchronně (<xref:System.IO.StreamWriter.WriteAsync%2A> a <xref:System.IO.StreamWriter.WriteLineAsync%2A>).  
  
- <xref:System.IO.File> poskytuje statické metody pro zápis textu do souboru, například <xref:System.IO.File.WriteAllLines%2A> a <xref:System.IO.File.WriteAllText%2A>, nebo přidat text do souboru, například <xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A>, a <xref:System.IO.File.AppendText%2A>.  
  
- <xref:System.IO.Path> slouží k řetězci, které obsahují informace o cestě souboru nebo adresáře. Obsahuje <xref:System.IO.Path.Combine%2A> metoda a, v .NET Core 2.1 a později, <xref:System.IO.Path.Join%2A> a <xref:System.IO.Path.TryJoin%2A> metody, které umožňují zřetězení řetězců k sestavení cesty k souboru nebo adresáře.

> [!NOTE]
> Následující příklady ukazují jenom minimální množství kódu, které jsou potřeba. Reálné aplikace obvykle poskytuje robustnější kontroly chyb a zpracování výjimek.  
  
## <a name="example-synchronously-write-text-with-streamwriter"></a>Příklad: Synchronně napsat text pomocí třídy StreamWriter

Následující příklad ukazuje způsob použití <xref:System.IO.StreamWriter> tříd synchronně zápisu textu na nový řádek jeden soubor současně. Protože <xref:System.IO.StreamWriter> objekt je deklarovaný a instance v `using` příkaz, <xref:System.IO.StreamWriter.Dispose%2A> je vyvolána metoda, která automaticky vyprázdní a zavře datový proud.  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/write.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/write.vb)]  

## <a name="example-synchronously-append-text-with-streamwriter"></a>Příklad: Synchronně připojit text pomocí třídy StreamWriter

Následující příklad ukazuje způsob použití <xref:System.IO.StreamWriter> tříd synchronně přidat text do textového souboru vytvořeného v prvním příkladu.   

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/append.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/append.vb)]  

## <a name="example-asynchronously-write-text-with-streamwriter"></a>Příklad: Asynchronně napsat text pomocí třídy StreamWriter

Následující příklad ukazuje způsob asynchronního zápisu textu do nového souboru pomocí <xref:System.IO.StreamWriter> třídy. K vyvolání <xref:System.IO.StreamWriter.WriteAsync%2A> metody volání metody, které musí být v rámci `async` metody. C# Příklad vyžaduje C# 7.1 nebo novější, který přidává podporu pro `async` modifikátor na vstupní bod programu. 

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/async.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/async.vb)]  

## <a name="example-write-and-append-text-with-the-file-class"></a>Příklad: Zapsat a připojit text pomocí třídy souboru

Následující příklad ukazuje, jak zápis textu do nového souboru a přidávat nové řádky textu do stejného souboru pomocí <xref:System.IO.File> třídy. <xref:System.IO.File.WriteAllText%2A> a <xref:System.IO.File.AppendAllLines%2A> metod otevřete a zavřete soubor automaticky. Pokud cesta poskytnete <xref:System.IO.File.WriteAllText%2A> metoda již existuje, přepíše se.  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/file.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/file.vb)]  

## <a name="see-also"></a>Viz také:

- <xref:System.IO.StreamWriter>
- <xref:System.IO.Path>
- <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>
- [Postupy: Vytvoření výčtu adresářů a souborů](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)
- [Postupy: Čtení a zápis do nově vytvořeného datového souboru](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)
- [Postupy: Otevření a připojení k souboru protokolu](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)
- [Postupy: Čtení textu ze souboru](../../../docs/standard/io/how-to-read-text-from-a-file.md)
- [Vstupně-výstupních operací souborů a datových proudů](../../../docs/standard/io/index.md)