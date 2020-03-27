---
title: Připojovací řetězce a konfigurační soubory
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 37df2641-661e-407a-a3fb-7bf9540f01e8
ms.openlocfilehash: 8862aa34c2d2677f5bc3e737c01cc61036c243e1
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345059"
---
# <a name="connection-strings-and-configuration-files"></a>Připojovací řetězce a konfigurační soubory

Vložení připojovacích řetězců do kódu aplikace může vést k ohrožení zabezpečení a problémům s údržbou. Nešifrované připojovací řetězce zkompilované do zdrojového kódu aplikace lze zobrazit pomocí nástroje [Ildasm.exe (IL Disassembler).](../../tools/ildasm-exe-il-disassembler.md) Navíc pokud se připojovací řetězec někdy změní, musí být aplikace znovu zkompilována. Z těchto důvodů doporučujeme ukládat připojovací řetězce do konfiguračního souboru aplikace.  
  
## <a name="working-with-application-configuration-files"></a>Práce s konfiguračními soubory aplikace  
 Konfigurační soubory aplikace obsahují nastavení, která jsou specifická pro konkrétní aplikaci. ASP.NET aplikace může mít například jeden nebo více souborů **web.config** a aplikace pro Windows může mít volitelný soubor **application.config.** Konfigurační soubory sdílejí společné prvky, i když název a umístění konfiguračního souboru se liší v závislosti na hostiteli aplikace.  
  
### <a name="the-connectionstrings-section"></a>Oddíl connectionStrings  
 Připojovací řetězce mohou být uloženy jako páry klíč/hodnota v části **connectionStrings** **konfiguračního** prvku konfiguračního souboru aplikace. Podřízené prvky zahrnují **přidat**, **vymazat**a **odebrat**.  
  
 Následující fragment konfiguračního souboru demonstruje schéma a syntaxi pro uložení připojovacího řetězce. Atribut **name** je název, který zadáte jednoznačně identifikovat připojovací řetězec tak, aby jej lze načíst za běhu. Název **providerName** je invariantní název zprostředkovatele dat rozhraní .NET Framework, který je registrován v souboru machine.config.  
  
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
> Část připojovacího řetězce můžete uložit do <xref:System.Data.Common.DbConnectionStringBuilder> konfiguračního souboru a použít třídu k jeho dokončení za běhu. To je užitečné ve scénářích, kde neznáte prvky připojovacího řetězce předem nebo pokud nechcete ukládat citlivé informace do konfiguračního souboru. Další informace naleznete v [tématu Connection String Builders](connection-string-builders.md).  
  
### <a name="using-external-configuration-files"></a>Použití externích konfiguračních souborů  
 Externí konfigurační soubory jsou samostatné soubory, které obsahují fragment konfiguračního souboru skládající ho z jednoho oddílu. Na externí konfigurační soubor pak odkazuje hlavní konfigurační soubor. Ukládání části **connectionStrings** ve fyzicky samostatném souboru je užitečné v situacích, kdy mohou být připojovací řetězce upraveny po nasazení aplikace. Standardní chování ASP.NET je například restartování domény aplikace při změně konfiguračních souborů, což má za následek ztrátu informací o stavu. Úprava externího konfiguračního souboru však nezpůsobí restartování aplikace. Externí konfigurační soubory nejsou omezeny na ASP.NET; mohou být také použity aplikacemi systému Windows. Kromě toho lze zabezpečení přístupu k souborům a oprávnění použít k omezení přístupu k externím konfiguračním souborům. Práce s externími konfiguračními soubory za běhu je transparentní a nevyžaduje žádné speciální kódování.  
  
 Chcete-li uložit připojovací řetězce do externího konfiguračního souboru, vytvořte samostatný soubor, který obsahuje pouze oddíl **connectionStrings.** Nezahrnejte žádné další prvky, oddíly nebo atributy. Tento příklad ukazuje syntaxi externího konfiguračního souboru.  
  
```xml  
<connectionStrings>  
  <add name="Name"
   providerName="System.Data.ProviderName"
   connectionString="Valid Connection String;" />  
</connectionStrings>  
```  
  
 V konfiguračním souboru hlavní aplikace můžete pomocí atributu **configSource** zadat plně kvalifikovaný název a umístění externího souboru. Tento příklad odkazuje na externí `connections.config`konfigurační soubor s názvem .  
  
```xml  
<?xml version='1.0' encoding='utf-8'?>  
<configuration>  
    <connectionStrings configSource="connections.config"/>  
</configuration>  
```  
  
## <a name="retrieving-connection-strings-at-run-time"></a>Načítání připojovacích řetězců za běhu  
 Rozhraní .NET Framework 2.0 zavedlo <xref:System.Configuration> nové třídy v oboru názvů pro zjednodušení načítání připojovacích řetězců z konfiguračních souborů za běhu. Připojovací řetězec můžete programově načíst podle názvu nebo podle názvu zprostředkovatele.  
  
> [!NOTE]
> Soubor **machine.config** také obsahuje oddíl **connectionStrings,** který obsahuje připojovací řetězce používané visual studio. Při načítání připojovacích řetězců podle názvu zprostředkovatele ze souboru **app.config** v aplikaci systému Windows se nejprve načtou připojovací řetězce v **souboru machine.config** a potom položky z **souboru app.config**. Přidání **vymazat** ihned po **connectionStringstrings** element odebere všechny zděděné odkazy z datové struktury v paměti, takže jsou považovány pouze připojovací řetězce definované v místním souboru **app.config.**  
  
### <a name="working-with-the-configuration-classes"></a>Práce s třídami konfigurace  
 Počínaje rozhraním .NET Framework <xref:System.Configuration.ConfigurationManager> 2.0 se používá při práci s konfiguračními <xref:System.Configuration.ConfigurationSettings>soubory v místním počítači a nahrazuje zastaralé . <xref:System.Web.Configuration.WebConfigurationManager>slouží k práci s ASP.NET konfiguračními soubory. Je navržen pro práci s konfiguračními soubory na webovém serveru a umožňuje programový přístup k oddílům konfiguračních souborů, jako je **system.web**.  
  
> [!NOTE]
> Přístup ke konfiguračním souborům za běhu vyžaduje udělení oprávnění volajícímu. požadovaná oprávnění závisí na typu aplikace, konfiguračním souboru a umístění. Další informace naleznete [v tématu Použití tříd konfigurace](https://docs.microsoft.com/previous-versions/aspnet/ms228063(v=vs.100)) a <xref:System.Web.Configuration.WebConfigurationManager> ASP.NET aplikací a <xref:System.Configuration.ConfigurationManager> aplikací systému Windows.  
  
 Můžete použít <xref:System.Configuration.ConnectionStringSettingsCollection> k načtení připojovacích řetězců z konfiguračních souborů aplikace. Obsahuje kolekci <xref:System.Configuration.ConnectionStringSettings> objektů, z nichž každá představuje jednu položku v části **connectionStrings.** Jeho vlastnosti jsou mapovány na atributy připojovacího řetězce, což umožňuje načíst připojovací řetězec zadáním názvu nebo názvu zprostředkovatele.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Configuration.ConnectionStringSettings.Name%2A>|Název připojovacího řetězce. Mapuje na atribut **name.**|  
|<xref:System.Configuration.ConnectionStringSettings.ProviderName%2A>|Plně kvalifikovaný název zprostředkovatele. Mapuje na atribut **providerName.**|  
|<xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A>|Připojovací řetězec Mapuje atribut **connectionString.**|  
  
### <a name="example-listing-all-connection-strings"></a>Příklad: Výpis všech připojovacích řetězců  
 Tento příklad itetuje <xref:System.Configuration.ConnectionStringSettingsCollection> <xref:System.Configuration.ConnectionStringSettings.Name%2A?displayProperty=nameWithType>a <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A?displayProperty=nameWithType>zobrazuje <xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A?displayProperty=nameWithType> vlastnosti , a vlastnosti v okně konzoly.  
  
> [!NOTE]
> Soubor System.Configuration.dll není součástí všech typů projektů a může být nutné nastavit odkaz na něj, aby bylo možné použít třídy konfigurace. Název a umístění konkrétního konfiguračního souboru aplikace se liší podle typu aplikace a procesu hostování.  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfig#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfig/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfig#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfig/VB/source.vb#1)]  
  
### <a name="example-retrieving-a-connection-string-by-name"></a>Příklad: Načítání připojovacího řetězce podle názvu  
 Tento příklad ukazuje, jak načíst připojovací řetězec z konfiguračního souboru zadáním jeho názvu. Kód vytvoří <xref:System.Configuration.ConnectionStringSettings> objekt, odpovídající zadaný vstupní <xref:System.Configuration.ConfigurationManager.ConnectionStrings%2A> parametr název. Pokud není nalezen žádný odpovídající `null` název, funkce vrátí (v`Nothing` jazyce Visual Basic).  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByName#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByName/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByName#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByName/VB/source.vb#1)]  
  
### <a name="example-retrieving-a-connection-string-by-provider-name"></a>Příklad: Načítání připojovacího řetězce podle názvu zprostředkovatele  
 Tento příklad ukazuje, jak načíst připojovací řetězec zadáním názvu zprostředkovatele invariant ve formátu *System.Data.ProviderName*. Kód iterates prostřednictvím <xref:System.Configuration.ConnectionStringSettingsCollection> a vrátí připojovací řetězec pro první <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> nalezen. Pokud není nalezen název zprostředkovatele, `null` `Nothing` funkce vrátí (v jazyce Visual Basic).  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="encrypting-configuration-file-sections-using-protected-configuration"></a>Šifrování oddílů konfiguračních souborů pomocí chráněné konfigurace  
 ASP.NET. 2.0 zavedlnovou funkci nazvanou *chráněná konfigurace*, která umožňuje šifrovat citlivé informace v konfiguračním souboru. Přestože je chráněná konfigurace primárně určena pro ASP.NET, lze ji také použít k šifrování oddílů konfiguračních souborů v aplikacích systému Windows. Podrobný popis chráněných možností konfigurace naleznete v [tématu Šifrování informací o konfiguraci pomocí chráněné konfigurace](https://docs.microsoft.com/previous-versions/aspnet/53tyfkaw(v=vs.100)).  
  
 Následující fragment konfiguračního souboru zobrazuje oddíl **connectionStrings** po zašifrování. **ConfigProtectionProvider** určuje chráněného zprostředkovatele konfigurace, který slouží k šifrování a dešifrování připojovacích řetězců. Část **EncryptedData** obsahuje šifrovaný text.  
  
```xml  
<connectionStrings configProtectionProvider="DataProtectionConfigurationProvider">  
  <EncryptedData>  
    <CipherData>  
      <CipherValue>AQAAANCMnd8BFdERjHoAwE/Cl+sBAAAAH2... </CipherValue>  
    </CipherData>  
  </EncryptedData>  
</connectionStrings>  
```  
  
 Při načítání šifrovaného připojovacího řetězce za běhu používá rozhraní .NET Framework určeného zprostředkovatele k dešifrování **hodnoty CipherValue** a její zpřístupnění vaší aplikaci. Není nutné psát žádný další kód pro správu procesu dešifrování.  
  
### <a name="protected-configuration-providers"></a>Chránění zprostředkovatelé konfigurace  
 Chránění poskytovatelé konfigurace jsou registrováni v části **configProtectedData** souboru **machine.config** v místním počítači, jak je znázorněno na následujícím fragmentu, který zobrazuje dva chráněné zprostředkovatele konfigurace dodávané s rozhraním .NET Framework. Zde uvedené hodnoty byly zkráceny pro čitelnost.  
  
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
  
 Přidáním dalších chráněných poskytovatelů konfigurace do souboru **machine.config** můžete nakonfigurovat další chráněné poskytovatele konfigurace. Můžete také vytvořit vlastní chráněné zprostředkovatele konfigurace <xref:System.Configuration.ProtectedConfigurationProvider> děděním z abstraktní základní třídy. Následující tabulka popisuje dva konfigurační soubory, které jsou součástí rozhraní .NET Framework.  
  
|Poskytovatel|Popis|  
|--------------|-----------------|  
|<xref:System.Configuration.RsaProtectedConfigurationProvider>|Používá šifrovací algoritmus RSA k šifrování a dešifrování dat. Algoritmus RSA lze použít jak pro šifrování veřejného klíče, tak pro digitální podpisy. Je také známý jako "veřejný klíč" nebo asymetrické šifrování, protože používá dva různé klíče. Pomocí nástroje [ASP.NET nástroje pro registraci služby IIS (Aspnet_regiis.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/k6h9cz8h(v=vs.90)) můžete zašifrovat oddíly v souboru Web.config a spravovat šifrovací klíče. ASP.NET dešifruje konfigurační soubor při jeho zpracuje. Identita aplikace ASP.NET musí mít přístup pro čtení k šifrovacímu klíči, který se používá k šifrování a dešifrování šifrovaných oddílů.|  
|<xref:System.Configuration.DpapiProtectedConfigurationProvider>|Používá rozhraní Windows Data Protection API (DPAPI) k šifrování konfiguračních oddílů. Používá integrované kryptografické služby systému Windows a lze jej nakonfigurovat pro ochranu specifickou pro počítač nebo uživatelský účet. Ochrana specifické pro počítač je užitečná pro více aplikací na stejném serveru, které potřebují sdílet informace. Ochranu specifickou pro uživatelský účet lze použít se službami, které běží s určitou identitou uživatele, jako je například sdílené hostitelské prostředí. Každá aplikace běží pod samostatnou identitou, která omezuje přístup k prostředkům, jako jsou soubory a databáze.|  
  
 Oba poskytovatelé nabízejí silné šifrování dat. Pokud však plánujete použít stejný šifrovaný konfigurační soubor na <xref:System.Configuration.RsaProtectedConfigurationProvider> více serverech, například ve webové farmě, umožňuje exportovat šifrovací klíče používané k šifrování dat a jejich importu na jiný server. Další informace naleznete [v tématu Import a export kontejnerů klíčů RSA s chráněnou konfigurací](https://docs.microsoft.com/previous-versions/aspnet/yxw286t2(v=vs.100)).  
  
### <a name="using-the-configuration-classes"></a>Použití konfiguračních tříd  
 Obor <xref:System.Configuration> názvů poskytuje třídy pro práci s nastavením konfigurace programově. Třída <xref:System.Configuration.ConfigurationManager> poskytuje přístup k konfiguračním souborům počítače, aplikace a uživatele. Pokud vytváříte ASP.NET aplikaci, můžete <xref:System.Web.Configuration.WebConfigurationManager> použít třídu, která poskytuje stejné funkce a zároveň umožňuje přístup k nastavení, která jsou jedinečná pro ASP.NET aplikace, například ty, které se nacházejí v ** \<system.web>**.  
  
> [!NOTE]
> Obor <xref:System.Security.Cryptography> názvů obsahuje třídy, které poskytují další možnosti šifrování a dešifrování dat. Tyto třídy použijte, pokud požadujete kryptografické služby, které nejsou k dispozici pomocí chráněné konfigurace. Některé z těchto tříd jsou obálky pro nespravované Rozhraní Microsoft CryptoAPI, zatímco jiné jsou čistě spravované implementace. Další informace naleznete v tématu [Cryptographic Services](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/93bskf9z(v=vs.90)).  
  
### <a name="appconfig-example"></a>Příklad app.config  
 Tento příklad ukazuje, jak přepnout šifrování části **connectionStrings** v souboru **app.config** pro aplikaci systému Windows. V tomto příkladu postup přebírá název aplikace jako argument, například "MyApplication.exe". Soubor **app.config** bude poté zašifrován a zkopírován do složky, která obsahuje spustitelný soubor pod názvem "MyApplication.exe.config".  
  
> [!NOTE]
> Připojovací řetězec lze dešifrovat pouze v počítači, ve kterém byl zašifrován.  
  
 Kód používá <xref:System.Configuration.ConfigurationManager.OpenExeConfiguration%2A> metodu k otevření souboru **app.config** <xref:System.Configuration.ConfigurationManager.GetSection%2A> pro úpravy a metoda vrátí oddíl **connectionStrings.** Kód pak zkontroluje <xref:System.Configuration.SectionInformation.IsProtected%2A> vlastnost, <xref:System.Configuration.SectionInformation.ProtectSection%2A> volání šifrovat oddíl, pokud není šifrována. Metoda <xref:System.Configuration.SectionInformation.UnprotectSection%2A> je vyvolána k dešifrování oddílu. Metoda <xref:System.Configuration.Configuration.Save%2A> dokončí operaci a uloží změny.  
  
> [!NOTE]
> Chcete-li `System.Configuration.dll` spustit kód, musíte v projektu nastavit odkaz.  
  
 [!code-csharp[DataWorks ConnectionStrings.Encrypt#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStrings.Encrypt/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStrings.Encrypt#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStrings.Encrypt/VB/source.vb#1)]  
  
### <a name="webconfig-example"></a>Příklad web.config  
 Tento příklad <xref:System.Web.Configuration.WebConfigurationManager.OpenWebConfiguration%2A> používá metodu `WebConfigurationManager`. Všimněte si, že v tomto případě můžete zadat relativní cestu k souboru **Web.config** pomocí vlnovky. Kód vyžaduje odkaz na `System.Web.Configuration` třídu.  
  
 [!code-csharp[DataWorks ConnectionStringsWeb.Encrypt#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringsWeb.Encrypt/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringsWeb.Encrypt#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringsWeb.Encrypt/VB/source.vb#1)]  
  
 Další informace o zabezpečení aplikací ASP.NET naleznete v [tématu Zabezpečení ASP.NET webových stránek](https://docs.microsoft.com/previous-versions/aspnet/91f66yxt(v=vs.100)).  
  
## <a name="see-also"></a>Viz také

- [Tvůrci připojovacích řetězců](connection-string-builders.md)
- [Ochrana informací o připojení](protecting-connection-information.md)
- [Použití konfiguračních tříd](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ms228063(v=vs.90))
- [Konfigurace aplikací](../../configure-apps/index.md)
- [správa webu ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/6hy1xzbw(v=vs.100))
- [Přehled ADO.NET](ado-net-overview.md)
