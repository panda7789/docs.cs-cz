---
title: 'Postupy: zápis textu do souboru'
description: Naučte se, jak zapisovat nebo připojovat text k souboru pro aplikaci .NET. Použijte metody z tříd StreamWriter nebo File pro synchronní nebo asynchronní zápis textu.
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
ms.openlocfilehash: 52d3d07f4ffdbdc6510425a65fc173d36e674d06
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2020
ms.locfileid: "84447209"
---
# <a name="how-to-write-text-to-a-file"></a>Postupy: zápis textu do souboru
V tomto tématu se dozvíte o různých způsobech zápisu textu do souboru pro aplikaci .NET.

Následující třídy a metody se obvykle používají k zápisu textu do souboru:  
  
- <xref:System.IO.StreamWriter>obsahuje metody, jak zapisovat do souboru synchronně ( <xref:System.IO.StreamWriter.Write%2A> a <xref:System.IO.TextWriter.WriteLine%2A> ) nebo asynchronně ( <xref:System.IO.StreamWriter.WriteAsync%2A> a <xref:System.IO.StreamWriter.WriteLineAsync%2A> ).  
  
- <xref:System.IO.File>poskytuje statické metody pro zápis textu do souboru, například <xref:System.IO.File.WriteAllLines%2A> a <xref:System.IO.File.WriteAllText%2A> , nebo k přidání textu do souboru, například, <xref:System.IO.File.AppendAllLines%2A> <xref:System.IO.File.AppendAllText%2A> a <xref:System.IO.File.AppendText%2A> .  
  
- <xref:System.IO.Path>je pro řetězce, které obsahují informace o cestě k souboru nebo adresáři. Obsahuje metodu a <xref:System.IO.Path.Combine%2A> v rozhraní .NET Core 2,1 a novějších <xref:System.IO.Path.Join%2A> <xref:System.IO.Path.TryJoin%2A> metody a, které umožňují zřetězení řetězců k sestavení cesty k souboru nebo adresáři.

> [!NOTE]
> Následující příklady znázorňují pouze minimální požadovaný kód. Reálné aplikace obvykle poskytují robustnější kontrolu chyb a zpracování výjimek.  
  
## <a name="example-synchronously-write-text-with-streamwriter"></a>Příklad: synchronní zápis textu pomocí StreamWriter

Následující příklad ukazuje, jak použít <xref:System.IO.StreamWriter> třídu k synchronnímu zápisu textu do nového souboru po jednom řádku. Vzhledem k tomu, že <xref:System.IO.StreamWriter> objekt je deklarován a vytvořen v `using` příkazu, je <xref:System.IO.StreamWriter.Dispose%2A> vyvolána metoda, která automaticky vyprázdní a uzavře datový proud.  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/write.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/write.vb)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="example-synchronously-append-text-with-streamwriter"></a>Příklad: synchronní připojení textu pomocí StreamWriter

Následující příklad ukazuje, jak použít <xref:System.IO.StreamWriter> třídu k synchronnímu připojení textu k textovému souboru vytvořenému v prvním příkladu.

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/append.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/append.vb)]  

## <a name="example-asynchronously-write-text-with-streamwriter"></a>Příklad: asynchronní zápis textu pomocí StreamWriter

Následující příklad ukazuje, jak asynchronně zapisovat text do nového souboru pomocí <xref:System.IO.StreamWriter> třídy. Chcete-li vyvolat <xref:System.IO.StreamWriter.WriteAsync%2A> metodu, musí být volání metody v rámci `async` metody. Příklad jazyka C# vyžaduje C# 7,1 nebo novější, který přidává podporu `async` modifikátoru v vstupním bodě programu.

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/async.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/async.vb)]  

## <a name="example-write-and-append-text-with-the-file-class"></a>Příklad: zápis a přidávání textu pomocí třídy File

Následující příklad ukazuje, jak napsat text do nového souboru a připojit nové řádky textu ke stejnému souboru pomocí <xref:System.IO.File> třídy. <xref:System.IO.File.WriteAllText%2A>Metody a <xref:System.IO.File.AppendAllLines%2A> otevřou a zavřou soubor automaticky. Pokud cesta, kterou zadáte do <xref:System.IO.File.WriteAllText%2A> metody, již existuje, je soubor přepsán.  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/file.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/file.vb)]  

## <a name="see-also"></a>Viz také

- <xref:System.IO.StreamWriter>
- <xref:System.IO.Path>
- <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>
- [Postupy: zobrazení výčtu adresářů a souborů](how-to-enumerate-directories-and-files.md)
- [Postupy: čtení a zápis do nově vytvořeného datového souboru](how-to-read-and-write-to-a-newly-created-data-file.md)
- [Postupy: otevření a připojení k souboru protokolu](how-to-open-and-append-to-a-log-file.md)
- [Postupy: čtení textu ze souboru](how-to-read-text-from-a-file.md)
- [Vstup/výstup souborů a streamů](index.md)
