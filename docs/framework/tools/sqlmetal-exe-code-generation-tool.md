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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044080"
---
# <a name="sqlmetalexe-code-generation-tool"></a>SqlMetal.exe (nástroj pro vytváření kódu)
Nástroj příkazového řádku SQLMetal generuje kód a mapování pro [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] komponentu .NET Framework. Použitím možností uvedených dále v tomto tématu můžete dát nástroji SqlMetal pokyn, aby provedl několik různých úkonů, které zahrnují následující:  
  
- Vygenerování zdrojového kódu a atributů mapování nebo souboru mapování z databáze.  
  
- Vygenerování přechodného souboru .dbml (database markup language) z databáze za účelem přizpůsobení.  
  
- Vygenerování zdrojového kódu a atributů mapování nebo souboru mapování ze souboru .dbml.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Ve výchozím nastavení se soubor nachází v `drive`umístění: \Program Files\Microsoft SDKs\Windows\v \Bin.`n.nn` Pokud nenainstalujete aplikaci Visual Studio, můžete také získat soubor SQLMetal stažením [Windows SDK](https://go.microsoft.com/fwlink/?LinkId=142225).  
  
> [!NOTE]
> Vývojáři, kteří používají Visual Studio, mohou také použít Návrhář relací objektů k vygenerování tříd entit. Metoda využívající příkazový řádek je vhodná u velkých databází. Protože SqlMetal je nástroj příkazového řádku, můžete ho použít v procesu sestavení.  
  
 Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md). Na příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
sqlmetal [options] [<input file>]  
```  
  
## <a name="options"></a>Možnosti  
 Chcete-li zobrazit nejaktuálnější seznam možností, zadejte `sqlmetal /?` do příkazového řádku z nainstalovaného umístění.  
  
 **Možnosti připojení**  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/Server:**  *název\<>*|Určuje název databázového serveru.|  
|**/Database:**  *název\<>*|Určuje katalog databází na serveru.|  
|**/User:**  *název\<>*|Určuje přihlašovací jméno uživatele. Výchozí hodnota: Použijte ověřování systému Windows.|  
|**/Password:**  *>\<hesla*|Určuje heslo pro přihlášení. Výchozí hodnota: Použijte ověřování systému Windows.|  
|**/Conn:** > připojovacího řetězce  *\<*|Určuje připojovací řetězec databáze. Nelze použít s možnostmi **/Server**, **/Database**, **/User**nebo **/Password** .<br /><br /> Nezahrnujte název souboru do připojovacího řetězce. Místo toho přidejte název souboru do příkazového řádku jako vstupní soubor. Například následující řádek určuje "c:\northwnd.mdf" jako vstupní soubor: **SQLMetal/Code: "c:\Northwind.cs"/Language: CSharp "c:\northwnd.mdf"** .|  
|**/timeout:**  *>\<sekund*|Určuje hodnotu časového limitu při přístupu SqlMetal k databázi. Výchozí hodnota: 0 (tj. žádný časový limit).|  
  
 **Možnosti extrakce**  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/views**|Extrahuje zobrazení databáze.|  
|**/functions**|Extrahuje funkce databáze.|  
|**/sprocs**|Extrahuje uložené procedury.|  
  
 **Možnosti výstupu**  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/dbml** *[: soubor]*|Odešle výstup jako .dbml. Nelze použít s možností **/map** .|  
|**/Code** *[: soubor]*|Odešle výstup jako zdrojový kód. Nelze použít s možností **/dbml** .|  
|**/map** *[: soubor]*|Generuje soubor mapování XML namísto atributů. Nelze použít s možností **/dbml** .|  
  
 **Různé**  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/Language:**  *>\<jazyka*|Určuje jazyk zdrojového kódu.<br /><br /> *Platný\<jazyk >* : VB, CSharp.<br /><br /> Výchozí hodnota: Odvozeno z rozšíření názvu souboru kódu.|  
|**/Namespace:**  *název\<>*|Určuje obor názvů generovaného kódu. Výchozí hodnota: Žádný obor názvů.|  
|**/Context:**  *Zadejte\<>*|Určuje název třídy datového kontextu. Výchozí hodnota: Odvozeno z názvu databáze.|  
|**/entitybase:**  *Zadejte\<>*|Určuje základní třídu z tříd entit v generovaném kódu. Výchozí hodnota: Entity nemají žádnou základní třídu.|  
|**/pluralize**|Automaticky převádí názvy tříd a členů do množného nebo jednotného čísla.<br /><br /> Tato možnost je dostupná jenom v USA. Anglická verze|  
|**/Serialization:**  *možnost\<>*|Generuje serializovatelné třídy.<br /><br /> *Platná\<možnost >* : None, jednosměrný. Výchozí hodnota: Žádné<br /><br /> Další informace naleznete v tématu [serializace](../data/adonet/sql/linq/serialization.md).|  
  
 **Vstupní soubor**  
  
|Možnost|Popis|  
|------------|-----------------|  
|**\<> vstupního souboru**|Určuje SQL Server Express soubor. mdf, soubor SQL Server Compact 3,5. sdf nebo zprostředkující soubor. dbml.|  
  
## <a name="remarks"></a>Poznámky  
 Funkce SqlMetal ve skutečnosti probíhá ve dvou krocích:  
  
- Extrahování metadat databáze do souboru .dbml.  
  
- Generování výstupního souboru s kódem.  
  
     Pomocí příslušných možností příkazového řádku můžete vyvolat Visual Basic nebo C# zdrojový kód nebo můžete vystavit soubor mapování XML.  
  
 Chcete-li extrahovat metadata ze souboru .mdf, musíte zadat název souboru .mdf za všemi ostatními možnostmi.  
  
 Pokud se nezadá žádný **/Server** , předpokládá se **localhost/SQLEXPRESS** .  
  
 Microsoft SQL Server 2005 vyvolá výjimku, pokud je splněna jedna nebo více z následujících podmínek:  
  
- SqlMetal se pokusí extrahovat uloženou proceduru, která volá sama sebe.  
  
- Úroveň vnoření uložené procedury, funkce nebo zobrazení je vyšší než 32.  
  
     SqlMetal tuto výjimku zachytí a ohlásí ji jako varování.  
  
 Chcete-li zadat název vstupního souboru, přidejte název souboru do příkazového řádku jako vstupní soubor. Zahrnutí názvu souboru do připojovacího řetězce (pomocí možnosti **/Conn** ) není podporováno.  
  
## <a name="examples"></a>Příklady  
 Vygenerování souboru .dbml obsahujícího extrahovaná metadata SQL:  
  
 **SQLMetal/Server: MyServer/Database: Northwind/dbml: mymeta. dbml**  
  
 Vygenerování souboru .dbml obsahujícího extrahovaná metadata SQL ze souboru .mdf pomocí SQL Server Express:  
  
 **SQLMetal/dbml: mymeta. dbml mydbfile. mdf**  
  
 Vygenerování souboru .dbml obsahujícího extrahovaná metadata SQL z SQL Server Express:  
  
 **SQLMetal/Server: .\SQLEXPRESS/dbml: mymeta. dbml/Database: Northwind**  
  
 Vygenerování zdrojového kódu ze souboru metadat .dbml:  
  
 **SQLMetal/Namespace: NWIND/Code: NWIND. cs/Language: CSharp mymetal. dbml**  
  
 Vygenerování zdrojového kódu přímo z metadat SQL:  
  
 **sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**  
  
> [!NOTE]
> Když použijete možnost **/pluralize** s ukázkovou databází Northwind, pamatujte na následující chování. Když SqlMetal vytváří názvy řádků pro tabulky, názvy tabulek jsou v jednotném čísle. Když vytváří <xref:System.Data.Linq.DataContext> vlastnosti pro tabulky, názvy tabulek jsou plural. Tabulky v ukázkové databázi Northwind jsou shodou okolností již v množném čísle. Proto neuvidíte, jak tato část funguje. Přestože jsou názvy tabulek databáze zpravidla zapisovány v jednotném čísle, v rozhraní .NET je rovněž obvyklé pojmenovávání kolekcí v množném čísle.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Generování objektového modelu v Visual Basic neboC#](../data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)
- [Generování kódu v LINQ to SQL](../data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [Externí mapování](../data/adonet/sql/linq/external-mapping.md)
