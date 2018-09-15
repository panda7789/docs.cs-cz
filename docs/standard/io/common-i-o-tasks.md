---
title: Obecné vstupně-výstupní úlohy
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- I/O, common tasks
ms.assetid: bf00c380-706a-4e38-b829-454a480629fc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f205040e0f044ab04112683c7bdb8edccdfb9f71
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/15/2018
ms.locfileid: "45641505"
---
# <a name="common-io-tasks"></a>Obecné vstupně-výstupní úlohy
<xref:System.IO> Obor názvů poskytuje několik tříd, které umožňují nejrůznější akce, jako je čtení a zápis, pro soubory, adresáře a datové proudy. Další informace najdete v tématu [Souborová služba a vstupně-výstupní operace Stream](../../../docs/standard/io/index.md).  
  
## <a name="common-file-tasks"></a>Běžné úlohy se soubory  
  
|Postup...|Další informace naleznete v příkladu v tomto tématu...|  
|-------------------|--------------------------------------|  
|Vytvoření textového souboru|<xref:System.IO.File.CreateText%2A?displayProperty=nameWithType> – Metoda<br /><br /> <xref:System.IO.FileInfo.CreateText%2A?displayProperty=nameWithType> – Metoda<br /><br /> <xref:System.IO.File.Create%2A?displayProperty=nameWithType> – Metoda<br /><br /> <xref:System.IO.FileInfo.Create%2A?displayProperty=nameWithType> – Metoda|  
|Zápis do textového souboru|[Postupy: Zápis textu do souboru](../../../docs/standard/io/how-to-write-text-to-a-file.md)<br /><br /> [Postupy: Zápis do textového souboru (C++/CLI)](/cpp/dotnet/how-to-write-a-text-file-cpp-cli)|  
|Čtení z textového souboru|[Postupy: Čtení textu ze souboru](../../../docs/standard/io/how-to-read-text-from-a-file.md)|  
|Připojení textu k souboru|[Postupy: Otevření a připojení k souboru protokolu](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)<br /><br /> <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType> – Metoda<br /><br /> <xref:System.IO.FileInfo.AppendText%2A?displayProperty=nameWithType> – Metoda|  
|Přejmenování nebo přesunutí souboru|<xref:System.IO.File.Move%2A?displayProperty=nameWithType> – Metoda<br /><br /> <xref:System.IO.FileInfo.MoveTo%2A?displayProperty=nameWithType> – Metoda|  
|Odstranění souboru|<xref:System.IO.File.Delete%2A?displayProperty=nameWithType> – Metoda<br /><br /> <xref:System.IO.FileInfo.Delete%2A?displayProperty=nameWithType> – Metoda|  
|Kopírování souboru|<xref:System.IO.File.Copy%2A?displayProperty=nameWithType> – Metoda<br /><br /> <xref:System.IO.FileInfo.CopyTo%2A?displayProperty=nameWithType> – Metoda|  
|Zjištění velikosti souboru|<xref:System.IO.FileInfo.Length%2A?displayProperty=nameWithType> Vlastnost|  
|Zjištění atributů souboru|<xref:System.IO.File.GetAttributes%2A?displayProperty=nameWithType> – Metoda|  
|Nastavení atributů souboru|<xref:System.IO.File.SetAttributes%2A?displayProperty=nameWithType> – Metoda|  
|Zjištění existence souboru|<xref:System.IO.File.Exists%2A?displayProperty=nameWithType> – Metoda|  
|Čtení z binárního souboru|[Postupy: Čtení a zápis do nově vytvořeného datového souboru](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)|  
|Zápis do binárního souboru|[Postupy: Čtení a zápis do nově vytvořeného datového souboru](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)|  
|Načtení přípony názvu souboru|<xref:System.IO.Path.GetExtension%2A?displayProperty=nameWithType> – Metoda|  
|Získání plně kvalifikované cesty k souboru|<xref:System.IO.Path.GetFullPath%2A?displayProperty=nameWithType> – Metoda|  
|Získání názvu a přípony souboru z cesty k souboru|<xref:System.IO.Path.GetFileName%2A?displayProperty=nameWithType> – Metoda|  
|Změna přípony souboru|<xref:System.IO.Path.ChangeExtension%2A?displayProperty=nameWithType> – Metoda|  
  
## <a name="common-directory-tasks"></a>Běžné úlohy s adresáři  
  
|Postup...|Další informace naleznete v příkladu v tomto tématu...|  
|-------------------|--------------------------------------|  
|Přístup k souboru ve zvláštní složce, jako například Dokumenty|[Postupy: Zápis textu do souboru](../../../docs/standard/io/how-to-write-text-to-a-file.md)|  
|Vytvoření adresáře|<xref:System.IO.Directory.CreateDirectory%2A?displayProperty=nameWithType> – Metoda<br /><br /> <xref:System.IO.FileInfo.Directory%2A?displayProperty=nameWithType> Vlastnost|  
|Vytvoření podadresáře|<xref:System.IO.DirectoryInfo.CreateSubdirectory%2A?displayProperty=nameWithType> – Metoda|  
|Přejmenování nebo přesunutí adresáře|<xref:System.IO.Directory.Move%2A?displayProperty=nameWithType> – Metoda<br /><br /> <xref:System.IO.DirectoryInfo.MoveTo%2A?displayProperty=nameWithType> – Metoda|  
|Kopírování adresáře|[Postupy: Kopírování adresářů](../../../docs/standard/io/how-to-copy-directories.md)|  
|Odstranění adresáře|<xref:System.IO.Directory.Delete%2A?displayProperty=nameWithType> – Metoda<br /><br /> <xref:System.IO.DirectoryInfo.Delete%2A?displayProperty=nameWithType> – Metoda|  
|Zobrazení souborů a podadresářů v adresáři|[Postupy: Vytvoření výčtu adresářů a souborů](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)|  
|Vyhledání velikosti adresáře|<xref:System.IO.Directory?displayProperty=nameWithType> Třída|  
|Zjištění existence adresáře|<xref:System.IO.Directory.Exists%2A?displayProperty=nameWithType> – Metoda|  
  
## <a name="see-also"></a>Viz také:

- [Vstup/výstup souborů a streamů](../../../docs/standard/io/index.md)  
- [Skládání streamů](../../../docs/standard/io/composing-streams.md)  
- [Asynchronní vstupně-výstupní operace se soubory](../../../docs/standard/io/asynchronous-file-i-o.md)
