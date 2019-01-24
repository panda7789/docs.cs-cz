---
title: 'Postupy: Vytvoření výčtu adresářů a souborů'
ms.date: 12/27/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 463c751ab03875b6af89c325981c65b7bc69d0ef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580457"
---
# <a name="how-to-enumerate-directories-and-files"></a>Postupy: Vytvoření výčtu adresářů a souborů
Vyčíslitelné kolekce poskytují lepší výkon než pole při práci s rozsáhlých kolekcí adresářů a souborů. Vytvoření výčtu adresářů a souborů, použijte metody, které vrací vyčíslitelné kolekce názvů adresář nebo soubor, nebo jejich <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, nebo <xref:System.IO.FileSystemInfo> objekty.  
  
Pokud chcete vyhledat a vrátí pouze názvy adresářů a souborů, použijte metody výčet <xref:System.IO.Directory> třídy. Pokud chcete vyhledat a vrátit jiné vlastnosti adresářů a souborů, použijte <xref:System.IO.DirectoryInfo> a <xref:System.IO.FileSystemInfo> třídy.  
  
Můžete použít vyčíslitelné kolekce z těchto metod, jako <xref:System.Collections.Generic.IEnumerable%601> parametr pro konstruktory tříd kolekcí, jako jsou <xref:System.Collections.Generic.List%601>.  
  
Následující tabulka shrnuje metody, které vrací vyčíslitelné kolekce souborů a adresářů:  
  
|K vyhledání a vrácení|Použít – metoda|  
|------------------|-------------------------------------|-------------------|  
|Názvy adresářů|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|Informace o adresáři (<xref:System.IO.DirectoryInfo>)|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|Názvy souborů|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
|Informace o souboru (<xref:System.IO.FileInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|Názvy pro položku systému souborů|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
|Informace o souborovém systému položku (<xref:System.IO.FileSystemInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
|Názvy adresářů a souborů |<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  

> [!NOTE]
> I když můžete okamžitě vytvořit výčet všech souborů v podadresářích nadřazený adresář pomocí <xref:System.IO.SearchOption.AllDirectories> možnost volitelné <xref:System.IO.SearchOption> výčet, <xref:System.UnauthorizedAccessException> chyby může být výčet neúplné. Zachytit tyto výjimky tak, že nejprve vytváření výčtů adresářů a potom výčet souborů.  
  
## <a name="examples-use-the-directory-class"></a>Příklady: Použití třídy adresáře  
  
V následujícím příkladu <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> metodu k získání seznamu názvů adresář nejvyšší úrovně v zadané cestě.  

[!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
[!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  

V následujícím příkladu <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> metoda rekurzivně výčet všechny názvy souborů v adresáře a podadresářů, které odpovídají určité vzoru. Pak přečte každý řádek v jednotlivých souborů a zobrazí řádky, které obsahují zadaného řetězce s názvy souborů a cesty.

[!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
[!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
## <a name="examples-use-the-directoryinfo-class"></a>Příklady: Použití třídy DirectoryInfo  
  
V následujícím příkladu <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> metodu do seznamu kolekce adresářů nejvyšší úrovně jehož <xref:System.IO.FileSystemInfo.CreationTimeUtc> je starší než určitým <xref:System.DateTime> hodnotu.  

[!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs)]
[!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb)]  
  
V následujícím příkladu <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> metodu pro výpis všech souborů, jejichž <xref:System.IO.FileInfo.Length> přesahuje 10 MB. Tento příklad nejprve vytvoří výčet adresářů nejvyšší úrovně, jak zachytávat výjimky možné neoprávněnému přístupu a potom vytvoří výčet souborů.  

[!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
[!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a>Viz také:

[Vstupně-výstupních operací souborů a datových proudů](../../../docs/standard/io/index.md)
