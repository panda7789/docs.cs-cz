---
title: Základy vstupně-výstupních operací se soubory a systému souborů v rozhraní .NET Framework (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- file access, file I/O in Visual Basic
- file attributes, determining
- streams, fundamental operations
- file permissions
- streams
- streams, definition
ms.assetid: 49d837c0-cf28-416f-8606-4d83d7b479ef
ms.openlocfilehash: 3ff305a6b22918681561ed7262a7377dbdf7aadc
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591516"
---
# <a name="basics-of-net-framework-file-io-and-the-file-system-visual-basic"></a>Základy vstupně-výstupních operací se soubory a systému souborů v rozhraní .NET Framework (Visual Basic)

Třídy v <xref:System.IO> obor názvů se používají k práci s disky, soubory a adresáře.

<xref:System.IO> Obsahuje obor názvů <xref:System.IO.File> a <xref:System.IO.Directory> třídy, které poskytují funkce rozhraní .NET Framework, které pracují se soubory a adresáře. Protože jsou statické metody z těchto objektů nebo sdílené členy, můžete využít přímo bez vytvoření instance třídy nejprve. Související s tyto třídy jsou <xref:System.IO.FileInfo> a <xref:System.IO.DirectoryInfo> třídy, které budou pro uživatele srozumitelná `My` funkce. K použití těchto tříd, musíte plně kvalifikovat názvy nebo importovat obory názvů včetně `Imports` příkazů na začátek ovlivněné kódu. Další informace najdete v tématu [příkaz Imports (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).

> [!NOTE]
> Další témata v této části používají `My.Computer.FileSystem` místo objektu `System.IO` tříd pro práci s disky, soubory a adresáře. `My.Computer.FileSystem` Objektu je určená primárně pro použití v aplikacích jazyka Visual Basic. `System.IO` třídy jsou určeny k použití v jakémkoliv jazyce, který podporuje rozhraní .NET Framework, včetně jazyka Visual Basic.

## <a name="definition-of-a-stream"></a>Definice Stream

Rozhraní .NET Framework používá pro podporu čtení a zápis do souborů datových proudů. Datový proud si lze představit jako jednorozměrné sadu souvislých dat, který má začátek a konec a kdy kurzor ukazuje aktuální pozici v datovém proudu.

![Kurzor ukazuje aktuální pozici v filestream.](./media/basics-of-net-framework-file-io-and-the-file-system/filestream-cursor-position.gif)

## <a name="stream-operations"></a>Operace Stream

Data obsažená v datovém proudu mohou pocházet z paměti, soubor nebo soket TCP/IP. Datové proudy mají základní operace, které mohou být použity k nim:

- **Čtení**. Můžete číst z datového proudu, přenos dat z datového proudu do datové struktury, jako je například řetězce nebo pole bajtů.

- **Zápis**. Můžete napsat do datového proudu, přenos dat ze zdroje dat do datového proudu.

- **Hledání**. Můžete dotazování a modifikaci svou pozici v datovém proudu.

Další informace najdete v tématu [vytváření datových proudů](../../../../standard/io/composing-streams.md).

## <a name="types-of-streams"></a>Typy datových proudů

V rozhraní .NET Framework, je reprezentována datový proud <xref:System.IO.Stream> třídu, která tvoří abstraktní třídu pro všechny datové proudy. Nelze přímo vytvořit instanci <xref:System.IO.Stream> třídy, ale musí používat jednu z tříd implementuje.

Existuje mnoho typů datových proudů, ale pro účely práce s vstupu a výstupu souboru (vstupně-výstupní operace), jsou nejdůležitější typy <xref:System.IO.FileStream> třídu, která poskytuje způsob, jak číst a zapisovat do souborů, a <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> třídu, která poskytuje způsob, jak vytvořit soubory a adresářů v izolovaném úložišti. Datové proudy, které se dá použít při práci s vstupně-výstupní operace souboru zahrnují:

- <xref:System.IO.BufferedStream>

- <xref:System.Security.Cryptography.CryptoStream>

- <xref:System.IO.MemoryStream>

- <xref:System.Net.Sockets.NetworkStream>.

V následující tabulce jsou uvedeny úlohy, které jsou obvykle provedeno pomocí datového proudu:

|Chcete-li|Další informace naleznete v tématu|
|---|---|
|Čtení a zápis do datového souboru|[Postupy: Čtení a zápis do nově vytvořeného datového souboru](../../../../standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)|
|Čtení textu ze souboru|[Postupy: Čtení textu ze souboru](../../../../standard/io/how-to-read-text-from-a-file.md)|
|Zápis textu do souboru|[Postupy: Zápis textu do souboru](../../../../standard/io/how-to-write-text-to-a-file.md)|
|Čtení znaků z řetězce|[Postupy: Čtení znaků z řetězce](../../../../standard/io/how-to-read-characters-from-a-string.md)|
|Zápis znaků do řetězce|[Postupy: Zápis znaků do řetězce](../../../../standard/io/how-to-write-characters-to-a-string.md)|
|Šifrování dat|[Šifrování dat](../../../../standard/security/encrypting-data.md)|
|Dešifrování dat|[Dešifrování dat](../../../../standard/security/decrypting-data.md)|

## <a name="file-access-and-attributes"></a>Přístup k souborům a atributy

Můžete řídit, jak jsou vytvořené soubory, otevřené a sdílené s <xref:System.IO.FileAccess>, <xref:System.IO.FileMode>, a <xref:System.IO.FileShare> výčty, které obsahují příznaky používat konstruktory <xref:System.IO.FileStream> třídy. Například pokud otevřete nebo vytvořte novou <xref:System.IO.FileStream>, <xref:System.IO.FileMode> výčet umožňuje určit, zda je soubor otevřen pro přidávání, zda je vytvořen nový soubor Pokud zadaný soubor neexistuje, nebo zda je soubor přepsán a tak dále.

<xref:System.IO.FileAttributes> Výčet umožňuje shromažďování informací specifických pro soubor. <xref:System.IO.FileAttributes> Vrátí výčet atributu uložené souboru, například určuje, zda je komprimovaný, šifrování, skrytých, jen pro čtení, archivu, adresář, systémový soubor nebo dočasný soubor.

V následující tabulce jsou uvedeny úlohy týkající se přístupu k souborům a atributů souboru:

|Chcete-li|Další informace naleznete v tématu|
|---|---|
|Otevření a připojení textu k souboru protokolu|[Postupy: Otevření a připojení k souboru protokolu](../../../../standard/io/how-to-open-and-append-to-a-log-file.md)|
|Určení atributů souboru|<xref:System.IO.FileAttributes>|

## <a name="file-permissions"></a>Oprávnění k souboru

Řízení přístupu k souborům a adresářům lze provést s <xref:System.Security.Permissions.FileIOPermission> třídy. To může být obzvláště důležité pro vývojáře, kteří pracují s webovými formuláři, který ve výchozím nastavení běží v kontextu zvláštní místní uživatelský účet s názvem ASPNET, který je vytvořen jako součást instalace technologie ASP.NET a .NET Framework. Pokud tato aplikace požaduje přístup k prostředku, ASPNET uživatelský účet má omezená oprávnění, která může zabránit uživateli v provádění akcí, jako je například zápis do souboru z webové aplikace. Další informace naleznete v tématu <xref:System.Security.Permissions.FileIOPermission>.

## <a name="isolated-file-storage"></a>Izolované úložiště souboru

Izolované úložiště je pokus o vyřešení problémů, které vznikají při práci se soubory, ve kterém uživatel nebo kód nemusí mít nezbytná oprávnění. Izolované úložiště přiřadí každému uživateli datové přihrádky, která může obsahovat jedno nebo více úložišť. Úložiště můžou být izolované od sebe navzájem podle uživatele a podle sestavení. K dispozici pouze uživatele a sestavení, které vytvořili úložiště. Úložiště funguje jako kompletní virtuální systém souborů – v rámci jednoho úložiště můžete vytvořit a pracovat s adresářů a souborů.

V následující tabulce jsou uvedeny úkoly, obvykle je spojena s izolované úložiště souboru.

|Chcete-li|Další informace naleznete v tématu|
|---|---|
|Vytvoření izolované úložiště|[Postupy: Získávání úložišť pro izolované úložiště](../../../../standard/io/how-to-obtain-stores-for-isolated-storage.md)|
|Zobrazení výčtu izolovaných úložišť|[Postupy: Vytvoření výčtu úložišť pro izolované úložiště](../../../../standard/io/how-to-enumerate-stores-for-isolated-storage.md)|
|Odstranit izolované úložiště|[Postupy: Odstraňování úložišť v izolovaném úložišti](../../../../standard/io/how-to-delete-stores-in-isolated-storage.md)|
|Vytvořit soubor nebo adresář v izolovaném úložišti|[Postupy: Vytváření souborů a adresářů v izolovaném úložišti](../../../../standard/io/how-to-create-files-and-directories-in-isolated-storage.md)|
|Hledání souboru v izolovaném úložišti|[Postupy: Hledání existujících souborů a adresářů v izolovaném úložišti](../../../../standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md)|
|Čtení nebo zápis do souboru v izolovaném úložišti|[Postupy: Čtení a zápis do souborů v izolovaném úložišti](../../../../standard/io/how-to-read-and-write-to-files-in-isolated-storage.md)|
|Odstranit soubor nebo adresář v izolovaném úložišti|[Postupy: Odstraňování souborů a adresářů v izolovaném úložišti](../../../../standard/io/how-to-delete-files-and-directories-in-isolated-storage.md)|

## <a name="file-events"></a>Soubor událostí

<xref:System.IO.FileSystemWatcher> Komponenta umožňuje sledovat změny souborů a adresářů v systému nebo v libovolném počítači, ke kterému máte přístup k síti. Pokud se změní soubor, můžete chtít odeslat oznámení změny proběhla uživatele. Při změnách, jeden nebo více událostí jsou aktivovaná, uloženy ve vyrovnávací paměti a předána <xref:System.IO.FileSystemWatcher> komponent pro zpracování.

## <a name="see-also"></a>Viz také:

- [Skládání streamů](../../../../standard/io/composing-streams.md)
- [Vstup/výstup souborů a streamů](../../../../standard/io/index.md)
- [Asynchronní vstupně-výstupní operace se soubory](../../../../standard/io/asynchronous-file-i-o.md)
- [Třídy používané ve vstupně-výstupní operace souboru rozhraní .NET Framework a systému souborů (Visual Basic)](../../../../visual-basic/developing-apps/programming/drives-directories-files/classes-used-in-net-framework-file-io-and-the-file-system.md)
