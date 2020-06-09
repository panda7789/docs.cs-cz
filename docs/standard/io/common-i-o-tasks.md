---
title: Obecné vstupně-výstupní úlohy
description: Naučte se provádět běžné úlohy se soubory & běžných úlohách adresáře pomocí tříd & metod v oboru názvů System.IO v .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- I/O, common tasks
ms.assetid: bf00c380-706a-4e38-b829-454a480629fc
ms.openlocfilehash: 4b97b4e464622e482a9ef45e143865ee82e6b5d4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598603"
---
# <a name="common-io-tasks"></a>Obecné vstupně-výstupní úlohy
<xref:System.IO>Obor názvů poskytuje několik tříd, které umožňují provádět různé akce, jako je čtení a zápis, k provádění souborů, adresářů a datových proudů. Další informace najdete v tématu [vstupně-výstupní operace se soubory a datovým proudem](index.md).  
  
## <a name="common-file-tasks"></a>Běžné úlohy se soubory  
  
|Požadovaná akce...|Další informace naleznete v příkladu v tomto tématu...|  
|-------------------|--------------------------------------|  
|Vytvoření textového souboru|Metoda <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType><br /><br /> Metoda <xref:System.IO.FileInfo.CreateText%2A?displayProperty=nameWithType><br /><br /> Metoda <xref:System.IO.File.Create%2A?displayProperty=nameWithType><br /><br /> Metoda <xref:System.IO.FileInfo.Create%2A?displayProperty=nameWithType>|  
|Zápis do textového souboru|[Postupy: Zápis textu do souboru](how-to-write-text-to-a-file.md)<br /><br /> [Postupy: Zápis do textového souboru (C++/CLI)](/cpp/dotnet/how-to-write-a-text-file-cpp-cli)|  
|Čtení z textového souboru|[Postupy: Čtení textu ze souboru](how-to-read-text-from-a-file.md)|  
|Připojení textu k souboru|[Postupy: Otevření a připojení k souboru protokolu](how-to-open-and-append-to-a-log-file.md)<br /><br /> Metoda <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType><br /><br /> Metoda <xref:System.IO.FileInfo.AppendText%2A?displayProperty=nameWithType>|  
|Přejmenování nebo přesunutí souboru|Metoda <xref:System.IO.File.Move%2A?displayProperty=nameWithType><br /><br /> Metoda <xref:System.IO.FileInfo.MoveTo%2A?displayProperty=nameWithType>|  
|Odstranění souboru|Metoda <xref:System.IO.File.Delete%2A?displayProperty=nameWithType><br /><br /> Metoda <xref:System.IO.FileInfo.Delete%2A?displayProperty=nameWithType>|  
|Kopírování souboru|Metoda <xref:System.IO.File.Copy%2A?displayProperty=nameWithType><br /><br /> Metoda <xref:System.IO.FileInfo.CopyTo%2A?displayProperty=nameWithType>|  
|Zjištění velikosti souboru|<xref:System.IO.FileInfo.Length%2A?displayProperty=nameWithType>majetek|  
|Zjištění atributů souboru|Metoda <xref:System.IO.File.GetAttributes%2A?displayProperty=nameWithType>|  
|Nastavení atributů souboru|Metoda <xref:System.IO.File.SetAttributes%2A?displayProperty=nameWithType>|  
|Zjištění existence souboru|Metoda <xref:System.IO.File.Exists%2A?displayProperty=nameWithType>|  
|Čtení z binárního souboru|[Postupy: Čtení a zápis do nově vytvořeného datového souboru](how-to-read-and-write-to-a-newly-created-data-file.md)|  
|Zápis do binárního souboru|[Postupy: Čtení a zápis do nově vytvořeného datového souboru](how-to-read-and-write-to-a-newly-created-data-file.md)|  
|Načtení přípony názvu souboru|Metoda <xref:System.IO.Path.GetExtension%2A?displayProperty=nameWithType>|  
|Získání plně kvalifikované cesty k souboru|Metoda <xref:System.IO.Path.GetFullPath%2A?displayProperty=nameWithType>|  
|Získání názvu a přípony souboru z cesty k souboru|Metoda <xref:System.IO.Path.GetFileName%2A?displayProperty=nameWithType>|  
|Změna přípony souboru|Metoda <xref:System.IO.Path.ChangeExtension%2A?displayProperty=nameWithType>|  
  
## <a name="common-directory-tasks"></a>Běžné úlohy s adresáři  
  
|Požadovaná akce...|Další informace naleznete v příkladu v tomto tématu...|  
|-------------------|--------------------------------------|  
|Přístup k souboru ve zvláštní složce, jako například Dokumenty|[Postupy: Zápis textu do souboru](how-to-write-text-to-a-file.md)|  
|Vytvoření adresáře|Metoda <xref:System.IO.Directory.CreateDirectory%2A?displayProperty=nameWithType><br /><br /> <xref:System.IO.FileInfo.Directory%2A?displayProperty=nameWithType>majetek|  
|Vytvoření podadresáře|Metoda <xref:System.IO.DirectoryInfo.CreateSubdirectory%2A?displayProperty=nameWithType>|  
|Přejmenování nebo přesunutí adresáře|Metoda <xref:System.IO.Directory.Move%2A?displayProperty=nameWithType><br /><br /> Metoda <xref:System.IO.DirectoryInfo.MoveTo%2A?displayProperty=nameWithType>|  
|Kopírování adresáře|[Postupy: Kopírování adresářů](how-to-copy-directories.md)|  
|Odstranění adresáře|Metoda <xref:System.IO.Directory.Delete%2A?displayProperty=nameWithType><br /><br /> Metoda <xref:System.IO.DirectoryInfo.Delete%2A?displayProperty=nameWithType>|  
|Zobrazení souborů a podadresářů v adresáři|[Postupy: Vytvoření výčtu adresářů a souborů](how-to-enumerate-directories-and-files.md)|  
|Vyhledání velikosti adresáře|Třída <xref:System.IO.Directory?displayProperty=nameWithType>|  
|Zjištění existence adresáře|Metoda <xref:System.IO.Directory.Exists%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Viz také

- [Vstupně-výstupní operace se soubory a datovým proudem](index.md)
- [Skládání streamů](composing-streams.md)
- [I/O asynchronní soubory](asynchronous-file-i-o.md)
