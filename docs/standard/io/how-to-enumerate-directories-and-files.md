---
title: 'Postupy: Vytvoření výčtu adresářů a souborů'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4cd7b7542e5cf9352e965717368399dcf4a9ecd2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-enumerate-directories-and-files"></a>Postupy: Vytvoření výčtu adresářů a souborů
Můžete vytvořit výčet adresářů a souborů pomocí metod, které vrací vyčíslitelná kolekce řetězců jejich názvů. Můžete také použít metody, které vrací kolekce vyčíslitelná <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, nebo <xref:System.IO.FileSystemInfo> objekty. Vyčíslitelná kolekce poskytují lepší výkon než pole při práci s rozsáhlých kolekcí adresářů a souborů.  
  
 Vyčíslitelná kolekce získané z těchto metod můžete také použít k poskytování <xref:System.Collections.Generic.IEnumerable%601> parametr pro konstruktory kolekce tříd, jako <xref:System.Collections.Generic.List%601> třídy.  
  
 Pokud chcete získat pouze názvy adresáře nebo soubory, použijte výčtové metody <xref:System.IO.Directory> třídy. Pokud chcete získat další vlastnosti adresáře nebo soubory, použijte <xref:System.IO.DirectoryInfo> a <xref:System.IO.FileSystemInfo> třídy.  
  
 Následující tabulka poskytuje vodítko k metody, které vracejí vyčíslitelná kolekce.  
  
|Výčet|Vyčíslitelná kolekce vrátit|Metoda se má použít|  
|------------------|-------------------------------------|-------------------|  
|Adresáře|Názvy adresářů|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
||Informace o adresáři (<xref:System.IO.DirectoryInfo>)|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|Soubory|Názvy souborů|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
||Informace o souborech (<xref:System.IO.FileInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|Informace o systému souborů|Položky systémového souboru|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
||V systému souborů (<xref:System.IO.FileSystemInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
  
 I když můžete okamžitě vytvořit výčet všech souborů v podadresářích adresáře nadřazené pomocí <xref:System.IO.SearchOption.AllDirectories> hledání možnost poskytované <xref:System.IO.SearchOption> výčtu, výjimky neoprávněného přístupu (<xref:System.UnauthorizedAccessException>) může způsobit, že bude výčet být neúplné. Pokud tyto výjimky je možné, můžete je zachytit a pokračovat tak, že nejprve vytváření výčtu adresářů a pak výčet souborů.  
  
### <a name="to-enumerate-directory-names"></a>Vytvoření výčtu názvů adresářů  
  
-   Použití <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> metodu k získání seznamu názvů adresář nejvyšší úrovně v zadané cestě.  
  
     [!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
     [!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  
  
### <a name="to-enumerate-file-names-in-a-directory-and-subdirectories"></a>Výčet názvů souborů v adresáři a podadresáře  
  
-   Použití <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> metoda k hledání a (volitelně) jeho podadresářů adresáře a získat seznam názvů souborů, které odpovídají zadaný hledaný vzorku.  
  
     [!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
     [!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-directoryinfo-objects"></a>Vytvoření výčtu kolekce objektů DirectoryInfo  
  
-   Použití <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> metody pro získání kolekce adresářů nejvyšší úrovně.  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-fileinfo-objects-in-all-directories"></a>Vytvoření výčtu kolekce objektů FileInfo ve všech adresářích  
  
-   Použití <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> metodu za účelem získání kolekce souborů, které odpovídají zadanému vyhledávacímu vzorku ve všech adresářích. Tento příklad nejprve vytvoří výčet adresářů nejvyšší úrovně k zachycení výjimky možné neoprávněného přístupu a potom vytvoří výčet souborů.  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Vstup/výstup souborů a streamů](../../../docs/standard/io/index.md)
