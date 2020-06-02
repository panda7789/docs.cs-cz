---
title: Připojovací řetězce a konfigurační soubory
description: Naučte se, jak ukládat připojovací řetězce pro aplikace ADO.NET do konfiguračního souboru aplikace, jako osvědčený postup pro zabezpečení a údržbu.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 37df2641-661e-407a-a3fb-7bf9540f01e8
ms.openlocfilehash: 572c5be1bd639e8d4b38935f5be49782f0b0316e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287035"
---
# <a name="connection-strings-and-configuration-files"></a>Připojovací řetězce a konfigurační soubory

Vkládání připojovacích řetězců do kódu aplikace může vést k ohrožení zabezpečení a problémům s údržbou. Nešifrované připojovací řetězce zkompilované do zdrojového kódu aplikace lze zobrazit pomocí nástroje [Ildasm. exe (IL Disassembler)](../../tools/ildasm-exe-il-disassembler.md) . Navíc platí, že pokud se připojovací řetězec někdy změní, vaše aplikace musí být znovu zkompilována. Z těchto důvodů doporučujeme ukládat připojovací řetězce do konfiguračního souboru aplikace.  
  
## <a name="working-with-application-configuration-files"></a>Práce s konfiguračními soubory aplikace  
 Konfigurační soubory aplikace obsahují nastavení, která jsou specifická pro konkrétní aplikaci. Například aplikace ASP.NET může mít jeden nebo více souborů **Web. config** a aplikace systému Windows může mít volitelný soubor **App. config** . Konfigurační soubory sdílejí společné prvky, i když se název a umístění konfiguračního souboru liší v závislosti na hostiteli aplikace.  
  
### <a name="the-connectionstrings-section"></a>Oddíl connectionStrings  
 Připojovací řetězce mohou být uloženy jako páry klíč/hodnota v sekci **connectionStrings** **konfiguračního souboru** aplikace. Podřízené elementy zahrnují **Přidání**, **zrušení**a **Odebrání**.  
  
 Následující fragment konfiguračního souboru ukazuje schéma a syntaxi pro uložení připojovacího řetězce. Atribut **Name** je název, který zadáte k jedinečné identifikaci připojovacího řetězce, aby jej bylo možné načíst v době běhu. Název **ProviderName** je neutrální název poskytovatele dat .NET Framework, který je zaregistrován v souboru Machine. config.  
  
```xml  
<?xml version='1.0' encoding='utf-8'?>  
  <configuration>  
    <connectionStrings>  
      <clear />  
      <add name="Name"
       providerName="System.Data.ProviderName"
       connectionString="Valid Connection String;" />  
    </connectionStrings>  
  </configuration>  
```  
  
> [!NOTE]
> Můžete uložit část připojovacího řetězce do konfiguračního souboru a použít <xref:System.Data.Common.DbConnectionStringBuilder> třídu k jeho dokončení za běhu. To je užitečné ve scénářích, kdy neznáte prvky připojovacího řetězce před časem, nebo pokud nechcete ukládat citlivé informace do konfiguračního souboru. Další informace najdete v tématu [tvůrci připojovacích řetězců](connection-string-builders.md).  
  
### <a name="using-external-configuration-files"></a>Použití externích konfiguračních souborů  
 Externí konfigurační soubory jsou samostatné soubory, které obsahují fragment konfiguračního souboru skládajícího se z jednoho oddílu. Na externí konfigurační soubor se pak odkazuje pomocí hlavního konfiguračního souboru. Uložení oddílu **connectionStrings** do fyzicky odděleného souboru je užitečné v situacích, kdy je možné upravit připojovací řetězce po nasazení aplikace. Například standardní chování ASP.NET je restartování domény aplikace při úpravě konfiguračních souborů, což vede ke ztrátě informací o stavu. Úpravy externího konfiguračního souboru ale nezpůsobí restart aplikace. Externí konfigurační soubory nejsou omezené na ASP.NET; je možné je používat i v aplikacích pro Windows. Kromě toho je možné k omezení přístupu k externím konfiguračním souborům použít oprávnění a zabezpečení přístupu k souborům. Práce s externími konfiguračními soubory v době běhu je transparentní a nevyžaduje žádné speciální kódování.  
  
 Chcete-li uložit připojovací řetězce v externím konfiguračním souboru, vytvořte samostatný soubor, který obsahuje pouze část **connectionStrings** . Nezahrnujte žádné další prvky, oddíly ani atributy. Tento příklad ukazuje syntaxi pro externí konfigurační soubor.  
  
```xml  
<connectionStrings>  
  <add name="Name"
   providerName="System.Data.ProviderName"
   connectionString="Valid Connection String;" />  
</connectionStrings>  
```  
  
 V hlavním konfiguračním souboru aplikace použijete atribut **configSource** k určení plně kvalifikovaného názvu a umístění externího souboru. Tento příklad odkazuje na externí konfigurační soubor s názvem `connections.config` .  
  
```xml  
<?xml version='1.0' encoding='utf-8'?>  
<configuration>  
    <connectionStrings configSource="connections.config"/>  
</configuration>  
```  
  
## <a name="retrieving-connection-strings-at-run-time"></a>Načítání připojovacích řetězců v době běhu  
 .NET Framework 2,0 zavedl nové třídy v <xref:System.Configuration> oboru názvů, aby bylo možné zjednodušit načítání připojovacích řetězců z konfiguračních souborů v době běhu. Připojovací řetězec můžete programově načíst podle názvu nebo podle názvu poskytovatele.  
  
> [!NOTE]
> Soubor **Machine. config** také obsahuje oddíl **connectionStrings** , který obsahuje připojovací řetězce používané v aplikaci Visual Studio. Při načítání připojovacích řetězců podle názvu poskytovatele ze souboru **App. config** v aplikaci systému Windows jsou nejprve načteny připojovací řetězce v souboru **Machine. config** a následně položky z **App. config**. Přidání **jasných** hodnot ihned poté, co prvek **connectionStrings** odebere všechny zděděné odkazy z struktury dat v paměti, aby byly zváženy pouze připojovací řetězce definované v souboru místní soubor **App. config** .  
  
### <a name="working-with-the-configuration-classes"></a>Práce s třídami konfigurace  
 Počínaje .NET Framework 2,0 <xref:System.Configuration.ConfigurationManager> se používá při práci s konfiguračními soubory v místním počítači a nahrazuje zastaralé <xref:System.Configuration.ConfigurationSettings> . <xref:System.Web.Configuration.WebConfigurationManager>se používá pro práci s konfiguračními soubory ASP.NET. Je navržená pro práci s konfiguračními soubory na webovém serveru a umožňuje programový přístup k oddílům konfiguračního souboru, jako je **System. Web**.  
  
> [!NOTE]
> Přístup ke konfiguračním souborům v době běhu vyžaduje udělení oprávnění volajícímu; požadovaná oprávnění závisí na typu aplikace, konfiguračním souboru a umístění. Další informace najdete v tématech [použití tříd konfigurace](https://docs.microsoft.com/previous-versions/aspnet/ms228063(v=vs.100)) a <xref:System.Web.Configuration.WebConfigurationManager> pro aplikace ASP.NET a <xref:System.Configuration.ConfigurationManager> pro aplikace pro Windows.  
  
 Můžete použít <xref:System.Configuration.ConnectionStringSettingsCollection> k načtení připojovacích řetězců z konfiguračních souborů aplikace. Obsahuje kolekci <xref:System.Configuration.ConnectionStringSettings> objektů, z nichž každý představuje jednu položku v sekci **connectionStrings** . Jeho vlastnosti jsou mapovány na atributy připojovacího řetězce, což vám umožní načíst připojovací řetězec zadáním názvu nebo názvu poskytovatele.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Configuration.ConnectionStringSettings.Name%2A>|Název připojovacího řetězce Provede mapování na atribut **Name** .|  
|<xref:System.Configuration.ConnectionStringSettings.ProviderName%2A>|Plně kvalifikovaný název poskytovatele. Provede mapování na atribut **ProviderName** .|  
|<xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A>|Připojovací řetězec Provede mapování na atribut **ConnectionString** .|  
  
### <a name="example-listing-all-connection-strings"></a>Příklad: výpis všech připojovacích řetězců  
 Tento příklad provede iteraci <xref:System.Configuration.ConnectionStringSettingsCollection> a zobrazí <xref:System.Configuration.ConnectionStringSettings.Name%2A?displayProperty=nameWithType> <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A?displayProperty=nameWithType> vlastnosti, a <xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A?displayProperty=nameWithType> v okně konzoly.  
  
> [!NOTE]
> System. Configuration. dll není zahrnut ve všech typech projektů a může být nutné nastavit odkaz na něj, aby bylo možné použít třídy konfigurace. Název a umístění konkrétního konfiguračního souboru aplikace se liší podle typu aplikace a hostitelského procesu.  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfig#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfig/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfig#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfig/VB/source.vb#1)]  
  
### <a name="example-retrieving-a-connection-string-by-name"></a>Příklad: Načtení připojovacího řetězce podle názvu  
 Tento příklad ukazuje, jak načíst připojovací řetězec z konfiguračního souboru zadáním jeho názvu. Kód vytvoří <xref:System.Configuration.ConnectionStringSettings> objekt, který odpovídá zadanému vstupnímu parametru <xref:System.Configuration.ConfigurationManager.ConnectionStrings%2A> názvu. Pokud se nenajde žádný shodný název, funkce vrátí `null` ( `Nothing` v Visual Basic).  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByName#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByName/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByName#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByName/VB/source.vb#1)]  
  
### <a name="example-retrieving-a-connection-string-by-provider-name"></a>Příklad: Načtení připojovacího řetězce podle názvu poskytovatele  
 Tento příklad ukazuje, jak načíst připojovací řetězec zadáním neutrálního názvu poskytovatele ve formátu *System. data. ProviderName*. Kód provede iteraci pomocí <xref:System.Configuration.ConnectionStringSettingsCollection> a vrátí připojovací řetězec pro první <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> nalezený řetězec. Pokud se název poskytovatele nenajde, funkce vrátí `null` ( `Nothing` v Visual Basic).  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="encrypting-configuration-file-sections-using-protected-configuration"></a>Šifrování oddílů konfiguračního souboru pomocí chráněné konfigurace  
 ASP.NET 2,0 představil novou funkci nazvanou *Protected Configuration*, která umožňuje šifrování citlivých informací v konfiguračním souboru. I když jsou primárně určené pro ASP.NET, můžete chráněnou konfiguraci použít také k šifrování oddílů konfiguračního souboru v aplikacích pro Windows. Podrobný popis možností chráněné konfigurace najdete v tématu [šifrování informací o konfiguraci pomocí chráněné konfigurace](https://docs.microsoft.com/previous-versions/aspnet/53tyfkaw(v=vs.100)).  
  
 Následující fragment konfiguračního souboru ukazuje sekci **connectionStrings** poté, co byla zašifrována. **ConfigProtectionProvider** Určuje poskytovatele chráněné konfigurace, který se používá k šifrování a dešifrování připojovacích řetězců. Oddíl **EncryptedData** obsahuje text šifry.  
  
```xml  
<connectionStrings configProtectionProvider="DataProtectionConfigurationProvider">  
  <EncryptedData>  
    <CipherData>  
      <CipherValue>AQAAANCMnd8BFdERjHoAwE/Cl+sBAAAAH2... </CipherValue>  
    </CipherData>  
  </EncryptedData>  
</connectionStrings>  
```  
  
 Při načtení šifrovaného připojovacího řetězce v době běhu .NET Framework používá zadaného poskytovatele k dešifrování **element CipherValue** a zpřístupnění pro vaši aplikaci. Pro správu procesu dešifrování není nutné psát žádný další kód.  
  
### <a name="protected-configuration-providers"></a>Poskytovatelé chráněných konfigurací  
 Poskytovatelé chráněných konfigurací jsou registrováni v části **configProtectedData** souboru **Machine. config** v místním počítači, jak je znázorněno v následujícím fragmentu, který zobrazuje dva poskytovatele chráněných konfigurací dodaných s .NET Framework. Hodnoty, které jsou zde zobrazeny, byly zkráceny pro čitelnost.  
  
```xml  
<configProtectedData defaultProvider="RsaProtectedConfigurationProvider">  
  <providers>  
    <add name="RsaProtectedConfigurationProvider"
      type="System.Configuration.RsaProtectedConfigurationProvider" />  
    <add name="DataProtectionConfigurationProvider"
      type="System.Configuration.DpapiProtectedConfigurationProvider" />  
  </providers>  
</configProtectedData>  
```  
  
 Další poskytovatele chráněných konfigurací můžete nakonfigurovat tak, že je přidáte do souboru **Machine. config** . Můžete také vytvořit vlastního poskytovatele chráněné konfigurace děděním z <xref:System.Configuration.ProtectedConfigurationProvider> abstraktní základní třídy. Následující tabulka popisuje dva konfigurační soubory, které jsou součástí .NET Framework.  
  
|Poskytovatel|Popis|  
|--------------|-----------------|  
|<xref:System.Configuration.RsaProtectedConfigurationProvider>|K šifrování a dešifrování dat používá šifrovací algoritmus RSA. Algoritmus RSA lze použít jak pro šifrování veřejného klíče, tak pro digitální podpisy. Označuje se také jako "veřejný klíč" nebo asymetrické šifrování, protože používá dva různé klíče. K šifrování oddílů v souboru Web. config a správě šifrovacích klíčů můžete použít [registrační nástroj ASP.NET služby IIS (Aspnet_regiis. exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/k6h9cz8h(v=vs.90)) . ASP.NET dešifruje konfigurační soubor při zpracovávání souboru. Identita aplikace ASP.NET musí mít oprávnění ke čtení šifrovacího klíče, který se používá k šifrování a dešifrování šifrovaných oddílů.|  
|<xref:System.Configuration.DpapiProtectedConfigurationProvider>|K šifrování konfiguračních oddílů používá Windows Data Protection API (DPAPI). Používá integrované kryptografické služby systému Windows a je možné ji nakonfigurovat pro ochranu specifickou pro konkrétní počítač nebo pro uživatelské účty. Ochrana specifická pro konkrétní počítač je užitečná pro více aplikací na stejném serveru, které potřebují sdílet informace. Ochranu pomocí uživatelského účtu lze použít se službami, které se spouštějí s konkrétní identitou uživatele, jako je například sdílené hostitelské prostředí. Každá aplikace běží v rámci samostatné identity, která omezuje přístup k prostředkům, jako jsou soubory a databáze.|  
  
 Oba poskytovatelé nabízejí silné šifrování dat. Pokud však plánujete použít stejný zašifrovaný konfigurační soubor na více serverech, jako je například webová farma, <xref:System.Configuration.RsaProtectedConfigurationProvider> umožňuje exportovat šifrovací klíče používané k šifrování dat a importovat je na jiný server. Další informace najdete v tématu [Import a export chráněných konfigurací kontejnerů klíčů RSA](https://docs.microsoft.com/previous-versions/aspnet/yxw286t2(v=vs.100)).  
  
### <a name="using-the-configuration-classes"></a>Použití tříd konfigurace  
 <xref:System.Configuration>Obor názvů poskytuje třídy pro práci s nastavením konfigurace programově. <xref:System.Configuration.ConfigurationManager>Třída poskytuje přístup k souborům konfigurace počítače, aplikace a uživatele. Pokud vytváříte aplikaci ASP.NET, můžete použít <xref:System.Web.Configuration.WebConfigurationManager> třídu, která poskytuje stejné funkce a zároveň umožňuje přístup k nastavení, která jsou jedinečná pro aplikace ASP.NET, jako jsou ty, které se nacházejí v **\<system.web>** .  
  
> [!NOTE]
> <xref:System.Security.Cryptography>Obor názvů obsahuje třídy, které poskytují další možnosti pro šifrování a dešifrování dat. Tyto třídy použijte, pokud požadujete kryptografické služby, které nejsou k dispozici pomocí chráněné konfigurace. Některé z těchto tříd jsou obálky pro nespravované rozhraní Microsoft CryptoAPI, zatímco jiné jsou čistě spravované implementace. Další informace najdete v tématu [kryptografické služby](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/93bskf9z(v=vs.90)).  
  
### <a name="appconfig-example"></a>Příklad App. config  
 Tento příklad ukazuje, jak přepnout šifrování oddílu **connectionStrings** v souboru **App. config** pro aplikaci systému Windows. V tomto příkladu procedura převezme název aplikace jako argument, například "MyApplication. exe". Soubor **App. config** bude poté zašifrován a zkopírován do složky, která obsahuje spustitelný soubor pod názvem "MyApplication. exe. config".  
  
> [!NOTE]
> Připojovací řetězec lze dešifrovat pouze v počítači, ve kterém byl zašifrovaný.  
  
 Kód používá <xref:System.Configuration.ConfigurationManager.OpenExeConfiguration%2A> metodu k otevření souboru **App. config** pro úpravy a <xref:System.Configuration.ConfigurationManager.GetSection%2A> Metoda vrátí oddíl **connectionStrings** . Kód pak kontroluje <xref:System.Configuration.SectionInformation.IsProtected%2A> vlastnost, voláním metody <xref:System.Configuration.SectionInformation.ProtectSection%2A> k zašifrování oddílu, pokud není zašifrovaný. <xref:System.Configuration.SectionInformation.UnprotectSection%2A>Metoda je vyvolána pro dešifrování oddílu. <xref:System.Configuration.Configuration.Save%2A>Metoda dokončí operaci a uloží změny.  
  
> [!NOTE]
> Chcete-li spustit kód, je nutné nastavit odkaz na `System.Configuration.dll` v projektu.  
  
 [!code-csharp[DataWorks ConnectionStrings.Encrypt#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStrings.Encrypt/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStrings.Encrypt#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStrings.Encrypt/VB/source.vb#1)]  
  
### <a name="webconfig-example"></a>Příklad souboru Web. config  
 V tomto příkladu se používá <xref:System.Web.Configuration.WebConfigurationManager.OpenWebConfiguration%2A> Metoda `WebConfigurationManager` . Všimněte si, že v tomto případě můžete použít relativní cestu k souboru **Web. config** pomocí tildy. Kód vyžaduje odkaz na `System.Web.Configuration` třídu.  
  
 [!code-csharp[DataWorks ConnectionStringsWeb.Encrypt#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringsWeb.Encrypt/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringsWeb.Encrypt#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringsWeb.Encrypt/VB/source.vb#1)]  
  
 Další informace o zabezpečení aplikací ASP.NET najdete v tématu [zabezpečení webů ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/91f66yxt(v=vs.100)).  
  
## <a name="see-also"></a>Viz také

- [Tvůrci připojovacích řetězců](connection-string-builders.md)
- [Ochrana informací o připojení](protecting-connection-information.md)
- [Použití tříd konfigurace](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ms228063(v=vs.90))
- [Konfigurace aplikací](../../configure-apps/index.md)
- [Správa webu ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/6hy1xzbw(v=vs.100))
- [Přehled ADO.NET](ado-net-overview.md)
