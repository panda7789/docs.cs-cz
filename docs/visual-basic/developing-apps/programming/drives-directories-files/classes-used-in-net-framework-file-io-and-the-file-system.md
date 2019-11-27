---
title: Třídy používané ve vstupně-výstupních operacích se soubory a v systému souborů v rozhraní .NET Framework
ms.date: 07/20/2015
helpviewer_keywords:
- file I/O classes
ms.assetid: 4a5ca924-eea8-4a95-a5f0-6ac10de276a3
ms.openlocfilehash: fe70f8fb655579049bb36fc324d04530259d25f2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348920"
---
# <a name="classes-used-in-net-framework-file-io-and-the-file-system-visual-basic"></a>Třídy používané ve vstupně-výstupních operacích se soubory a v systému souborů v rozhraní .NET Framework (Visual Basic)

V následujících tabulkách jsou uvedeny třídy, které se běžně používají pro .NET Framework vstupně-výstupních operací v souborech, třídách používaných k vytváření datových proudů a tříd používaných ke čtení a zápisu do datových proudů.  
  
Komplexnější seznam naleznete v tématu [Přehled knihovny tříd](../../../../standard/class-library-overview.md).  
  
## <a name="basic-io-classes-for-files-drives-and-directories"></a>Základní třídy I/O pro soubory, jednotky a adresáře  

 Následující tabulka uvádí a popisuje hlavní třídy používané pro vstupně-výstupní operace se soubory.  
  
|Třída|Popis|  
|-----------|-----------------|  
|<xref:System.IO.Directory?displayProperty=nameWithType>|Poskytuje statické metody pro vytváření, přesouvání a vytváření výčtu adresářů a podadresářů.|  
|<xref:System.IO.DirectoryInfo?displayProperty=nameWithType>|Poskytuje metody instance pro vytváření, přesouvání a vytváření výčtu adresářů a podadresářů.|  
|<xref:System.IO.DriveInfo?displayProperty=nameWithType>|Poskytuje metody instance pro vytváření, přesouvání a vytváření výčtu jednotek prostřednictvím jednotek.|  
|<xref:System.IO.File?displayProperty=nameWithType>|Poskytuje statické metody pro vytváření, kopírování, odstraňování, přesouvání a otevírání souborů a pomůcky při vytváření `FileStream`.|  
|<xref:System.IO.FileAccess?displayProperty=nameWithType>|Definuje konstanty pro přístup pro čtení, zápis nebo čtení a zápis do souboru.|  
|<xref:System.IO.FileAttributes?displayProperty=nameWithType>|Poskytuje atributy pro soubory a adresáře, například `Archive`, `Hidden`a `ReadOnly`.|  
|<xref:System.IO.FileInfo?displayProperty=nameWithType>|Poskytuje statické metody pro vytváření, kopírování, odstraňování, přesouvání a otevírání souborů a pomůcky při vytváření `FileStream`.|  
|<xref:System.IO.FileMode?displayProperty=nameWithType>|Určuje, jak je soubor otevřen. Tento parametr je zadán v mnoha konstruktorech pro `FileStream` a `IsolatedStorageFileStream`a pro metody `Open` <xref:System.IO.File> a <xref:System.IO.FileInfo>.|  
|<xref:System.IO.FileShare?displayProperty=nameWithType>|Definuje konstanty pro řízení typu přístupu k jiným datovým proudům souborů může být stejný soubor.|  
|<xref:System.IO.Path?displayProperty=nameWithType>|Poskytuje metody a vlastnosti pro zpracování řetězců adresáře.|  
|<xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>|Řídí přístup k souborům a složkám definováním <xref:System.Security.Permissions.FileIOPermissionAttribute.Read%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Write%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Append%2A> a <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> oprávnění.|  
  
## <a name="classes-used-to-create-streams"></a>Třídy používané k vytváření datových proudů  

 Následující tabulka uvádí a popisuje hlavní třídy používané k vytváření datových proudů.  
  
|Třída|Popis|  
|-----------|-----------------|  
|<xref:System.IO.BufferedStream?displayProperty=nameWithType>|Přidá vrstvu vyrovnávací paměti pro operace čtení a zápisu v jiném datovém proudu.|  
|<xref:System.IO.FileStream?displayProperty=nameWithType>|Podporuje náhodný přístup k souborům prostřednictvím své <xref:System.IO.FileStream.Seek%2A> metody. ve výchozím nastavení <xref:System.IO.FileStream> otevře soubory synchronně, ale podporuje také asynchronní operace.|  
|<xref:System.IO.MemoryStream?displayProperty=nameWithType>|Vytvoří datový proud, jehož záložní úložiště je paměť, nikoli soubor.|  
|<xref:System.Net.Sockets.NetworkStream?displayProperty=nameWithType>|Poskytuje podkladový datový proud dat pro přístup k síti.|  
|<xref:System.Security.Cryptography.CryptoStream?displayProperty=nameWithType>|Definuje datový proud, který propojuje datové proudy s kryptografickými transformacemi.|  
  
## <a name="classes-used-to-read-from-and-write-to-streams"></a>Třídy používané pro čtení a zápis do datových proudů  

 V následující tabulce jsou uvedeny konkrétní třídy používané pro čtení a zápis do souborů s datovými proudy.  
  
|**Deník**|**Popis**|  
|---------------|---------------------|  
|<xref:System.IO.BinaryReader?displayProperty=nameWithType>|Čte kódované řetězce a primitivní datové typy z <xref:System.IO.FileStream>.|  
|<xref:System.IO.BinaryWriter?displayProperty=nameWithType>|Zapisuje kódované řetězce a primitivní datové typy do <xref:System.IO.FileStream>.|  
|<xref:System.IO.StreamReader?displayProperty=nameWithType>|Přečte znaky z <xref:System.IO.FileStream>pomocí <xref:System.IO.StreamReader.CurrentEncoding%2A> k převodu znaků do a z bajtů. <xref:System.IO.StreamReader> má konstruktor, který se pokouší zjistit správný <xref:System.IO.StreamReader.CurrentEncoding%2A> pro daný datový proud, na základě přítomnosti <xref:System.IO.StreamReader.CurrentEncoding%2A>ho konkrétního preambule, jako je například značka pořadí bajtů.|  
|<xref:System.IO.StreamWriter?displayProperty=nameWithType>|Zapisuje znaky do `FileStream`pomocí <xref:System.IO.StreamWriter.Encoding%2A> k převodu znaků na bajty.|  
|<xref:System.IO.StringReader?displayProperty=nameWithType>|Přečte znaky z `String`. Výstup může být buď datový proud v jakémkoli kódování, nebo `String`.|  
|<xref:System.IO.StringWriter?displayProperty=nameWithType>|Zapisuje znaky do `String`. Výstup může být buď datový proud v jakémkoli kódování, nebo `String`.|  
  
## <a name="see-also"></a>Viz také:

- [Skládání streamů](../../../../standard/io/composing-streams.md)
- [Vstup/výstup souborů a datových proudů](../../../../standard/io/index.md)
- [Asynchronní vstupně-výstupní operace se soubory](../../../../standard/io/asynchronous-file-i-o.md)
- [Základy .NET Frameworkch vstupně-výstupních operací se soubory a systém souborů (Visual Basic)](../../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)
