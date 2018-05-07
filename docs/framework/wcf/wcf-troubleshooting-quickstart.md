---
title: Řešení potíží s WCF – úvodní příručka
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], troubleshooting
- Windows Communication Foundation [WCF], troubleshooting
ms.assetid: a9ea7a53-f31a-46eb-806e-898e465a4992
ms.openlocfilehash: 5a6ea4f3ba121f419d1a8c46fc2534988a93d554
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="wcf-troubleshooting-quickstart"></a>Řešení potíží s WCF – úvodní příručka
Toto téma uvádí počet známé problémy, se kterými se zákazníci spustili do při vývoj klienti WCF a služeb. Pokud problém, který běží na není v tomto seznamu, doporučujeme že konfigurovat trasování pro služby. Tím se vygeneruje soubor trasování, můžete zobrazit pomocí prohlížeče soubor trasování a získat podrobné informace o výjimkách, který může vyskytovat v rámci služby. Další informace o konfiguraci trasování najdete v tématu: [Konfigurace trasování](../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md). Další informace o prohlížeči soubor trasování najdete v tématu: [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).  
  
1.  [Po instalaci systému Windows 7 a IIS, při pokusu o přejděte do služby WCF zobrazí následující chybová zpráva: HTTP Chyba 404.3 – nebyla nalezena](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#bkmk_0)  
  
     Chyba protokolu HTTP 404.3 – není FoundThe stránku nelze zpracovat kvůli konfiguraci rozšíření. Pokud je stránce skript, přidejte obslužnou rutinu. Pokud by měl být soubor stažen, přidejte mapování dat MIME. Iisver InformationModule podrobné informace o chybě.  
  
2.  [Pokud klient nečinný nějakou dobu, po prvním požadavku se někdy zobrazí messagesecurityexception – na druhý žádosti. Co se děje?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q1)  
  
3.  [Moje služba začne odmítnout nové klienty po asi 10 klienti komunikují s ním. Co se děje?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q2)  
  
4.  [Můžete načíst Moje konfigurace služby z jinde, než konfigurační soubor WCF aplikace?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q3)  
  
5.  [Moje služba a klient pracovní velká, ale I nelze získat nich mohli pracovat, když se klient nachází v jiném počítači? Co se děje?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q4)  
  
6.  [I když throw FaultException\<výjimka > typ jsou výjimku, bylo vždycky přijímat obecného typu FaultException na straně klienta a není obecného typu. Co se děje?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q5)  
  
7.  [Podle všeho jako jednosměrný a operace požadavek odpověď vracet přibližně stejnou rychlostí odpověď neobsahuje žádná data. Co se děje?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q6)  
  
8.  [Používám certifikát X.509 s mé služby a získat System.Security.Cryptography.CryptographicException. Co se děje?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q77)  
  
9. [První parametr operace bylo změněno z velkých písmen na malá písmena; Teď Moje klienta vyvolá výjimku. Co se děje?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q88)  
  
10. [Používám jeden z mých trasování nástrojů a získat endpointnotfoundexception –. Co se děje?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q99)  
  
11. [Při volání z aplikace WCF SOAP služby WCF Web HTTP aplikace vrátí následující chybu: není povoleno 405 – Metoda](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BK_MK99)  
  
 [Co je základní adresa? Jak vztahují k adresu koncového bodu?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q10)  
  
<a name="bkmk_0"></a>   
## <a name="after-installing-windows-7-and-iis-when-i-attempt-to-browse-to-a-wcf-service-i-get-the-following-error-message-http-error-4043--not-found"></a>Po instalaci systému Windows 7 a IIS, při pokusu o přejděte do služby WCF zobrazí následující chybová zpráva: HTTP Chyba 404.3 – nebyla nalezena  
 Je celá chybová zpráva:  
  
 Chyba protokolu HTTP 404.3 – není FoundThe stránku nelze zpracovat kvůli konfiguraci rozšíření. Pokud je stránce skript, přidejte obslužnou rutinu. Pokud by měl být soubor stažen, přidejte mapování dat MIME. Iisver InformationModule podrobné informace o chybě.  
  
 Tato chybová zpráva nastane, když "Windows Communication Foundation HTTP aktivace" není explicitně nastavena v Ovládacích panelech. Nastavit tento přejděte na ovládacích panelech, klikněte v levém dolním rohu okna programy. Zapnout nebo vypnout, klikněte na možnost zapnout funkce systému Windows. Rozhraní Microsoft .NET Framework 3.5.1 rozbalte a vyberte aktivace Windows Communication Foundation HTTP.  
  
<a name="BKMK_q1"></a>   
## <a name="sometimes-i-receive-a-messagesecurityexception-on-the-second-request-if-my-client-is-idle-for-a-while-after-the-first-request-what-is-happening"></a>Pokud klient nečinný nějakou dobu, po prvním požadavku se někdy zobrazí messagesecurityexception – na druhý žádosti. Co se děje?  
 Druhá žádost neúspěšně především dvou důvodů: Vypršel časový limit relace (1) nebo (2) je webový server, který je hostitelem služby je recykluje. V prvním případě relace je platný, dokud služba vyprší časový limit. Když službu neobdrží žádost od klienta v rámci doba zadaná v vazby služby (<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>), služba ukončuje relaci zabezpečení. Výsledkem zprávy následné klienta <xref:System.ServiceModel.Security.MessageSecurityException>. Klient musí znovu vytvořit relaci zabezpečené službou odeslat další zprávy nebo použijte tokenu kontextu stavová zabezpečení. Tokeny kontextu zabezpečení stavová také povolit zabezpečené relace zůstanou zachovány i recyklovány webového serveru. Další informace o používání tokenů stavová kontextu zabezpečení v zabezpečené relaci najdete v tématu [postupy: vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md). Alternativně můžete zakázat zabezpečených relací. Při použití [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) vazby, můžete nastavit `establishSecurityContext` vlastnost `false` zakázání zabezpečených relací. Zakázání zabezpečených relací u dalších vazeb, musíte vytvořit vlastní vazby. Podrobnosti o vytváření vlastních vazeb najdete v tématu [postupy: vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md). Než použijete některý z těchto možností, musíte pochopit požadavky na zabezpečení vaší aplikace.  
  
<a name="BKMK_q2"></a>   
## <a name="my-service-starts-to-reject-new-clients-after-about-10-clients-are-interacting-with-it-what-is-happening"></a>Moje služba začne odmítnout nové klienty po asi 10 klienti komunikují s ním. Co se děje?  
 Ve výchozím nastavení služby může mít jenom 10 souběžných relací. Proto pokud vazby služby použít relací, služba přijímá nová připojení klienta dokud nedosáhne počet, po jejímž uplynutí odmítne nová připojení klienta až jeden z konců aktuální relace. Může podporovat více klientů v několika způsoby. Pokud vaše služba nevyžaduje relací, nepoužívejte vazbu relacemi. (Další informace najdete v tématu [pomocí relace](../../../docs/framework/wcf/using-sessions.md).) Další možností je zvýšení limitu relace tak, že změníte hodnotu <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> vlastnost na číslo, které jsou vhodné pro vaše okolnosti.  
  
<a name="BKMK_q3"></a>   
## <a name="can-i-load-my-service-configuration-from-somewhere-other-than-the-wcf-applications-configuration-file"></a>Můžete načíst Moje konfigurace služby z jinde, než konfigurační soubor WCF aplikace?  
 Ano, ale je nutné vytvořit vlastní <xref:System.ServiceModel.ServiceHost> třídu, která přepisuje <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> metoda. Uvnitř této metody můžete volat základní nejdřív načíst konfiguraci (Pokud chcete načíst informace o standardní konfiguraci i), ale můžete také úplně nahradit konfigurace načítání systému. Všimněte si, že pokud chcete načíst konfiguraci z konfiguračního souboru, který se liší od konfiguračního souboru aplikace, musíte analyzovat konfigurační soubor a načíst konfiguraci.  
  
 Následující příklad kódu ukazuje, jak lze přepsat <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> metoda a přímo konfigurace koncového bodu.  
  
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
## <a name="my-service-and-client-work-great-but-i-cant-get-them-to-work-when-the-client-is-on-another-computer-whats-happening"></a>Moje služba a klient pracovní velká, ale I nelze získat nich mohli pracovat, když se klient nachází v jiném počítači? Co se děje?  
 V závislosti na výjimku, může existovat několik výhrad:  
  
-   Možná budete muset změňte adresy koncových bodů klienta na název hostitele a není "localhost".  
  
-   Možná budete muset otevřít port, který se aplikace. Podrobnosti najdete v tématu [pokyny k bráně Firewall](../../../docs/framework/wcf/samples/firewall-instructions.md) z ukázky SDK.  
  
-   Další možných problémů naleznete v tématu ukázky [spuštění ukázky v pracovní skupině a počítačů přes](http://msdn.microsoft.com/library/a451a525-e7ce-452d-9da9-620221260113).  
  
-   Pokud je váš klient je pomocí pověření systému Windows a výjimky <xref:System.ServiceModel.Security.SecurityNegotiationException>, následujícím způsobem konfigurace protokolu Kerberos.  
  
    1.  Přidejte tato pověření identity do koncového bodu element v souboru App.config klienta:  
  
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
  
    2.  Spusťte službu vlastním hostováním pod účtem systému nebo NetworkService. Můžete spustit tento příkaz k vytvoření příkazové okno pod účtem System:  
  
        ```console
        at 12:36 /interactive "cmd.exe"  
        ```  
  
    3.  Hostování v části Internetovou informační služby (IIS), což, standardně používá účet služby (SPN) pro hlavní název služby.  
  
    4.  Zaregistrujte novou hlavního názvu služby k doméně pomocí nástroje SetSPN. Všimněte si, že musíte být správce domény, pokud to chcete provést.  
  
 Další informace o protokolu Kerberos najdete v tématu [zabezpečení koncepty používané ve službě WCF](../../../docs/framework/wcf/feature-details/security-concepts-used-in-wcf.md) a:  
  
-   [Ladění chyb u ověřování Windows](../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
  
-   [Registrace pomocí ovladače Http.sys hlavní názvy služby protokolu Kerberos](http://go.microsoft.com/fwlink/?LinkId=86943)  
  
-   [Vysvětlení protokolu Kerberos](http://go.microsoft.com/fwlink/?LinkId=86946)  
  
<a name="BKMK_q5"></a>   
## <a name="when-i-throw-a-faultexceptionexception-where-the-type-is-an-exception-i-always-receive-a-general-faultexception-type-on-the-client-and-not-the-generic-type-whats-happening"></a>I když throw FaultException\<výjimka > typ jsou výjimku, bylo vždycky přijímat obecného typu FaultException na straně klienta a není obecného typu. Co se děje?  
 Důrazně doporučujeme, abyste vytvořili vlastní vlastní chybové datový typ a prohlásí, že jako typ podrobností v vaše chyba – kontrakt. Důvodem je, že použití typů poskytované systémem výjimka:  
  
-   Vytvoří závislost na typ, který odebere jeden z největších výhod aplikace orientované na služby.  
  
-   Nelze závisí na výjimky serializaci standardním způsobem. Některé – jako <xref:System.Security.SecurityException>– nemusí být serializovatelný vůbec.  
  
-   Zpřístupní podrobnosti interní implementace klientům. Další informace najdete v tématu [zadání a zpracování chyb v kontraktech a službách](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
 Pokud ladíte aplikaci, ale může serializovat informace o výjimce a vrátí klientovi pomocí <xref:System.ServiceModel.Description.ServiceDebugBehavior> třídy.  
  
<a name="BKMK_q6"></a>   
## <a name="it-seems-like-one-way-and-request-reply-operations-return-at-roughly-the-same-speed-when-the-reply-contains-no-data-whats-happening"></a>Podle všeho jako jednosměrný a operace požadavek odpověď vracet přibližně stejnou rychlostí odpověď neobsahuje žádná data. Co se děje?  
 Určení, že operace je jedním ze způsobů pouze znamená, že operace kontrakt přijímá zprávy při zadávání a nevrací zprávu výstup. V [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], všechna volání vrátí, když se odchozí data byla zapsána na sítě, nebo je vyvolána výjimka. Jednosměrná operace fungují stejně a můžete vyvolají, pokud služba nemůže najít nebo blokovat, pokud služba není připraven na příjem dat ze sítě. Obvykle v [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], výsledkem je jednosměrný volání vrácením klientovi rychleji než požadavek odpověď; ale žádné podmínku, která zpomalí odesílání odchozí data v síti zpomalí Jednosměrná operace, jakož i operace požadavek odpověď. Další informace najdete v tématu [One-Way služby](../../../docs/framework/wcf/feature-details/one-way-services.md) a [přístup k službám pomocí klienta WCF](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md).  
  
<a name="BKMK_q77"></a>   
## <a name="im-using-an-x509-certificate-with-my-service-and-i-get-a-systemsecuritycryptographycryptographicexception-whats-happening"></a>Používám certifikát X.509 s mé služby a získat System.Security.Cryptography.CryptographicException. Co se děje?  
 K tomu obvykle dochází po změně uživatelský účet, pod kterým služba IIS pracovní proces běží. Například v [!INCLUDE[wxp](../../../includes/wxp-md.md)], pokud změníte výchozí uživatelský účet, který Aspnet_wp.exe spouští pod z ASPNET na vlastní uživatelský účet, se zobrazí tato chyba. Pokud používáte privátní klíč, proces, který používá je potřeba mít oprávnění pro přístup k souboru ukládání klíči.  
  
 Pokud je to tento případ, musí udělit přístup pro čtení oprávnění k účtu procesu pro soubor obsahující privátní klíč. Například pokud pracovní proces služby IIS běží pod účtem Bob, pak musíte poskytnout přístup pro čtení Bob k souboru, který obsahuje soukromý klíč.  
  
 Další informace o tom, jak poskytnout správné uživatelský účet přístup k souboru, který obsahuje soukromý klíč pro konkrétní certifikát X.509 najdete v tématu [postup: usnadnit X.509 certifikáty přístup do WCF](../../../docs/framework/wcf/feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md).  
  
<a name="BKMK_q88"></a>   
## <a name="i-changed-the-first-parameter-of-an-operation-from-uppercase-to-lowercase-now-my-client-throws-an-exception-whats-happening"></a>První parametr operace bylo změněno z velkých písmen na malá písmena; Teď Moje klienta vyvolá výjimku. Co se děje?  
 Hodnota názvy parametrů v podpis operace jsou součástí kontraktu a malých a velkých písmen. Použití <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> atribut až budete potřebovat k rozlišení názvu parametru místní a metadata, která popisuje operaci pro klientské aplikace.  
  
<a name="BKMK_q99"></a>   
## <a name="im-using-one-of-my-tracing-tools-and-i-get-an-endpointnotfoundexception-whats-happening"></a>Používám jeden z mých trasování nástrojů a získat endpointnotfoundexception –. Co se děje?  
 Pokud používáte nástroj trasování, který není poskytované systémem [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] mechanismus trasování a zobrazí se <xref:System.ServiceModel.EndpointNotFoundException> určující, že došlo neshodě adres filtru, budete muset použít <xref:System.ServiceModel.Description.ClientViaBehavior> třída směrovat zprávy, které mají trasování nástroje a mít nástroj přesměruje tyto zprávy na adresu služby. <xref:System.ServiceModel.Description.ClientViaBehavior> Třída mění `Via` indikován adresování záhlaví zadat další síťová adresa odděleně od ultimate příjemce, `To` adresování záhlaví. Pokud v takovém případě však neměňte adresa koncového bodu, který se používá k navázání `To` hodnotu.  
  
 Následující příklad kódu ukazuje klientem příklad konfiguračního souboru.  
  
```xml
<endpoint   
  address=http://localhost:8000/MyServer/  
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
## <a name="what-is-the-base-address-how-does-it-relate-to-an-endpoint-address"></a>Co je základní adresa? Jak vztahují k adresu koncového bodu?  
 Základní adresa je adresa kořenové pro <xref:System.ServiceModel.ServiceHost> třídy. Ve výchozím nastavení, pokud přidáte <xref:System.ServiceModel.Description.ServiceMetadataBehavior> třídy do konfigurace služby webové služby popis Language (WSDL) pro hostitele publikuje všechny koncové body jsou načteny z základní adresu HTTP plus všechny relativní adresa zadaná v chování metadat plus "? wsdl". Pokud jste se seznámili s [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] a služby IIS, základní adresa je ekvivalentní do virtuálního adresáře.  
  
## <a name="sharing-a-port-between-a-service-endpoint-and-a-mex-endpoint-using-the-nettcpbinding"></a>Sdílení portů mezi koncového bodu služby a koncový bod mex pomocí NetTcpBinding  
 Pokud zadáte adresu základní pro služby jako net.tcp://MyServer: 8080/Moje_služba a přidejte následující koncové body:  
  
```xml  
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
 A pokud změníte jedno z nastavení NetTcpBinding jak je znázorněno v následujícím fragmentu kódu konfigurace:  
  
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
  
 Zobrazí se chyba takto: neošetřená výjimka: System.ServiceModel.AddressAlreadyInUseException: na 0.0.0.0:9000 koncový bod IP tuto chybu můžete vyřešit tak, že zadáte plně kvalifikovanou adresu URL s jiným portem pro je již naslouchací proces MEX endpoint, jak je znázorněno v následujícím fragmentu kódu konfigurace:  
  
```xml
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="net.tcp://localhost:9001/servicemodelsamples/mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
<a name="BK_MK99"></a>   
## <a name="when-calling-a-wcf-web-http-application-from-a-wcf-soap-application-the-service-returns-the-following-error-405-method-not-allowed"></a>Při volání z aplikace WCF SOAP služby WCF Web HTTP aplikace vrátí následující chybu: není povoleno 405 – Metoda  
 Volání aplikace WCF Web HTTP (služba, která využívá <xref:System.ServiceModel.WebHttpBinding> a <xref:System.ServiceModel.Description.WebHttpBehavior>) z službou WCF služba může generovat následující výjimky: `Unhandled Exception: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: vzdálený server vrátil neočekávanou odpověď : (405) metoda není povoleno. ", protože WCF přepíše odchozích došlo k této výjimce <xref:System.ServiceModel.OperationContext> s příchozí <xref:System.ServiceModel.OperationContext>. Chcete-li vyřešit tento problém vytvořit <xref:System.ServiceModel.OperationContextScope> v rámci operace služby WCF Web HTTP. Příklad:  
  
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
 [Ladění chyb u ověřování Windows](../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)
