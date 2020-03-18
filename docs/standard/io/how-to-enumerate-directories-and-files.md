---
title: 'Postup: Výčet adresářů a souborů'
ms.date: 12/27/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
ms.openlocfilehash: 6a26d0ef529b81976c4d2caafed34bb5f08d8d46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75707742"
---
# <a name="how-to-enumerate-directories-and-files"></a>Postup: Výčet adresářů a souborů
Výčet kolekce poskytují lepší výkon než pole při práci s velké kolekce adresářů a souborů. Chcete-li vytvořit výčet adresářů a souborů, použijte metody, které vracejí výčet <xref:System.IO.FileInfo>názvů <xref:System.IO.FileSystemInfo> adresářů nebo souborů nebo jejich <xref:System.IO.DirectoryInfo>, nebo objektů.  
  
Pokud chcete hledat a vrátit pouze názvy adresářů nebo souborů, použijte <xref:System.IO.Directory> metody výčtu třídy. Pokud chcete prohledávat a vracet další vlastnosti <xref:System.IO.DirectoryInfo> adresářů nebo souborů, použijte třídy a. <xref:System.IO.FileSystemInfo>  
  
Můžete použít výčet kolekce z těchto <xref:System.Collections.Generic.IEnumerable%601> metod jako parametr pro konstruktory tříd kolekce jako <xref:System.Collections.Generic.List%601>.  
  
Následující tabulka shrnuje metody, které vracejí početné kolekce souborů a adresářů:  
  
|Hledání a návrat|Použít metodu|  
|------------------|-------------------------------------|-------------------|  
|Názvy adresářů|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|Informace o<xref:System.IO.DirectoryInfo>adresáři ( )|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|Názvy souborů|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
|Informace o<xref:System.IO.FileInfo>souboru ( )|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|Názvy položek systému souborů|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
|Informace o zadávání<xref:System.IO.FileSystemInfo>systému souborů ( )|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
|Názvy adresářů a souborů |<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  

> [!NOTE]
> I když můžete okamžitě výčet všech souborů v podadresářích nadřazeného <xref:System.IO.SearchOption> adresáře pomocí <xref:System.UnauthorizedAccessException> <xref:System.IO.SearchOption.AllDirectories> možnosti volitelné výčtu, chyby mohou způsobit, že výčet neúplný. Tyto výjimky můžete zachytit nejprve výčet adresářů a potom výčet souborů.  
  
## <a name="examples-use-the-directory-class"></a>Příklady: Použití třídy Directory  
  
Následující příklad používá <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> metodu k získání seznamu názvů adresářů nejvyšší úrovně v zadané cestě.  

[!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
[!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  

Následující příklad používá <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> metodu k rekurzivnívý výčet všech názvů souborů v adresáři a podadresářích, které odpovídají určitému vzoru. Potom přečte každý řádek každého souboru a zobrazí řádky, které obsahují zadaný řetězec, s jejich názvy souborů a cesty.

[!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
[!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
## <a name="examples-use-the-directoryinfo-class"></a>Příklady: Použití třídy DirectoryInfo  
  
Následující příklad používá <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> metodu k zobrazení seznamu kolekce <xref:System.IO.FileSystemInfo.CreationTimeUtc> adresářů nejvyšší <xref:System.DateTime> úrovně, jejichž je starší než určitá hodnota.  

[!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs)]
[!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb)]  
  
Následující příklad používá <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> metodu k <xref:System.IO.FileInfo.Length> vypsat všechny soubory, jejichž přesahuje 10 MB. Tento příklad nejprve vytvoří výčet adresářů nejvyšší úrovně, zachytí možné výjimky neoprávněného přístupu a potom vytvoří výčet souborů.  

[!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
[!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a>Viz také

- [Vstupně-tono-videa](../../../docs/standard/io/index.md)
