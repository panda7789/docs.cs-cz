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
ms.openlocfilehash: c978f79571494d9b716df4e8a42e7f40d20766f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="basics-of-net-framework-file-io-and-the-file-system-visual-basic"></a>Základy vstupně-výstupních operací se soubory a systému souborů v rozhraní .NET Framework (Visual Basic)
Třídy v <xref:System.IO> obor názvů se používají k práci s disky, souborů a adresářů.  
  
 <xref:System.IO> Obor názvů obsahuje <xref:System.IO.File> a <xref:System.IO.Directory> třídy, které poskytují [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] funkce, které pracují souborů a adresářů. Protože jsou statické metody třídy tyto objekty nebo sdílení členové, můžete je přímo bez vytvoření instance třídy nejdřív. Přidružené tyto třídy jsou <xref:System.IO.FileInfo> a <xref:System.IO.DirectoryInfo> třídy, které budou pro uživatele `My` funkce. K použití těchto tříd, musí plně kvalifikovat názvy nebo importovat obory názvů zahrnutím `Imports` příkazů na začátek ovlivněného kódu. Další informace najdete v tématu [příkaz Imports (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
> [!NOTE]
>  Další témata v této části použijte `My.Computer.FileSystem` objektu místo `System.IO` třídy pro práci s disky, souborů a adresářů. `My.Computer.FileSystem` Objektu je určena především pro použití v aplikacích jazyka Visual Basic. `System.IO` třídy jsou určeny k použití v jakémkoli jazyce, který podporuje [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], včetně Visual Basic.  
  
## <a name="definition-of-a-stream"></a>Definice datových proudů  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Používá datové proudy k čtení a zápis do souborů. Datový proud s si můžete představit jako jednorozměrné sadu souvislý dat, který má začátek a konec a kurzor označující aktuální pozici v datovém proudu.  
  
 ![Kurzor ukazuje aktuální pozici v filestream. ] (../../../../visual-basic/developing-apps/programming/drives-directories-files/media/filestream.gif "FileStream")  
  
## <a name="stream-operations"></a>Operace s datovými proudy  
 Data obsažená v datovém proudu mohou pocházet z paměti, soubor nebo soketů protokolu TCP/IP. Datové proudy mají základní operace, které mohou být použity k nim:  
  
-   Čtení. Můžete číst z datového proudu, přenosu dat z datového proudu do struktury dat, jako je řetězec nebo pole bajtů.  
  
-   **Zápis**. Můžete napsat do datového proudu, přenosu dat ze zdroje dat do datového proudu.  
  
-   **Vyhledávání**. Můžete vyhledat a upravit vaši pozici v datovém proudu.  
  
 Další informace najdete v tématu [vytváření datových proudů](../../../../standard/io/composing-streams.md).  
  
## <a name="types-of-streams"></a>Typy datových proudů  
 V [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], je reprezentována datový proud <xref:System.IO.Stream> třída, která tvoří abstraktní třídu pro všechny datové proudy. Nelze vytvořit přímo instance <xref:System.IO.Stream> třídy, ale musí používat jednu z tříd implementuje.  
  
 Existuje mnoho typů datových proudů, ale pro účely práce s souboru vstupní a výstupní (I/O), jsou nejdůležitější typy <xref:System.IO.FileStream> třídy, která poskytuje způsob, jak číst z a zapisovat do souborů, a <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> třídy, která poskytuje způsob, jak vytvářet soubory a adresářů v izolovaném úložišti. Datové proudy, které lze použít při práci s vstupně-výstupních souborů patří:  
  
-   <xref:System.IO.BufferedStream>  
  
-   <xref:System.Security.Cryptography.CryptoStream>  
  
-   <xref:System.IO.MemoryStream>  
  
-   <xref:System.Net.Sockets.NetworkStream>.  
  
 V následující tabulce jsou uvedeny úlohy, které jsou běžně provést pomocí datového proudu:  
  
|Chcete-li|Další informace naleznete v tématu|
|---|---|   
|Čtení a zápisu do datového souboru|[Postupy: Čtení a zápis do nově vytvořeného datového souboru](../../../../standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)|  
|Čtení textu ze souboru|[Postupy: Čtení textu ze souboru](../../../../standard/io/how-to-read-text-from-a-file.md)|  
|Zápis textu do souboru|[Postupy: Zápis textu do souboru](../../../../standard/io/how-to-write-text-to-a-file.md)|  
|Čtení znaků z řetězce|[Postupy: Čtení znaků z řetězce](../../../../standard/io/how-to-read-characters-from-a-string.md)|  
|Zápis znaků do řetězce|[Postupy: Zápis znaků do řetězce](../../../../standard/io/how-to-write-characters-to-a-string.md)|  
|Šifrování dat|[Šifrování dat](../../../../standard/security/encrypting-data.md)|  
|Dešifrování dat|[Dešifrování dat](../../../../standard/security/decrypting-data.md)|  
  
## <a name="file-access-and-attributes"></a>Přístup k souborům a atributy  
 Můžete řídit, jak se vytváří soubory, otevřenou a sdíleny s <xref:System.IO.FileAccess>, <xref:System.IO.FileMode>, a <xref:System.IO.FileShare> výčty, které budou obsahovat příznaky, které používají konstruktory z <xref:System.IO.FileStream> třídy. Například při otevření nebo vytvořte novou <xref:System.IO.FileStream>, <xref:System.IO.FileMode> výčtu umožňuje určit, zda je soubor otevřen pro přidávání, zda je vytvořen nový soubor Pokud zadaný soubor neexistuje, nebo zda je soubor přepsán a tak dále.  
  
 <xref:System.IO.FileAttributes> Výčtu umožňuje shromažďování informace specifické pro soubor. <xref:System.IO.FileAttributes> Výčtu vrátí uložené atributy souboru, například zda je komprimovaný, šifrovaná, skrytý, jen pro čtení, archiv, adresář, systémový soubor nebo dočasný soubor.  
  
 V následující tabulce jsou uvedeny úlohy zahrnující přístup k souborům a atributů souboru:  
  
|Chcete-li|Další informace naleznete v tématu|  
|---|---|
|Otevření a přidání textu do souboru protokolu|[Postupy: Otevření a připojení k souboru protokolu](../../../../standard/io/how-to-open-and-append-to-a-log-file.md)|  
|Určit atributy souboru|<xref:System.IO.FileAttributes>|  
  
## <a name="file-permissions"></a>Oprávnění souborů  
 Řízení přístupu pro soubory a adresáře lze provést pomocí <xref:System.Security.Permissions.FileIOPermission> třídy. To může být obzvláště důležité pro vývojáře, kteří pracují s webovými formuláři, který ve výchozím nastavení běží v kontextu speciální místní uživatelský účet s názvem ASPNET, který je vytvořen jako součást [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] instalace. Pokud tyto aplikace požaduje přístup k prostředku, ASPNET uživatelský účet má omezená oprávnění, která může zabránit uživateli v provádění akcí, jako je zápis do souboru z webové aplikace. Další informace naleznete v tématu <xref:System.Security.Permissions.FileIOPermission>.  
  
## <a name="isolated-file-storage"></a>Izolované úložiště  
 Izolované úložiště je pokus o řešení problémů, které jsou vytvořeny při práci se soubory, které uživatele nebo kód nemusí mít nezbytná oprávnění. Izolované úložiště přiřadí každému uživateli datový prostor, která může pojmout jednoho nebo více úložišť. Úložiště může být od sebe navzájem oddělené uživatelem a sestavením. Pouze uživatel a sestavení, které vytvoření úložiště k dispozici. Úložiště funguje jako dokončení virtuálním souborovém systému – v rámci jednoho úložiště můžete vytvořit a upravit adresářů a souborů.  
  
 Následující tabulka obsahuje seznam úloh běžně spojovaných se izolované úložiště souborů.  
  
|Chcete-li|Další informace naleznete v tématu|
|---|---|  
|Vytvoření izolovaného úložiště|[Postupy: Získávání úložišť pro izolované úložiště](../../../../standard/io/how-to-obtain-stores-for-isolated-storage.md)|  
|Zobrazení výčtu izolované úložiště|[Postupy: Vytvoření výčtu úložišť pro izolované úložiště](../../../../standard/io/how-to-enumerate-stores-for-isolated-storage.md)|  
|Odstranění izolovaného úložiště|[Postupy: Odstraňování úložišť v izolovaném úložišti](../../../../standard/io/how-to-delete-stores-in-isolated-storage.md)|  
|Vytvořit soubor nebo adresář v izolovaném úložišti|[Postupy: Vytváření souborů a adresářů v izolovaném úložišti](../../../../standard/io/how-to-create-files-and-directories-in-isolated-storage.md)|  
|Vyhledat soubor v izolovaném úložišti|[Postupy: Hledání existujících souborů a adresářů v izolovaném úložišti](../../../../standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md)|  
|Číst nebo zapisovat do souboru v izolovaném úložišti|[Postupy: Čtení a zápis do souborů v izolovaném úložišti](../../../../standard/io/how-to-read-and-write-to-files-in-isolated-storage.md)|  
|Odstranit soubor nebo adresář v izolovaném úložišti|[Postupy: Odstraňování souborů a adresářů v izolovaném úložišti](../../../../standard/io/how-to-delete-files-and-directories-in-isolated-storage.md)|  
  
## <a name="file-events"></a>Soubor události  
 <xref:System.IO.FileSystemWatcher> Součást umožňuje sledovat změny souborů a adresářů v systému nebo na libovolném počítači, ke které máte přístup k síti. Pokud je upraven soubor, můžete chtít odesílat oznámení došlo změně uživatele. Při změnách, jeden nebo více událostí se vyvolá, uložené do vyrovnávací paměti a předávány <xref:System.IO.FileSystemWatcher> součásti pro zpracování.  
  
## <a name="see-also"></a>Viz také  
 [Skládání streamů](../../../../standard/io/composing-streams.md)  
 [Vstup/výstup souborů a streamů](../../../../standard/io/index.md)  
 [Asynchronní vstupně-výstupní operace se soubory](../../../../standard/io/asynchronous-file-i-o.md)  
 [Třídy používané v rozhraní .NET Framework vstupně-výstupní a systému souborů (Visual Basic)](../../../../visual-basic/developing-apps/programming/drives-directories-files/classes-used-in-net-framework-file-io-and-the-file-system.md)
