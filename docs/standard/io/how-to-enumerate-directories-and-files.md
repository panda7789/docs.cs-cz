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
ms.openlocfilehash: 3de83395df9e8c89a92e85b96ddd15e9f0be6ad5
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44067156"
---
# <a name="how-to-enumerate-directories-and-files"></a>Postupy: Vytvoření výčtu adresářů a souborů
Můžete zobrazit výčet adresářů a souborů pomocí metod, které vrací vyčíslitelné kolekce řetězců názvů. Můžete také použít metody, které vrací vyčíslitelné kolekce <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, nebo <xref:System.IO.FileSystemInfo> objekty. Vyčíslitelné kolekce poskytují lepší výkon než pole při práci s rozsáhlých kolekcí adresářů a souborů.  
  
 Vyčíslitelné kolekce získané z těchto metod můžete také použít k zadání <xref:System.Collections.Generic.IEnumerable%601> parametr pro konstruktory kolekce tříd, jako <xref:System.Collections.Generic.List%601> třídy.  
  
 Pokud chcete získat jenom názvy adresářů a souborů, použijte metody výčet <xref:System.IO.Directory> třídy. Pokud chcete získat další vlastnosti adresářů a souborů, použijte <xref:System.IO.DirectoryInfo> a <xref:System.IO.FileSystemInfo> třídy.  
  
 Následující tabulka obsahuje pokyny pro metody, které vrací vyčíslitelné kolekce.  
  
|Výčet|Vyčíslitelné kolekce pro vrácení|Metoda se má použít|  
|------------------|-------------------------------------|-------------------|  
|Adresáře|Názvy adresářů|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
||Informace o adresáři (<xref:System.IO.DirectoryInfo>)|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|Soubory|Názvy souborů|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
||Informace o souboru (<xref:System.IO.FileInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|Informace o systému souborů|Položky systémového souboru|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
||Informace o souborovém systému (<xref:System.IO.FileSystemInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
  
 I když můžete okamžitě vytvořit výčet všech souborů v podadresářích nadřazený adresář pomocí <xref:System.IO.SearchOption.AllDirectories> poskytuje možnosti vyhledávání <xref:System.IO.SearchOption> výčet, před neoprávněným přístupem výjimky (<xref:System.UnauthorizedAccessException>) může způsobit, že bude výčet nebudou úplné. Pokud jsou tyto výjimky je to možné, můžete jejich zachycení a pokračovat tak, že nejprve vytváření výčtů adresářů a potom výčet souborů.  
  
### <a name="to-enumerate-directory-names"></a>Výčet názvů adresářů  
  
-   Použití <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> metoda získat seznam názvů adresářů nejvyšší úrovně v zadané cestě.  
  
     [!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
     [!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  
  
### <a name="to-enumerate-file-names-in-a-directory-and-subdirectories"></a>Výčet názvů souborů v adresáři a jeho podadresářích  
  
-   Použití <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> metoda prohledat adresář a (volitelně) jeho podadresářích a získat seznam názvů souborů, které odpovídají zadanému vyhledávacímu vzoru.  
  
     [!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
     [!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-directoryinfo-objects"></a>Vytvoření výčtu kolekce DirectoryInfo objektů  
  
-   Použití <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> metody pro získání kolekce adresářů nejvyšší úrovně.  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-fileinfo-objects-in-all-directories"></a>Vytvoření výčtu kolekce FileInfo objektů ve všech adresářích  
  
-   Použití <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> metody pro získání kolekce souborů, které vyhovují zadanému vyhledávacímu vzoru ve všech adresářích. Tento příklad nejprve vytvoří výčet adresářů nejvyšší úrovně pro zachycení výjimky je to možné neoprávněného přístupu a pak vytvoří výčet souborů.  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Vstup/výstup souborů a streamů](../../../docs/standard/io/index.md)
