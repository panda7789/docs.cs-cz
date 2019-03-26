---
title: Připojovací řetězce a konfigurační soubory
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 37df2641-661e-407a-a3fb-7bf9540f01e8
ms.openlocfilehash: 5e83d13d24a0b17fd886995e552dd0a7e2cf8ff4
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409949"
---
# <a name="connection-strings-and-configuration-files"></a>Připojovací řetězce a konfigurační soubory
Vkládání připojovacích řetězců v kódu vaší aplikace může vést k ohrožení zabezpečení a problémy s údržbou. Nešifrované připojovací řetězce, které jsou kompilovány do zdrojového kódu aplikace lze zobrazit pomocí [Ildasm.exe (IL Disassembler)](../../../../docs/framework/tools/ildasm-exe-il-disassembler.md) nástroj. Kromě toho pokud připojovací řetězec neustále mění, musí aplikace zopakovat. Z těchto důvodů doporučujeme ukládání připojovacích řetězců do konfiguračního souboru aplikace.  
  
## <a name="working-with-application-configuration-files"></a>Práce s konfigurační soubory aplikace  
 Aplikace konfigurační soubory obsahují nastavení, které jsou specifické pro konkrétní aplikaci. Například aplikace ASP.NET může mít jeden nebo více **web.config** soubory a aplikace Windows může mít volitelně **app.config** souboru. Konfigurační soubory sdílejí společné prvky, i když se název a umístění konfiguračního souboru se liší v závislosti na hostiteli aplikace.  
  
### <a name="the-connectionstrings-section"></a>ConnectionStrings oddílu  
 Připojovací řetězce mohou být uloženy jako dvojice klíč/hodnota v **connectionStrings** část **konfigurace** element konfiguračního souboru aplikace. Zahrnout podřízené prvky **přidat**, **vymazat**, a **odebrat**.  
  
 Následující fragment konfigurační soubor ukazuje schématu a syntaxe pro uložení připojovacího řetězce. **Název** atribut je název, který poskytnete k jednoznačné identifikaci připojovací řetězec tak, aby se dá načíst za běhu. **ProviderName** je výchozí název zprostředkovatele dat .NET Framework, která je registrována v souboru machine.config.  
  
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
>  Můžete uložit součást připojovacího řetězce v konfiguračním souboru a použít <xref:System.Data.Common.DbConnectionStringBuilder> třídy k jejímu dokončení v době běhu. To je užitečné v situacích, kde si nejste jisti prvky připojovacího řetězce předem nebo při ukládání citlivých informací v konfiguračním souboru. Další informace najdete v tématu [tvůrci připojovacích řetězců](../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
### <a name="using-external-configuration-files"></a>Pomocí externích konfiguračních souborů  
 Externí konfigurační soubory jsou samostatné soubory, které obsahují fragment konfigurační soubor, který se skládá z jednoho oddílu. Externí konfigurační soubor je pak odkazuje hlavní konfigurační soubor. Ukládání **connectionStrings** oddíl v souboru fyzicky oddělená je užitečné v situacích, kde lze upravit připojovací řetězce po nasazení aplikace. Standardní chování technologie ASP.NET je například restartovat doménu aplikace při změně konfiguračních souborů, takže se použila ke ztrátě informací o stavu. Úprava externí konfiguračního souboru ale nezpůsobí restartování aplikace. Externí konfigurační soubory nejsou omezeny na ASP.NET; Můžete také používají aplikace Windows. Kromě toho zabezpečení přístupu k souboru a oprávnění lze použít k omezení přístupu k externí konfigurační soubory. Práce s externí konfigurační soubory v době běhu je transparentní a vyžaduje žádné speciální kódování.  
  
 K ukládání připojovacích řetězců v externí konfigurační soubor, vytvořit samostatný soubor, který obsahuje pouze **connectionStrings** oddílu. Neobsahují žádné další prvky, oddíly nebo atributy. Tento příklad ukazuje syntaxi pro externí konfigurační soubor.  
  
```xml  
<connectionStrings>  
  <add name="Name"   
   providerName="System.Data.ProviderName"   
   connectionString="Valid Connection String;" />  
</connectionStrings>  
```  
  
 V konfiguračním souboru hlavní aplikace použijete **configSource** atribut zadejte plně kvalifikovaný název a umístění externího souboru. V tomto příkladu odkazuje na externí konfigurační soubor s názvem `connections.config`.  
  
```xml  
<?xml version='1.0' encoding='utf-8'?>  
<configuration>  
    <connectionStrings configSource="connections.config"/>  
</configuration>  
```  
  
## <a name="retrieving-connection-strings-at-run-time"></a>Načítání připojovacích řetězců v době běhu  
 Zavedeny nové třídy v rozhraní .NET Framework 2.0 <xref:System.Configuration> obor názvů pro zjednodušení načítání připojovacích řetězců z konfiguračních souborů v době běhu. Připojovací řetězec můžete programově načítat podle názvu nebo podle názvu zprostředkovatele.  
  
> [!NOTE]
>  **Machine.config** soubor obsahuje také **connectionStrings** oddílu, který obsahuje připojovací řetězec používaný sady Visual Studio. Při načítání připojovacích řetězců prostřednictvím jeho názvu zprostředkovatele **app.config** souboru v aplikaci Windows, připojovací řetězce v **machine.config** získat načíst první a potom položky z **app.config**. Přidání **vymazat** ihned po **connectionStrings** element odebere všechny zděděné odkazy z datové struktury v paměti, tak, aby pouze připojovací řetězce definované v místních **app.config** jsou považovány za souboru.  
  
### <a name="working-with-the-configuration-classes"></a>Práce s třídami konfigurace  
 Od verze rozhraní .NET Framework 2.0, <xref:System.Configuration.ConfigurationManager> se používá při práci s konfigurační soubory v místním počítači, nahraďte zastaralá <xref:System.Configuration.ConfigurationSettings>. <xref:System.Web.Configuration.WebConfigurationManager> slouží k práci s konfiguračních souborů ASP.NET. Je navržena pro práci s konfigurační soubory na webovém serveru a umožňuje programový přístup k souboru konfigurační oddíly funkce, jako **system.web**.  
  
> [!NOTE]
>  Přístup k konfigurační soubory v době běhu vyžaduje udělení oprávnění volajícího požadovaná oprávnění závisí na typu aplikace, konfiguračním souboru a umístění. Další informace najdete v tématu [pomocí tříd konfigurace](https://docs.microsoft.com/previous-versions/aspnet/ms228063(v=vs.100)) a <xref:System.Web.Configuration.WebConfigurationManager> pro aplikace ASP.NET a <xref:System.Configuration.ConfigurationManager> pro aplikace Windows.  
  
 Můžete použít <xref:System.Configuration.ConnectionStringSettingsCollection> načíst připojovací řetězce z konfiguračních souborů aplikace. Obsahuje kolekci <xref:System.Configuration.ConnectionStringSettings> objektů, z nichž každý představuje jednu položku v **connectionStrings** oddílu. Vlastností namapovat na atributy řetězce připojení, umožňuje získat připojovací řetězec tak, že zadáte jméno nebo název poskytovatele.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Configuration.ConnectionStringSettings.Name%2A>|Název připojovacího řetězce. Mapuje **název** atribut.|  
|<xref:System.Configuration.ConnectionStringSettings.ProviderName%2A>|Zprostředkovatel plně kvalifikovaný název. Mapuje **providerName** atribut.|  
|<xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A>|Připojovací řetězec. Mapuje **connectionString** atribut.|  
  
### <a name="example-listing-all-connection-strings"></a>Příklad: Výpis všech připojovacích řetězců  
 Tento příklad provede iteraci <xref:System.Configuration.ConnectionStringSettingsCollection> a zobrazí <xref:System.Configuration.ConnectionStringSettings.Name%2A?displayProperty=nameWithType>, <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A?displayProperty=nameWithType>, a <xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A?displayProperty=nameWithType> vlastnosti v okně konzoly.  
  
> [!NOTE]
>  System.Configuration.dll není zahrnut ve všech typech projektů a budete muset nastavit na ni odkaz použít třídy konfigurace. Název a umístění konfiguračního souboru pro konkrétní aplikace se liší podle typu aplikace a proces hostování.  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfig#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfig/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfig#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfig/VB/source.vb#1)]  
  
### <a name="example-retrieving-a-connection-string-by-name"></a>Příklad: Načtení připojovacího řetězce podle názvu  
 Tento příklad ukazuje, jak načtení připojovacího řetězce z konfiguračního souboru tak, že zadáte jeho název. Kód vytvoří <xref:System.Configuration.ConnectionStringSettings> objektu odpovídající zadaných vstupních parametrů do <xref:System.Configuration.ConfigurationManager.ConnectionStrings%2A> název. Pokud se nenašel žádný odpovídající název, funkce vrátí `null` (`Nothing` v jazyce Visual Basic).  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByName#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByName/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByName#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByName/VB/source.vb#1)]  
  
### <a name="example-retrieving-a-connection-string-by-provider-name"></a>Příklad: Načtení připojovacího řetězce podle názvu zprostředkovatele  
 Tento příklad ukazuje, jak získat připojovací řetězec tak, že zadáte název poskytovatele invariantní ve formátu *System.Data.ProviderName*. Kód prochází <xref:System.Configuration.ConnectionStringSettingsCollection> a vrátí připojovací řetězec v první <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> nalezen. Pokud není nalezen název zprostředkovatele, funkce vrátí `null` (`Nothing` v jazyce Visual Basic).  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="encrypting-configuration-file-sections-using-protected-configuration"></a>Šifrování pomocí konfigurační soubor oddíly chráněné konfigurace  
 ASP.NET 2.0 zavedli novou funkci, volá *chráněné konfigurace*, která umožňuje šifrování citlivých informací v konfiguračním souboru. I když primárně určený pro technologii ASP.NET, chráněné konfigurace lze také k šifrování souborů konfigurační oddíly funkce v aplikacích Windows. Podrobný popis možností chráněné konfigurace najdete v tématu [šifrování konfigurační informace pomocí Protected Configuration](https://docs.microsoft.com/previous-versions/aspnet/53tyfkaw(v=vs.100)).  
  
 Následující konfigurační soubor fragmentu ukazuje **connectionStrings** části po byla dříve zašifrována. **ConfigProtectionProvider** určuje chráněné konfigurace zprostředkovatele, který používá k šifrování a dešifrování řetězce připojení. **EncryptedData** oddíl obsahuje šifrovaného textu.  
  
```xml  
<connectionStrings configProtectionProvider="DataProtectionConfigurationProvider">  
  <EncryptedData>  
    <CipherData>  
      <CipherValue>AQAAANCMnd8BFdERjHoAwE/Cl+sBAAAAH2... </CipherValue>  
    </CipherData>  
  </EncryptedData>  
</connectionStrings>  
```  
  
 Když šifrované připojovací řetězec je načten v době běhu, rozhraní .NET Framework používá k dešifrování zadaného zprostředkovatele **element CipherValue** a zpřístupní ji pro vaše aplikace. Nemusíte psát žádný další kód ke správě procesu dešifrování.  
  
### <a name="protected-configuration-providers"></a>Poskytovatelé konfigurace chráněné  
 Poskytovatelé konfigurace chráněné jsou registrované ve **configProtectedData** část **machine.config** souboru na místním počítači, jak je znázorněno v následující fragment, který ukazuje dvě chráněné konfigurace poskytovatele dodané s rozhraním .NET Framework. Pro lepší čitelnost, byly zkráceny hodnoty uvedené tady.  
  
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
  
 Můžete nakonfigurovat další chráněné konfigurace poskytovatelů jejich přidáním do **machine.config** souboru. Můžete také vytvořit poskytovatele chráněné konfigurace děděním z <xref:System.Configuration.ProtectedConfigurationProvider> abstraktní základní třída. Následující tabulka popisuje dva konfigurační soubory zahrnuté v rozhraní .NET Framework.  
  
|Poskytovatel|Popis|  
|--------------|-----------------|  
|<xref:System.Configuration.RsaProtectedConfigurationProvider>|K šifrování a dešifrování dat používá šifrovací algoritmus RSA. Algoritmus RSA lze použít pro šifrování s veřejným klíčem a digitálním podpisům. Je také známý jako "veřejný klíč" nebo asymetrické šifrování protože využívá dva různé klíče. Můžete použít [registrační nástroj služby IIS technologie ASP.NET (Aspnet_regiis.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/k6h9cz8h(v=vs.90)) pro šifrování oddílů v souboru Web.config a správu šifrovacích klíčů. ASP.NET dešifruje konfigurační soubor při zpracování souboru. Identita aplikace technologie ASP.NET musí mít přístup pro čtení k šifrovacímu klíči, který se používá k šifrování a dešifrování šifrovaných oddílů.|  
|<xref:System.Configuration.DpapiProtectedConfigurationProvider>|Windows Data Protection API (DPAPI) používá k šifrování konfigurační oddíly funkce. Používá Windows vestavěné kryptografické služby a může být nakonfigurována pro ochranu specifické pro počítač nebo konkrétního uživatele účtu. Je užitečné pro více aplikací na stejném serveru, potřebujete sdílet informace specifické pro počítač ochrany. Uživatelská účet ochrany je možné pomocí služeb, které fungují s specifická identita uživatele, jako jsou sdílené hostitelského prostředí. Každá aplikace běží pod samostatnou identitu, která omezuje přístup k prostředkům, například soubory a databáze.|  
  
 Oba poskytovatelé nabízejí silné šifrování data. Nicméně pokud máte v úmyslu použít stejný soubor zašifrovanou konfiguraci na více serverech, jako jsou webové farmy, pouze <xref:System.Configuration.RsaProtectedConfigurationProvider> umožňuje exportovat šifrovací klíče použité k šifrování dat a import na jiném serveru. Další informace najdete v tématu [import a export chráněné konfigurace RSA kontejnery klíčů](https://docs.microsoft.com/previous-versions/aspnet/yxw286t2(v=vs.100)).  
  
### <a name="using-the-configuration-classes"></a>Použití tříd konfigurace  
 <xref:System.Configuration> Obor názvů obsahuje třídy pro práci s nastavením konfigurace prostřednictvím kódu programu. <xref:System.Configuration.ConfigurationManager> Třídě poskytuje přístup ke konfigurační soubory počítače, aplikace a uživatele. Pokud vytváříte aplikaci ASP.NET, můžete použít <xref:System.Web.Configuration.WebConfigurationManager> třídu, která poskytuje stejné funkce, zatímco služba také umožňuje přístup k nastavení, které jsou jedinečné pro aplikace ASP.NET, jako jsou ty součástí  **\< System.Web >**.  
  
> [!NOTE]
>  <xref:System.Security.Cryptography> Obor názvů obsahuje třídy, které poskytují další možnosti pro šifrování a dešifrování dat. Použití těchto tříd, pokud budete potřebovat chránit kryptografické služby, které nejsou k dispozici pomocí konfigurace. Některé z těchto tříd jsou obálky pro nespravované CryptoAPI Microsoft jiné implementace čistě spravovaná. Další informace najdete v tématu [šifrovacím službám](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/93bskf9z(v=vs.90)).  
  
### <a name="appconfig-example"></a>App.config Example  
 Tento příklad ukazuje, jak přepnout šifrování **connectionStrings** v tématu **app.config** soubor pro aplikaci Windows. V tomto příkladu, které procedura používá název aplikace jako argument, například "MyApplication.exe". **App.config** soubor pak bude zašifrovaný a zkopírovány do složky, která obsahuje spustitelný soubor pod názvem "MyApplication.exe.config".  
  
> [!NOTE]
>  Připojovací řetězec mohou ho dešifrovat jenom na počítače, na kterém byl zašifrován.  
  
 Tento kód použije <xref:System.Configuration.ConfigurationManager.OpenExeConfiguration%2A> metoda otevřete **app.config** soubor pro úpravy a <xref:System.Configuration.ConfigurationManager.GetSection%2A> vrátí metoda **connectionStrings** oddílu. Zkontroluje kód <xref:System.Configuration.SectionInformation.IsProtected%2A> vlastnost, volání <xref:System.Configuration.SectionInformation.ProtectSection%2A> šifrování oddílu, pokud není zašifrovaný. <xref:System.Configuration.SectionInformation.UnprotectSection%2A> Metoda vyvolána k dešifrování části. <xref:System.Configuration.Configuration.Save%2A> Metoda se dokončí operace a uloží změny.  
  
> [!NOTE]
>  Je nutné nastavit odkaz na `System.Configuration.dll` ve vašem projektu pro spuštění kódu.  
  
 [!code-csharp[DataWorks ConnectionStrings.Encrypt#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStrings.Encrypt/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStrings.Encrypt#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStrings.Encrypt/VB/source.vb#1)]  
  
### <a name="webconfig-example"></a>Příklad souboru Web.config  
 V tomto příkladu <xref:System.Web.Configuration.WebConfigurationManager.OpenWebConfiguration%2A> metodu `WebConfigurationManager`. Všimněte si, že v tomto případě můžete zadat relativní cestu k **Web.config** souboru s použitím vlnovkou. Kód vyžaduje přidání odkazu na `System.Web.Configuration` třídy.  
  
 [!code-csharp[DataWorks ConnectionStringsWeb.Encrypt#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringsWeb.Encrypt/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringsWeb.Encrypt#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringsWeb.Encrypt/VB/source.vb#1)]  
  
 Další informace o zabezpečení aplikace ASP.NET najdete v tématu [webů ASP.NET zabezpečení](https://docs.microsoft.com/previous-versions/aspnet/91f66yxt(v=vs.100)).  
  
## <a name="see-also"></a>Viz také:
- [Tvůrci připojovacích řetězců](../../../../docs/framework/data/adonet/connection-string-builders.md)
- [Ochrana informací o připojení](../../../../docs/framework/data/adonet/protecting-connection-information.md)
- [Použití tříd konfigurace](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ms228063(v=vs.90))
- [Konfigurace aplikací](../../../../docs/framework/configure-apps/index.md)
- [Správa webu technologie ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/6hy1xzbw(v=vs.100))
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
