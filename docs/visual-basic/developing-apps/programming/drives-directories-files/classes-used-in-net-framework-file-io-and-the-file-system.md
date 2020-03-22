---
title: Třídy používané ve vstupně-výstupních operacích se soubory a v systému souborů v rozhraní .NET Framework
ms.date: 07/20/2015
helpviewer_keywords:
- file I/O classes
ms.assetid: 4a5ca924-eea8-4a95-a5f0-6ac10de276a3
ms.openlocfilehash: fe70f8fb655579049bb36fc324d04530259d25f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348920"
---
# <a name="classes-used-in-net-framework-file-io-and-the-file-system-visual-basic"></a>Třídy používané ve vstupně-výstupních operacích se soubory a v systému souborů v rozhraní .NET Framework (Visual Basic)

V následujících tabulkách jsou uvedeny třídy běžně používané pro vstupně-videa souboru rozhraní .NET Framework, zařazené do tříd vstupně-v.o souborů, třídy používané pro vytváření datových proudů a třídy používané ke čtení a zápisu do datových proudů.  
  
Podrobnější výpis najdete v tématu [Přehled knihovny tříd](../../../../standard/class-library-overview.md).  
  
## <a name="basic-io-classes-for-files-drives-and-directories"></a>Základní vstupně-nosné třídy pro soubory, jednotky a adresáře  

 V následující tabulce jsou uvedeny a popsány hlavní třídy používané pro vstupně-va souboru.  
  
|Třída|Popis|  
|-----------|-----------------|  
|<xref:System.IO.Directory?displayProperty=nameWithType>|Poskytuje statické metody pro vytváření, přesouvání a vytváření výčtu prostřednictvím adresářů a podadresářů.|  
|<xref:System.IO.DirectoryInfo?displayProperty=nameWithType>|Poskytuje metody instance pro vytváření, přesouvání a vytváření výčtu prostřednictvím adresářů a podadresářů.|  
|<xref:System.IO.DriveInfo?displayProperty=nameWithType>|Poskytuje metody instance pro vytváření, přesouvání a vytváření výčtu prostřednictvím jednotek.|  
|<xref:System.IO.File?displayProperty=nameWithType>|Poskytuje statické metody pro vytváření, kopírování, mazání, přesouvání a otevírání souborů `FileStream`a pomáhá při vytváření .|  
|<xref:System.IO.FileAccess?displayProperty=nameWithType>|Definuje konstanty pro čtení, zápis nebo přístup pro čtení i zápis do souboru.|  
|<xref:System.IO.FileAttributes?displayProperty=nameWithType>|Obsahuje atributy souborů a adresářů, například `Archive`, `Hidden`a `ReadOnly`.|  
|<xref:System.IO.FileInfo?displayProperty=nameWithType>|Poskytuje statické metody pro vytváření, kopírování, mazání, přesouvání a otevírání souborů `FileStream`a pomáhá při vytváření .|  
|<xref:System.IO.FileMode?displayProperty=nameWithType>|Určuje způsob otevření souboru. Tento parametr je určen v mnoha `FileStream` `IsolatedStorageFileStream`konstruktorech pro `Open` a <xref:System.IO.File> <xref:System.IO.FileInfo>, a pro metody a .|  
|<xref:System.IO.FileShare?displayProperty=nameWithType>|Definuje konstanty pro řízení typu přístupu, který mohou mít jiné datové proudy souborů ke stejnému souboru.|  
|<xref:System.IO.Path?displayProperty=nameWithType>|Poskytuje metody a vlastnosti pro zpracování řetězců adresáře.|  
|<xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>|Určuje přístup k souborům a <xref:System.Security.Permissions.FileIOPermissionAttribute.Read%2A> <xref:System.Security.Permissions.FileIOPermissionAttribute.Write%2A>složkám definováním a <xref:System.Security.Permissions.FileIOPermissionAttribute.Append%2A> <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> oprávněními .|  
  
## <a name="classes-used-to-create-streams"></a>Třídy používané k vytváření datových proudů  

 V následující tabulce jsou uvedeny a popsány hlavní třídy používané k vytváření datových proudů.  
  
|Třída|Popis|  
|-----------|-----------------|  
|<xref:System.IO.BufferedStream?displayProperty=nameWithType>|Přidá vrstvu ukládání do vyrovnávací paměti pro čtení a zápis operací na jiný datový proud.|  
|<xref:System.IO.FileStream?displayProperty=nameWithType>|Podporuje náhodný přístup k <xref:System.IO.FileStream.Seek%2A> souborům prostřednictvím své metody. <xref:System.IO.FileStream>otevře soubory synchronně ve výchozím nastavení, ale také podporuje asynchronní operace.|  
|<xref:System.IO.MemoryStream?displayProperty=nameWithType>|Vytvoří datový proud, jehož úložiště zálohování je paměť, nikoli soubor.|  
|<xref:System.Net.Sockets.NetworkStream?displayProperty=nameWithType>|Poskytuje základní datový proud dat pro přístup k síti.|  
|<xref:System.Security.Cryptography.CryptoStream?displayProperty=nameWithType>|Definuje datový proud, který propojuje datové proudy s kryptografickými transformacemi.|  
  
## <a name="classes-used-to-read-from-and-write-to-streams"></a>Třídy používané ke čtení a zápisu do datových proudů  

 V následující tabulce jsou uvedeny konkrétní třídy používané pro čtení a zápis do souborů s datovými proudy.  
  
|**Třída**|**Popis**|  
|---------------|---------------------|  
|<xref:System.IO.BinaryReader?displayProperty=nameWithType>|Čte kódované řetězce a primitivní datové <xref:System.IO.FileStream>typy z .|  
|<xref:System.IO.BinaryWriter?displayProperty=nameWithType>|Zapíše kódované řetězce a primitivní <xref:System.IO.FileStream>datové typy do .|  
|<xref:System.IO.StreamReader?displayProperty=nameWithType>|Čte znaky <xref:System.IO.FileStream>z <xref:System.IO.StreamReader.CurrentEncoding%2A> , pomocí převést znaky do a z bajtů. <xref:System.IO.StreamReader>má konstruktor, který se pokouší <xref:System.IO.StreamReader.CurrentEncoding%2A> zjistit správné pro daný datový proud, na základě přítomnosti <xref:System.IO.StreamReader.CurrentEncoding%2A>-specific preambule, jako je například značka pořadí bajtu.|  
|<xref:System.IO.StreamWriter?displayProperty=nameWithType>|Zapisuje `FileStream` <xref:System.IO.StreamWriter.Encoding%2A> znaky do aplikace , pomocí které se používají k převodu znaků na bajty.|  
|<xref:System.IO.StringReader?displayProperty=nameWithType>|Čte znaky `String`z . Výstup emituje datový proud v `String`libovolném kódování nebo .|  
|<xref:System.IO.StringWriter?displayProperty=nameWithType>|Zapisuje znaky do . `String` Výstup emituje datový proud v `String`libovolném kódování nebo .|  
  
## <a name="see-also"></a>Viz také

- [Skládání streamů](../../../../standard/io/composing-streams.md)
- [I/O souborů a proudů](../../../../standard/io/index.md)
- [Asynchronní I/O soubory](../../../../standard/io/asynchronous-file-i-o.md)
- [Základy vstupně-výstupních operací se soubory a systému souborů v rozhraní .NET Framework (Visual Basic)](../../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)
