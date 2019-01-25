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
ms.openlocfilehash: c9631ed7ecc854fe6f355eb4bbc2bfb5097ea770
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540621"
---
# <a name="sqlmetalexe-code-generation-tool"></a>SqlMetal.exe (nástroj pro vytváření kódu)
Nástroj příkazového řádku SqlMetal generuje kód a mapování pro [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] komponentu [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Použitím možností uvedených dále v tomto tématu můžete dát nástroji SqlMetal pokyn, aby provedl několik různých úkonů, které zahrnují následující:  
  
-   Vygenerování zdrojového kódu a atributů mapování nebo souboru mapování z databáze.  
  
-   Vygenerování přechodného souboru .dbml (database markup language) z databáze za účelem přizpůsobení.  
  
-   Vygenerování zdrojového kódu a atributů mapování nebo souboru mapování ze souboru .dbml.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Ve výchozím nastavení, se nachází v souboru `drive`: \Program Files\Microsoft SDKs\Windows\v`n.nn`\bin. Pokud nenainstalujete sady Visual Studio, můžete také si soubor SQLMetal Stáhnout [sady Windows SDK](https://go.microsoft.com/fwlink/?LinkId=142225).  
  
> [!NOTE]
>  Vývojáři, kteří používají Visual Studio můžete také použít [!INCLUDE[vs_ordesigner_long](../../../includes/vs-ordesigner-long-md.md)] k vytvoření tříd entit. Metoda využívající příkazový řádek je vhodná u velkých databází. Protože SqlMetal je nástroj příkazového řádku, můžete ho použít v procesu sestavení.  
  
 Ke spuštění nástroje, použijte příkazový řádek pro vývojáře pro Visual Studio (nebo příkazový řádek Visual Studio ve Windows 7). Další informace najdete v tématu [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md). Na příkazovém řádku zadejte následující příkaz:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
sqlmetal [options] [<input file>]  
```  
  
## <a name="options"></a>Možnosti  
 Pokud chcete zobrazit aktuální seznam možností, zadejte `sqlmetal /?` příkazového řádku z umístění instalace.  
  
 **Možnosti připojení**  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/ Server:**  *\<name >*|Určuje název databázového serveru.|  
|**/ databáze:**  *\<name >*|Určuje katalog databází na serveru.|  
|**/ user:**  *\<name >*|Určuje přihlašovací jméno uživatele. Výchozí hodnota: Použijte ověřování Windows.|  
|**/password:** *\<password>*|Určuje heslo pro přihlášení. Výchozí hodnota: Použijte ověřování Windows.|  
|**/ conn:**  *\<připojovací řetězec >*|Určuje připojovací řetězec databáze. Nelze použít s **/server**, **/database**, **/User**, nebo **/Password** možnosti.<br /><br /> Nezahrnujte název souboru do připojovacího řetězce. Místo toho přidejte název souboru do příkazového řádku jako vstupní soubor. Například následující řádek určuje "c:\northwnd.mdf" jako vstupní soubor: **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**.|  
|**/ timeout:**  *\<sekund >*|Určuje hodnotu časového limitu při přístupu SqlMetal k databázi. Výchozí hodnota: 0 (to znamená žádný časový limit).|  
  
 **Možnosti extrahování**  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/Views**|Extrahuje zobrazení databáze.|  
|**/functions**|Extrahuje funkce databáze.|  
|**/sprocs**|Extrahuje uložené procedury.|  
  
 **Možnosti výstupu**  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/dbml** *[: file]*|Odešle výstup jako .dbml. Nelze použít s **/map** možnost.|  
|**/ code** *[: file]*|Odešle výstup jako zdrojový kód. Nelze použít s **/dbml** možnost.|  
|**/ map** *[: file]*|Generuje soubor mapování XML namísto atributů. Nelze použít s **/dbml** možnost.|  
  
 **Různé**  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/Language:**  *\<jazyk >*|Určuje jazyk zdrojového kódu.<br /><br /> Platný  *\<jazyk >*: vb, csharp.<br /><br /> Výchozí hodnota: Odvozeno z přípony názvu souboru kódu.|  
|**/ NAMESPACE:**  *\<name >*|Určuje obor názvů generovaného kódu. Výchozí hodnota: Žádný obor názvů.|  
|**/ Context:**  *\<typ >*|Určuje název třídy datového kontextu. Výchozí hodnota: Odvozený od názvu databáze.|  
|**/entitybase:**  *\<typ >*|Určuje základní třídu z tříd entit v generovaném kódu. Výchozí hodnota: Entity nemají žádnou základní třídu.|  
|**/pluralize**|Automaticky převádí názvy tříd a členů do množného nebo jednotného čísla.<br /><br /> Tato možnost je dostupná jenom v USA. Anglickou verzi.|  
|**/Serialization:**  *\<možnost >*|Generuje serializovatelné třídy.<br /><br /> Platný  *\<možnost >*: Žádný, jednosměrný. Výchozí hodnota: Žádné<br /><br /> Další informace najdete v tématu [serializace](../../../docs/framework/data/adonet/sql/linq/serialization.md).|  
  
 **Vstupní soubor**  
  
|Možnost|Popis|  
|------------|-----------------|  
|**\<vstupní soubor >**|Určuje soubor .mdf serveru SQL Server Express [!INCLUDE[ssEW](../../../includes/ssew-md.md)] soubor SDF nebo přechodný soubor .dbml.|  
  
## <a name="remarks"></a>Poznámky  
 Funkce SqlMetal ve skutečnosti probíhá ve dvou krocích:  
  
-   Extrahování metadat databáze do souboru .dbml.  
  
-   Generování výstupního souboru s kódem.  
  
     Pomocí vhodných možností příkazového řádku můžete vytvářet zdrojový kód jazyka Visual Basic nebo C#, nebo můžete vytvořit soubor mapování XML.  
  
 Chcete-li extrahovat metadata ze souboru .mdf, musíte zadat název souboru .mdf za všemi ostatními možnostmi.  
  
 Pokud ne **/server** není zadána, **localhost/sqlexpress** se předpokládá, že.  
  
 [!INCLUDE[sqprsqext](../../../includes/sqprsqext-md.md)] vyvolá výjimku, pokud platí jedna nebo více z následujících podmínek:  
  
-   SqlMetal se pokusí extrahovat uloženou proceduru, která volá sama sebe.  
  
-   Úroveň vnoření uložené procedury, funkce nebo zobrazení je vyšší než 32.  
  
     SqlMetal tuto výjimku zachytí a ohlásí ji jako varování.  
  
 Chcete-li zadat název vstupního souboru, přidejte název souboru do příkazového řádku jako vstupní soubor. Včetně názvu souboru do připojovacího řetězce (pomocí **/conn** možnost) se nepodporuje.  
  
## <a name="examples"></a>Příklady  
 Vygenerování souboru .dbml obsahujícího extrahovaná metadata SQL:  
  
 **SqlMetal /server:myserver /database:northwind /dbml:mymeta.dbml**  
  
 Vygenerování souboru .dbml obsahujícího extrahovaná metadata SQL ze souboru .mdf pomocí SQL Server Express:  
  
 **SqlMetal /dbml:mymeta.dbml mydbfile.mdf**  
  
 Vygenerování souboru .dbml obsahujícího extrahovaná metadata SQL z SQL Server Express:  
  
 **SqlMetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**  
  
 Vygenerování zdrojového kódu ze souboru metadat .dbml:  
  
 **SqlMetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**  
  
 Vygenerování zdrojového kódu přímo z metadat SQL:  
  
 **sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**  
  
> [!NOTE]
>  Při použití **/ pluralize** možnost s ukázkovou databází Northwind, pamatujte na následující chování. Když SqlMetal vytváří názvy řádků pro tabulky, názvy tabulek jsou v jednotném čísle. Který je <xref:System.Data.Linq.DataContext> vlastnosti pro tabulky, názvy tabulek jsou v množném čísle. Tabulky v ukázkové databázi Northwind jsou shodou okolností již v množném čísle. Proto neuvidíte, jak tato část funguje. Přestože jsou názvy tabulek databáze zpravidla zapisovány v jednotném čísle, v rozhraní .NET je rovněž obvyklé pojmenovávání kolekcí v množném čísle.  
  
## <a name="see-also"></a>Viz také:
- [Postupy: Generování objektového modelu v jazyce Visual Basic neboC#](../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)
- [Generování kódu v LINQ to SQL](../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [Externí mapování](../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
