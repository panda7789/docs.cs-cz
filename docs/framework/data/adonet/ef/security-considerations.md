---
title: Aspekty zabezpečení (rozhraní Entity Framework)
ms.date: 03/30/2017
ms.assetid: 84758642-9b72-4447-86f9-f831fef46962
ms.openlocfilehash: 337424395186532969734e0977ea111d8995a154
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766618"
---
# <a name="security-considerations-entity-framework"></a>Aspekty zabezpečení (rozhraní Entity Framework)
Toto téma popisuje aspekty zabezpečení, které jsou specifické pro vývoj, nasazování a spouštění [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikace. Také postupujte podle doporučení pro vytvoření zabezpečeného [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] aplikace. Další informace najdete v tématu [Přehled zabezpečení](../../../../../docs/framework/data/adonet/security-overview.md).  
  
## <a name="general-security-considerations"></a>Obecné otázky zabezpečení  
 Na všechny aplikace, které používají, platí následující aspekty zabezpečení [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
#### <a name="use-only-trusted-data-source-providers"></a>Použití pouze důvěryhodné zprostředkovatele zdrojů dat.  
 Ke komunikaci se zdrojem dat, musíte udělat následující zprostředkovatele:  
  
-   Zobrazí řetězec připojení z [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
-   Převede na nativní dotazovacího jazyka pro zdroj dat strom příkazů.  
  
-   Sestavte a vrátí sad výsledků dotazu.  
  
 Během operace přihlášení se předávají informace založený na heslo uživatele k serveru prostřednictvím síťových knihoven zdroje dat, základní. Škodlivý zprostředkovatele může ukrást přihlašovací údaje uživatele, generovat škodlivý dotazy nebo manipulovat s sadu výsledků dotazu.  
  
#### <a name="encrypt-your-connection-to-protect-sensitive-data"></a>Šifrování připojení k chrání citlivá data.  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Nezpracovává šifrování dat přímo. Pokud uživatelé k datům přistupují přes veřejnou síť, vaše aplikace by měla navázání šifrovaného připojení ke zdroji dat ke zvýšení zabezpečení. Další informace naleznete v dokumentaci týkající se zabezpečení pro zdroj dat. Zdroj dat systému SQL Server, najdete v části [šifrování připojení k systému SQL Server](http://go.microsoft.com/fwlink/?LinkId=119544).  
  
#### <a name="secure-the-connection-string"></a>Zabezpečené připojovací řetězec.  
 Zabezpečení přístupu ke zdroji dat je jedním z nejdůležitějších cílů při zabezpečení aplikace. Připojovací řetězec uvede potenciální ohrožení zabezpečení, pokud není zabezpečen, nebo pokud je nesprávně vytvořený. Při ukládání informací o připojení ve formátu prostého textu nebo zachovat v paměti, riziko ohrožení celého systému. Doporučené metody pro zabezpečení připojovací řetězce jsou následující:  
  
-   Pomocí ověřování systému Windows se zdrojem dat systému SQL Server.  
  
     Pokud používáte ověřování systému Windows pro připojení ke zdroji dat systému SQL Server, připojovací řetězec neobsahuje informace o přihlášení a heslo.  
  
-   Šifrování oddíly konfiguračního souboru pomocí chráněné konfigurace.  
  
     Technologie ASP.NET poskytuje funkci chráněné konfigurace, která umožňuje šifrování citlivých informací v konfiguračním souboru. I když primárně určený pro technologii ASP.NET, které můžete použít chráněné konfigurace k zašifrování částí konfigurační soubory v aplikacích Windows. Podrobný popis nové funkce, které chráněné konfigurace, najdete v části [šifrování informací pomocí chráněné konfigurace](http://msdn.microsoft.com/library/51cdfe5b-9d82-458c-94ff-c551c4f38ed1).  
  
-   Ukládání připojovacích řetězců v zabezpečené konfigurační soubory.  
  
     Nikdy vložte připojovací řetězce ve zdrojovém kódu. Můžete uložit připojovací řetězce v konfiguračních souborech, což eliminuje potřebu vložit do kódu aplikace. Ve výchozím nastavení ukládá průvodci Entity Data Model připojovací řetězce v konfiguračním souboru aplikace. Je nutné zabezpečit před neoprávněným přístupem tento soubor.  
  
-   Tvůrci řetězců pro připojení používejte při vytváření dynamicky připojení.  
  
     Pokud je nutné vytvořit připojovací řetězce za běhu, použijte <xref:System.Data.EntityClient.EntityConnectionStringBuilder> třídy. Tato třída Tvůrce řetězec pomáhá zabránit útokům vkládání řetězec připojení tak, že ověřování a uvozovací znaky neplatné vstupní informace. Další informace najdete v tématu [postupy: sestavení řetězec připojení EntityConnection](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md). Také použít třídu Tvůrce příslušným řetězcem vytvořit řetězec připojení zdroje dat, který je součástí [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] připojovací řetězec. Informace o připojení počítačů řetězec pro zprostředkovatele ADO.NET naleznete v tématu [Tvůrci řetězců pro připojení](../../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
 Další informace najdete v tématu [chrání informace o připojení](../../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
#### <a name="do-not-expose-an-entityconnection-to-untrusted-users"></a>Nevystavujte EntityConnection nedůvěryhodným uživatelům.  
 <xref:System.Data.EntityClient.EntityConnection> Objekt poskytuje připojovací řetězec příslušné připojení. Uživatel s přístupem k <xref:System.Data.EntityClient.EntityConnection> objekt můžete také změnit <xref:System.Data.ConnectionState> základní připojení. <xref:System.Data.EntityClient.EntityConnection> Třída není bezpečná pro přístup z více vláken.  
  
#### <a name="do-not-pass-connections-outside-the-security-context"></a>Nepředávejte připojení mimo kontext zabezpečení.  
 Po vytvoření připojení nesmí předejte ji mimo kontext zabezpečení. Například by nemělo jedno vlákno s oprávněním k otevření připojení uložit připojení v globálním umístění. Pokud připojení je k dispozici v globálním umístění, pak jiné vlákno škodlivý slouží bez nutnosti tato oprávnění explicitně udělit otevřené připojení.  
  
#### <a name="be-aware-that-logon-information-and-passwords-may-be-visible-in-a-memory-dump"></a>Upozorňujeme, že přihlašovací informace a hesla můžou být vidět ve výpisu stavu paměti.  
 Při přihlášení a heslo informace o zdroji dat zadaný v připojovacím řetězci, tyto informace udržována v paměti uvolňování paměti získá prostředky. Díky tomu je možné k určení, kdy řetězec hesla je již v paměti. Pokud aplikace spadne, souboru výpisu paměti může obsahovat informace o citlivých zabezpečení a uživatel, který spouští aplikace a každý uživatel s oprávněními přístupu správce k počítači, můžete zobrazit výpis stavu paměti. Pomocí ověřování systému Windows pro připojení k serveru Microsoft SQL Server.  
  
#### <a name="grant-users-only-the-necessary-permissions-in-the-data-source"></a>Uživatelům udělte jenom nezbytná oprávnění v datovém zdroji.  
 Správce zdrojů dat měli udělit jenom nezbytná oprávnění pro uživatele. I když [!INCLUDE[esql](../../../../../includes/esql-md.md)] nemá příkazy DML podpory, které upravují data, jako jsou uživatelé INSERT, UPDATE nebo DELETE, můžete pořád přístup k připojení ke zdroji dat. Uživatel se zlými úmysly může provést příkazy DML v nativním jazyce zdroje dat používat toto připojení.  
  
#### <a name="run-applications-with-the-minimum-permissions"></a>Spuštění aplikace s minimální oprávnění.  
 Když povolíte spravované aplikaci spustit s oprávněním plné důvěryhodnosti [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] neomezuje přístup aplikace k vašemu počítači. To může povolit ohrožení zabezpečení ve vaší aplikaci ohrozit celý systém. Použít zabezpečení přístupu kódu a další mechanismy zabezpečení v [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)], byste měli spustit aplikace s částečným vztahem důvěryhodnosti oprávněními a s minimální sadu oprávnění, která jsou potřebná k povolení funkce aplikace. Následující kód přístupová oprávnění jsou minimální oprávnění vaší [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] potřebám aplikace:  
  
-   <xref:System.Security.Permissions.FileIOPermission>: <xref:System.Security.Permissions.FileIOPermissionAccess.Write> otevírat soubory Zadaná metadata nebo <xref:System.Security.Permissions.FileIOPermissionAccess.PathDiscovery> vyhledat adresáři pro soubory metadat.  
  
-   <xref:System.Security.Permissions.ReflectionPermission>: <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess> pro podporu LINQ dotazy entity.  
  
-   <xref:System.Transactions.DistributedTransactionPermission>: <xref:System.Security.Permissions.PermissionState.Unrestricted> zařazení v <xref:System.Transactions> <xref:System.Transactions.Transaction>.  
  
-   <xref:System.Security.Permissions.SecurityPermission>: <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> k serializaci výjimky pomocí <xref:System.Runtime.Serialization.ISerializable> rozhraní.  
  
-   Oprávnění k otevření připojení k databázi a provést příkazy proti databázi, jako například <xref:System.Data.SqlClient.SqlClientPermission> pro databázi systému SQL Server.  
  
 Další informace najdete v tématu [zabezpečení přístupu kódu a ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md).  
  
#### <a name="do-not-install-untrusted-applications"></a>Neinstalujte nedůvěryhodných aplikací.  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Nevynucuje žádné oprávnění zabezpečení a bude vyvolat žádné uživatelem zadané data objektu kód v procesu bez ohledu na to, zda je důvěryhodný nebo ne. Zajistěte, že úložiště dat a aplikací se provádí ověřování a autorizace klienta.  
  
#### <a name="restrict-access-to-all-configuration-files"></a>Omezte přístup na všechny konfigurační soubory.  
 Správce musí omezit přístup pro zápis pro všechny soubory, které zadat konfiguraci pro aplikaci, včetně enterprisesec.config, security.config, machine.conf, a konfigurační soubor aplikace \< *aplikace* >. exe.config.  
  
 Neutrální název zprostředkovatele je upravitelnými v souboru app.config. Klientská aplikace musí převzít odpovědnost za přístup k výchozí zprostředkovatel prostřednictvím standardního poskytovatele modelu objektu pro vytváření s použitím silným názvem.  
  
#### <a name="restrict-permissions-to-the-model-and-mapping-files"></a>Omezte oprávnění modelu a mapování souborů.  
 Správce musí omezit přístup pro zápis modelu a soubory mapování (.edmx, .csdl, .ssdl nebo .msl) jenom na uživatele, kteří upravit mapování nebo model. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Vyžaduje pouze k těmto souborům přístup pro čtení, v době běhu. Správce by měl taky omezit přístup k objektové vrstvě a předem kompilovaném zobrazit zdrojový kód soubory, které jsou generované [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] nástroje.  
  
## <a name="security-considerations-for-queries"></a>Důležité informace o zabezpečení pro dotazy  
 Při dotazování Koncepční model, platí následující aspekty zabezpečení. Tyto aspekty platí pro [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotazy s EntityClient a objekt dotazy pomocí LINQ, [!INCLUDE[esql](../../../../../includes/esql-md.md)]a metody Tvůrce dotazu.  
  
#### <a name="prevent-sql-injection-attacks"></a>Zabránit útokům Injektáž SQL.  
 Aplikace často trvat externí vstup (uživatele nebo jiné externí agenta) a provádět akce na základě těchto informací. Všechny vstup, který je přímo nebo nepřímo odvozený od uživatele nebo externí agenta může mít obsah, který se používá syntaxe jazyka cíl za účelem provedení neoprávněným akcím. Pokud cílový jazyk je jazyka SQL (Structured Query), například [!INCLUDE[tsql](../../../../../includes/tsql-md.md)], tato manipulace se říká útok prostřednictvím injektáže SQL. Uživatel se zlými úmysly můžete vložit příkazy přímo do dotazu a vyřadit tabulku databáze, způsobit odepření služby nebo v opačném případě změňte povaha prováděnou operaci.  
  
-   [!INCLUDE[esql](../../../../../includes/esql-md.md)] vkládání útoků:  
  
     Útok prostřednictvím injektáže SQL mohou být prováděny v [!INCLUDE[esql](../../../../../includes/esql-md.md)] zadáním škodlivého zadání hodnoty, které jsou použity v predikátu dotazu a názvy parametrů. Aby nedošlo k ohrožení Injektáž SQL, doporučujeme, abyste nikdy zkombinovali vstup uživatele s [!INCLUDE[esql](../../../../../includes/esql-md.md)] text příkazu.  
  
     [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotazy přijmout všude, kde parametry, že jsou přijaty literály. Parametrizované dotazy byste měli používat místo vložení literály z externí agenta přímo do dotazu. Měli byste také zvážit použití metody Tvůrce dotazů bezpečně vytvořit [Entity SQL](http://msdn.microsoft.com/library/05685434-05e6-41c2-8d5e-8933b88a40b0).  
  
-   [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)] vkládání útoků:  
  
     I když je možné v sestavení dotazu [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)], se provádí prostřednictvím rozhraní API modelu objektu. Na rozdíl od [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotazy, [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)] dotazy nejsou sestavit pomocí zacházení s řetězci nebo zřetězení a nejsou náchylné k tradiční prostřednictvím injektáže SQL.  
  
#### <a name="prevent-very-large-result-sets"></a>Zabránit velmi velké množství výsledků.  
 Velmi velké výslednou sadu by mohl způsobit klientský systém vypnout, pokud klient provádí operace, které mohly spotřebovávat prostředky velikosti sady výsledků dotazu. Neočekávaně velké množství výsledků může dojít za následujících podmínek:  
  
-   V dotazy pro velké databáze, které neobsahují podmínky příslušný filtr.  
  
-   V dotazech, které vytvářejí kartézských spojení na serveru.  
  
-   Ve vnořených [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotazy.  
  
 Při přijetí vstupu uživatele, musí se ujistěte, že vstup nelze způsobit sad výsledků dotazu na velikost větší než co může systém zpracovat. Můžete také <xref:System.Linq.Queryable.Take%2A> metoda v [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)] nebo [LIMIT](../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) operátor v [!INCLUDE[esql](../../../../../includes/esql-md.md)] k omezení velikosti sady výsledků dotazu.  
  
#### <a name="avoid-returning-iqueryable-results-when-exposing-methods-to-potentially-untrusted-callers"></a>Vrací výsledky IQueryable Vyhněte se při zpřístupňuje metody potenciálně nedůvěryhodných volající.  
 Vyhněte se vrací <xref:System.Linq.IQueryable%601> typy z metod, které jsou zpřístupněny potenciálně nedůvěryhodné volající z následujících důvodů:  
  
-   Příjemce dotaz, který zveřejňuje <xref:System.Linq.IQueryable%601> typu může volat metody pro výsledek, který vystavit zabezpečených dat nebo zvětšete velikost sady výsledků dotazu. Zvažte například následující podpis metody:  
  
    ```  
    public IQueryable<Customer> GetCustomer(int customerId)  
    ```  
  
     Příjemce tento dotaz může volat `.Include("Orders")` na vrácený `IQueryable<Customer>` načíst data, která dotaz nechtěli vystavit. To můžete vyhnout tak, že změníte návratový typ metody, která <xref:System.Collections.Generic.IEnumerable%601> a volání metody (například `.ToList()`), bude realizována výsledky.  
  
-   Protože <xref:System.Linq.IQueryable%601> dotazy se spustí, až se výsledky jsou vstupní přes příjemce dotaz, který zveřejňuje <xref:System.Linq.IQueryable%601> typu může catch výjimky, které jsou vydány. Výjimky můžou obsahovat informace, které nejsou určeny k příjemce.  
  
## <a name="security-considerations-for-entities"></a>Důležité informace o zabezpečení pro entity  
 Při vytváření a práci s typy entit, platí následující aspekty zabezpečení.  
  
#### <a name="do-not-share-an-objectcontext-across-application-domains"></a>Mezi doménami aplikace nesdílejí objektu ObjectContext.  
 Sdílení <xref:System.Data.Objects.ObjectContext> s více než jednu aplikaci může domény zveřejnění informací v připojovacím řetězci. Místo toho by měla přenos serializovaných objektů nebo grafy objekt do jiné domény aplikace a pak připojte těchto objektů do <xref:System.Data.Objects.ObjectContext> v této doméně. Další informace najdete v tématu [serializaci objektů](http://msdn.microsoft.com/library/06c77f9b-5b2e-4c78-b3e3-8c148ba0ea99).  
  
#### <a name="prevent-type-safety-violations"></a>Nedošlo k narušení bezpečnosti typu.  
 Pokud je typ zabezpečení došlo k porušení, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] nemůže zaručit integritu dat v objektech. Typ porušení zabezpečení mohlo dojít, pokud povolíte nedůvěryhodných aplikací ke spuštění s zabezpečení přístupu kódu plné důvěryhodnosti.  
  
#### <a name="handle-exceptions"></a>Zpracování výjimek.  
 Přístup k metody a vlastnosti <xref:System.Data.Objects.ObjectContext> v rámci bloku try-catch. Zachytávání výjimek brání neošetřené výjimky z vystavení položek v <xref:System.Data.Objects.ObjectStateManager> nebo informace o modelu (například názvy tabulek) pro uživatele vaší aplikace.  
  
## <a name="security-considerations-for-aspnet-applications"></a>Důležité informace o zabezpečení pro aplikace ASP.NET  
 Následující potřeba vzít v úvahu při práci s cesty v [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] aplikace.  
  
#### <a name="verify-whether-your-host-performs-path-checks"></a>Ověřte, zda váš hostitel provádí kontroly cestu.  
 Když `|DataDirectory|` (uzavřený v kanálu symboly) náhradní řetězec se používá, [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] ověřuje, že se podporuje přeložená cesta. Například "..." není povolena za `DataDirectory`. Stejné kontroly pro vyřešení operátor kořenové webových aplikací (`~`) se provádí pomocí procesu hostování [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)]. Služba IIS provede tato kontrola; hostitelé než IIS však nemusí ověřte, zda je podporovat přeložená cesta. Měli byste vědět chování hostitele, na kterém je nasazená [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikace.  
  
#### <a name="do-not-make-assumptions-about-resolved-path-names"></a>Neprovádějte předpoklady o názvech vyřešen cestu.  
 I když hodnoty, na kterou operátor kořenové (`~`) a `DataDirectory` náhradní řetězec vyřešte by měla zůstat konstantní při běhu aplikace [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] neomezuje hostitele upravování tyto hodnoty.  
  
#### <a name="verify-the-path-length-before-deployment"></a>Ověřte délka cesty před nasazením.  
 Před nasazením [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikace, ujistěte se, že hodnoty operátoru kořenové (~) a `DataDirectory` náhradní řetězec nepřekračují omezení délky cesty v operačním systému. [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] Zprostředkovatelé dat není zajistěte, aby byl délka cesty v platné rozsahu.  
  
## <a name="security-considerations-for-adonet-metadata"></a>Důležité informace o zabezpečení pro ADO.NET Metadata  
 Při vytváření a práci se soubory mapování a modelu, platí následující aspekty zabezpečení.  
  
#### <a name="do-not-expose-sensitive-information-through-logging"></a>Nevystavujte citlivých informací prostřednictvím protokolování.  
 [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] součásti služby metadata nepřihlašujte nějaké soukromé informace. Pokud jsou výsledky, které nelze z důvodu omezení přístupu, databázové systémy a systémy souborů by měl vrátit nulové výsledky místo vyvolání k výjimce, která by mohla obsahovat citlivé informace.  
  
#### <a name="do-not-accept-metadataworkspace-objects-from-untrusted-sources"></a>Nepřijímají objektu MetadataWorkspace objekty z nedůvěryhodných zdrojů.  
 Aplikace by neměla přijímat instance <xref:System.Data.Metadata.Edm.MetadataWorkspace> třídy z nedůvěryhodných zdrojů. Místo toho by měla explicitně vytvořit a naplnit prostoru z takových zdroje.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Důležité informace o nasazení](../../../../../docs/framework/data/adonet/ef/deployment-considerations.md)  
 [Důležité informace o migraci](../../../../../docs/framework/data/adonet/ef/migration-considerations.md)
