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

Třídy <xref:System.IO> v oboru názvů se používají pro práci s jednotkami, soubory a adresáři.

Obor <xref:System.IO> názvů obsahuje <xref:System.IO.File> <xref:System.IO.Directory> třídy a, které poskytují funkci rozhraní .NET Framework, která manipuluje se soubory a adresáři. Vzhledem k tomu, že metody těchto objektů jsou statické nebo sdílené členy, můžete je použít přímo bez vytvoření instance třídy jako první. Přidružené s těmito <xref:System.IO.FileInfo> <xref:System.IO.DirectoryInfo> třídami jsou a třídy, `My` které budou obeznámeni s uživateli funkce. Chcete-li použít tyto třídy, musíte plně kvalifikovat názvy nebo importovat příslušné obory názvů zahrnutím `Imports` příkazu na začátku příslušného kódu. Další informace naleznete [v tématu Imports Statement (Obor názvů.NET a Typ).](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)

> [!NOTE]
> Další témata v této `My.Computer.FileSystem` části `System.IO` používají objekt namísto tříd pro práci s jednotkami, soubory a adresáři. Objekt `My.Computer.FileSystem` je určen především pro použití v aplikacích jazyka Visual Basic. `System.IO`třídy jsou určeny pro použití libovolným jazykem, který podporuje rozhraní .NET Framework, včetně jazyka Visual Basic.

## <a name="definition-of-a-stream"></a>Definice datového proudu

Rozhraní .NET Framework používá datové proudy pro podporu čtení a zápisu do souborů. Datový proud si můžete usuzovat jako jednorozměrnou sadu souvislých dat, která má začátek a konec a kde kurzor označuje aktuální pozici v datovém proudu.

![Kurzor zobrazuje aktuální pozici v datovém proudu souboru.](./media/basics-of-net-framework-file-io-and-the-file-system/filestream-cursor-position.gif)

## <a name="stream-operations"></a>Operace datového proudu

Data obsažená v datovém proudu mohou pocházet z paměti, souboru nebo soketu TCP/IP. Datové proudy mají základní operace, které lze použít na ně:

- **Čtení**. Můžete číst z datového proudu, přenos dat z datového proudu do datové struktury, jako je například řetězec nebo pole bajtů.

- **Psaní**. Můžete zapisovat do datového proudu a přenášet data ze zdroje dat do datového proudu.

- **Hledám**. Můžete dotazovat a upravovat svou pozici v datovém proudu.

Další informace naleznete [v tématu Skládání datových proudů](../../../../standard/io/composing-streams.md).

## <a name="types-of-streams"></a>Typy datových proudů

V rozhraní .NET Framework je datový <xref:System.IO.Stream> proud reprezentován třídou, která tvoří abstraktní třídu pro všechny ostatní datové proudy. Nelze přímo vytvořit instanci <xref:System.IO.Stream> třídy, ale musí použít jednu z tříd, které implementuje.

Existuje mnoho typů datových proudů, ale pro účely práce se vstupem a výstupem <xref:System.IO.FileStream> souboru (I/O) jsou nejdůležitějšími typy <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> třída, která poskytuje způsob čtení a zápisu do souborů a třídu, která poskytuje způsob vytváření souborů a adresářů v izolovaném úložišti. Mezi další datové proudy, které lze použít při práci s vstupně-va souborem, patří:

- <xref:System.IO.BufferedStream>

- <xref:System.Security.Cryptography.CryptoStream>

- <xref:System.IO.MemoryStream>

- <xref:System.Net.Sockets.NetworkStream>.

V následující tabulce jsou uvedeny úkoly běžně prováděné datovým proudem:

|Akce|Seznamte se s |
|---|---|
|Čtení a zápis do datového souboru|[Postupy: Čtení a zápis do nově vytvořeného datového souboru](../../../../standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)|
|Čtení textu ze souboru|[Postupy: Čtení textu ze souboru](../../../../standard/io/how-to-read-text-from-a-file.md)|
|Zápis textu do souboru|[Postupy: Zápis textu do souboru](../../../../standard/io/how-to-write-text-to-a-file.md)|
|Čtení znaků z řetězce|[Postupy: Čtení znaků z řetězce](../../../../standard/io/how-to-read-characters-from-a-string.md)|
|Zápis znaků do řetězce|[Postupy: Zápis znaků do řetězce](../../../../standard/io/how-to-write-characters-to-a-string.md)|
|Šifrování dat|[Šifrování dat](../../../../standard/security/encrypting-data.md)|
|Dešifrování dat|[Dešifrování dat](../../../../standard/security/decrypting-data.md)|

## <a name="file-access-and-attributes"></a>Přístup k souborům a atributy

Můžete řídit, jak jsou soubory vytvářeny, <xref:System.IO.FileAccess> <xref:System.IO.FileMode>otevírané a sdílené s , a <xref:System.IO.FileShare> výčty, <xref:System.IO.FileStream> které obsahují příznaky používané konstruktory třídy. Například při otevření nebo vytvoření <xref:System.IO.FileStream>nového , <xref:System.IO.FileMode> výčet umožňuje určit, zda je soubor otevřen pro připojení, zda je vytvořen nový soubor, pokud zadaný soubor neexistuje, zda je soubor přepsán a tak dále.

Výčet <xref:System.IO.FileAttributes> umožňuje shromažďování informací specifických pro soubor. Výčet <xref:System.IO.FileAttributes> vrátí uložené atributy souboru, například zda je komprimovaný, šifrovaný, skrytý, jen pro čtení, archiv, adresář, systémový soubor nebo dočasný soubor.

V následující tabulce jsou uvedeny úkoly týkající se přístupu k souborům a atributů souborů:

|Akce|Seznamte se s |
|---|---|
|Otevření a připojení textu k souboru protokolu|[Postupy: Otevření a připojení k souboru protokolu](../../../../standard/io/how-to-open-and-append-to-a-log-file.md)|
|Určení atributů souboru|<xref:System.IO.FileAttributes>|

## <a name="file-permissions"></a>Oprávnění k souborům

Řízení přístupu k souborům a <xref:System.Security.Permissions.FileIOPermission> adresářům lze provést pomocí třídy. To může být obzvláště důležité pro vývojáře pracující s webovými formuláři, které jsou ve výchozím nastavení spuštěny v rámci speciálního místního uživatelského účtu s názvem ASPNET, který je vytvořen jako součást instalace ASP.NET a rozhraní .NET Framework. Pokud taková aplikace požaduje přístup k prostředku, má uživatelský účet ASPNET omezená oprávnění, která mohou uživateli bránit v provádění akcí, jako je zápis do souboru z webové aplikace. Další informace naleznete v tématu <xref:System.Security.Permissions.FileIOPermission>.

## <a name="isolated-file-storage"></a>Izolované úložiště souborů

Izolované úložiště je pokus o řešení problémů vytvořených při práci se soubory, kde uživatel nebo kód může postrádat potřebná oprávnění. Izolované úložiště přiřadí každému uživateli datový prostor, který může obsahovat jeden nebo více úložišť. Obchody mohou být izolovány od sebe navzájem uživatelem a sestavení. Přístup k němu mají pouze uživatel a sestavení, kteří vytvořili úložiště. Obchod funguje jako kompletní virtuální systém souborů – v rámci jednoho úložiště můžete vytvářet adresáře a soubory a manipulovat s nimi.

V následující tabulce jsou uvedeny úkoly běžně spojené s izolovaným úložištěm souborů.

|Akce|Seznamte se s |
|---|---|
|Vytvoření izolovaného úložiště|[Postupy: Získávání úložišť pro izolované úložiště](../../../../standard/io/how-to-obtain-stores-for-isolated-storage.md)|
|Výčet izolovaných obchodů|[Postupy: Vytvoření výčtu úložišť pro izolované úložiště](../../../../standard/io/how-to-enumerate-stores-for-isolated-storage.md)|
|Odstranění izolovaného úložiště|[Postupy: Odstraňování úložišť v izolovaném úložišti](../../../../standard/io/how-to-delete-stores-in-isolated-storage.md)|
|Vytvoření souboru nebo adresáře v izolovaném úložišti|[Postupy: Vytváření souborů a adresářů v izolovaném úložišti](../../../../standard/io/how-to-create-files-and-directories-in-isolated-storage.md)|
|Vyhledání souboru v izolovaném úložišti|[Postupy: Hledání existujících souborů a adresářů v izolovaném úložišti](../../../../standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md)|
|Čtení nebo zápis do souboru v izolovaném úložišti|[Postupy: Čtení a zápis do souborů v izolovaném úložišti](../../../../standard/io/how-to-read-and-write-to-files-in-isolated-storage.md)|
|Odstranění souboru nebo adresáře v izolovaném úložišti|[Postupy: Odstraňování souborů a adresářů v izolovaném úložišti](../../../../standard/io/how-to-delete-files-and-directories-in-isolated-storage.md)|

## <a name="file-events"></a>Události souborů

Komponenta <xref:System.IO.FileSystemWatcher> umožňuje sledovat změny v souborech a adresářích v systému nebo v libovolném počítači, ke kterému máte přístup k síti. Pokud je například soubor změněn, můžete uživateli odeslat upozornění, že ke změně došlo. Dojde-li ke změnám, jsou vyvolány jedny nebo <xref:System.IO.FileSystemWatcher> více událostí, uloženy ve vyrovnávací paměti a předány komponentě ke zpracování.

## <a name="see-also"></a>Viz také

- [Skládání streamů](../../../../standard/io/composing-streams.md)
- [I/O souborů a proudů](../../../../standard/io/index.md)
- [Asynchronní I/O soubory](../../../../standard/io/asynchronous-file-i-o.md)
- [Třídy používané ve vstupně-výstupních operacích se soubory a v systému souborů v rozhraní .NET Framework (Visual Basic)](../../../../visual-basic/developing-apps/programming/drives-directories-files/classes-used-in-net-framework-file-io-and-the-file-system.md)
