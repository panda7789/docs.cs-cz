---
title: "SqlMetal.exe (nástroj pro vytváření kódu)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLMetal [LINQ to SQL]
- code generation tool
- SQLMetal.exe
- LINQ to SQL, serialization
- LINQ to SQL, DBML files
- LINQ to SQL, SQLMetal
ms.assetid: 819e5a96-7646-4fdb-b14b-fe31221b0614
caps.latest.revision: "43"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c14c01c670eccbc7f13210d3c0bb7df7bec07679
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="sqlmetalexe-code-generation-tool"></a>SqlMetal.exe (nástroj pro vytváření kódu)
Nástroj příkazového řádku na SqlMetal generuje kód a mapování [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] komponentu [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Použitím možností uvedených dále v tomto tématu můžete dát nástroji SqlMetal pokyn, aby provedl několik různých úkonů, které zahrnují následující:  
  
-   Vygenerování zdrojového kódu a atributů mapování nebo souboru mapování z databáze.  
  
-   Vygenerování přechodného souboru .dbml (database markup language) z databáze za účelem přizpůsobení.  
  
-   Vygenerování zdrojového kódu a atributů mapování nebo souboru mapování ze souboru .dbml.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Ve výchozím nastavení, je uložen v souboru `drive`: \Program Files\Microsoft SDKs\Windows\v`n.nn`\bin. Pokud nenainstalujete Visual Studio, můžete získat také na SQLMetal soubor stáhněte [Windows SDK](http://go.microsoft.com/fwlink/?LinkId=142225).  
  
> [!NOTE]
>  Vývojáři, kteří používají Visual Studio můžete také použít [!INCLUDE[vs_ordesigner_long](../../../includes/vs-ordesigner-long-md.md)] ke generování tříd entit. Metoda využívající příkazový řádek je vhodná u velkých databází. Protože SqlMetal je nástroj příkazového řádku, můžete ho použít v procesu sestavení.  
  
 Chcete-li spustit tento nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio v systému Windows 7). Další informace najdete v tématu [příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md). Na příkazovém řádku zadejte následující příkaz:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
sqlmetal [options] [<input file>]  
```  
  
## <a name="options"></a>Možnosti  
 Chcete-li zobrazit aktuální seznam možnost, zadejte `sqlmetal /?` na příkazovém řádku z umístění instalace.  
  
 **Možnosti připojení**  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/ Server:**  *\<name >*|Určuje název databázového serveru.|  
|**/ databáze:**  *\<name >*|Určuje katalog databází na serveru.|  
|**Parametr/user:**  *\<name >*|Určuje přihlašovací jméno uživatele. Výchozí hodnota: Použít ověřování systému Windows.|  
|**/ Password:**  *\<heslo >*|Určuje heslo pro přihlášení. Výchozí hodnota: Použít ověřování systému Windows.|  
|**/ kontext:**  *\<připojovací řetězec >*|Určuje připojovací řetězec databáze. Nelze použít s **/server**, **/databáze**, **User**, nebo **/Password** možnosti.<br /><br /> Nezahrnujte název souboru do připojovacího řetězce. Místo toho přidejte název souboru do příkazového řádku jako vstupní soubor. Například následující řádek určuje "c:\northwnd.mdf" jako vstupní soubor: **/code:"c:\northwind.cs na sqlmetal" /language:csharp "c:\northwnd.mdf"**.|  
|**/ timeout:**  *\<sekund >*|Určuje hodnotu časového limitu při přístupu SqlMetal k databázi. Výchozí hodnota: 0 (to znamená žádný časový limit).|  
  
 **Možnosti extrakce**  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/Views**|Extrahuje zobrazení databáze.|  
|**/functions**|Extrahuje funkce databáze.|  
|**/sprocs**|Extrahuje uložené procedury.|  
  
 **Možnosti výstupu**  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/dbml** *[: soubor]*|Odešle výstup jako .dbml. Nelze použít s **/map** možnost.|  
|**/ kódu** *[: soubor]*|Odešle výstup jako zdrojový kód. Nelze použít s **/dbml** možnost.|  
|**/ map** *[: soubor]*|Generuje soubor mapování XML namísto atributů. Nelze použít s **/dbml** možnost.|  
  
 **Různé**  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/Language:**  *\<jazyka >*|Určuje jazyk zdrojového kódu.<br /><br /> Platný  *\<jazyk >*: vb, csharp.<br /><br /> Výchozí hodnota: Odvozeno z přípony názvu souboru kódu.|  
|**/ NAMESPACE:**  *\<name >*|Určuje obor názvů generovaného kódu. Výchozí hodnota: Žádný obor názvů.|  
|**/ Context:**  *\<typ >*|Určuje název třídy datového kontextu. Výchozí hodnota: Odvozen od názvu databáze.|  
|**/entitybase:**  *\<typ >*|Určuje základní třídu z tříd entit v generovaném kódu. Výchozí hodnota: Entity nemají žádnou základní třídu.|  
|**/ pluralizovat**|Automaticky převádí názvy tříd a členů do množného nebo jednotného čísla.<br /><br /> Tato možnost je dostupná pouze v USA Anglickou verzi.|  
|**/Serialization:**  *\<možnost >*|Generuje serializovatelné třídy.<br /><br /> Platný  *\<možnost >*: None, Unidirectional. Výchozí hodnota: Žádný.<br /><br /> Další informace najdete v tématu [serializace](../../../docs/framework/data/adonet/sql/linq/serialization.md).|  
  
 **Vstupní soubor**  
  
|Možnost|Popis|  
|------------|-----------------|  
|**\<vstupní soubor >**|Určuje soubor MDF systému SQL Server Express [!INCLUDE[ssEW](../../../includes/ssew-md.md)] soubor SDF nebo dbml pomocný soubor.|  
  
## <a name="remarks"></a>Poznámky  
 Funkce SqlMetal ve skutečnosti probíhá ve dvou krocích:  
  
-   Extrahování metadat databáze do souboru .dbml.  
  
-   Generování výstupního souboru s kódem.  
  
     Pomocí možnosti příkazového řádku, můžete vytvořit [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] nebo zdrojového kódu C#, nebo můžete vytvořit mapování souboru XML.  
  
 Chcete-li extrahovat metadata ze souboru .mdf, musíte zadat název souboru .mdf za všemi ostatními možnostmi.  
  
 Pokud žádné **/server** není zadaný, **localhost nebo sqlexpress** se předpokládá.  
  
 [!INCLUDE[sqprsqext](../../../includes/sqprsqext-md.md)]Pokud jeden nebo více z následujících podmínek jsou splněny, vyvolá výjimku:  
  
-   SqlMetal se pokusí extrahovat uloženou proceduru, která volá sama sebe.  
  
-   Úroveň vnoření uložené procedury, funkce nebo zobrazení je vyšší než 32.  
  
     SqlMetal tuto výjimku zachytí a ohlásí ji jako varování.  
  
 Chcete-li zadat název vstupního souboru, přidejte název souboru do příkazového řádku jako vstupní soubor. Včetně názvu souboru v připojovacím řetězci (pomocí **/kontext** možnost) není podporován.  
  
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
  
 **SqlMetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**  
  
> [!NOTE]
>  Při použití **/ pluralizovat** možnost s ukázková databáze Northwind, Všimněte si následujícího chování. Když SqlMetal vytváří názvy řádků pro tabulky, názvy tabulek jsou v jednotném čísle. Když umožňuje <xref:System.Data.Linq.DataContext> vlastnosti pro tabulky, názvy tabulek jsou množném čísle. Tabulky v ukázkové databázi Northwind jsou shodou okolností již v množném čísle. Proto neuvidíte, jak tato část funguje. Přestože jsou názvy tabulek databáze zpravidla zapisovány v jednotném čísle, v rozhraní .NET je rovněž obvyklé pojmenovávání kolekcí v množném čísle.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Generování objektového modelu v jazyce Visual Basic nebo C#](../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)  
 [Generování kódu v LINQ to SQL](../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)  
 [Externí mapování](../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
