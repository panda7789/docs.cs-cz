---
title: Řešení potíží s WCF – úvodní příručka
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], troubleshooting
- Windows Communication Foundation [WCF], troubleshooting
ms.assetid: a9ea7a53-f31a-46eb-806e-898e465a4992
ms.openlocfilehash: d1cae7ad2ac0fdf963d11911484b1bd534cbc129
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094732"
---
# <a name="wcf-troubleshooting-quickstart"></a>Řešení potíží s WCF – úvodní příručka
Toto téma obsahuje seznam známých problémů, se kterými se zákazníci v průběhu vývoje služeb a klientů WCF spouštěli. Pokud problém, který používáte, není v tomto seznamu, doporučujeme vám nakonfigurovat trasování pro vaši službu. Tím se vygeneruje trasovací soubor, který můžete zobrazit pomocí prohlížeče trasovacích souborů a získat podrobné informace o výjimkách, ke kterým může docházet v rámci služby. Další informace o konfiguraci trasování naleznete v tématu: [Configure Tracing](./diagnostics/tracing/configuring-tracing.md). Další informace o prohlížeči trasovacích souborů naleznete v tématu: [nástroj Service Trace Viewer (SvcTraceViewer. exe)](service-trace-viewer-tool-svctraceviewer-exe.md).  
  
1. [Při pokusu o přechod na službu WCF po instalaci systému Windows 7 a IIS se zobrazí následující chybová zpráva: Chyba protokolu HTTP 404,3 – Nenalezeno](#bkmk_0)  
  
     Chyba protokolu HTTP 404,3 – FoundThe stránku, kterou požadujete, nelze zpracovat z důvodu konfigurace rozšíření. Pokud je stránka skriptem, přidejte obslužnou rutinu. Pokud se má soubor stáhnout, přidejte mapu MIME. Podrobná chyba InformationModule StaticFileModule.  
  
2. [V případě, že je můj klient v době, kdy se po prvním požadavku nečinný, se někdy na druhou žádost dostanou MessageSecurityException –. Co se děje?](#BKMK_q1)  
  
3. [Moje služba začne odmítat nové klienty po tom, co s nimi pracuje 10 klientů. Co se děje?](#BKMK_q2)  
  
4. [Můžu konfiguraci služby načíst z jiného místa než do konfiguračního souboru aplikace WCF?](#BKMK_q3)  
  
5. [Moje služba a klient fungují skvěle, ale nemůžu je nechat fungovat, když je klient v jiném počítači? Co se děje?](#BKMK_q4)  
  
6. [Když vyvolám výjimku FaultException\<> kde typ je výjimka, vždy na klientovi získáme obecný typ FaultException, nikoli obecný typ. Co se děje?](#BKMK_q5)  
  
7. [Vypadá to, že se operace jednosměrového a odpovědi vrátí přibližně stejnou rychlost, když odpověď neobsahuje žádná data. Co se děje?](#BKMK_q6)  
  
8. [Používám certifikát X. 509 s mojí službou a získám System. Security. Cryptography. CryptographicException –. Co se děje?](#BKMK_q77)  
  
9. [Změnil (a) jsem první parametr operace z velkých písmen na malá. Nyní můj klient vyvolá výjimku. Co se děje?](#BKMK_q88)  
  
10. [Používám jeden z mých nástrojů pro trasování a zobrazí se EndpointNotFoundException. Co se děje?](#BKMK_q99)  
  
11. [Při volání webové aplikace HTTP WCF z aplikace WCF SOAP služba vrátí následující chybu: metoda 405 není povolena.](#BK_MK99)  
  
 [Jaká je základní adresa? Jak se vztahuje na adresu koncového bodu?](#BKMK_q10)  
  
<a name="bkmk_0"></a>   
## <a name="after-installing-windows-7-and-iis-when-i-attempt-to-browse-to-a-wcf-service-i-get-the-following-error-message-http-error-4043--not-found"></a>Při pokusu o přechod na službu WCF po instalaci systému Windows 7 a IIS se zobrazí následující chybová zpráva: Chyba protokolu HTTP 404,3 – Nenalezeno  
 Úplná chybová zpráva:  
  
 Chyba protokolu HTTP 404,3 – FoundThe stránku, kterou požadujete, nelze zpracovat z důvodu konfigurace rozšíření. Pokud je stránka skriptem, přidejte obslužnou rutinu. Pokud se má soubor stáhnout, přidejte mapu MIME. Podrobná chyba InformationModule StaticFileModule.  
  
 Tato chybová zpráva se zobrazí, když v Ovládacích panelech není explicitně nastavená možnost Windows Communication Foundation aktivace protokolu HTTP. Chcete-li nastavit tuto možnost, přejděte na ovládací panely a v levém dolním rohu okna klikněte na položku programy. Klikněte na zapnout nebo vypnout funkce systému Windows. Rozbalte položku Microsoft .NET Framework 3.5.1 a vyberte možnost Windows Communication Foundation aktivace protokolem HTTP.  
  
<a name="BKMK_q1"></a>   
## <a name="sometimes-i-receive-a-messagesecurityexception-on-the-second-request-if-my-client-is-idle-for-a-while-after-the-first-request-what-is-happening"></a>V případě, že je můj klient v době, kdy se po prvním požadavku nečinný, se někdy na druhou žádost dostanou MessageSecurityException –. Co se děje?  
 Druhá žádost může selhat hlavně ze dvou důvodů: (1) vypršel časový limit relace nebo (2) webový server, který je hostitelem služby, se recykluje. V prvním případě je relace platná až do vypršení časového limitu služby. Pokud služba neobdrží požadavek od klienta v časovém intervalu určeném vazbou služby (<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>), služba ukončí relaci zabezpečení. Následné zprávy klienta mají za následek <xref:System.ServiceModel.Security.MessageSecurityException>. Klient musí znovu vytvořit zabezpečenou relaci se službou pro odesílání budoucích zpráv nebo použití tokenu kontextového kontextu zabezpečení. Tokeny kontextového kontextu zabezpečení také umožňují zabezpečenou relaci překonání webového serveru, který se recykluje. Další informace o použití stavových tokenů zabezpečeného kontextu v zabezpečené relaci naleznete v tématu [How to: Create a Security Context token for the Secure Session](./feature-details/how-to-create-a-security-context-token-for-a-secure-session.md). Můžete také zakázat zabezpečené relace. Při použití vazby [\<wsHttpBinding >](../configure-apps/file-schema/wcf/wshttpbinding.md) můžete nastavit vlastnost `establishSecurityContext` na `false` pro zakázání zabezpečených relací. Chcete-li zakázat zabezpečené relace pro jiné vazby, je nutné vytvořit vlastní vazbu. Podrobnosti o vytvoření vlastní vazby naleznete v tématu [How to: Create a Custom Binding using the SecurityBindingElement](./feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md). Než použijete některou z těchto možností, musíte pochopit požadavky na zabezpečení vaší aplikace.  
  
<a name="BKMK_q2"></a>   
## <a name="my-service-starts-to-reject-new-clients-after-about-10-clients-are-interacting-with-it-what-is-happening"></a>Moje služba začne odmítat nové klienty po tom, co s nimi pracuje 10 klientů. Co se děje?  
 Ve výchozím nastavení můžou služby mít jenom 10 souběžných relací. Proto pokud vazby služby používají relace, akceptuje nová připojení klientů, dokud nedosáhne tohoto čísla, a poté odmítne nová připojení klientů, dokud nebude ukončena jedna z aktuálních relací. Více klientů můžete podporovat několika různými způsoby. Pokud vaše služba nevyžaduje relace, nepoužívejte vazbu s relacemi. (Další informace najdete v tématu [použití relací](using-sessions.md).) Další možností je zvýšit limit relace změnou hodnoty vlastnosti <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> na číslo odpovídající vaší situaci.  
  
<a name="BKMK_q3"></a>   
## <a name="can-i-load-my-service-configuration-from-somewhere-other-than-the-wcf-applications-configuration-file"></a>Můžu konfiguraci služby načíst z jiného místa než do konfiguračního souboru aplikace WCF?  
 Ano, ale je nutné vytvořit vlastní třídu <xref:System.ServiceModel.ServiceHost>, která přepíše metodu <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A>. Uvnitř této metody můžete zavolat základ pro načtení konfigurace (Pokud chcete načíst i standardní informace o konfiguraci), ale můžete také zcela nahradit systém načítání konfigurace. Pokud chcete načíst konfiguraci z konfiguračního souboru, který se liší od konfiguračního souboru aplikace, musíte konfigurační soubor analyzovat sami a načíst konfiguraci.  
  
 Následující příklad kódu ukazuje, jak přepsat metodu <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> a jak přímo nakonfigurovat koncový bod.  
  
```csharp
public class MyServiceHost : ServiceHost  
{  
    public MyServiceHost(Type serviceType, params Uri[] baseAddresses)    
      : base(serviceType, baseAddresses)  
    {
        Console.WriteLine("MyServiceHost Constructor");
    }  
  
    protected override void ApplyConfiguration()  
    {  
        string straddress = GetAddress();  
        Uri address = new Uri(straddress);  
        Binding binding = GetBinding();  
        base.AddServiceEndpoint(typeof(IData), binding, address);  
    }  
  
    string GetAddress()  
    {
        return "http://MyMachine:7777/MyEndpointAddress/";
    }  
  
    Binding GetBinding()  
    {  
        WSHttpBinding binding = new WSHttpBinding();  
        binding.Security.Mode = SecurityMode.None;  
        return binding;  
    }  
}  
```  
  
<a name="BKMK_q4"></a>   
## <a name="my-service-and-client-work-great-but-i-cant-get-them-to-work-when-the-client-is-on-another-computer-whats-happening"></a>Moje služba a klient fungují skvěle, ale nemůžu je nechat fungovat, když je klient v jiném počítači? Co se děje?  
 V závislosti na výjimce může dojít k několika problémům:  
  
- Je možné, že budete muset změnit adresy koncových bodů klienta na název hostitele a ne na "localhost".  
  
- Je možné, že budete muset otevřít port do aplikace. Podrobnosti najdete v tématu [pokyny k bráně firewall](./samples/firewall-instructions.md) z ukázek sady SDK.  
  
- Další možné problémy najdete v tématu ukázky, na [kterých běží ukázky Windows Communication Foundation](./samples/running-the-samples.md).  
  
- Pokud klient používá pověření systému Windows a výjimka je <xref:System.ServiceModel.Security.SecurityNegotiationException>, nakonfigurujte protokol Kerberos následujícím způsobem.  
  
    1. Přidejte přihlašovací údaje identity do prvku koncového bodu v souboru App. config klienta:  
  
        ```xml
        <endpoint   
          address="http://MyServer:8000/MyService/"   
          binding="wsHttpBinding"   
          bindingConfiguration="WSHttpBinding_IServiceExample"   
          contract="IServiceExample"   
          behaviorConfiguration="ClientCredBehavior"   
          name="WSHttpBinding_IServiceExample">  
          <identity>  
            <userPrincipalName value="name@corp.contoso.com"/>  
          </identity>  
        </endpoint>  
        ```  
  
    2. Spusťte samoobslužnou službu pod účtem System nebo NetworkService. Spuštěním tohoto příkazu můžete vytvořit okno příkazového řádku v rámci účtu System:  
  
        ```console
        at 12:36 /interactive "cmd.exe"  
        ```  
  
    3. Služba je hostitelem služby Internetová informační služba (IIS), která ve výchozím nastavení používá účet hlavního názvu služby (SPN).  
  
    4. Zaregistrujte nový hlavní název služby (SPN) s doménou pomocí SetSPN. Aby to bylo možné, musíte být správcem domény.  
  
 Další informace o protokolu Kerberos najdete v tématu [koncepty zabezpečení používané ve službě WCF](./feature-details/security-concepts-used-in-wcf.md) a:  
  
- [Ladění chyb u ověřování Windows](./feature-details/debugging-windows-authentication-errors.md)  
  
- [Registrace hlavních názvů služby Kerberos pomocí HTTP. sys](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms178119(v=sql.105))  
  
- [Vysvětlení protokolu Kerberos](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-2000-server/bb742516(v%3dtechnet.10))  
  
<a name="BKMK_q5"></a>   
## <a name="when-i-throw-a-faultexceptionexception-where-the-type-is-an-exception-i-always-receive-a-general-faultexception-type-on-the-client-and-not-the-generic-type-whats-happening"></a>Když vyvolám výjimku FaultException\<> kde typ je výjimka, vždy na klientovi získáme obecný typ FaultException, nikoli obecný typ. Co se děje?  
 Důrazně doporučujeme vytvořit vlastní chybový datový typ a deklarovat ho jako typ podrobností ve smlouvě o selhání. Důvodem je použití typů výjimek poskytovaných systémem:  
  
- Vytvoří závislost typu, která odebere jednu z největších silných aplikací orientovaných na služby.  
  
- Nemůže záviset na výjimce při serializaci standardním způsobem. Některé – například <xref:System.Security.SecurityException>– nemusí být serializovatelný vůbec.  
  
- Zveřejňuje podrobnosti interní implementace klientům. Další informace najdete v tématu [určení a zpracování chyb v kontraktech a službách](specifying-and-handling-faults-in-contracts-and-services.md).  
  
 Pokud však ladíte aplikaci, můžete serializovat informace o výjimce a vrátit ji do klienta pomocí <xref:System.ServiceModel.Description.ServiceDebugBehavior> třídy.  
  
<a name="BKMK_q6"></a>   
## <a name="it-seems-like-one-way-and-request-reply-operations-return-at-roughly-the-same-speed-when-the-reply-contains-no-data-whats-happening"></a>Vypadá to, že se operace jednosměrového a odpovědi vrátí přibližně stejnou rychlost, když odpověď neobsahuje žádná data. Co se děje?  
 Určení, že operace je jedním ze způsobů, že kontrakt operace přijímá vstupní zprávu a nevrací výstupní zprávu. V rámci služby WCF vrátí všechna volání klientů, když byla výstupní data zapsána do přenosu, nebo je vyvolána výjimka. Jednosměrné operace fungují stejným způsobem a můžou vyvolat, jestli službu není možné najít nebo blokovat, pokud služba není připravená přijmout data ze sítě. V rámci WCF to obvykle vede k jednosměrné volání, které vrací klientovi rychleji než požadavek-odpověď; jakákoli podmínka, která zpomaluje odesílání odchozích dat přes síť, zpomaluje jednosměrné operace a také operace požadavek-odpověď. Další informace najdete v tématu [jednosměrné služby](./feature-details/one-way-services.md) a [přístup ke službám pomocí klienta WCF](./feature-details/accessing-services-using-a-client.md).  
  
<a name="BKMK_q77"></a>   
## <a name="im-using-an-x509-certificate-with-my-service-and-i-get-a-systemsecuritycryptographycryptographicexception-whats-happening"></a>Používám certifikát X. 509 s mojí službou a získám System. Security. Cryptography. CryptographicException –. Co se děje?  
 K tomu obvykle dochází po změně uživatelského účtu, pod kterým běží pracovní proces služby IIS. Pokud například v systému Windows XP změníte výchozí uživatelský účet, který Aspnet_wp. exe spustí v rámci z ASPNET na vlastní uživatelský účet, může se zobrazit tato chyba. Pokud používáte privátní klíč, bude mít proces, který ho používá, oprávnění pro přístup k souboru, který tento klíč ukládá.  
  
 V takovém případě je nutné udělit účtu procesu oprávnění ke čtení pro soubor, který obsahuje privátní klíč. Pokud například pracovní proces služby IIS běží pod účtem Bob, budete muset uživateli udělit přístup pro čtení k souboru, který obsahuje soukromý klíč.  
  
 Další informace o tom, jak poskytnout správnému uživatelskému účtu přístup k souboru, který obsahuje privátní klíč pro určitý certifikát X. 509, najdete v tématu [How to: zpřístupnit certifikáty X. 509 pro WCF](./feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md).  
  
<a name="BKMK_q88"></a>   
## <a name="i-changed-the-first-parameter-of-an-operation-from-uppercase-to-lowercase-now-my-client-throws-an-exception-whats-happening"></a>Změnil (a) jsem první parametr operace z velkých písmen na malá. Nyní můj klient vyvolá výjimku. Co se děje?  
 Hodnoty názvů parametrů v signatuře operace jsou součástí kontraktu a rozlišují velká a malá písmena. Atribut <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> použijte v případě, že potřebujete rozlišovat mezi názvem místního parametru a metadaty, které popisují operaci pro klientské aplikace.  
  
<a name="BKMK_q99"></a>   
## <a name="im-using-one-of-my-tracing-tools-and-i-get-an-endpointnotfoundexception-whats-happening"></a>Používám jeden z mých nástrojů pro trasování a zobrazí se EndpointNotFoundException. Co se děje?  
 Pokud používáte trasovací nástroj, který není systémem poskytnutý mechanismus trasování WCF a obdržíte <xref:System.ServiceModel.EndpointNotFoundException>, který indikuje, že došlo ke neshodě filtru adres, je nutné použít třídu <xref:System.ServiceModel.Description.ClientViaBehavior> k nasměrování zpráv do trasovacího nástroje a nechat nástroj přesměrovat tyto zprávy na adresu služby. Třída <xref:System.ServiceModel.Description.ClientViaBehavior> mění hlavičku adresování `Via`, aby určovala další síťovou adresu nezávisle na konečném přijímači, kterou uvádí hlavička `To` adresování. V takovém případě ale neměňte adresu koncového bodu, která se používá k navázání `To` hodnoty.  
  
 Následující příklad kódu ukazuje příklad konfiguračního souboru klienta.  
  
```xml
<endpoint   
  address="http://localhost:8000/MyServer/"  
  binding="wsHttpBinding"  
  bindingConfiguration="WSHttpBinding_IMyContract"  
  behaviorConfiguration="MyClient"   
  contract="IMyContract"   
  name="WSHttpBinding_IMyContract">  
</endpoint>  
<behaviors>  
  <endpointBehaviors>  
    <behavior name="MyClient">  
      <clientVia viaUri="http://localhost:8001/MyServer/"/>  
    </behavior>  
  </endpointBehaviors>  
</behaviors>  
```  
  
<a name="BKMK_q10"></a>   
## <a name="what-is-the-base-address-how-does-it-relate-to-an-endpoint-address"></a>Jaká je základní adresa? Jak se vztahuje na adresu koncového bodu?  
 Základní adresa je kořenová adresa pro třídu <xref:System.ServiceModel.ServiceHost>. Ve výchozím nastavení platí, že pokud do konfigurace služby přidáte třídu <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, jazyk WSDL (Web Services Description Language) pro všechny koncové body, který hostitel publikuje, se načte z základní adresy HTTP a veškerá relativní adresa poskytnutá chování metadat a také "? WSDL". Pokud jste obeznámeni s ASP.NET a službou IIS, základní adresa je ekvivalentní virtuálnímu adresáři.  
  
## <a name="sharing-a-port-between-a-service-endpoint-and-a-mex-endpoint-using-the-nettcpbinding"></a>Sdílení portu mezi koncovým bodem služby a koncovým bodem MEX pomocí NetTcpBinding  
 Pokud zadáte základní adresu pro službu jako NET. TCP://MyServer: 8080/Mojesluzba a přidejte následující koncové body:  
  
```xml  
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
 A pokud změníte jedno z nastavení NetTcpBinding, jak je znázorněno v následujícím fragmentu konfigurace:  
  
```xml  
<bindings>  
  <netTcpBinding>  
    <binding closeTimeout="00:01:00" openTimeout="00:01:00" receiveTimeout="00:10:00" sendTimeout="00:01:00" transactionFlow="false" transferMode="Buffered" transactionProtocol="OleTransactions" hostNameComparisonMode="StrongWildcard" listenBacklog="10" maxBufferPoolSize="524288" maxBufferSize="65536" maxConnections="11" maxReceivedMessageSize="65536">  
      <readerQuotas maxDepth="32" maxStringContentLength="8192" maxArrayLength="16384" maxBytesPerRead="4096" maxNameTableCharCount="16384"/>  
      <reliableSession ordered="true" inactivityTimeout="00:10:00" enabled="false"/>  
      <security mode="Transport">  
        <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign"/>  
      </security>  
    </binding>  
  </netTcpBinding>  
</bindings>  
```  
  
 Zobrazí se chyba podobný následujícímu: došlo k neošetřené výjimce: System. ServiceModel. AddressAlreadyInUseException –: naslouchací proces na koncovém bodu IP 0.0.0.0:9000 tuto chybu můžete obejít zadáním plně kvalifikované adresy URL s jiným portem pro koncový bod MEX, jak je znázorněno v následujícím fragmentu konfigurace:  
  
```xml
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="net.tcp://localhost:9001/servicemodelsamples/mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
<a name="BK_MK99"></a>   
## <a name="when-calling-a-wcf-web-http-application-from-a-wcf-soap-application-the-service-returns-the-following-error-405-method-not-allowed"></a>Při volání webové aplikace HTTP WCF z aplikace WCF SOAP služba vrátí následující chybu: metoda 405 není povolena.  
 Volání webové aplikace HTTP WCF (služba, která používá <xref:System.ServiceModel.WebHttpBinding> a <xref:System.ServiceModel.Description.WebHttpBehavior>) ze služby WCF může generovat následující výjimku: ``Unhandled Exception: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: The remote server returned an unexpected response: (405) Method Not Allowed.`` k této výjimce dojde, protože služba WCF přepíše odchozí <xref:System.ServiceModel.OperationContext> s příchozími <xref:System.ServiceModel.OperationContext>y. Chcete-li tento problém vyřešit, vytvořte <xref:System.ServiceModel.OperationContextScope> v rámci operace služby HTTP webu WCF. Například:  
  
```csharp
public string Echo(string input)  
{  
    using (new OperationContextScope(this.InnerChannel))  
    {  
        return base.Channel.Echo(input);  
    }  
}  
```  
  
## <a name="see-also"></a>Viz také

- [Ladění chyb u ověřování Windows](./feature-details/debugging-windows-authentication-errors.md)
