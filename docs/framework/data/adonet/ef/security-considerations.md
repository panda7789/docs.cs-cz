---
title: Požadavky na zabezpečení (Entity Framework)
ms.date: 03/30/2017
ms.assetid: 84758642-9b72-4447-86f9-f831fef46962
ms.openlocfilehash: 9a560db5dbcb7a87a1c933febfb8bf676cc8816b
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968408"
---
# <a name="security-considerations-entity-framework"></a>Požadavky na zabezpečení (Entity Framework)
Toto téma popisuje požadavky na zabezpečení, které jsou specifické pro vývoj, nasazování a spouštění aplikací Entity Framework. Měli byste také postupovat podle doporučení pro vytváření zabezpečených .NET Framework aplikací. Další informace najdete v tématu [Přehled zabezpečení](../security-overview.md).  
  
## <a name="general-security-considerations"></a>Obecné požadavky na zabezpečení  
 Následující požadavky na zabezpečení platí pro všechny aplikace, které používají Entity Framework.  
  
#### <a name="use-only-trusted-data-source-providers"></a>Používejte pouze důvěryhodné zprostředkovatele zdrojů dat.  
 Aby mohl poskytovatel komunikovat se zdrojem dat, musí provést následující akce:  
  
- Příjem připojovacího řetězce z Entity Framework.  
  
- Přeložte strom příkazů do nativního dotazovacího jazyka zdroje dat.  
  
- Sestavte a vraťte sady výsledků dotazu.  
  
 Během operace přihlášení jsou informace, které jsou založeny na hesle uživatele, předány serveru přes síťové knihovny základního zdroje dat. Škodlivý zprostředkovatel může ukrást přihlašovací údaje uživatele, generovat škodlivé dotazy nebo manipulovat se sadou výsledků dotazu.  
  
#### <a name="encrypt-your-connection-to-protect-sensitive-data"></a>Zašifrujte připojení pro ochranu citlivých dat.  
 Entity Framework nezpracovává přímo šifrování dat. Pokud uživatelé přistupují k datům přes veřejnou síť, měla by vaše aplikace vytvořit šifrované připojení ke zdroji dat, aby se zvýšilo zabezpečení. Další informace naleznete v dokumentaci týkající se zabezpečení pro váš zdroj dat. Zdroj dat SQL Server najdete v tématu [šifrování připojení k SQL Server](https://go.microsoft.com/fwlink/?LinkId=119544).  
  
#### <a name="secure-the-connection-string"></a>Zabezpečte připojovací řetězec.  
 Ochrana přístupu ke zdroji dat je jedním z nejdůležitějších cílů při zabezpečení aplikace. Připojovací řetězec představuje potenciální chybu zabezpečení, pokud není zabezpečena nebo pokud není správně vytvořena. Když ukládáte informace o připojení do prostého textu nebo je zachová v paměti, riskujete, že dojde k narušení celého systému. Níže jsou uvedené doporučené metody zabezpečení připojovacích řetězců:  
  
- Použijte ověřování systému Windows s SQL Serverm zdrojem dat.  
  
     Použijete-li ověřování systému Windows pro připojení k SQL Servermu zdroji dat, připojovací řetězec neobsahuje informace o přihlášení a hesle.  
  
- Zašifrujte oddíly konfiguračního souboru pomocí chráněné konfigurace.  
  
     ASP.NET poskytuje funkci nazvanou chráněná konfigurace, která umožňuje šifrování citlivých informací v konfiguračním souboru. I když jsou primárně určené pro ASP.NET, můžete také použít chráněnou konfiguraci k šifrování oddílů konfiguračních souborů v aplikacích pro Windows. Podrobný popis nových možností chráněné konfigurace najdete v tématu [šifrování informací o konfiguraci pomocí chráněné konfigurace](https://docs.microsoft.com/previous-versions/aspnet/53tyfkaw(v=vs.100)).  
  
- Uložte připojovací řetězce do zabezpečených konfiguračních souborů.  
  
     Do zdrojového kódu byste nikdy neměli vkládat připojovací řetězce. Připojovací řetězce můžete ukládat v konfiguračních souborech, což eliminuje nutnost jejich vložení do kódu vaší aplikace. Ve výchozím nastavení Průvodce model EDM (Entity Data Model) ukládá připojovací řetězce do konfiguračního souboru aplikace. Tento soubor musíte zabezpečit, aby se zabránilo neoprávněnému přístupu.  
  
- Při dynamickém vytváření připojení použijte tvůrci připojovacích řetězců.  
  
     Pokud je nutné sestavit připojovací řetězce za běhu, použijte třídu <xref:System.Data.EntityClient.EntityConnectionStringBuilder>. Tato třída tvůrce řetězců pomáhá zabránit útokům prostřednictvím injektáže připojovacího řetězce pomocí ověření a uvozovacího neplatných vstupních informací. Další informace naleznete v tématu [How to: Build a EntityConnection Connection String](how-to-build-an-entityconnection-connection-string.md). Použijte také příslušnou třídu tvůrce řetězců k vytvoření připojovacího řetězce zdroje dat, který je součástí připojovacího řetězce Entity Framework. Informace o sestavách připojovacích řetězců pro poskytovatele ADO.NET naleznete v tématu [tvůrci připojovacích řetězců](../connection-string-builders.md).  
  
 Další informace najdete v tématu [ochrana informací o připojení](../protecting-connection-information.md).  
  
#### <a name="do-not-expose-an-entityconnection-to-untrusted-users"></a>Nezveřejňujte EntityConnection k nedůvěryhodným uživatelům.  
 Objekt <xref:System.Data.EntityClient.EntityConnection> zpřístupňuje připojovací řetězec podkladového připojení. Uživatel s přístupem k objektu <xref:System.Data.EntityClient.EntityConnection> může také změnit <xref:System.Data.ConnectionState> základního připojení. Třída <xref:System.Data.EntityClient.EntityConnection> není bezpečná pro přístup z více vláken.  
  
#### <a name="do-not-pass-connections-outside-the-security-context"></a>Neprovádějte předávání připojení mimo kontext zabezpečení.  
 Po navázání spojení je nesmíte předat mimo kontext zabezpečení. Například jedno vlákno s oprávněním k otevření připojení by nemělo ukládat připojení v globálním umístění. Pokud je připojení k dispozici v globálním umístění, pak jiné škodlivé vlákno může používat otevřené připojení, aniž by mu bylo uděleno oprávnění explicitně.  
  
#### <a name="be-aware-that-logon-information-and-passwords-may-be-visible-in-a-memory-dump"></a>Upozorňujeme, že přihlašovací údaje a hesla můžou být v výpisu paměti viditelné.  
 Pokud jsou v připojovacím řetězci zadány přihlašovací údaje zdroje dat a heslo, jsou tyto informace uchovávány v paměti, dokud uvolňování paměti neuvolní prostředky. To znemožňuje určit, kdy už řetězec hesla není v paměti. Pokud dojde k chybě aplikace, může soubor výpisu paměti obsahovat citlivé informace o zabezpečení a uživatel, který spouští aplikaci, a každý uživatel, který má přístup správce k počítači, může zobrazit soubor výpisu paměti. Pro připojení k Microsoft SQL Server použít ověřování systému Windows.  
  
#### <a name="grant-users-only-the-necessary-permissions-in-the-data-source"></a>Udělte uživatelům pouze nezbytná oprávnění ve zdroji dat.  
 Správce zdroje dat by měl uživatelům udělit jenom potřebná oprávnění. I když [!INCLUDE[esql](../../../../../includes/esql-md.md)] nepodporuje příkazy DML, které mění data, jako je například vložení, aktualizace nebo odstranění, uživatelé mají stále přístup k připojení ke zdroji dat. Uživatel se zlými úmysly může pomocí tohoto připojení spustit příkazy DML v nativním jazyce zdroje dat.  
  
#### <a name="run-applications-with-the-minimum-permissions"></a>Spouštějte aplikace s minimálními oprávněními.  
 Pokud povolíte, aby se spravovaná aplikace spouštěla s oprávněním s úplným vztahem důvěryhodnosti, .NET Framework neomezuje přístup aplikace k vašemu počítači. To může v aplikaci umožnit ohrožení zabezpečení pro celý systém. Pro použití zabezpečení přístupu kódu a dalších mechanismů zabezpečení v .NET Framework byste měli spouštět aplikace pomocí oprávnění částečné důvěryhodnosti a s minimální sadou oprávnění, která jsou potřebná k tomu, aby aplikace mohla fungovat. Následující přístupová oprávnění kódu jsou minimální oprávnění, která vaše Entity Framework aplikace potřebuje:  
  
- <xref:System.Security.Permissions.FileIOPermission>: <xref:System.Security.Permissions.FileIOPermissionAccess.Write> pro otevření zadaných souborů metadat nebo <xref:System.Security.Permissions.FileIOPermissionAccess.PathDiscovery> pro hledání souborů metadat v adresáři.  
  
- <xref:System.Security.Permissions.ReflectionPermission>: <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess> pro podporu LINQ to Entitiesch dotazů.  
  
- <xref:System.Transactions.DistributedTransactionPermission>: <xref:System.Security.Permissions.PermissionState.Unrestricted> zařazení do <xref:System.Transactions>ho<xref:System.Transactions.Transaction>.  
  
- <xref:System.Security.Permissions.SecurityPermission>: <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> k serializaci výjimek pomocí rozhraní <xref:System.Runtime.Serialization.ISerializable>.  
  
- Oprávnění k otevření připojení k databázi a provedení příkazů pro databázi, jako je například <xref:System.Data.SqlClient.SqlClientPermission> pro databázi SQL Server.  
  
 Další informace najdete v tématu [zabezpečení přístupu kódu a ADO.NET](../code-access-security.md).  
  
#### <a name="do-not-install-untrusted-applications"></a>Neinstalujte nedůvěryhodné aplikace.  
 Entity Framework nevynutila žádná oprávnění zabezpečení a vyvolá libovolný uživatelem zadaný datový objekt v procesu bez ohledu na to, zda je důvěryhodný nebo nikoli. Ujistěte se, že úložiště dat a aplikace provádí ověřování a autorizaci klienta.  
  
#### <a name="restrict-access-to-all-configuration-files"></a>Omezte přístup ke všem konfiguračním souborům.  
 Správce musí omezit přístup pro zápis do všech souborů, které určují konfiguraci aplikace, včetně souborů enterprisesec. config, Security. config, Machine. conf a konfiguračního souboru aplikace \<> *aplikace*. exe. config.  
  
 Neutrální název zprostředkovatele je v App. config upravitelný. Klientská aplikace musí převzít zodpovědnost za přístup k základnímu poskytovateli prostřednictvím modelu výroby standardního zprostředkovatele pomocí silného názvu.  
  
#### <a name="restrict-permissions-to-the-model-and-mapping-files"></a>Omezte oprávnění k modelu a mapování souborů.  
 Správce musí omezit přístup pro zápis k modelu a mapování souborů (. edmx,. csdl,. ssdl a. MSL) pouze na uživatele, kteří mění model nebo mapování. Entity Framework vyžaduje pouze přístup pro čtení těchto souborů v době běhu. Správce by měl také omezit přístup ke vrstvě objektů a předkompilovaným souborům zdrojového kódu zobrazení, které jsou generovány nástroji model EDM (Entity Data Model).  
  
## <a name="security-considerations-for-queries"></a>Otázky zabezpečení pro dotazy  
 Při dotazování konceptuálního modelu platí následující informace o zabezpečení. Tyto požadavky platí pro [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotazy pomocí zprostředkovatele EntityClient a k vytváření dotazů na objekty pomocí metod LINQ, [!INCLUDE[esql](../../../../../includes/esql-md.md)]a tvůrce dotazů.  
  
#### <a name="prevent-sql-injection-attacks"></a>Zabraňuje útokům prostřednictvím injektáže SQL.  
 Aplikace často přijímají externí vstup (od uživatele nebo jiného externího agenta) a provádějí akce založené na tomto vstupu. Jakýkoli vstup, který je přímo nebo nepřímo odvozený od uživatele nebo externího agenta, může mít obsah, který používá syntaxi cílového jazyka, aby mohl provádět neoprávněné akce. Pokud je cílovým jazykem jazyk SQL (Structured Query Language) (SQL), jako je například Transact-SQL, tato manipulace je označována jako útok prostřednictvím injektáže SQL. Uživatel se zlými úmysly může vložit příkazy přímo do dotazu a odstranit databázovou tabulku, způsobit odepření služby nebo jinak měnit povahu prováděné operace.  
  
- útoky prostřednictvím injektáže [!INCLUDE[esql](../../../../../includes/esql-md.md)]:  
  
     Útoky prostřednictvím injektáže SQL je možné provádět v [!INCLUDE[esql](../../../../../includes/esql-md.md)] tím, že zadáváte škodlivý vstup k hodnotám, které se používají v predikátu dotazu a v názvech parametrů. Abyste se vyhnuli riziku injektáže SQL, neměli byste nikdy kombinovat vstup uživatele s textem příkazu [!INCLUDE[esql](../../../../../includes/esql-md.md)].  
  
     [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotazy přijímají parametry všude, kde jsou povoleny literály. Měli byste použít parametrizované dotazy namísto vložení literálů z externího agenta přímo do dotazu. Měli byste taky zvážit použití [metod Tvůrce dotazů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896238(v=vs.100)) k bezpečnému vytváření Entity SQL.  
  
- Útoky prostřednictvím injektáže LINQ to Entities:  
  
     I když je v LINQ to Entities možné kompozice dotazů, provádí se prostřednictvím rozhraní API objektového modelu. Na rozdíl od [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotazů se LINQ to Entities dotazy neskládají pomocí manipulace s řetězci nebo zřetězení a nejsou náchylné k tradičním útokům prostřednictvím injektáže SQL.  
  
#### <a name="prevent-very-large-result-sets"></a>Prevence velkých sad výsledků.  
 Velmi velká sada výsledků by mohla způsobit vypnutí klienta, pokud klient provádí operace, které spotřebovávají prostředky úměrné velikosti sady výsledků dotazu. Neočekávané velké sady výsledků můžou nastat za následujících podmínek:  
  
- V dotazech na velkou databázi, která neobsahuje příslušné podmínky filtrování.  
  
- V dotazech, které vytvářejí kartézském spojení na serveru.  
  
- Ve vnořených [!INCLUDE[esql](../../../../../includes/esql-md.md)]ch dotazech.  
  
 Při přijímání uživatelského vstupu je nutné zajistit, aby vstup nemohlo způsobit, že se sady výsledků budou větší než to, co systém dokáže zpracovat. Můžete také použít metodu <xref:System.Linq.Queryable.Take%2A> v LINQ to Entities nebo operátor [limit](./language-reference/limit-entity-sql.md) v [!INCLUDE[esql](../../../../../includes/esql-md.md)] pro omezení velikosti sady výsledků dotazu.  
  
#### <a name="avoid-returning-iqueryable-results-when-exposing-methods-to-potentially-untrusted-callers"></a>Vyhněte se vrácení výsledků IQueryable při vystavení metod potenciálním nedůvěryhodným volajícím.  
 Vyhněte se vrácení <xref:System.Linq.IQueryable%601> typů z metod, které jsou vystaveny potenciálně nedůvěryhodným volajícím z následujících důvodů:  
  
- Příjemce dotazu, který zveřejňuje typ <xref:System.Linq.IQueryable%601>, může volat metody pro výsledek, který zveřejňuje zabezpečená data nebo zvětší velikost sady výsledků dotazu. Zvažte například následující signatura metody:  

    ```csharp
    public IQueryable<Customer> GetCustomer(int customerId)
    ```

    Příjemce tohoto dotazu může volat `.Include("Orders")` u vrácených `IQueryable<Customer>` a načíst data, která dotaz nechtěl vystavit. To lze vyhnout změnou návratového typu metody pro <xref:System.Collections.Generic.IEnumerable%601> a voláním metody (například `.ToList()`), která materializuje výsledky.  
  
- Vzhledem k tomu, že <xref:System.Linq.IQueryable%601> dotazy jsou spouštěny při iteraci výsledků, příjemce dotazu, který zveřejňuje typ <xref:System.Linq.IQueryable%601>, může zachytit výjimky, které jsou vyvolány. Výjimky mohou obsahovat informace, které nejsou určeny pro příjemce.  
  
## <a name="security-considerations-for-entities"></a>Požadavky na zabezpečení pro entity  
 Při generování a práci s typy entit platí následující požadavky na zabezpečení.  
  
#### <a name="do-not-share-an-objectcontext-across-application-domains"></a>Nesdílejte ObjectContext napříč aplikačními doménami.  
 Sdílení <xref:System.Data.Objects.ObjectContext> s více než jednou aplikační doménou může vystavovat informace v připojovacím řetězci. Místo toho byste měli přenést Serializované objekty nebo grafy objektů do druhé domény aplikace a pak tyto objekty připojit k <xref:System.Data.Objects.ObjectContext> v dané doméně aplikace. Další informace naleznete v tématu [serializace objektů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738446(v=vs.100)).  
  
#### <a name="prevent-type-safety-violations"></a>Zabraňte narušení bezpečnosti typů.  
 V případě porušení zabezpečení typu Entity Framework nemůže zaručit integritu dat v objektech. Pokud povolíte, aby nedůvěryhodné aplikace běžely s plně důvěryhodným zabezpečením přístupu ke kódu, mohlo by dojít k narušení bezpečnosti typů.  
  
#### <a name="handle-exceptions"></a>Zpracování výjimek.  
 Přístup k metodám a vlastnostem <xref:System.Data.Objects.ObjectContext> v rámci bloku try-catch. Zachycování výjimek zabraňuje neošetřeným výjimkám při vystavení záznamů v <xref:System.Data.Objects.ObjectStateManager> nebo informace o modelu (například názvy tabulek) uživatelům vaší aplikace.  
  
## <a name="security-considerations-for-aspnet-applications"></a>Požadavky na zabezpečení pro aplikace ASP.NET  

Při práci s cestami v aplikacích ASP.NET byste měli vzít v úvahu následující:  
  
#### <a name="verify-whether-your-host-performs-path-checks"></a>Ověřte, zda hostitel provádí kontroly cest.  
 Pokud je použit náhradní řetězec `|DataDirectory|` (uzavřeno v symbolech kanálu), ADO.NET ověří, zda je přeložená cesta podporována. Například ".." není povoleno za `DataDirectory`. Tuto stejnou kontrolu pro vyřešení kořenového operátoru webové aplikace (`~`) provádí proces hostující ASP.NET. Tato kontrolu provede služba IIS. hostitelé jiné než IIS ale nemusí ověřit, jestli je přeložená cesta podporovaná. Měli byste znát chování hostitele, na kterém nasazujete Entity Framework aplikaci.  
  
#### <a name="do-not-make-assumptions-about-resolved-path-names"></a>Nevytvářejte předpoklady o vyřešených názvech cest.  
 I když hodnoty, na které kořenový operátor (`~`) a `DataDirectory` náhradní řetězec by měly zůstat během modulu runtime aplikace konstantní, Entity Framework neomezuje hostitele na úpravu těchto hodnot.  
  
#### <a name="verify-the-path-length-before-deployment"></a>Před nasazením ověřte délku cesty.  
 Před nasazením Entity Framework aplikace byste měli zajistit, aby hodnoty kořenového operátoru (~) a `DataDirectory` náhradního řetězce nepřekročily omezení délky cesty v operačním systému. Poskytovatelé dat ADO.NET nezajistí, že délka cesty spadá do platných omezení.  
  
## <a name="security-considerations-for-adonet-metadata"></a>Požadavky na zabezpečení pro metadata ADO.NET  
 Následující požadavky na zabezpečení platí při generování a práci s modelem a mapováním souborů.  
  
#### <a name="do-not-expose-sensitive-information-through-logging"></a>Nezveřejňujte citlivé informace prostřednictvím protokolování.  
Součásti služby ADO.NET metadata neprotokolují žádné soukromé informace. Pokud dojde k výsledkům, které nelze vrátit z důvodu omezení přístupu, systémy správy databáze a systémy souborů by měly vracet nula výsledků namísto vyvolání výjimky, která by mohla obsahovat citlivé informace.  
  
#### <a name="do-not-accept-metadataworkspace-objects-from-untrusted-sources"></a>Nepřijímejte objekty MetadataWorkspace z nedůvěryhodných zdrojů.  
 Aplikace by neměly přijímat instance <xref:System.Data.Metadata.Edm.MetadataWorkspace> třídy z nedůvěryhodných zdrojů. Místo toho byste měli explicitně vytvořit a naplnit pracovní prostor z takového zdroje.  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení aplikací ADO.NET](../securing-ado-net-applications.md)
- [Důležité informace o nasazení](deployment-considerations.md)
- [Důležité informace o migraci](migration-considerations.md)
