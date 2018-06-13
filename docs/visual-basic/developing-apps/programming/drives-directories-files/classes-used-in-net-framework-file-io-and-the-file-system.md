---
title: Třídy používané ve vstupně-výstupních operacích se soubory a v systému souborů v rozhraní .NET Framework (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- file I/O classes
ms.assetid: 4a5ca924-eea8-4a95-a5f0-6ac10de276a3
ms.openlocfilehash: 4c13b482ddbb3c1c109ca8dfe36ed76a2025d61a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590696"
---
# <a name="classes-used-in-net-framework-file-io-and-the-file-system-visual-basic"></a>Třídy používané ve vstupně-výstupních operacích se soubory a v systému souborů v rozhraní .NET Framework (Visual Basic)
Následující tabulka uvádí třídy běžně používané pro rozhraní .NET Framework soubor vstupně-výstupních operací, rozděleny do třídy vstupně-výstupních souborů, třídy používané pro vytváření datových proudů a třídy používané pro čtení a zápis do datových proudů.  
  
 Zadat [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] dokumentaci a najít komplexnější seznam, najdete v části [– přehled knihovny tříd](../../../../standard/class-library-overview.md).  
  
## <a name="basic-io-classes-for-files-drives-and-directories"></a>Vstupně-výstupních operací základní třídy pro soubory, jednotky a adresáře  
 Následující tabulka uvádí a popisuje hlavní třídy používané pro soubor vstupně-výstupní operace.  
  
|Třída|Popis|  
|-----------|-----------------|  
|<xref:System.IO.Directory?displayProperty=nameWithType>|Poskytuje statické metody pro vytváření, přesunutí a výčet prostřednictvím adresářů a podadresářů.|  
|<xref:System.IO.DirectoryInfo?displayProperty=nameWithType>|Poskytuje metody instance pro vytváření, přesunutí a výčet prostřednictvím adresářů a podadresářů.|  
|<xref:System.IO.DriveInfo?displayProperty=nameWithType>|Poskytuje metody instance pro vytváření, přesunutí a výčet prostřednictvím jednotky.|  
|<xref:System.IO.File?displayProperty=nameWithType>|Poskytuje statické metody pro vytvoření, kopírování, odstranění, přesunutí a otevírání souborů a pomáhá při vytváření `FileStream`.|  
|<xref:System.IO.FileAccess?displayProperty=nameWithType>|Definuje konstanty pro čtení, zápisu nebo přístup pro čtení a zápis do souboru.|  
|<xref:System.IO.FileAttributes?displayProperty=nameWithType>|Poskytuje atributy pro soubory a adresáře například `Archive`, `Hidden`, a `ReadOnly`.|  
|<xref:System.IO.FileInfo?displayProperty=nameWithType>|Poskytuje statické metody pro vytvoření, kopírování, odstranění, přesunutí a otevírání souborů a pomáhá při vytváření `FileStream`.|  
|<xref:System.IO.FileMode?displayProperty=nameWithType>|Určuje, jak otevřít soubor. Tento parametr je zadán v mnoha z konstruktorů `FileStream` a `IsolatedStorageFileStream`a `Open` metody <xref:System.IO.File> a <xref:System.IO.FileInfo>.|  
|<xref:System.IO.FileShare?displayProperty=nameWithType>|Definuje konstanty pro řízení typ přístupu, kterou může mít jiné datové proudy souboru do stejného souboru.|  
|<xref:System.IO.Path?displayProperty=nameWithType>|Poskytuje metody a vlastnosti pro zpracování řetězců adresářů.|  
|<xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>|Řídí přístup souborů a složek definováním <xref:System.Security.Permissions.FileIOPermissionAttribute.Read%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Write%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Append%2A> a <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> oprávnění.|  
  
## <a name="classes-used-to-create-streams"></a>Třídy používané k vytváření datových proudů  
 Následující tabulka uvádí a popisuje hlavní třídy používané k vytváření datových proudů.  
  
|Třída|Popis|  
|-----------|-----------------|  
|<xref:System.IO.BufferedStream?displayProperty=nameWithType>|Přidá vyrovnávací vrstvu ke čtení a zápisu operace na jiný datový proud.|  
|<xref:System.IO.FileStream?displayProperty=nameWithType>|Podporuje náhodný přístup k souborům pomocí jeho <xref:System.IO.FileStream.Seek%2A> metoda. <xref:System.IO.FileStream> ve výchozím nastavení otevře soubory synchronně, ale také podporuje asynchronní operace.|  
|<xref:System.IO.MemoryStream?displayProperty=nameWithType>|Vytvoří datový proud, s jehož záložní úložiště je paměť, nikoli soubor.|  
|<xref:System.Net.Sockets.NetworkStream?displayProperty=nameWithType>|Poskytuje základní datový proud dat pro přístup k síti.|  
|<xref:System.Security.Cryptography.CryptoStream?displayProperty=nameWithType>|Definuje datový proud, který odkazuje datových proudů na kryptografických transformace.|  
  
## <a name="classes-used-to-read-from-and-write-to-streams"></a>Třídy používané číst z a zapisovat do datových proudů  
 V následující tabulce jsou uvedeny konkrétní třídy používané pro čtení a zápis do souborů s datovými proudy.  
  
|**– Třída**|**Popis**|  
|---------------|---------------------|  
|<xref:System.IO.BinaryReader?displayProperty=nameWithType>|Přečte kódované řetězce a primitivní datové typy z <xref:System.IO.FileStream>.|  
|<xref:System.IO.BinaryWriter?displayProperty=nameWithType>|Zapíše kódované řetězce a primitivní datové typy <xref:System.IO.FileStream>.|  
|<xref:System.IO.StreamReader?displayProperty=nameWithType>|Přečte znaky z <xref:System.IO.FileStream>pomocí <xref:System.IO.StreamReader.CurrentEncoding%2A> převést znaků do a z bajtů. <xref:System.IO.StreamReader> má konstruktor, který se pokouší zjistit správný <xref:System.IO.StreamReader.CurrentEncoding%2A> pro daný datový proud, založené na přítomnost <xref:System.IO.StreamReader.CurrentEncoding%2A>-zvláštní preambule, jako je například značka pořadí bajtů.|  
|<xref:System.IO.StreamWriter?displayProperty=nameWithType>|Zapíše znaky `FileStream`pomocí <xref:System.IO.StreamWriter.Encoding%2A> převést znaky na bajty.|  
|<xref:System.IO.StringReader?displayProperty=nameWithType>|Přečte znaky z `String`. Výstup může být buď datový proud v jakémkoli kódování nebo `String`.|  
|<xref:System.IO.StringWriter?displayProperty=nameWithType>|Zapíše znaky `String`. Výstup může být buď datový proud v jakémkoli kódování nebo `String`.|  
  
## <a name="see-also"></a>Viz také  
 [Skládání streamů](../../../../standard/io/composing-streams.md)  
 [Vstup/výstup souborů a streamů](../../../../standard/io/index.md)  
 [Asynchronní vstupně-výstupní operace se soubory](../../../../standard/io/asynchronous-file-i-o.md)  
 [Základní informace o souborech vstupně-výstupních operací a systému souborů (Visual Basic)](../../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)
