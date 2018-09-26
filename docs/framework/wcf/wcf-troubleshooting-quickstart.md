---
title: Řešení potíží s WCF – úvodní příručka
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], troubleshooting
- Windows Communication Foundation [WCF], troubleshooting
ms.assetid: a9ea7a53-f31a-46eb-806e-898e465a4992
ms.openlocfilehash: 368faf0881c5c0073fe8367a051b6c6c802b9110
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47200851"
---
# <a name="wcf-troubleshooting-quickstart"></a>Řešení potíží s WCF – úvodní příručka
Toto téma uvádí počet známé problémy, které mají zákazníci spouštět do při vývoji klientů WCF a služeb. Pokud se problém, který běží na není v tomto seznamu, doporučujeme že nakonfigurovat trasování pro vaši službu. Tím se vygeneruje soubor trasování, můžete zobrazit pomocí prohlížeče trasování souboru a získat podrobné informace o výjimkách, které může docházet v rámci služby. Další informace o konfiguraci trasování, naleznete v tématu: [Konfigurace trasování](../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md). Další informace o souboru prohlížeče trasování, naleznete v tématu: [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).  
  
1.  [Po instalaci Windows 7 a IIS se při pokusu přejděte na službu WCF zobrazila tato chybová zpráva: Chyba 404.3 HTTP – nebyl nalezen](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#bkmk_0)  
  
     Chyba protokolu HTTP 404.3 – Not FoundThe stránky, pro který žádáte nelze zpracovat z důvodu konfigurace rozšíření. Pokud na stránce je skript, přidejte obslužnou rutinu. Pokud mají být stažené souboru, přidejte mapování MIME. Iisver InformationModule podrobné informace o chybě.  
  
2.  [Někdy zobrazila messagesecurityexception – na druhou žádost, pokud klient je nečinný po nějakou dobu od prvního požadavku. Co se děje?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q1)  
  
3.  [Služba začne odmítnout nové klienty po přibližně 10 klientů jsou interakci s ní. Co se děje?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q2)  
  
4.  [Můžete načíst konfiguraci služby z jinde, než konfigurační soubor WCF aplikace?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q3)  
  
5.  [Služba a skvěle fungují klienta, ale nemůžu nelze získat pracovat nacházející se v jiném počítači? Co se děje?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q4)  
  
6.  [Kdy můžu výjimku FaultException\<výjimky > tam, kde je typ výjimky, vždy zobrazila se obecným typem FaultException v klientském počítači a ne obecného typu. Co se děje?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q5)  
  
7.  [To vypadá jako jsou jednosměrná a operace požadavek odpověď vracet rychlostí přibližně stejnou odpověď neobsahuje žádná data. Co se děje?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q6)  
  
8.  [Používám certifikát X.509 pomocí svojí služby a získat System.Security.Cryptography.CryptographicException. Co se děje?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q77)  
  
9. [Můžu změnit první parametr operace z velkých písmen na malá písmena; Klient teď dojde k výjimce. Co se děje?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q88)  
  
10. [Používám jedním z nástrojů Moje trasování a získat endpointnotfoundexception –. Co se děje?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q99)  
  
11. [Při volání webových služeb HTTP WCF aplikace z aplikace WCF SOAP služby vrátí následující chybu: není povoleno 405 – Metoda](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BK_MK99)  
  
 [Co je základní adresa? Jak to souvisí adresy koncového bodu?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q10)  
  
<a name="bkmk_0"></a>   
## <a name="after-installing-windows-7-and-iis-when-i-attempt-to-browse-to-a-wcf-service-i-get-the-following-error-message-http-error-4043--not-found"></a>Po instalaci Windows 7 a IIS se při pokusu přejděte na službu WCF zobrazila tato chybová zpráva: Chyba 404.3 HTTP – nebyl nalezen  
 Je úplné chybová zpráva:  
  
 Chyba protokolu HTTP 404.3 – Not FoundThe stránky, pro který žádáte nelze zpracovat z důvodu konfigurace rozšíření. Pokud na stránce je skript, přidejte obslužnou rutinu. Pokud mají být stažené souboru, přidejte mapování MIME. Iisver InformationModule podrobné informace o chybě.  
  
 Této chybě dochází, když "Windows Communication Foundation HTTP aktivace" není explicitně nastavena v Ovládacích panelech. Pokud chcete nastavit přejděte do ovládacích panelů, klikněte na programy v dolním levém dolním rohu okna. Zapnutí nebo vypnutí, klikněte na zapnout Windows funkce. Rozhraní Microsoft .NET Framework 3.5.1 rozbalte a vyberte aktivace protokolu HTTP Windows Communication Foundation.  
  
<a name="BKMK_q1"></a>   
## <a name="sometimes-i-receive-a-messagesecurityexception-on-the-second-request-if-my-client-is-idle-for-a-while-after-the-first-request-what-is-happening"></a>Někdy zobrazila messagesecurityexception – na druhou žádost, pokud klient je nečinný po nějakou dobu od prvního požadavku. Co se děje?  
 Druhou žádost může selhat především pro dva důvody: Vypršel časový limit relace (1) nebo (2) na webový server, který je hostitelem služby recykluje. V prvním případě relace je platné, dokud služba vyprší časový limit. Když služba neobdrží žádost o z klienta v době, zadaná ve vazbě služby (<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>), služba ukončuje relace zabezpečení. Výsledkem zpráv následné klienta <xref:System.ServiceModel.Security.MessageSecurityException>. Klient musí znovu vytvořit relaci zabezpečení ve službě odeslat další zprávy nebo použít token kontextu zabezpečení stavové. Tokeny kontextu zabezpečení stavové umožňují zabezpečenou relaci nezbytné k překonání neumožňovala recyklaci, webový server. Další informace o použití tokenů stavové zabezpečené kontextu v zabezpečené relaci v tématu [jak: vytvořit Token kontextu zabezpečení pro zabezpečenou relaci](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md). Alternativně můžete zakázat zabezpečených relací. Při použití [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) vazby, můžete nastavit `establishSecurityContext` vlastnost `false` zakázání zabezpečených relací. Zakázání zabezpečených relací u jiných vazeb, musíte vytvořit vlastní vazby. Podrobnosti o vytvoření vlastní vazby najdete v tématu [postupy: vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md). Než použijete některý z těchto možností, musíte pochopit požadavky na zabezpečení vaší aplikace.  
  
<a name="BKMK_q2"></a>   
## <a name="my-service-starts-to-reject-new-clients-after-about-10-clients-are-interacting-with-it-what-is-happening"></a>Služba začne odmítnout nové klienty po přibližně 10 klientů jsou interakci s ní. Co se děje?  
 Ve výchozím nastavení služby může mít jenom 10 souběžných relací. Proto pokud vazby služby použít relace, služba přijímá nová připojení klientů. dokud nebude dosaženo toto číslo, po jejímž uplynutí odmítne nová připojení klientů. dokud jeden z konců aktuální relace. Může podporovat více klientů v několika způsoby. Pokud vaše služba nevyžaduje žádné relace, nepoužívejte vazby s relacemi. (Další informace najdete v tématu [s využitím relací](../../../docs/framework/wcf/using-sessions.md).) Další možností je, aby zvýšil limit relace tak, že změníte hodnotu <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> vlastnost na číslo, které jsou vhodné pro vaši situaci.  
  
<a name="BKMK_q3"></a>   
## <a name="can-i-load-my-service-configuration-from-somewhere-other-than-the-wcf-applications-configuration-file"></a>Můžete načíst konfiguraci služby z jinde, než konfigurační soubor WCF aplikace?  
 Ano, ale je nutné vytvořit vlastní <xref:System.ServiceModel.ServiceHost> třídu, která přepíše <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> metody. Uvnitř této metody lze volat základní nejdřív načíst konfiguraci (Pokud chcete načíst informace o konfiguraci standardní i), ale můžete nahradit také zcela konfiguraci načítání systému. Všimněte si, že pokud chcete načíst konfiguraci z konfiguračního souboru, který se liší od konfiguračního souboru aplikace, musíte analyzovat konfigurační soubor a načíst konfiguraci.  
  
 Následující příklad kódu ukazuje, jak přepsat <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> metoda a přímo konfigurace koncového bodu.  
  
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
## <a name="my-service-and-client-work-great-but-i-cant-get-them-to-work-when-the-client-is-on-another-computer-whats-happening"></a>Služba a skvěle fungují klienta, ale nemůžu nelze získat pracovat nacházející se v jiném počítači? Co se děje?  
 V závislosti na výjimku, může existovat několik problémů:  
  
-   Můžete potřebovat změnit adresy koncových bodů klienta na název hostitele a není "localhost".  
  
-   Můžete potřebovat pro otevření portu pro aplikaci. Podrobnosti najdete v tématu [pokyny k bráně Firewall](../../../docs/framework/wcf/samples/firewall-instructions.md) z ukázky SDK.  
  
-   Další možné problémy, naleznete v tématu ukázky [spouštění ukázek v určité pracovní skupině a počítačů přes](https://msdn.microsoft.com/library/a451a525-e7ce-452d-9da9-620221260113).  
  
-   Pokud váš klient se pomocí přihlašovacích údajů Windows a je výjimka <xref:System.ServiceModel.Security.SecurityNegotiationException>, následujícím způsobem konfigurace protokolu Kerberos.  
  
    1.  Přidáte přihlašovací údaje identity na element koncového bodu v souboru App.config pro klienta:  
  
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
  
    2.  Spusťte službu v místním prostředí pomocí účtu systému nebo NetworkService. Můžete spustit tento příkaz vytvoří příkazové okno pod účtem systému:  
  
        ```console
        at 12:36 /interactive "cmd.exe"  
        ```  
  
    3.  Hostování služby v rámci formátu RTF (Internetová informační služba), která standardně používá účet (SPN) pro hlavní název služby.  
  
    4.  Nový název SPN zaregistrujte domény pomocí nástroje SetSPN. Všimněte si, že musíte být správcem domény, pokud to chcete udělat.  
  
 Další informace o protokolu Kerberos najdete v tématu [zabezpečení koncepty používané ve službě WCF](../../../docs/framework/wcf/feature-details/security-concepts-used-in-wcf.md) a:  
  
-   [Ladění chyb u ověřování Windows](../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
  
-   [Registrace pomocí Http.sys hlavní názvy služby protokolu Kerberos](https://go.microsoft.com/fwlink/?LinkId=86943)  
  
-   [Vysvětlení protokolu Kerberos](https://go.microsoft.com/fwlink/?LinkId=86946)  
  
<a name="BKMK_q5"></a>   
## <a name="when-i-throw-a-faultexceptionexception-where-the-type-is-an-exception-i-always-receive-a-general-faultexception-type-on-the-client-and-not-the-generic-type-whats-happening"></a>Kdy můžu výjimku FaultException\<výjimky > tam, kde je typ výjimky, vždy zobrazila se obecným typem FaultException v klientském počítači a ne obecného typu. Co se děje?  
 Důrazně doporučujeme vytvořit vlastní vlastní chybové datový typ a deklarovat, že jako typ podrobností ve vaší smlouvě selhání. Důvodem je, že pomocí typy poskytované systémem výjimek:  
  
-   Vytvoří závislost na typ, který odebere jeden z největších výhod aplikací orientovaných na služby.  
  
-   Nemohou záviset na výjimky serializace standardním způsobem. Některé – například <xref:System.Security.SecurityException>– nemusí být vůbec serializovatelný.  
  
-   Poskytuje podrobnosti interní implementace klientům. Další informace najdete v tématu [zadání a zpracování chyb v kontraktech a službách](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
 Pokud ladíte aplikaci, ale může serializovat informace o výjimce a vrátí klientovi pomocí <xref:System.ServiceModel.Description.ServiceDebugBehavior> třídy.  
  
<a name="BKMK_q6"></a>   
## <a name="it-seems-like-one-way-and-request-reply-operations-return-at-roughly-the-same-speed-when-the-reply-contains-no-data-whats-happening"></a>To vypadá jako jsou jednosměrná a operace požadavek odpověď vracet rychlostí přibližně stejnou odpověď neobsahuje žádná data. Co se děje?  
 Určení, že operace je jedním ze způsobů pouze znamená, že kontrakt přijímá vstupní zprávy a nevrací výstupní zprávu. Ve službě WCF všechna volání klienta vrátí, pokud byl zapsán do přenosu odchozích dat nebo dojde k výjimce. Jednosměrná operace pracovat stejným způsobem a generují výjimku-li služba nemůže najít nebo blokovat, pokud služba není připraven pro příjem dat ze sítě. Obvykle ve službě WCF, výsledkem je jednosměrná volání rychleji než požadavek odpověď, vrácením klientovi ale jakoukoli podmínku, která zpomaluje odesílání odchozích dat v síti, zpomalí jednocestné operace, jakož i operace požadavek odpověď. Další informace najdete v tématu [One-Way služby](../../../docs/framework/wcf/feature-details/one-way-services.md) a [přístup ke službám pomocí klienta WCF](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md).  
  
<a name="BKMK_q77"></a>   
## <a name="im-using-an-x509-certificate-with-my-service-and-i-get-a-systemsecuritycryptographycryptographicexception-whats-happening"></a>Používám certifikát X.509 pomocí svojí služby a získat System.Security.Cryptography.CryptographicException. Co se děje?  
 K tomu běžně dochází po změně uživatelský účet, pod kterým pracovní proces služby IIS běží. Například v [!INCLUDE[wxp](../../../includes/wxp-md.md)], pokud změníte výchozí uživatelský účet, který Aspnet_wp.exe běží pod z ASPNET vlastní uživatelský účet, může se zobrazit tato chyba. Pokud používáte privátní klíč, proces, který používá ho bude muset mít oprávnění pro přístup k souboru uložení tohoto klíče.  
  
 Pokud je to tento případ, je potřeba předat čtení přístupová oprávnění procesu účtu pro soubor, který obsahuje privátní klíč. Například pokud pracovní proces služby IIS běží pod účtem Bob, pak je potřeba poskytnout oprávnění ke čtení Bob k souboru, který obsahuje privátní klíč.  
  
 Další informace o tom, jak poskytnout přístup k účtu uživatele správný soubor, který obsahuje privátní klíč pro konkrétní certifikát X.509, naleznete v tématu [postup: Ujistěte se, X.509 certifikáty přístupné pro WCF](../../../docs/framework/wcf/feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md).  
  
<a name="BKMK_q88"></a>   
## <a name="i-changed-the-first-parameter-of-an-operation-from-uppercase-to-lowercase-now-my-client-throws-an-exception-whats-happening"></a>Můžu změnit první parametr operace z velkých písmen na malá písmena; Klient teď dojde k výjimce. Co se děje?  
 Hodnota názvy parametrů v signatuře operace jsou součástí kontraktu a jsou malá a velká písmena. Použití <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> atribut, pokud je potřeba rozlišovat mezi místní parametr name a metadat, který popisuje operace, která pro klientské aplikace.  
  
<a name="BKMK_q99"></a>   
## <a name="im-using-one-of-my-tracing-tools-and-i-get-an-endpointnotfoundexception-whats-happening"></a>Používám jedním z nástrojů Moje trasování a získat endpointnotfoundexception –. Co se děje?  
 Pokud používáte nástroj pro sledování, které nejsou poskytované systémem mechanismus trasování WCF a zobrazí se <xref:System.ServiceModel.EndpointNotFoundException> , která označuje, že došlo neshodě filtr adresy, budete muset použít <xref:System.ServiceModel.Description.ClientViaBehavior> třídy ke směrování zpráv do nástroj trasování a mají nástroje těchto zpráv přesměrování na adresu služby. <xref:System.ServiceModel.Description.ClientViaBehavior> Třídy mění `Via` indikován adresování záhlaví, chcete-li určit další síťová adresa odděleně od ultimate příjemce `To` adresování záhlaví. Při tomto postupu, ale neměňte adresu koncového bodu, který se používá k navázání `To` hodnotu.  
  
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
## <a name="what-is-the-base-address-how-does-it-relate-to-an-endpoint-address"></a>Co je základní adresa? Jak to souvisí adresy koncového bodu?  
 Základní adresa je adresa kořenové <xref:System.ServiceModel.ServiceHost> třídy. Ve výchozím nastavení, pokud chcete přidat <xref:System.ServiceModel.Description.ServiceMetadataBehavior> třídy do konfigurace služby, webové služby WSDL (Description Language) pro hostitele publikuje všechny koncové body jsou načteny z základní adresu HTTP, a navíc všechny relativní adresa zadaná metadata chování plus "? wsdl". Pokud jste se seznámili s [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] a služby IIS, základní adresa je ekvivalentní k virtuálnímu adresáři.  
  
## <a name="sharing-a-port-between-a-service-endpoint-and-a-mex-endpoint-using-the-nettcpbinding"></a>Sdílení portů mezi koncového bodu služby a koncového bodu mex pomocí NetTcpBinding  
 Pokud zadáte základní adresu pro službu jako net.tcp://MyServer: 8080/Moje_služba a přidat následující koncové body:  
  
```xml  
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
 A pokud změníte některé z nastavení NetTcpBinding jak je znázorněno v následujícím fragmentu kódu konfigurace:  
  
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
  
 Zobrazí se chyba podobný tomuto: neošetřená výjimka: System.ServiceModel.addressalreadyinuseexception –: na již běží naslouchací proces tuto chybu můžete vyřešit tak, že zadáte plně kvalifikovanou adresu URL s jiným portem pro 0.0.0.0:9000 koncový bod IP MEX endpoint, jak je znázorněno v následujícím fragmentu kódu konfigurace:  
  
```xml
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="net.tcp://localhost:9001/servicemodelsamples/mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
<a name="BK_MK99"></a>   
## <a name="when-calling-a-wcf-web-http-application-from-a-wcf-soap-application-the-service-returns-the-following-error-405-method-not-allowed"></a>Při volání webových služeb HTTP WCF aplikace z aplikace WCF SOAP služby vrátí následující chybu: není povoleno 405 – Metoda  
 Volání aplikace webových služeb HTTP WCF (služba, která se používá <xref:System.ServiceModel.WebHttpBinding> a <xref:System.ServiceModel.Description.WebHttpBehavior>) z WCF service může generovat následující výjimku: `Unhandled Exception: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: vzdálený server vrátil neočekávanou odpověď : (405) metoda není povoleno. "touto výjimkou způsobeno WCF přepíše odchozích dat <xref:System.ServiceModel.OperationContext> s příchozí <xref:System.ServiceModel.OperationContext>. Chcete-li vyřešit tento problém vytvořit <xref:System.ServiceModel.OperationContextScope> v rámci operace služby webových služeb HTTP WCF. Příklad:  
  
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
