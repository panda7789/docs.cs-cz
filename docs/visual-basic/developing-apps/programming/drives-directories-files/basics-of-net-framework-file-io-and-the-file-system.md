---
title: Základy vstupně-výstupních operací se soubory a systému souborů v rozhraní .NET Framework
ms.date: 07/20/2015
helpviewer_keywords:
- file access, file I/O in Visual Basic
- file attributes, determining
- streams, fundamental operations
- file permissions
- streams
- streams, definition
ms.assetid: 49d837c0-cf28-416f-8606-4d83d7b479ef
ms.openlocfilehash: 5d60d0089d042c0be343c741c26de0b4b7778d6d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348933"
---
# <a name="basics-of-net-framework-file-io-and-the-file-system-visual-basic"></a>Základy vstupně-výstupních operací se soubory a systému souborů v rozhraní .NET Framework (Visual Basic)

Třídy v <xref:System.IO> oboru názvů slouží k práci s jednotkami, soubory a adresáři.

<xref:System.IO> Obor názvů obsahuje třídy <xref:System.IO.File> a <xref:System.IO.Directory> , které poskytují .NET Framework funkce, které pracují se soubory a adresáři. Vzhledem k tomu, že metody těchto objektů jsou statické nebo sdílené členy, můžete je použít přímo bez vytvoření instance třídy jako první. Asociováno s těmito třídami <xref:System.IO.FileInfo> jsou <xref:System.IO.DirectoryInfo> třídy a, které budou znát uživatele `My` funkce. Chcete-li použít tyto třídy, je nutné plně kvalifikovat názvy nebo importovat příslušné obory názvů zahrnutím `Imports` příkazů na začátek ovlivněného kódu. Další informace naleznete v tématu [příkaz Imports (obor názvů a typ rozhraní .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).

> [!NOTE]
> Další témata v této části používají `My.Computer.FileSystem` objekt namísto `System.IO` tříd pro práci s jednotkami, soubory a adresáři. `My.Computer.FileSystem` Objekt je určený hlavně pro použití v Visual Basicch programech. `System.IO`třídy jsou určené pro použití v jakémkoli jazyce, který podporuje .NET Framework, včetně Visual Basic.

## <a name="definition-of-a-stream"></a>Definice streamu

.NET Framework používá datové proudy k podpoře čtení a zápisu do souborů. Datový proud si můžete představit jako jednorozměrná sadu souvislých dat, která má začátek a konec, a kde ukazatel indikuje aktuální pozici v datovém proudu.

![Kurzor zobrazuje aktuální pozici v FileStream.](./media/basics-of-net-framework-file-io-and-the-file-system/filestream-cursor-position.gif)

## <a name="stream-operations"></a>Operace streamování

Data obsažená v datovém proudu můžou pocházet z paměti, souboru nebo zásuvky protokolu TCP/IP. Datové proudy mají základní operace, které mohou být pro ně aplikovány:

- Probíhá **čtení**. Můžete číst z datového proudu a přenášet data z datového proudu do datové struktury, jako je například řetězec nebo pole bajtů.

- Probíhá **zápis**. Můžete zapisovat do datového proudu a přenést data ze zdroje dat do datového proudu.

- **Hledání**. V datovém proudu můžete zadat dotaz a změnu pozice.

Další informace najdete v tématu [vytváření datových proudů](../../../../standard/io/composing-streams.md).

## <a name="types-of-streams"></a>Typy datových proudů

V .NET Framework je datový proud reprezentován <xref:System.IO.Stream> třídou, která tvoří abstraktní třídu pro všechny ostatní datové proudy. Nelze vytvořit instanci <xref:System.IO.Stream> třídy přímo, ale je nutné použít jednu z tříd, kterou implementuje.

Existuje mnoho typů datových proudů, ale pro účely práce s vstupně-výstupními soubory (I/O) jsou nejdůležitější typy <xref:System.IO.FileStream> třídy, což poskytuje způsob, jak číst soubory a zapisovat do nich a <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> třídu, která poskytuje způsob, jak vytvořit soubory a adresáře v izolovaném úložišti. K dalším datovým proudům, které se dají použít při práci se vstupně-výstupními soubory, patří:

- <xref:System.IO.BufferedStream>

- <xref:System.Security.Cryptography.CryptoStream>

- <xref:System.IO.MemoryStream>

- <xref:System.Net.Sockets.NetworkStream>.

V následující tabulce jsou uvedeny úlohy, které se běžně doplňují s datovým proudem:

|Akce|Seznamte se s |
|---|---|
|Čtení a zápis do datového souboru|[Postupy: Čtení a zápis do nově vytvořeného datového souboru](../../../../standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)|
|Přečíst text ze souboru|[Postupy: Čtení textu ze souboru](../../../../standard/io/how-to-read-text-from-a-file.md)|
|Zápis textu do souboru|[Postupy: Zápis textu do souboru](../../../../standard/io/how-to-write-text-to-a-file.md)|
|Čtení znaků z řetězce|[Postupy: Čtení znaků z řetězce](../../../../standard/io/how-to-read-characters-from-a-string.md)|
|Zápis znaků do řetězce|[Postupy: Zápis znaků do řetězce](../../../../standard/io/how-to-write-characters-to-a-string.md)|
|Šifrování dat|[Šifrování dat](../../../../standard/security/encrypting-data.md)|
|Dešifrovat data|[Dešifrování dat](../../../../standard/security/decrypting-data.md)|

## <a name="file-access-and-attributes"></a>Přístup k souborům a atributy

Můžete ovládat způsob vytváření, otevírání a sdílení souborů s <xref:System.IO.FileAccess>výčty, <xref:System.IO.FileMode>a <xref:System.IO.FileShare> , které obsahují příznaky používané konstruktory <xref:System.IO.FileStream> třídy. Když například otevřete nebo vytvoříte nový <xref:System.IO.FileStream>, vytvoří <xref:System.IO.FileMode> výčet možnost zadat, zda je soubor otevřen pro připojení, zda je vytvořen nový soubor, pokud zadaný soubor neexistuje, zda je soubor přepsán a tak dále.

<xref:System.IO.FileAttributes> Výčet umožňuje shromažďování informací specifických pro soubor. <xref:System.IO.FileAttributes> Výčet vrátí uložené atributy souboru, například zda je komprimovaný, zašifrovaný, skrytý, jen pro čtení, archiv, adresář, systémový soubor nebo dočasný soubor.

V následující tabulce jsou uvedeny úkoly zahrnující přístup k souborům a atributy souborů:

|Akce|Seznamte se s |
|---|---|
|Otevření a přidání textu do souboru protokolu|[Postupy: Otevření a připojení k souboru protokolu](../../../../standard/io/how-to-open-and-append-to-a-log-file.md)|
|Určení atributů souboru|<xref:System.IO.FileAttributes>|

## <a name="file-permissions"></a>Oprávnění souboru

Řízení přístupu k souborům a adresářům lze provádět pomocí <xref:System.Security.Permissions.FileIOPermission> třídy. To může být zvláště důležité pro vývojáře, kteří pracují s webovými formuláři, které se ve výchozím nastavení spouštějí v rámci kontextu speciálního místního uživatelského účtu s názvem ASPNET, který je vytvořen jako součást instalace ASP.NET a .NET Framework. Pokud taková aplikace požaduje přístup k prostředku, má uživatelský účet ASPNET omezená oprávnění, což může zabránit uživateli v provádění akcí, jako je například zápis do souboru z webové aplikace. Další informace naleznete v tématu <xref:System.Security.Permissions.FileIOPermission>.

## <a name="isolated-file-storage"></a>Izolované File Storage

Izolované úložiště je pokus vyřešit problémy vytvořené při práci se soubory, kde uživatel nebo kód nemusí mít potřebná oprávnění. Izolované úložiště přiřadí každému uživateli Datový oddíl, který může obsahovat jeden nebo více obchodů. Obchody mohou být od sebe vzájemně oddělené uživatelem a sestavením. K němu má přístup jenom uživatel a sestavení, které vytvořilo úložiště. Úložiště funguje jako úplný virtuální systém souborů – v rámci jednoho úložiště můžete vytvářet a manipulovat s adresáři a soubory.

V následující tabulce jsou uvedeny úlohy běžně přidružené k izolovanému úložišti souborů.

|Akce|Seznamte se s |
|---|---|
|Vytvoření izolovaného úložiště|[Postupy: Získávání úložišť pro izolované úložiště](../../../../standard/io/how-to-obtain-stores-for-isolated-storage.md)|
|Zobrazení výčtu izolovaných úložišť|[Postupy: Vytvoření výčtu úložišť pro izolované úložiště](../../../../standard/io/how-to-enumerate-stores-for-isolated-storage.md)|
|Odstranění izolovaného úložiště|[Postupy: Odstraňování úložišť v izolovaném úložišti](../../../../standard/io/how-to-delete-stores-in-isolated-storage.md)|
|Vytvoření souboru nebo adresáře v izolovaném úložišti|[Postupy: Vytváření souborů a adresářů v izolovaném úložišti](../../../../standard/io/how-to-create-files-and-directories-in-isolated-storage.md)|
|Najít soubor v izolovaném úložišti|[Postupy: Hledání existujících souborů a adresářů v izolovaném úložišti](../../../../standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md)|
|Čtení nebo zápis do souboru v izolovaném úložišti|[Postupy: Čtení a zápis do souborů v izolovaném úložišti](../../../../standard/io/how-to-read-and-write-to-files-in-isolated-storage.md)|
|Odstranění souboru nebo adresáře v izolovaném úložišti|[Postupy: Odstraňování souborů a adresářů v izolovaném úložišti](../../../../standard/io/how-to-delete-files-and-directories-in-isolated-storage.md)|

## <a name="file-events"></a>Události souboru

Tato <xref:System.IO.FileSystemWatcher> součást umožňuje sledovat změny v souborech a adresářích ve vašem systému nebo na jakémkoli počítači, ke kterému máte přístup k síti. Například pokud je soubor upravený, může být vhodné odeslat uživateli výstrahu, že tato změna proběhla. Když dojde ke změnám, vyvolá se jedna nebo více událostí, uloží se do vyrovnávací paměti a předají se <xref:System.IO.FileSystemWatcher> komponentě ke zpracování.

## <a name="see-also"></a>Viz také

- [Skládání streamů](../../../../standard/io/composing-streams.md)
- [Vstupně-výstupní operace se soubory a datovým proudem](../../../../standard/io/index.md)
- [I/O asynchronní soubory](../../../../standard/io/asynchronous-file-i-o.md)
- [Třídy používané ve vstupně-výstupních operacích se soubory a v systému souborů v rozhraní .NET Framework (Visual Basic)](../../../../visual-basic/developing-apps/programming/drives-directories-files/classes-used-in-net-framework-file-io-and-the-file-system.md)
