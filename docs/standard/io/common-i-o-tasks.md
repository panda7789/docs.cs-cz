---
title: Obecné vstupně-výstupní úlohy
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- I/O, common tasks
ms.assetid: bf00c380-706a-4e38-b829-454a480629fc
ms.openlocfilehash: 01e9d6b50bd7eeafea792a772ca86a81e40dafd4
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708175"
---
# <a name="common-io-tasks"></a>Obecné vstupně-výstupní úlohy
Obor názvů <xref:System.IO> poskytuje několik tříd, které umožňují provádět různé akce, jako je čtení a zápis, k provádění souborů, adresářů a datových proudů. Další informace najdete v tématu [vstupně-výstupní operace se soubory a datovým proudem](../../../docs/standard/io/index.md).  
  
## <a name="common-file-tasks"></a>Běžné úlohy se soubory  
  
|Postup...|Další informace naleznete v příkladu v tomto tématu...|  
|-------------------|--------------------------------------|  
|Vytvoření textového souboru|Metoda <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType><br /><br /> Metoda <xref:System.IO.FileInfo.CreateText%2A?displayProperty=nameWithType><br /><br /> Metoda <xref:System.IO.File.Create%2A?displayProperty=nameWithType><br /><br /> Metoda <xref:System.IO.FileInfo.Create%2A?displayProperty=nameWithType>|  
|Zápis do textového souboru|[Postupy: Zápis textu do souboru](../../../docs/standard/io/how-to-write-text-to-a-file.md)<br /><br /> [Postupy: Zápis do textového souboru (C++/CLI)](/cpp/dotnet/how-to-write-a-text-file-cpp-cli)|  
|Čtení z textového souboru|[Postupy: Čtení textu ze souboru](../../../docs/standard/io/how-to-read-text-from-a-file.md)|  
|Připojení textu k souboru|[Postupy: Otevření a připojení k souboru protokolu](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)<br /><br /> Metoda <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType><br /><br /> Metoda <xref:System.IO.FileInfo.AppendText%2A?displayProperty=nameWithType>|  
|Přejmenování nebo přesunutí souboru|Metoda <xref:System.IO.File.Move%2A?displayProperty=nameWithType><br /><br /> Metoda <xref:System.IO.FileInfo.MoveTo%2A?displayProperty=nameWithType>|  
|Odstranění souboru|Metoda <xref:System.IO.File.Delete%2A?displayProperty=nameWithType><br /><br /> Metoda <xref:System.IO.FileInfo.Delete%2A?displayProperty=nameWithType>|  
|Kopírování souboru|Metoda <xref:System.IO.File.Copy%2A?displayProperty=nameWithType><br /><br /> Metoda <xref:System.IO.FileInfo.CopyTo%2A?displayProperty=nameWithType>|  
|Zjištění velikosti souboru|<xref:System.IO.FileInfo.Length%2A?displayProperty=nameWithType> – vlastnost|  
|Zjištění atributů souboru|Metoda <xref:System.IO.File.GetAttributes%2A?displayProperty=nameWithType>|  
|Nastavení atributů souboru|Metoda <xref:System.IO.File.SetAttributes%2A?displayProperty=nameWithType>|  
|Zjištění existence souboru|Metoda <xref:System.IO.File.Exists%2A?displayProperty=nameWithType>|  
|Čtení z binárního souboru|[Postupy: Čtení a zápis do nově vytvořeného datového souboru](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)|  
|Zápis do binárního souboru|[Postupy: Čtení a zápis do nově vytvořeného datového souboru](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)|  
|Načtení přípony názvu souboru|Metoda <xref:System.IO.Path.GetExtension%2A?displayProperty=nameWithType>|  
|Získání plně kvalifikované cesty k souboru|Metoda <xref:System.IO.Path.GetFullPath%2A?displayProperty=nameWithType>|  
|Získání názvu a přípony souboru z cesty k souboru|Metoda <xref:System.IO.Path.GetFileName%2A?displayProperty=nameWithType>|  
|Změna přípony souboru|Metoda <xref:System.IO.Path.ChangeExtension%2A?displayProperty=nameWithType>|  
  
## <a name="common-directory-tasks"></a>Běžné úlohy s adresáři  
  
|Postup...|Další informace naleznete v příkladu v tomto tématu...|  
|-------------------|--------------------------------------|  
|Přístup k souboru ve zvláštní složce, jako například Dokumenty|[Postupy: Zápis textu do souboru](../../../docs/standard/io/how-to-write-text-to-a-file.md)|  
|Vytvoření adresáře|Metoda <xref:System.IO.Directory.CreateDirectory%2A?displayProperty=nameWithType><br /><br /> <xref:System.IO.FileInfo.Directory%2A?displayProperty=nameWithType> – vlastnost|  
|Vytvoření podadresáře|Metoda <xref:System.IO.DirectoryInfo.CreateSubdirectory%2A?displayProperty=nameWithType>|  
|Přejmenování nebo přesunutí adresáře|Metoda <xref:System.IO.Directory.Move%2A?displayProperty=nameWithType><br /><br /> Metoda <xref:System.IO.DirectoryInfo.MoveTo%2A?displayProperty=nameWithType>|  
|Kopírování adresáře|[Postupy: Kopírování adresářů](../../../docs/standard/io/how-to-copy-directories.md)|  
|Odstranění adresáře|Metoda <xref:System.IO.Directory.Delete%2A?displayProperty=nameWithType><br /><br /> Metoda <xref:System.IO.DirectoryInfo.Delete%2A?displayProperty=nameWithType>|  
|Zobrazení souborů a podadresářů v adresáři|[Postupy: Vytvoření výčtu adresářů a souborů](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)|  
|Vyhledání velikosti adresáře|Třída <xref:System.IO.Directory?displayProperty=nameWithType>|  
|Zjištění existence adresáře|Metoda <xref:System.IO.Directory.Exists%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Viz také:

- [Vstup/výstup souborů a datových proudů](../../../docs/standard/io/index.md)
- [Skládání streamů](../../../docs/standard/io/composing-streams.md)
- [Asynchronní vstupně-výstupní operace se soubory](../../../docs/standard/io/asynchronous-file-i-o.md)
