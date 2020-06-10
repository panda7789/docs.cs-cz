---
title: 'Postupy: zobrazení výčtu adresářů a souborů'
description: Naučte se vytvářet výčet adresářů a souborů pomocí vyčíslitelné kolekce, což může poskytovat lepší výkon než pole v .NET.
ms.date: 12/27/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
ms.openlocfilehash: 276668f4a3eee89610a81b1256820770d1f72dc3
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662573"
---
# <a name="how-to-enumerate-directories-and-files"></a>Postupy: zobrazení výčtu adresářů a souborů
Vyčíslitelné kolekce poskytují lepší výkon než pole při práci s velkými kolekcemi adresářů a souborů. Chcete-li vytvořit výčet adresářů a souborů, použijte metody, které vracejí vyčíslitelné kolekce názvů adresářů nebo souborů, nebo jejich <xref:System.IO.DirectoryInfo> <xref:System.IO.FileInfo> objektů, nebo <xref:System.IO.FileSystemInfo> .  
  
Pokud chcete vyhledávat a vracet pouze názvy adresářů nebo souborů, použijte metody výčtu <xref:System.IO.Directory> třídy. Pokud chcete hledat a vracet jiné vlastnosti adresářů nebo souborů, použijte <xref:System.IO.DirectoryInfo> <xref:System.IO.FileSystemInfo> třídy a.  
  
Vyčíslitelné kolekce z těchto metod lze použít jako <xref:System.Collections.Generic.IEnumerable%601> parametr pro konstruktory tříd kolekcí, jako je <xref:System.Collections.Generic.List%601> .  
  
Následující tabulka shrnuje metody, které vracejí vyčíslitelné kolekce souborů a adresářů:  
  
|Hledání a vrácení|Use – metoda|  
|------------------|-------------------------------------|-------------------|  
|Názvy adresářů|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|Informace o adresáři ( <xref:System.IO.DirectoryInfo> )|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|Názvy souborů|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
|Informace o souboru ( <xref:System.IO.FileInfo> )|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|Názvy položek systému souborů|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
|Informace o záznamech systému souborů ( <xref:System.IO.FileSystemInfo> )|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
|Názvy adresářů a souborů |<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  

> [!NOTE]
> I když můžete okamžitě vytvořit výčet všech souborů v podadresářích nadřazeného adresáře pomocí <xref:System.IO.SearchOption.AllDirectories> Možnosti volitelného <xref:System.IO.SearchOption> výčtu, <xref:System.UnauthorizedAccessException> chyby mohou vytvořit výčet nekompletní. Tyto výjimky můžete zachytit při prvním vytváření výčtu adresářů a pak při vytváření výčtu souborů.  
  
## <a name="examples-use-the-directory-class"></a>Příklady: použití třídy adresáře  
  
Následující příklad používá <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> metodu k získání seznamu názvů adresářů nejvyšší úrovně v zadané cestě.  

[!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
[!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  

Následující příklad používá <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> metodu k rekurzivnímu zobrazení výčtu všech názvů souborů v adresáři a podadresářích, které odpovídají určitému vzoru. Pak přečte jednotlivé řádky jednotlivých souborů a zobrazí řádky, které obsahují zadaný řetězec, s názvy souborů a cestami.

[!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
[!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
## <a name="examples-use-the-directoryinfo-class"></a>Příklady: použití třídy DirectoryInfo  
  
Následující příklad používá <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> metodu k vypsání kolekce adresářů nejvyšší úrovně <xref:System.IO.FileSystemInfo.CreationTimeUtc> , jejichž hodnota je starší než určitá <xref:System.DateTime> hodnota.  

[!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs)]
[!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb)]  
  
Následující příklad používá <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> metodu k vypsání všech souborů, jejichž velikost <xref:System.IO.FileInfo.Length> překračuje 10 MB. Tento příklad nejprve vytvoří výčet adresářů nejvyšší úrovně, aby se zachytily možné výjimky neoprávněného přístupu, a potom vytvoří výčet souborů.  

[!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
[!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a>Viz také

- [Vstup/výstup souborů a streamů](index.md)
