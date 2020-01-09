---
title: 'Postupy: zobrazení výčtu adresářů a souborů'
ms.date: 12/27/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
ms.openlocfilehash: 6a26d0ef529b81976c4d2caafed34bb5f08d8d46
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75707742"
---
# <a name="how-to-enumerate-directories-and-files"></a>Postupy: zobrazení výčtu adresářů a souborů
Vyčíslitelné kolekce poskytují lepší výkon než pole při práci s velkými kolekcemi adresářů a souborů. Chcete-li vytvořit výčet adresářů a souborů, použijte metody, které vracejí vyčíslitelné kolekce názvů adresářů nebo souborů, nebo jejich <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>nebo <xref:System.IO.FileSystemInfo> objektů.  
  
Pokud chcete vyhledávat a vracet pouze názvy adresářů nebo souborů, použijte metody výčtu třídy <xref:System.IO.Directory>. Pokud chcete hledat a vracet jiné vlastnosti adresářů nebo souborů, použijte třídy <xref:System.IO.DirectoryInfo> a <xref:System.IO.FileSystemInfo>.  
  
Vyčíslitelné kolekce z těchto metod lze použít jako parametr <xref:System.Collections.Generic.IEnumerable%601> pro konstruktory tříd kolekcí, jako je například <xref:System.Collections.Generic.List%601>.  
  
Následující tabulka shrnuje metody, které vracejí vyčíslitelné kolekce souborů a adresářů:  
  
|Hledání a vrácení|Use – metoda|  
|------------------|-------------------------------------|-------------------|  
|Názvy adresářů|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|Informace o adresáři (<xref:System.IO.DirectoryInfo>)|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|Názvy souborů|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
|Informace o souboru (<xref:System.IO.FileInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|Názvy položek systému souborů|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
|Informace o záznamech systému souborů (<xref:System.IO.FileSystemInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
|Názvy adresářů a souborů |<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  

> [!NOTE]
> I když můžete okamžitě vytvořit výčet všech souborů v podadresářích nadřazeného adresáře pomocí možnosti <xref:System.IO.SearchOption.AllDirectories> volitelného výčtu <xref:System.IO.SearchOption>, <xref:System.UnauthorizedAccessException> chyby můžou výčet nekompletní. Tyto výjimky můžete zachytit při prvním vytváření výčtu adresářů a pak při vytváření výčtu souborů.  
  
## <a name="examples-use-the-directory-class"></a>Příklady: použití třídy adresáře  
  
Následující příklad používá metodu <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> k získání seznamu názvů adresářů nejvyšší úrovně v zadané cestě.  

[!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
[!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  

Následující příklad používá metodu <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> k rekurzivnímu zobrazení výčtu všech názvů souborů v adresáři a podadresářích, které odpovídají určitému vzoru. Pak přečte jednotlivé řádky jednotlivých souborů a zobrazí řádky, které obsahují zadaný řetězec, s názvy souborů a cestami.

[!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
[!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
## <a name="examples-use-the-directoryinfo-class"></a>Příklady: použití třídy DirectoryInfo  
  
Následující příklad používá metodu <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> k vypsání kolekce adresářů nejvyšší úrovně, jejichž <xref:System.IO.FileSystemInfo.CreationTimeUtc> je dřívější než určitá <xref:System.DateTime> hodnota.  

[!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs)]
[!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb)]  
  
Následující příklad používá metodu <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> k vypsání všech souborů, jejichž <xref:System.IO.FileInfo.Length> překračuje 10 MB. Tento příklad nejprve vytvoří výčet adresářů nejvyšší úrovně, aby se zachytily možné výjimky neoprávněného přístupu, a potom vytvoří výčet souborů.  

[!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
[!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Vstupně-výstupní operace se soubory a datovým proudem](../../../docs/standard/io/index.md)
