---
title: SqlMetal.exe (nástroj pro vytváření kódu)
ms.date: 03/30/2017
helpviewer_keywords:
- SQLMetal [LINQ to SQL]
- code generation tool
- SQLMetal.exe
- LINQ to SQL, serialization
- LINQ to SQL, DBML files
- LINQ to SQL, SQLMetal
ms.assetid: 819e5a96-7646-4fdb-b14b-fe31221b0614
ms.openlocfilehash: d5b4c2b59b585b3d3a3584ef9055e70c9d998e85
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71044080"
---
# <a name="sqlmetalexe-code-generation-tool"></a>SqlMetal.exe (nástroj pro vytváření kódu)
Nástroj příkazového řádku SqlMetal generuje kód [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] a mapování pro součást rozhraní .NET Framework. Použitím možností uvedených dále v tomto tématu můžete dát nástroji SqlMetal pokyn, aby provedl několik různých úkonů, které zahrnují následující:  
  
- Vygenerování zdrojového kódu a atributů mapování nebo souboru mapování z databáze.  
  
- Vygenerování přechodného souboru .dbml (database markup language) z databáze za účelem přizpůsobení.  
  
- Vygenerování zdrojového kódu a atributů mapování nebo souboru mapování ze souboru .dbml.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Ve výchozím nastavení je `drive`soubor umístěn na adrese :\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin. Pokud nenainstalujete visual studio, můžete také získat soubor SQLMetal stažením [sady Windows SDK](https://go.microsoft.com/fwlink/?LinkId=142225).  
  
> [!NOTE]
> Vývojáři, kteří používají Visual Studio můžete také použít objekt relační návrháře ke generování tříd entit. Metoda využívající příkazový řádek je vhodná u velkých databází. Protože SqlMetal je nástroj příkazového řádku, můžete ho použít v procesu sestavení.  
  
 Chcete-li nástroj spustit, použijte příkazový řádek pro vývojáře pro sadu Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace naleznete v [příkazových koncích](developer-command-prompt-for-vs.md). Na příkazovém řádku zadejte následující příkaz:  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
sqlmetal [options] [<input file>]  
```  
  
## <a name="options"></a>Možnosti  
 Chcete-li zobrazit nejaktuálnější `sqlmetal /?` seznam možností, zadejte příkazový řádek z nainstalovaného umístění.  
  
 **Možnosti připojení**  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/server:** * \<název>*|Určuje název databázového serveru.|  
|**/databáze:** * \<název>*|Určuje katalog databází na serveru.|  
|**/uživatel:** * \<jméno>*|Určuje id přihlašovacího uživatele. Výchozí hodnota: Použijte ověřování systému Windows.|  
|**/heslo:** * \<>hesla*|Určuje heslo pro přihlášení. Výchozí hodnota: Použít ověřování systému Windows.|  
|**/conn:** * \<>připojovacího řetězce*|Určuje připojovací řetězec databáze. Nelze použít s možnostmi **/server**, **/database**, **/user**nebo **/password.**<br /><br /> Nezahrnujte název souboru do připojovacího řetězce. Místo toho přidejte název souboru do příkazového řádku jako vstupní soubor. Například následující řádek určuje jako vstupní soubor "c:\northwnd.mdf": **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**.|  
|**/timeout:** * \<sekundy>*|Určuje hodnotu časového limitu při přístupu SqlMetal k databázi. Výchozí hodnota: 0 (to znamená žádný časový limit).|  
  
 **Možnosti extrakce**  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/zobrazení**|Extrahuje zobrazení databáze.|  
|**/funkce**|Extrahuje funkce databáze.|  
|**/sprocs**|Extrahuje uložené procedury.|  
  
 **Možnosti výstupu**  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/dbml** *[:soubor]*|Odešle výstup jako .dbml. Nelze použít s parametrem **/map.**|  
|**/code** *[:soubor]*|Odešle výstup jako zdrojový kód. Nelze použít s parametrem **/dbml.**|  
|**/map** *[:soubor]*|Generuje soubor mapování XML namísto atributů. Nelze použít s parametrem **/dbml.**|  
  
 **Různé**  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/jazyk:** * \<jazyková>*|Určuje jazyk zdrojového kódu.<br /><br /> Platný * \<jazyk>*: vb, csharp.<br /><br /> Výchozí hodnota: Odvozeno z přípony názvu souboru kódu.|  
|**/obor názvů:** * \<>*|Určuje obor názvů generovaného kódu. Výchozí hodnota: Žádný obor názvů.|  
|**/context:** * \<typ>*|Určuje název třídy datového kontextu. Výchozí hodnota: Odvozen od názvu databáze.|  
|**/entitybase:** * \<typ>*|Určuje základní třídu z tříd entit v generovaném kódu. Výchozí hodnota: Entity nemají žádnou základní třídu.|  
|**/pluralize**|Automaticky převádí názvy tříd a členů do množného nebo jednotného čísla.<br /><br /> Tato možnost je dostupná pouze v anglické verzi (USA).|  
|**/serializace:** * \<>možnost*|Generuje serializovatelné třídy.<br /><br /> Platná * \<volba>*: Žádný, Jednosměrný. Výchozí hodnota: Žádný.<br /><br /> Další informace naleznete v tématu [Serializace](../data/adonet/sql/linq/serialization.md).|  
  
 **Vstupní soubor**  
  
|Možnost|Popis|  
|------------|-----------------|  
|**\<>vstupního souboru**|Určuje soubor MDF serveru SQL Server Express, soubor DF Compact 3.5 .sdf nebo zprostředkující soubor DBML.|  
  
## <a name="remarks"></a>Poznámky  
 Funkce SqlMetal ve skutečnosti probíhá ve dvou krocích:  
  
- Extrahování metadat databáze do souboru .dbml.  
  
- Generování výstupního souboru s kódem.  
  
     Pomocí příslušných možností příkazového řádku můžete vytvořit zdrojový kód jazyka Visual Basic nebo C# nebo můžete vytvořit soubor mapování XML.  
  
 Chcete-li extrahovat metadata ze souboru .mdf, musíte zadat název souboru .mdf za všemi ostatními možnostmi.  
  
 Pokud není zadán **/server,** předpokládá **se localhost/sqlexpress.**  
  
 Microsoft SQL Server 2005 vyvolá výjimku, pokud platí jednu nebo více z následujících podmínek:  
  
- SqlMetal se pokusí extrahovat uloženou proceduru, která volá sama sebe.  
  
- Úroveň vnoření uložené procedury, funkce nebo zobrazení je vyšší než 32.  
  
     SqlMetal tuto výjimku zachytí a ohlásí ji jako varování.  
  
 Chcete-li zadat název vstupního souboru, přidejte název souboru do příkazového řádku jako vstupní soubor. Zahrnutí názvu souboru do připojovacího řetězce (pomocí možnosti **/conn)** není podporováno.  
  
## <a name="examples"></a>Příklady  
 Vygenerování souboru .dbml obsahujícího extrahovaná metadata SQL:  
  
 **sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**  
  
 Vygenerování souboru .dbml obsahujícího extrahovaná metadata SQL ze souboru .mdf pomocí SQL Server Express:  
  
 **sqlmetal /dbml:mymeta.dbml mydbfile.mdf**  
  
 Vygenerování souboru .dbml obsahujícího extrahovaná metadata SQL z SQL Server Express:  
  
 **sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**  
  
 Vygenerování zdrojového kódu ze souboru metadat .dbml:  
  
 **sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**  
  
 Vygenerování zdrojového kódu přímo z metadat SQL:  
  
 **sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**  
  
> [!NOTE]
> Při použití **možnost /pluralize** s ukázkovou databází Northwind, poznamenejte si následující chování. Když SqlMetal vytváří názvy řádků pro tabulky, názvy tabulek jsou v jednotném čísle. Při vytváří <xref:System.Data.Linq.DataContext> vlastnosti pro tabulky, názvy tabulek jsou množné číslo. Tabulky v ukázkové databázi Northwind jsou shodou okolností již v množném čísle. Proto neuvidíte, jak tato část funguje. Přestože jsou názvy tabulek databáze zpravidla zapisovány v jednotném čísle, v rozhraní .NET je rovněž obvyklé pojmenovávání kolekcí v množném čísle.  
  
## <a name="see-also"></a>Viz také

- [Postupy: Generování objektového modelu v jazyce Visual Basic nebo C#](../data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)
- [Generování kódu v LINQ to SQL](../data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [Externí mapování](../data/adonet/sql/linq/external-mapping.md)
