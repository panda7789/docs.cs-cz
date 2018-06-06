---
title: Připojovací řetězce a konfigurační soubory
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 37df2641-661e-407a-a3fb-7bf9540f01e8
ms.openlocfilehash: 629d08b60330125a7bb491a58499b5e2bc7d2091
ms.sourcegitcommit: fc70fcb9c789b6a4aefcdace46f3643fd076450f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2018
ms.locfileid: "34805682"
---
# <a name="connection-strings-and-configuration-files"></a>Připojovací řetězce a konfigurační soubory
Vložení připojovacích řetězců v kódu aplikace může vést k ohrožení zabezpečení a problémy při údržbě. Nezašifrované připojovací řetězce zkompilovat do zdrojového kódu aplikace lze zobrazit pomocí [Ildasm.exe (IL Disassembler)](../../../../docs/framework/tools/ildasm-exe-il-disassembler.md) nástroj. Navíc pokud se připojovací řetězec někdy změní, musí zopakovat vaší aplikace. Z těchto důvodů doporučujeme ukládání připojovacích řetězců v konfiguračním souboru aplikace.  
  
## <a name="working-with-application-configuration-files"></a>Práce s konfigurační soubory aplikace  
 Konfigurační soubory aplikace obsahují nastavení, které jsou specifické pro konkrétní aplikace. Například aplikace ASP.NET může mít jeden nebo více **web.config** soubory a aplikace pro systém Windows může mít volitelný **app.config** souboru. Konfigurační soubory sdílejí společné prvky, i když se název a umístění konfiguračního souboru se liší v závislosti na hostiteli aplikace.  
  
### <a name="the-connectionstrings-section"></a>ConnectionStrings části  
 Připojovací řetězce mohou být uloženy jako páry klíč hodnota **connectionStrings** části **konfigurace** element konfiguračního souboru aplikace. Podřízené elementy obsahovat **přidat**, **vymazat**, a **odebrat**.  
  
 Následující fragment souboru konfigurace ukazuje syntaxi pro ukládání připojovací řetězec a schéma. **Název** atribut je název, který zadáte k jednoznačné identifikaci připojovací řetězec tak, aby se dá načíst za běhu. **ProviderName** je invariantní název zprostředkovatele dat .NET Framework, která je registrována v souboru machine.config.  
  
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
>  Můžete uložit součást připojovací řetězec v konfiguračním souboru a použít <xref:System.Data.Common.DbConnectionStringBuilder> třída dokončit v době běhu. To je užitečné v situacích, kde si nejste jisti, elementy připojovacího řetězce předem, nebo pokud nechcete uložit citlivé informace v konfiguračním souboru. Další informace najdete v tématu [Tvůrci řetězců pro připojení](../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
### <a name="using-external-configuration-files"></a>Pomocí externích konfigurační soubory  
 Externí konfigurační soubory jsou samostatné soubory, které obsahují fragment konfigurační soubor, který se skládá z jedné části. Externí konfigurační soubor odkazuje hlavní konfiguračního souboru. Ukládání **connectionStrings** v fyzicky oddělené souboru je užitečné v situacích, kde může být připojovací řetězce upravit po nasazení aplikace. Standardní chování ASP.NET je například restartovat domény aplikace při změně konfigurační soubory, výsledkem je ke ztrátě informací o stavu. Úprava externí konfigurační soubor ale nezpůsobí restartování aplikace. Externí konfigurační soubory nejsou omezeny na ASP.NET; Můžete také používají aplikace Windows. Kromě toho zabezpečení přístupu k souboru a oprávnění lze omezit přístup k externí konfigurační soubory. Práce s externí konfigurační soubory v době běhu je transparentní a vyžaduje žádné speciální kódování.  
  
 K ukládání připojovacích řetězců v externí konfigurační soubor, vytvořit samostatný soubor, který obsahuje pouze **connectionStrings** části. Neobsahují žádné další prvky, oddíly nebo atributy. Tento příklad ukazuje syntaxi pro externí konfigurační soubor.  
  
```xml  
<connectionStrings>  
  <add name="Name"   
   providerName="System.Data.ProviderName"   
   connectionString="Valid Connection String;" />  
</connectionStrings>  
```  
  
 V konfiguračním souboru hlavní aplikace, můžete použít **vlastnost configSource** atributu zadejte plně kvalifikovaný název a umístění externího souboru. Tento příklad se týká externí konfigurační soubor s názvem `connections.config`.  
  
```xml  
<?xml version='1.0' encoding='utf-8'?>  
<configuration>  
    <connectionStrings configSource="connections.config"/>  
</configuration>  
```  
  
## <a name="retrieving-connection-strings-at-run-time"></a>Načítání řetězců připojení v době běhu  
 Zavedeny nové třídy v rozhraní .NET Framework 2.0 <xref:System.Configuration> obor názvů pro zjednodušení načítání připojovací řetězce z konfigurační soubory v době běhu. Připojovací řetězec lze načíst prostřednictvím kódu programu podle názvu nebo podle názvu zprostředkovatele.  
  
> [!NOTE]
>  **Machine.config** soubor zároveň obsahuje **connectionStrings** oddíl, který obsahuje připojovací řetězce, které využívá sada Visual Studio. Při načítání podle názvu zprostředkovatele z připojovací řetězce **app.config** souboru v aplikaci Windows, připojovací řetězce v **machine.config** získat načíst první a potom položky z **app.config**. Přidání **vymazat** ihned po **connectionStrings** element odebere všechny zděděné odkazy z datové struktury v paměti, tak, aby připojovací řetězce definované v místní **app.config** jsou považovány za souboru.  
  
### <a name="working-with-the-configuration-classes"></a>Práce s třídami konfigurace  
 Od verze rozhraní .NET Framework 2.0, <xref:System.Configuration.ConfigurationManager> se používá při práci s konfigurační soubory v místním počítači, nahraďte zastaralé <xref:System.Configuration.ConfigurationSettings>. <xref:System.Web.Configuration.WebConfigurationManager> se používá pro práci s konfigurační soubory technologie ASP.NET. Je navržen pro práci s použitím konfiguračních souborů na webovém serveru a umožňuje programový přístup k oddíly konfiguračního souboru, jako **system.web**.  
  
> [!NOTE]
>  Přístup k konfigurační soubory v době běhu vyžaduje udělení oprávnění ke volající; požadovaná oprávnění závisí na typu aplikace, konfigurační soubor a umístění. Další informace najdete v tématu [pomocí třídy konfigurace](http://msdn.microsoft.com/library/98d2b386-baf6-4a17-974b-76e3b4c87acc) a <xref:System.Web.Configuration.WebConfigurationManager> pro aplikace ASP.NET a <xref:System.Configuration.ConfigurationManager> pro aplikace pro Windows.  
  
 Můžete použít <xref:System.Configuration.ConnectionStringSettingsCollection> načíst připojovací řetězce z konfigurační soubory aplikace. Obsahuje kolekci <xref:System.Configuration.ConnectionStringSettings> objekty, z nichž každý představuje jednu položku v **connectionStrings** části. Jeho vlastnosti namapovat na atributy řetězec připojení, umožňují načíst připojovací řetězec tak, že zadáte název nebo název zprostředkovatele.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Configuration.ConnectionStringSettings.Name%2A>|Název připojovacího řetězce. Se mapuje **název** atribut.|  
|<xref:System.Configuration.ConnectionStringSettings.ProviderName%2A>|Zprostředkovatel plně kvalifikovaný název. Se mapuje **providerName** atribut.|  
|<xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A>|Připojovací řetězec. Se mapuje **connectionString** atribut.|  
  
### <a name="example-listing-all-connection-strings"></a>Příklad: Výpis všech připojovací řetězce  
 V tomto příkladu prochází `ConnectionStringSettings` kolekce a zobrazuje <xref:System.Configuration.ConnectionStringSettings.Name%2A>, <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A>, a <xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A> vlastnosti v okně konzoly.  
  
> [!NOTE]
>  System.Configuration.dll není zahrnut ve všech typech projektů a budete muset nastavit odkaz na jeho pro použití tříd konfigurace. Název a umístění konfiguračního souboru konkrétní aplikace se liší podle typu aplikace a proces hostování.  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfig#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfig/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfig#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfig/VB/source.vb#1)]  
  
### <a name="example-retrieving-a-connection-string-by-name"></a>Příklad: Načítání připojovací řetězec podle názvu  
 Tento příklad ukazuje, jak k získání připojovacího řetězce z konfiguračního souboru a to zadáním názvu. Kód vytvoří <xref:System.Configuration.ConnectionStringSettings> objekt, odpovídající zadaný vstupní parametr <xref:System.Configuration.ConfigurationManager.ConnectionStrings%2A> název. Pokud je nalezen žádný odpovídající název, funkce vrátí hodnotu `null` (`Nothing` v jazyce Visual Basic).  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByName#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByName/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByName#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByName/VB/source.vb#1)]  
  
### <a name="example-retrieving-a-connection-string-by-provider-name"></a>Příklad: Načítání podle názvu zprostředkovatele připojovací řetězec  
 Tento příklad ukazuje, jak načíst připojovací řetězec tak, že zadání názvu zprostředkovatele neutrální ve formátu *System.Data.ProviderName*. Kód iteruje <xref:System.Configuration.ConnectionStringSettingsCollection> a vrátí připojovací řetězec pro první <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> nalezen. Pokud není nalezen název zprostředkovatele, funkce vrátí hodnotu `null` (`Nothing` v jazyce Visual Basic).  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="encrypting-configuration-file-sections-using-protected-configuration"></a>Šifrování oddíly konfiguračního souboru pomocí chráněné konfigurace  
 ASP.NET 2.0 zavedly novou funkci, s názvem *chráněné konfigurace*, který umožňuje šifrování citlivých informací v konfiguračním souboru. I když primárně určený pro technologii ASP.NET, chráněné konfigurace mohou sloužit také k šifrování souboru konfigurační oddíly funkce v aplikace systému Windows. Podrobný popis funkcí chráněné konfigurace najdete v tématu [šifrování informací pomocí chráněné konfigurace](http://msdn.microsoft.com/library/51cdfe5b-9d82-458c-94ff-c551c4f38ed1).  
  
 Následující konfigurační soubor fragmentovat ukazuje **connectionStrings** části po byla zašifrována. **ConfigProtectionProvider** určuje chráněné konfigurace zprostředkovatele, který používá k šifrování a dešifrování řetězce připojení. **EncryptedData** část obsahuje šifrovaný text.  
  
```xml  
<connectionStrings configProtectionProvider="DataProtectionConfigurationProvider">  
  <EncryptedData>  
    <CipherData>  
      <CipherValue>AQAAANCMnd8BFdERjHoAwE/Cl+sBAAAAH2... </CipherValue>  
    </CipherData>  
  </EncryptedData>  
</connectionStrings>  
```  
  
 Pokud v době běhu je načteny šifrované připojovací řetězec, rozhraní .NET Framework používá k dešifrování zadaného zprostředkovatele **element CipherValue** a zpřístupní ji do vaší aplikace. Není nutné zapsat žádný další kód spravovat proces dešifrování.  
  
### <a name="protected-configuration-providers"></a>Zprostředkovatele chráněné konfigurace  
 Zprostředkovatele chráněné konfigurace jsou zaregistrovány v **configProtectedData** části **machine.config** souboru v místním počítači, jak je znázorněno v následujícím fragmentu, který ukazuje dva chráněné konfigurace poskytovatele dodané s rozhraním .NET Framework. Zde zobrazených hodnot byl pravděpodobně zkrácen čitelnější.  
  
```xml  
<configProtectedData defaultProvider="RsaProtectedConfigurationProvider">  
  <providers>  
    <add name="RsaProtectedConfigurationProvider"   
      type="System.Configuration.RsaProtectedConfigurationProvider, ... />  
    <add name="DataProtectionConfigurationProvider"   
      type="System.Configuration.DpapiProtectedConfigurationProvider, ... />  
  </providers>  
</configProtectedData>  
```  
  
 Můžete nakonfigurovat další chráněné konfigurace zprostředkovatele jejich přidáním do **machine.config** souboru. Můžete také vytvořit vlastní poskytovatele chráněné konfigurace, která dědí z <xref:System.Configuration.ProtectedConfigurationProvider> abstraktní základní třída. Následující tabulka popisuje dvě konfigurační soubory součástí rozhraní .NET Framework.  
  
|Zprostředkovatel|Popis|  
|--------------|-----------------|  
|<xref:System.Configuration.RsaProtectedConfigurationProvider>|K šifrování a dešifrování dat používá algoritmus šifrování RSA. Algoritmus RSA lze použít pro šifrování pomocí veřejného klíče a digitální podpisy. Je také známé jako "veřejný klíč" nebo asymetrické šifrování protože aktivuje dva různé klíče. Můžete použít [ASP.NET IIS Registration Tool (Aspnet_regiis.exe)](http://msdn.microsoft.com/library/6491c41e-e2b0-481f-9863-db3614d5f96b) k šifrování oddílů v souboru Web.config a správu šifrovacích klíčů. ASP.NET dešifruje konfigurační soubor při zpracování souboru. Identita aplikace ASP.NET musí mít přístup pro čtení k šifrovací klíč, který se používá k šifrování a dešifrování šifrovaných oddílů.|  
|<xref:System.Configuration.DpapiProtectedConfigurationProvider>|Rozhraní Windows Data Protection API (DPAPI) používá k šifrování konfiguračních oddílů. Pomocí předdefinovaných kryptografických služeb systému Windows a mohou být konfigurovány pro konkrétní počítač nebo konkrétního uživatele účtu ochranu. Je užitečné pro několik aplikací na stejném serveru, který potřebujete sdílet informace specifické pro počítač ochrany. Uživatelská účet ochrany lze použít s služby, které běží s specifická identita uživatele, jako je například sdíleném hostitelském prostředí. Každá aplikace kompatibilní se samostatnou identitu, která omezuje přístup k prostředkům, například soubory a databáze.|  
  
 Oba poskytovatelé nabízejí silné šifrování dat. Ale pokud máte v úmyslu použít stejný soubor šifrované konfigurace na více serverech, jako jsou webové farmy, jenom `RsaProtectedConfigurationProvider` umožňuje exportovat šifrovací klíče používá k šifrování dat a importovat je na jiný server. Další informace najdete v tématu [import a export chráněné konfigurace RSA klíč kontejnery](http://msdn.microsoft.com/library/f3022b39-f17f-48c1-b067-025eab0ce8bc).  
  
### <a name="using-the-configuration-classes"></a>Pomocí třídy konfigurace  
 <xref:System.Configuration> Obor názvů obsahuje třídy pro práci s nastavením konfigurace prostřednictvím kódu programu. <xref:System.Configuration.ConfigurationManager> Třída poskytuje přístup k počítači, aplikace a uživatele konfigurační soubory. Pokud chcete vytvořit aplikaci ASP.NET, můžete použít <xref:System.Web.Configuration.WebConfigurationManager> třídy, která poskytuje stejné funkce, zatímco také umožňuje přístup k nastavení, která jsou jedinečná pro aplikace ASP.NET, jako jsou součástí  **\< System.Web >**.  
  
> [!NOTE]
>  <xref:System.Security.Cryptography> Obor názvů obsahuje třídy, které poskytují další možnosti pro šifrování a dešifrování dat. Tyto třídy použijte, pokud budete potřebovat šifrovacím službám, které nejsou k dispozici pomocí chráněné konfigurace. Některé z těchto tříd jsou obálek pro nespravované Microsoft CryptoAPI, zatímco jiné jsou čistě spravované implementace. Další informace najdete v tématu [šifrovacím službám](http://msdn.microsoft.com/library/68a1e844-c63c-44af-9247-f6716eb23781).  
  
### <a name="appconfig-example"></a>Příklad souboru app.config  
 Tento příklad ukazuje, jak k přepnutí šifrování **connectionStrings** kapitoly **app.config** soubor pro aplikaci systému Windows. V tomto příkladu, které procedura používá název aplikace jako argument, například "MyApplication.exe". **App.config** soubor pak bude šifrované a zkopírovány do složky, která obsahuje spustitelný soubor pod názvem "MyApplication.exe.config".  
  
> [!NOTE]
>  Připojovací řetězec mohou ho dešifrovat jenom na počítači, na kterém byla zašifrovaná.  
  
 Kód používá <xref:System.Configuration.ConfigurationManager.OpenExeConfiguration%2A> metoda otevřete **app.config** soubor pro úpravy a <xref:System.Configuration.ConfigurationManager.GetSection%2A> metoda vrátí **connectionStrings** části. Zkontroluje kód <xref:System.Configuration.SectionInformation.IsProtected%2A> vlastnost, volání <xref:System.Configuration.SectionInformation.ProtectSection%2A> k zašifrování oddílu, pokud není šifrován. <xref:System.Configuration.SectionInformation.UnprotectSection%2A> Metoda je volána k dešifrování části. <xref:System.Configuration.Configuration.Save%2A> Metoda dokončí operaci a uloží změny.  
  
> [!NOTE]
>  Je nutné nastavit odkaz na `System.Configuration.dll` ve vašem projektu pro kód pro spuštění.  
  
 [!code-csharp[DataWorks ConnectionStrings.Encrypt#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStrings.Encrypt/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStrings.Encrypt#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStrings.Encrypt/VB/source.vb#1)]  
  
### <a name="webconfig-example"></a>Příklad souboru Web.config  
 Tento příklad používá <xref:System.Web.Configuration.WebConfigurationManager.OpenWebConfiguration%2A> metodu `WebConfigurationManager`. Všimněte si, že v tomto případě můžete zadat relativní cestu k **Web.config** souboru pomocí tildou. Kód vyžaduje odkaz na `System.Web.Configuration` třídy.  
  
 [!code-csharp[DataWorks ConnectionStringsWeb.Encrypt#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringsWeb.Encrypt/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringsWeb.Encrypt#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringsWeb.Encrypt/VB/source.vb#1)]  
  
 Další informace zabezpečení aplikace ASP.NET najdete v tématu [NIB: zabezpečení ASP.NET](http://msdn.microsoft.com/library/04b37532-18d9-40b4-8e5f-ee09a70b311d) a [postupy zabezpečení ASP.NET 2.0 na první pohled](http://go.microsoft.com/fwlink/?LinkId=59997) v Centru pro vývojáře technologie ASP.NET.  
  
## <a name="see-also"></a>Viz také  
 [Tvůrci připojovacích řetězců](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 [Ochrana informací o připojení](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 [Pomocí třídy konfigurace](http://msdn.microsoft.com/library/98d2b386-baf6-4a17-974b-76e3b4c87acc)  
 [Konfigurace aplikací](../../../../docs/framework/configure-apps/index.md)  
 [Správa webu ASP.NET](http://msdn.microsoft.com/library/1298034b-5f7d-464d-abd1-ad9e6b3eeb7e)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
