---
title: SqlMetal.exe (nástroj pro vytváření kódu)
description: Pochopení SqlMetal.exe nástroje pro generování kódu. Použijte nástroj k vygenerování kódu a mapování pro LINQ to SQL komponentu rozhraní .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- SQLMetal [LINQ to SQL]
- code generation tool
- SQLMetal.exe
- LINQ to SQL, serialization
- LINQ to SQL, DBML files
- LINQ to SQL, SQLMetal
ms.assetid: 819e5a96-7646-4fdb-b14b-fe31221b0614
ms.openlocfilehash: 84cad85a7a9fc4b420b57543b7f258607be4ab52
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517045"
---
# <a name="sqlmetalexe-code-generation-tool"></a>SqlMetal.exe (nástroj pro vytváření kódu)
Nástroj příkazového řádku SqlMetal generuje kód a mapování pro [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] komponentu .NET Framework. Použitím možností uvedených dále v tomto tématu můžete dát nástroji SqlMetal pokyn, aby provedl několik různých úkonů, které zahrnují následující:  
  
- Vygenerování zdrojového kódu a atributů mapování nebo souboru mapování z databáze.  
  
- Vygenerování přechodného souboru .dbml (database markup language) z databáze za účelem přizpůsobení.  
  
- Vygenerování zdrojového kódu a atributů mapování nebo souboru mapování ze souboru .dbml.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Ve výchozím nastavení se soubor nachází v umístění `drive` : \Program Files\Microsoft SDKs\Windows\v `n.nn` \Bin. Pokud nenainstalujete aplikaci Visual Studio, můžete také získat soubor SQLMetal stažením [Windows SDK](https://go.microsoft.com/fwlink/?LinkId=142225).  
  
> [!NOTE]
> Vývojáři, kteří používají Visual Studio, mohou také použít Návrhář relací objektů k vygenerování tříd entit. Metoda využívající příkazový řádek je vhodná u velkých databází. Protože SqlMetal je nástroj příkazového řádku, můžete ho použít v procesu sestavení.  
  
 Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md). Na příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntax  
  
```console  
sqlmetal [options] [<input file>]  
```  
  
## <a name="options"></a>Možnosti  
 Chcete-li zobrazit nejaktuálnější seznam možností, zadejte do `sqlmetal /?` příkazového řádku z nainstalovaného umístění.  
  
 **Možnosti připojení**  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/Server:***\<name>*|Určuje název databázového serveru.|  
|**/Database:***\<name>*|Určuje katalog databází na serveru.|  
|**/User:***\<name>*|Určuje ID přihlášeného uživatele. Výchozí hodnota: použijte ověřování systému Windows.|  
|**/Password:***\<password>*|Určuje heslo pro přihlášení. Výchozí hodnota: Použít ověřování systému Windows.|  
|**/Conn:***\<connection string>*|Určuje připojovací řetězec databáze. Nelze použít s možnostmi **/Server**, **/Database**, **/User**nebo **/Password** .<br /><br /> Nezahrnujte název souboru do připojovacího řetězce. Místo toho přidejte název souboru do příkazového řádku jako vstupní soubor. Například následující řádek určuje "c:\northwnd.mdf" jako vstupní soubor: **SQLMetal/Code: "c:\Northwind.cs"/Language: CSharp "c:\northwnd.mdf"**.|  
|**/timeout:***\<seconds>*|Určuje hodnotu časového limitu při přístupu SqlMetal k databázi. Výchozí hodnota: 0 (to znamená žádný časový limit).|  
  
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
|**/Language:***\<language>*|Určuje jazyk zdrojového kódu.<br /><br /> Platný *\<language>* : VB, CSharp.<br /><br /> Výchozí hodnota: Odvozeno z přípony názvu souboru kódu.|  
|**/Namespace:***\<name>*|Určuje obor názvů generovaného kódu. Výchozí hodnota: Žádný obor názvů.|  
|**/Context:***\<type>*|Určuje název třídy datového kontextu. Výchozí hodnota: Odvozen od názvu databáze.|  
|**/entitybase:***\<type>*|Určuje základní třídu z tříd entit v generovaném kódu. Výchozí hodnota: Entity nemají žádnou základní třídu.|  
|**/pluralize**|Automaticky převádí názvy tříd a členů do množného nebo jednotného čísla.<br /><br /> Tato možnost je dostupná pouze v anglické verzi (USA).|  
|**/Serialization:***\<option>*|Generuje serializovatelné třídy.<br /><br /> Platný *\<option>* : None, jednosměrný. Výchozí hodnota: Žádný.<br /><br /> Další informace naleznete v tématu [serializace](../data/adonet/sql/linq/serialization.md).|  
  
 **Vstupní soubor**  
  
|Možnost|Popis|  
|------------|-----------------|  
|**\<input file>**|Určuje SQL Server Express soubor. mdf, soubor SQL Server Compact 3,5. sdf nebo zprostředkující soubor. dbml.|  
  
## <a name="remarks"></a>Poznámky  
 Funkce SqlMetal ve skutečnosti probíhá ve dvou krocích:  
  
- Extrahování metadat databáze do souboru .dbml.  
  
- Generování výstupního souboru s kódem.  
  
     Pomocí příslušných možností příkazového řádku můžete vydávat Visual Basic nebo zdrojový kód v jazyce C# nebo můžete vytvoření souboru mapování XML.  
  
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
  
 **SQLMetal/Server: MyServer/Database: Northwind/Namespace: NWIND/Code: NWIND. cs/Language: CSharp**  
  
> [!NOTE]
> Když použijete možnost **/pluralize** s ukázkovou databází Northwind, pamatujte na následující chování. Když SqlMetal vytváří názvy řádků pro tabulky, názvy tabulek jsou v jednotném čísle. Když vytváří <xref:System.Data.Linq.DataContext> vlastnosti pro tabulky, názvy tabulek jsou plural. Tabulky v ukázkové databázi Northwind jsou shodou okolností již v množném čísle. Proto neuvidíte, jak tato část funguje. Přestože jsou názvy tabulek databáze zpravidla zapisovány v jednotném čísle, v rozhraní .NET je rovněž obvyklé pojmenovávání kolekcí v množném čísle.  
  
## <a name="see-also"></a>Viz také

- [Postupy: Generování objektového modelu v jazyce Visual Basic nebo C#](../data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)
- [Generování kódu v LINQ to SQL](../data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [Externí mapování](../data/adonet/sql/linq/external-mapping.md)
