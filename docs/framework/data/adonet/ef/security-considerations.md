---
title: Důležité informace o zabezpečení (Entity Framework)
ms.date: 03/30/2017
ms.assetid: 84758642-9b72-4447-86f9-f831fef46962
ms.openlocfilehash: 25d313f9c6f71d946ed8d9cc5db2e99dc84983b3
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43456841"
---
# <a name="security-considerations-entity-framework"></a>Důležité informace o zabezpečení (Entity Framework)
Toto téma popisuje důležité informace o zabezpečení, které jsou specifické pro vývoj, nasazování a spouštění [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikací. Měli postupovat také podle doporučení pro vytváření zabezpečených [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] aplikací. Další informace najdete v tématu [Přehled zabezpečení](../../../../../docs/framework/data/adonet/security-overview.md).  
  
## <a name="general-security-considerations"></a>Důležité informace o obecné zabezpečení  
 Platí následující aspekty zabezpečení pro všechny aplikace, které používají [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
#### <a name="use-only-trusted-data-source-providers"></a>Použijte pouze poskytovatelé zdrojů důvěryhodná data.  
 Ke komunikaci se zdrojem dat, musíte udělat následující zprostředkovatele:  
  
-   Zobrazit připojovací řetězec z [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
-   Převede uzel stromu příkazů na zdroj dat nativní dotazovací jazyk.  
  
-   Sestavení a vrátit sad výsledků dotazu.  
  
 Během přihlášení informace, které je založená na heslo uživatele se předává k serveru knihovny sítě podkladového zdroje dat. Škodlivý poskytovatele může ukrást přihlašovací údaje uživatele, generovat škodlivý dotazy nebo manipulovat s sadu výsledků dotazu.  
  
#### <a name="encrypt-your-connection-to-protect-sensitive-data"></a>Šifrovat připojení chránit citlivá data.  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Nezpracovává šifrování dat přímo. Pokud uživatelé k datům přistupují přes veřejnou síť, vaše aplikace by měla navázání šifrovaného připojení ke zdroji dat pro zvýšení zabezpečení. Další informace naleznete v dokumentaci týkající se zabezpečení pro zdroj dat. Zdroj dat SQL serveru, naleznete v tématu [šifrování připojení k serveru SQL Server](https://go.microsoft.com/fwlink/?LinkId=119544).  
  
#### <a name="secure-the-connection-string"></a>Zabezpečený připojovací řetězec.  
 Zabezpečení přístupu ke zdroji dat je jedním z nejdůležitějších cílů při zabezpečování aplikace. Připojovací řetězec představuje potenciální ohrožení zabezpečení, není-li zabezpečena, nebo pokud je nesprávně vytvořen. Při ukládání informací o připojení ve formátu prostého textu nebo jej zachovat v paměti, riskujete tím bylo narušeno celého systému. Dál jsou uvedené doporučené metody pro zabezpečení připojovací řetězce:  
  
-   Použijte ověřování Windows se zdrojem dat serveru SQL Server.  
  
     Pokud používáte ověřování Windows pro připojení ke zdroji dat SQL serveru, připojovací řetězec neobsahuje informace o přihlášení a hesla.  
  
-   Šifrování pomocí chráněné konfigurace oddíly konfiguračního souboru.  
  
     Technologie ASP.NET poskytuje funkci s názvem chráněné konfigurace, která umožňuje šifrování citlivých informací v konfiguračním souboru. Přestože primárně určený pro technologii ASP.NET, můžete také použít chráněné konfigurace šifrování oddíly konfiguračních souborů aplikace Windows. Podrobný popis nových funkcí chráněné konfigurace najdete v tématu [šifrování konfigurační informace pomocí Protected Configuration](https://msdn.microsoft.com/library/51cdfe5b-9d82-458c-94ff-c551c4f38ed1).  
  
-   Store připojovací řetězce v zabezpečené konfigurační soubory.  
  
     Ve zdrojovém kódu by nikdy vložit připojovací řetězce. Můžete ukládání připojovacích řetězců v konfiguračních souborech, které eliminuje potřebu vložení do kódu vaší aplikace. Ve výchozím nastavení ukládá Průvodce datovým modelem Entity připojovací řetězce v konfiguračním souboru aplikace. Tomuto souboru zabráníte neoprávněnému přístupu musíte zabezpečit.  
  
-   Tvůrci připojovacích řetězců používejte pro dynamicky vytváření připojení.  
  
     Pokud je nutné vytvořit připojovací řetězce za běhu, použijte <xref:System.Data.EntityClient.EntityConnectionStringBuilder> třídy. Tato třída Tvůrce řetězec pomáhá zabránit útoky prostřednictvím injektáže připojovací řetězec tak, že ověřování a uvozovací znaky neplatné vstupní informace. Další informace najdete v tématu [postupy: sestavení připojovacího řetězce EntityConnection](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md). Třídu Tvůrce příslušného řetězcového také použít k vytvoření připojovacího řetězce datového zdroje, který je součástí [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] připojovací řetězec. Informace o tvůrci připojovacích řetězců pro poskytovatele ADO.NET, naleznete v tématu [tvůrci připojovacích řetězců](../../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
 Další informace najdete v tématu [chrání informace o připojení](../../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
#### <a name="do-not-expose-an-entityconnection-to-untrusted-users"></a>Nezveřejňujte EntityConnection nedůvěryhodným uživatelům.  
 <xref:System.Data.EntityClient.EntityConnection> Zpřístupňuje připojovací řetězec z nadřízené připojení. Uživatel s přístupem k <xref:System.Data.EntityClient.EntityConnection> objektu můžete také změnit <xref:System.Data.ConnectionState> podkladové připojení. <xref:System.Data.EntityClient.EntityConnection> Třída není bezpečné pro vlákna.  
  
#### <a name="do-not-pass-connections-outside-the-security-context"></a>Nepředávejte připojení mimo kontext zabezpečení.  
 Po vytvoření připojení se nesmí předat mimo kontext zabezpečení. Například jedno vlákno s oprávněním k otevření připojení neměli ukládat připojení v globálním umístění. Pokud je připojení v globálním umístění k dispozici, pak jiné škodlivé vlákno můžete používat otevřené připojení bez nutnosti explicitně udělí oprávnění k němu oprávnění.  
  
#### <a name="be-aware-that-logon-information-and-passwords-may-be-visible-in-a-memory-dump"></a>Mějte na paměti, že informace o přihlášení a hesla můžou být vidět ve výpisu stavu paměti.  
 Pokud je přihlášení a hesla informace o zdroji dat je zadán v připojovacím řetězci, tyto informace je udržována v paměti, dokud uvolňování paměti získá prostředky. Díky tomu je možné určit, kdy řetězec hesla je již v paměti. Pokud aplikace spadne, souboru výpisu paměti může obsahovat citlivé bezpečnostní informace, a uživatel, který spouští aplikaci a každý uživatel s přístupem pro správu do počítače můžete zobrazit soubor výpisu paměti. Použijte ověřování Windows pro připojení k serveru Microsoft SQL Server.  
  
#### <a name="grant-users-only-the-necessary-permissions-in-the-data-source"></a>Uživatelům udělte pouze nezbytná oprávnění ve zdroji dat.  
 Správce zdrojů dat měli udělit pouze nezbytná oprávnění pro uživatele. I když [!INCLUDE[esql](../../../../../includes/esql-md.md)] nemá příkazy DML podpory, které mění data, jako jsou INSERT, UPDATE nebo DELETE, uživatelé stále přístup připojení ke zdroji dat. Uživatel se zlými úmysly může provádět příkazy DML v nativním jazyce zdroj dat použít toto připojení.  
  
#### <a name="run-applications-with-the-minimum-permissions"></a>Spouštění aplikací s minimálními oprávněními.  
 Když povolíte spravované aplikace na spuštění pomocí oprávnění plné důvěryhodnosti, [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] neomezuje přístup aplikace k vašemu počítači. To může umožnit ohrožení zabezpečení v aplikaci k ohrožení celý systém. Zabezpečení přístupu kódu a další mechanismy zabezpečení ve [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)], by měl spouštět aplikace s částečným vztahem důvěryhodnosti oprávněními a s minimální sadu oprávnění, která jsou potřebná k povolení aplikace pro funkce. Minimální oprávnění jsou následující přístupová oprávnění kódu vaší [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] potřeby aplikace:  
  
-   <xref:System.Security.Permissions.FileIOPermission>: <xref:System.Security.Permissions.FileIOPermissionAccess.Write> k otevírání souborů Zadaná metadata nebo <xref:System.Security.Permissions.FileIOPermissionAccess.PathDiscovery> adresáři pro soubory metadat.  
  
-   <xref:System.Security.Permissions.ReflectionPermission>: <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess> podporovat LINQ dotazů entity.  
  
-   <xref:System.Transactions.DistributedTransactionPermission>: <xref:System.Security.Permissions.PermissionState.Unrestricted> k zařazení <xref:System.Transactions> <xref:System.Transactions.Transaction>.  
  
-   <xref:System.Security.Permissions.SecurityPermission>: <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> k serializaci výjimky pomocí <xref:System.Runtime.Serialization.ISerializable> rozhraní.  
  
-   Oprávnění k otevření připojení k databázi a spusťte příkazy na databázi, jako například <xref:System.Data.SqlClient.SqlClientPermission> pro databázi serveru SQL Server.  
  
 Další informace najdete v tématu [zabezpečení přístupu kódu a ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md).  
  
#### <a name="do-not-install-untrusted-applications"></a>Nedůvěryhodné aplikace není nainstalovaný.  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Nevynucuje žádná oprávnění zabezpečení a vyvolá žádné uživatelem zadané data objektový kód v procesu bez ohledu na to, bez ohledu na to, zda je důvěryhodný. Ujistěte se, že ověřování a autorizaci klienta se provádí v úložišti dat a aplikací.  
  
#### <a name="restrict-access-to-all-configuration-files"></a>Omezení přístupu k všechny konfigurační soubory.  
 Správce musí omezit přístup pro zápis pro všechny soubory, které určují konfiguraci aplikace, včetně enterprisesec.config, security.config, machine.conf, a konfigurační soubor aplikace \< *aplikace* >. exe.config.  
  
 Výchozí název zprostředkovatele je upravitelná v app.config. Klientská aplikace musí nést odpovědnost za přístup k příslušný prostředkovatel prostřednictvím standardního poskytovatele objekt pro vytváření modelu pomocí silného názvu.  
  
#### <a name="restrict-permissions-to-the-model-and-mapping-files"></a>Omezení oprávnění k modelu a souborů mapování.  
 Správce musí omezit přístup pro zápis do modelu a souborů mapování (edmx, .csdl, .ssdl nebo .msl) pouze uživatelům, kteří upravit model nebo mapování. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Pouze za běhu vyžaduje k těmto souborům přístup pro čtení. Správce by měl také omezit přístup na objektové vrstvě a předem kompilovaných zobrazení souborů zdrojového kódu, které jsou generovány [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] nástroje.  
  
## <a name="security-considerations-for-queries"></a>Důležité informace o zabezpečení pro dotazy  
 Při dotazování na konceptuální model, platí následující aspekty zabezpečení. Tyto úvahy platí pro [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotazy s zprostředkovatel EntityClient a objekt dotazy pomocí jazyka LINQ, [!INCLUDE[esql](../../../../../includes/esql-md.md)]a metody Tvůrce dotazu.  
  
#### <a name="prevent-sql-injection-attacks"></a>Zabránění útokům prostřednictvím injektáže SQL.  
 Aplikace často trvat, než externí vstup (uživatele nebo jiné externí agenta) a provádět akce na základě těchto informací. Žádné vstup, který je přímo nebo nepřímo odvozen od uživatele nebo externí agenta může mít obsah, který používá syntaxi cílový jazyk k vykonávání neoprávněným akcím. Pokud cílový jazyk je jazyk SQL (Structured Query), například [!INCLUDE[tsql](../../../../../includes/tsql-md.md)], tato manipulace se označuje jako útok prostřednictvím injektáže SQL. Uživatel se zlými úmysly může vložit příkazy přímo do dotazu a vyřadit tabulku databáze, způsobit odepření služby nebo jinak změnit druh operace právě probíhá.  
  
-   [!INCLUDE[esql](../../../../../includes/esql-md.md)] útoky prostřednictvím injektáže:  
  
     Útoky prostřednictvím injektáže SQL lze provádět v [!INCLUDE[esql](../../../../../includes/esql-md.md)] zadáním škodlivého zadání hodnoty, které se používají v predikátu dotazu a názvy parametrů. Aby nedošlo k ohrožení útok prostřednictvím injektáže SQL, byste nikdy neměli kombinovat vstupu uživatele s [!INCLUDE[esql](../../../../../includes/esql-md.md)] text příkazu.  
  
     [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotazy přijímají parametry všude, že se přijímají literály. Parametrizované dotazy byste měli použít místo vloženého literály z externí agenta přímo do dotazu. Měli byste také zvážit použití metody Tvůrce dotazů bezpečně vytvořit [Entity SQL](https://msdn.microsoft.com/library/05685434-05e6-41c2-8d5e-8933b88a40b0).  
  
-   [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)] útoky prostřednictvím injektáže:  
  
     I když sestavení dotazu je možné v [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)], se provádí prostřednictvím rozhraní API objektu modelu. Na rozdíl od [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotazy, [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)] dotazy nejsou skládá pomocí zacházení s řetězci nebo zřetězení a nejsou náchylný k tradiční útoky prostřednictvím injektáže SQL.  
  
#### <a name="prevent-very-large-result-sets"></a>Zabraňte velmi velké množství výsledků.  
 Výsledek velmi velké sady může způsobit, že systém klienta pro vypnutí klient je provádění operací, které spotřebovávají prostředky přímo úměrná velikosti sady výsledků dotazu. Velké množství výsledků neočekávaně může dojít za následujících podmínek:  
  
-   V dotazech ve velké databázi, které neobsahují podmínek příslušný filtr.  
  
-   V dotazech, které vytvářejí Kartézském spojení na serveru.  
  
-   Ve vnořené [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotazy.  
  
 Při přijímání vstupu uživatele, musíte se ujistit, že vstup nemůže způsobit sad výsledků dotazu se větší, než co může systém zpracovat. Můžete také použít <xref:System.Linq.Queryable.Take%2A> metoda [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)] nebo [LIMIT](../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) operátor v [!INCLUDE[esql](../../../../../includes/esql-md.md)] omezení velikosti sady výsledků dotazu.  
  
#### <a name="avoid-returning-iqueryable-results-when-exposing-methods-to-potentially-untrusted-callers"></a>Vyhněte se vrací typ IQueryable výsledky při zpřístupňuje metody pro potenciálně nedůvěryhodných volajících.  
 Vyhněte se vracení <xref:System.Linq.IQueryable%601> typy z metod, které jsou vystaveny potenciálně nedůvěryhodných volajících z následujících důvodů:  
  
-   Příjemce dotaz, který poskytuje <xref:System.Linq.IQueryable%601> typ může volat metody ve výsledku, který vystavit zabezpečených dat, případně zvyšte velikost sady výsledků dotazu. Představte si třeba následující podpis metody:  
  
    ```  
    public IQueryable<Customer> GetCustomer(int customerId)  
    ```  
  
     Příjemce tento dotaz lze zavolat `.Include("Orders")` na vrácený `IQueryable<Customer>` data, která dotaz neměl v úmyslu ke zveřejnění. To se můžete vyhnout tak, že změníte návratový typ metody, která <xref:System.Collections.Generic.IEnumerable%601> a volání metody (například `.ToList()`), který bude realizována výsledky.  
  
-   Protože <xref:System.Linq.IQueryable%601> dotazy jsou spouštěny, když jsou procházen výsledky, příjemce dotaz, který poskytuje <xref:System.Linq.IQueryable%601> typ může zachytit výjimky, které jsou vyvolány. Výjimky mohou obsahovat informace, které nejsou určeny pro spotřebitele.  
  
## <a name="security-considerations-for-entities"></a>Důležité informace o zabezpečení pro entity  
 Při vytváření a práci s typy entit, platí následující aspekty zabezpečení.  
  
#### <a name="do-not-share-an-objectcontext-across-application-domains"></a>Nesdílejte objektu ObjectContext napříč doménami aplikace.  
 Sdílení <xref:System.Data.Objects.ObjectContext> více než jedné aplikace domény může zveřejnit informace v připojovacím řetězci. Místo toho by měl přenos Serializované objekty nebo grafů objektů do jiné domény aplikace a pak připojte těchto objektů do <xref:System.Data.Objects.ObjectContext> v této doméně aplikace. Další informace najdete v tématu [serializaci objektů](https://msdn.microsoft.com/library/06c77f9b-5b2e-4c78-b3e3-8c148ba0ea99).  
  
#### <a name="prevent-type-safety-violations"></a>Zabraňte porušení bezpečnosti typu.  
 Pokud je porušena bezpečnost typů, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] nemůže zaručit integritu dat v objektech. Typ bezpečný přístup z více narušením by mohlo dojít, pokud je povoleno nedůvěryhodné aplikace, které poběží s zabezpečení přístupu kódu úplného vztahu důvěryhodnosti.  
  
#### <a name="handle-exceptions"></a>Zpracování výjimek.  
 Přístup k metodám a vlastnostem <xref:System.Data.Objects.ObjectContext> v rámci bloku try-catch. Zachycování výjimek brání neošetřené výjimky z vystavení položky <xref:System.Data.Objects.ObjectStateManager> nebo informace o modelu (jako jsou názvy tabulek) pro uživatele vaší aplikace.  
  
## <a name="security-considerations-for-aspnet-applications"></a>Důležité informace o zabezpečení pro aplikace ASP.NET  
 Následující by měl být při práci s cestami v [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] aplikací.  
  
#### <a name="verify-whether-your-host-performs-path-checks"></a>Ověřte, zda váš hostitel provádí kontroly cestu.  
 Když `|DataDirectory|` (ohraničen symboly kanálu) náhradní řetězec se používá, [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] ověří, zda je podporována Vyhodnocená cesta. Například ".." není povolený za `DataDirectory`. Stejné kontroly pro vyřešení operátor kořenového adresáře webové aplikace (`~`) provádí proces hostování [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)]. Služba IIS provede tato kontrola; hostitelé než IIS však nemusí ověřte, že je podporované Vyhodnocená cesta. Měli byste vědět chování hostitele, na kterém je nasazená [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikace.  
  
#### <a name="do-not-make-assumptions-about-resolved-path-names"></a>Nedovolte, aby byly předpoklady o názvech Vyhodnocená cesta.  
 I když hodnotách, které kořenové – operátor (`~`) a `DataDirectory` vyřešit náhradní řetězec by měl zůstat konstantní za běhu aplikace [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] neomezuje hostitele v úpravách tyto hodnoty.  
  
#### <a name="verify-the-path-length-before-deployment"></a>Ověřte délku cesty před nasazením.  
 Před nasazením [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikace, ujistěte se, že hodnoty kořenové – operátor (~) a `DataDirectory` náhradní řetězec nepřekračují omezení délky cesty v operačním systému. [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] Zprostředkovatelé dat není jisté, že délka cesty je v mezích limitů platný.  
  
## <a name="security-considerations-for-adonet-metadata"></a>Důležité informace o zabezpečení pro ADO.NET Metadata  
 Při vytváření a práci s modelu a souborů mapování, platí následující aspekty zabezpečení.  
  
#### <a name="do-not-expose-sensitive-information-through-logging"></a>Nezveřejňujte citlivé informace přes protokolování.  
 [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] Metadata součásti služby neprotokolujte nějaké soukromé informace. Pokud neexistují výsledky, které nejde vrátit kvůli omezením přístupu, databázové systémy a systémy souborů by měl vrátit nula výsledků namísto vyvolání výjimky, které mohou obsahovat citlivé informace.  
  
#### <a name="do-not-accept-metadataworkspace-objects-from-untrusted-sources"></a>Nepřijmout objektu MetadataWorkspace objekty z nedůvěryhodných zdrojů.  
 Aplikace by neměla přijímat instance <xref:System.Data.Metadata.Edm.MetadataWorkspace> třídy z nedůvěryhodných zdrojů. By měl místo toho explicitně vytvořit a naplnit pracovní prostor z tyto zdroje.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Důležité informace o nasazení](../../../../../docs/framework/data/adonet/ef/deployment-considerations.md)  
 [Důležité informace o migraci](../../../../../docs/framework/data/adonet/ef/migration-considerations.md)
