---
title: Řešení potíží s WCF – úvodní příručka
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], troubleshooting
- Windows Communication Foundation [WCF], troubleshooting
ms.assetid: a9ea7a53-f31a-46eb-806e-898e465a4992
ms.openlocfilehash: f85d37fde19767d7fd1e3002776b4816666cc7e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183046"
---
# <a name="wcf-troubleshooting-quickstart"></a>Řešení potíží s WCF – úvodní příručka
Toto téma uvádí řadu známých problémů, které zákazníci narazili při vývoji klientů wcf a služeb. Pokud problém, do který pracujete, není v tomto seznamu, doporučujeme nakonfigurovat trasování pro vaši službu. Tím se vygeneruje trasovací soubor, který můžete zobrazit pomocí prohlížeče trasovacích souborů, a získáte podrobné informace o výjimkách, ke kterým může v rámci služby dostat. Další informace o konfiguraci trasování naleznete v [tématu: Konfigurace trasování](./diagnostics/tracing/configuring-tracing.md). Další informace o prohlížeči trasovacích souborů naleznete v [tématu: Service Trace Viewer Tool (SvcTraceViewer.exe)](service-trace-viewer-tool-svctraceviewer-exe.md).  
  
1. [Po instalaci systému Windows 7 a služby IIS se při pokusu o přechod na službu WCF zobrazí následující chybová zpráva: Chyba PROTOKOLU HTTP 404.3 – nebyl nalezen](#bkmk_0)  
  
     Chyba protokolu HTTP 404.3 – nebyla nalezenaStránka, kterou požadujete, nemůže být obsluhována z důvodu konfigurace rozšíření. Pokud je stránka skript, přidejte obslužnou rutinu. Pokud by měl být soubor stažen, přidejte mapu MIME. Podrobné informace o chyběModul StaticFileModule.  
  
2. [Někdy obdržím MessageSecurityException na druhý požadavek, pokud můj klient je nečinný na chvíli po první požadavek. Co se děje?](#BKMK_q1)  
  
3. [Moje služba začne odmítat nové klienty poté, co s ní spolupracuje asi 10 klientů. Co se děje?](#BKMK_q2)  
  
4. [Je možné načíst konfiguraci služby z jiného místa než z konfiguračního souboru aplikace WCF?](#BKMK_q3)  
  
5. [Moje služba a klient fungují skvěle, ale nemohu je dostat do práce, když je klient na jiném počítači? Co se děje?](#BKMK_q4)  
  
6. [Při vyvolání FaultException\<Exception>, kde typ je výjimka, vždy obdrží obecný FaultException typ na straně klienta a nikoli obecný typ. Co se děje?](#BKMK_q5)  
  
7. [Zdá se, že jednosměrné operace a operace požadavku a odpovědi se vrátí přibližně stejnou rychlostí, když odpověď neobsahuje žádná data. Co se děje?](#BKMK_q6)  
  
8. [Používám certifikát X.509 se svou službou a dostanu System.Security.Cryptography.CryptographicException. Co se děje?](#BKMK_q77)  
  
9. [Změnil jsem první parametr operace z velkých na malá písmena; Teď můj klient vyvolá výjimku. Co se děje?](#BKMK_q88)  
  
10. [Používám jeden z mých nástrojů trasování a získají EndpointNotFoundException. Co se děje?](#BKMK_q99)  
  
11. [Při volání webové http aplikace WCF z aplikace WCF SOAP vrátí služba následující chybu: Metoda 405 není povolena.](#BK_MK99)  
  
 [Jaká je základní adresa? Jak souvisí s adresou koncového bodu?](#BKMK_q10)  
  
<a name="bkmk_0"></a>
## <a name="after-installing-windows-7-and-iis-when-i-attempt-to-browse-to-a-wcf-service-i-get-the-following-error-message-http-error-4043--not-found"></a>Po instalaci systému Windows 7 a služby IIS se při pokusu o přechod na službu WCF zobrazí následující chybová zpráva: Chyba PROTOKOLU HTTP 404.3 – nebyl nalezen  
 Úplná chybová zpráva je:  
  
 Chyba protokolu HTTP 404.3 – nebyla nalezenaStránka, kterou požadujete, nemůže být obsluhována z důvodu konfigurace rozšíření. Pokud je stránka skript, přidejte obslužnou rutinu. Pokud by měl být soubor stažen, přidejte mapu MIME. Podrobné informace o chyběModul StaticFileModule.  
  
 Tato chybová zpráva se zobrazí, pokud není v ovládacím panelu explicitně nastavena aktivace http služby Windows Communication Foundation. Chcete-li tuto možnost nastavit, přejděte do Ovládacích panelů, klepněte na položku Programy v levém dolním rohu okna. Klikněte na Zapnout nebo vypnout funkce Windows. Rozbalte rozhraní Microsoft .NET Framework 3.5.1 a vyberte aktivaci protokolu HTTP nadace Windows Communication Foundation.  
  
<a name="BKMK_q1"></a>
## <a name="sometimes-i-receive-a-messagesecurityexception-on-the-second-request-if-my-client-is-idle-for-a-while-after-the-first-request-what-is-happening"></a>Někdy obdržím MessageSecurityException na druhý požadavek, pokud můj klient je nečinný na chvíli po první požadavek. Co se děje?  
 Druhý požadavek může selhat především ze dvou důvodů: (1) relace časový mat nebo (2) webový server, který je hostitelem služby je recyklován. V prvním případě je relace platná, dokud nevyjde časový čas služby. Pokud služba neobdrží požadavek od klienta ve lhůtě určené ve<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>vazbě služby ( ), služba ukončí relaci zabezpečení. Následné klientské zprávy <xref:System.ServiceModel.Security.MessageSecurityException>za následek . Klient musí znovu vytvořit zabezpečené relace se službou k odesílání budoucích zpráv nebo použít stavový token kontextu zabezpečení. Stavové kontextové tokeny zabezpečení také umožňují zabezpečené relaci přežít recyklovaný webový server. Další informace o použití stavových tokenů zabezpečeného kontextu v zabezpečené relaci naleznete v tématu [How to: Create a Security Context Token for a Secure Session](./feature-details/how-to-create-a-security-context-token-for-a-secure-session.md). Můžete také zakázat zabezpečené relace. Při použití [ \<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) vazba, `establishSecurityContext` můžete `false` nastavit vlastnost zakázat zabezpečené relace. Chcete-li zakázat zabezpečené relace pro jiné vazby, musíte vytvořit vlastní vazbu. Podrobnosti o vytvoření vlastní vazby naleznete v [tématu Postup: Vytvoření vlastní vazby pomocí SecurityBindingElement](./feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md). Před použitím některé z těchto možností je nutné pochopit požadavky na zabezpečení aplikace.  
  
<a name="BKMK_q2"></a>
## <a name="my-service-starts-to-reject-new-clients-after-about-10-clients-are-interacting-with-it-what-is-happening"></a>Moje služba začne odmítat nové klienty poté, co s ní spolupracuje asi 10 klientů. Co se děje?  
 Ve výchozím nastavení mohou mít služby pouze 10 souběžných relací. Proto pokud vazby služby používají relace, služba přijímá nová připojení klientů, dokud nedosáhne tohoto čísla, po kterém odmítne nová připojení klienta, dokud jedna z aktuálních relací neskončí. Můžete podporovat více klientů v mnoha způsoby. Pokud vaše služba nevyžaduje relace, nepoužívejte sessionful vazbu. (Další informace naleznete v tématu [Použití relací](using-sessions.md).) Další možností je zvýšit limit relace změnou <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> hodnoty vlastnosti na číslo odpovídající vaší situaci.  
  
<a name="BKMK_q3"></a>
## <a name="can-i-load-my-service-configuration-from-somewhere-other-than-the-wcf-applications-configuration-file"></a>Je možné načíst konfiguraci služby z jiného místa než z konfiguračního souboru aplikace WCF?  
 Ano, ale musíte vytvořit vlastní <xref:System.ServiceModel.ServiceHost> třídu, <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> která přepíše metodu. Uvnitř této metody můžete nejprve zavolat základnu pro načtení konfigurace (pokud chcete také načíst standardní informace o konfiguraci), ale můžete také zcela nahradit systém načítání konfigurace. Pokud chcete načíst konfiguraci z konfiguračního souboru, který se liší od konfiguračního souboru aplikace, musíte analyzovat konfigurační soubor sami a načíst konfiguraci.  
  
 Následující příklad kódu ukazuje, jak <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> přepsat metodu a přímo nakonfigurovat koncový bod.  
  
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
## <a name="my-service-and-client-work-great-but-i-cant-get-them-to-work-when-the-client-is-on-another-computer-whats-happening"></a>Moje služba a klient fungují skvěle, ale nemohu je dostat do práce, když je klient na jiném počítači? Co se děje?  
 V závislosti na výjimce může existovat několik problémů:  
  
- Možná budete muset změnit adresy koncového bodu klienta na název hostitele a ne "localhost".  
  
- Je možné, že bude nutné otevřít port aplikace. Podrobnosti naleznete v tématu [Pokyny brány firewall](./samples/firewall-instructions.md) z ukázky sady SDK.  
  
- Další možné problémy naleznete v tématu ukázky [spuštění ukázky Windows Communication Foundation](./samples/running-the-samples.md).  
  
- Pokud váš klient používá pověření systému <xref:System.ServiceModel.Security.SecurityNegotiationException>Windows a výjimkou je , nakonfigurujte protokol Kerberos následujícím způsobem.  
  
    1. Přidejte pověření identity do prvku koncového bodu v souboru App.config klienta:  
  
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
  
    2. Spusťte samoobslužnou službu pod účtem System nebo NetworkService. Tento příkaz můžete spustit a vytvořit příkazové okno pod systémovým účtem:  
  
        ```console
        at 12:36 /interactive "cmd.exe"  
        ```  
  
    3. Hostuj službu v rámci Internetové informační služby (IIS), která ve výchozím nastavení používá hlavní název služby (SPN).  
  
    4. Zaregistrujte nový hlavní název služby s doménou pomocí sady SetSPN. Chcete-li to provést, musíte být správcem domény.  
  
 Další informace o protokolu Kerberos naleznete [v tématu Koncepty zabezpečení používané v wcf](./feature-details/security-concepts-used-in-wcf.md) a:  
  
- [Ladění chyb u ověřování Windows](./feature-details/debugging-windows-authentication-errors.md)  
  
- [Registrace hlavních názvů služeb protokolu Kerberos pomocí souboru Http.sys](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms178119(v=sql.105))  
  
- [Kerberos vysvětlil](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-2000-server/bb742516(v%3dtechnet.10))  
  
<a name="BKMK_q5"></a>
## <a name="when-i-throw-a-faultexceptionexception-where-the-type-is-an-exception-i-always-receive-a-general-faultexception-type-on-the-client-and-not-the-generic-type-whats-happening"></a>Při vyvolání FaultException\<Exception>, kde typ je výjimka, vždy obdrží obecný FaultException typ na straně klienta a nikoli obecný typ. Co se děje?  
 Důrazně doporučujeme vytvořit vlastní datový typ vlastní chyby a deklarovat, že jako typ podrobností ve smlouvě o chybě. Důvodem je, že pomocí systémem poskytované typy výjimek:  
  
- Vytvoří typ závislost, která odebere jednu z největších silných stránek aplikací orientovaných na služby.  
  
- Nelze záviset na výjimkách serializace standardním způsobem. Některé – <xref:System.Security.SecurityException>jako – nemusí být vůbec serializovatelné.  
  
- Zpřístupní klientům podrobnosti interní implementace. Další informace naleznete [v tématu Určení a zpracování chyb ve smlouvách a službách](specifying-and-handling-faults-in-contracts-and-services.md).  
  
 Pokud však ladíte aplikaci, můžete serializovat informace o výjimce a <xref:System.ServiceModel.Description.ServiceDebugBehavior> vrátit je klientovi pomocí třídy.  
  
<a name="BKMK_q6"></a>
## <a name="it-seems-like-one-way-and-request-reply-operations-return-at-roughly-the-same-speed-when-the-reply-contains-no-data-whats-happening"></a>Zdá se, že jednosměrné operace a operace požadavku a odpovědi se vrátí přibližně stejnou rychlostí, když odpověď neobsahuje žádná data. Co se děje?  
 Určení, že operace je jedním ze způsobů, znamená pouze to, že kontrakt operace přijme vstupní zprávu a nevrátí výstupní zprávu. V WCF všechna vyvolání klienta vrátit při odchozí data byla zapsána do drátu nebo je vyvolána výjimka. Jednosměrné operace fungují stejným způsobem a mohou vyvolat, pokud službu nelze nalézt nebo blokovat, pokud služba není připravena přijmout data ze sítě. Obvykle v WCF, to má za následek jednosměrné volání návratu klientovi rychleji než požadavek odpověď; ale všechny podmínky, které zpomaluje odesílání odchozích dat v síti zpomaluje jednosměrné operace, jakož i operace požadavku a odpovědi. Další informace naleznete [v tématu Jednosměrné služby](./feature-details/one-way-services.md) a [přístup ke službám pomocí wcf klienta](./feature-details/accessing-services-using-a-client.md).  
  
<a name="BKMK_q77"></a>
## <a name="im-using-an-x509-certificate-with-my-service-and-i-get-a-systemsecuritycryptographycryptographicexception-whats-happening"></a>Používám certifikát X.509 se svou službou a dostanu System.Security.Cryptography.CryptographicException. Co se děje?  
 K tomu obvykle dochází po změně uživatelského účtu, pod kterým je spuštěn pracovní proces iis. Pokud například v systému Windows XP změníte výchozí uživatelský účet, pod kterým je Aspnet_wp.exe spuštěn z prostředí ASPNET na vlastní uživatelský účet, může se zobrazit tato chyba. Pokud používáte soukromý klíč, proces, který jej používá, bude muset mít oprávnění pro přístup k souboru, který tento klíč ukládá.  
  
 V takovém případě je nutné udělit oprávnění pro přístup ke čtení k účtu procesu pro soubor obsahující soukromý klíč. Pokud je například pracovní proces služby IIS spuštěn pod účtem Bob, budete muset udělit Petrovi přístup pro čtení k souboru obsahujícímu soukromý klíč.  
  
 Další informace o tom, jak udělit správný uživatelský účet přístup k souboru, který obsahuje soukromý klíč pro konkrétní certifikát X.509, naleznete v [tématu How to: Make X.509 Certificates Accessible to WCF](./feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md).  
  
<a name="BKMK_q88"></a>
## <a name="i-changed-the-first-parameter-of-an-operation-from-uppercase-to-lowercase-now-my-client-throws-an-exception-whats-happening"></a>Změnil jsem první parametr operace z velkých na malá písmena; Teď můj klient vyvolá výjimku. Co se děje?  
 Hodnoty názvů parametrů v podpisu operace jsou součástí smlouvy a rozlišují malá a velká písmena. Atribut <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> použijte, pokud potřebujete rozlišovat mezi názvem místního parametru a metadaty, která popisují operaci pro klientské aplikace.  
  
<a name="BKMK_q99"></a>
## <a name="im-using-one-of-my-tracing-tools-and-i-get-an-endpointnotfoundexception-whats-happening"></a>Používám jeden z mých nástrojů trasování a získají EndpointNotFoundException. Co se děje?  
 Pokud používáte nástroj trasování, který není systémem poskytované WCF trasování <xref:System.ServiceModel.EndpointNotFoundException> mechanismus a obdržíte, který označuje, že došlo <xref:System.ServiceModel.Description.ClientViaBehavior> k neshodě filtru adresy, je třeba použít třídu k přesměrování zprávy na nástroj pro trasování a nástroj přesměrovat tyto zprávy na adresu služby. Třída <xref:System.ServiceModel.Description.ClientViaBehavior> změní `Via` adresování záhlaví určit další síťovou adresu odděleně od konečného `To` příjemce, označené adresování záhlaví. Při této této, ale neměňte adresu koncového bodu, který se používá k vytvoření `To` hodnoty.  
  
 Následující příklad kódu ukazuje ukázkový konfigurační soubor klienta.  
  
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
## <a name="what-is-the-base-address-how-does-it-relate-to-an-endpoint-address"></a>Jaká je základní adresa? Jak souvisí s adresou koncového bodu?  
 Základní adresa je kořenová <xref:System.ServiceModel.ServiceHost> adresa třídy. Ve výchozím nastavení, <xref:System.ServiceModel.Description.ServiceMetadataBehavior> pokud přidáte třídu do konfigurace služby, jazyk popisu webových služeb (WSDL) pro všechny koncové body, které hostitel publikuje, se načte ze základní adresy HTTP plus jakákoli relativní adresa poskytnutá chování metadat plus "?wsdl". Pokud jste obeznámeni s ASP.NET a službou IIS, základní adresa je ekvivalentní virtuálnímu adresáři.  
  
## <a name="sharing-a-port-between-a-service-endpoint-and-a-mex-endpoint-using-the-nettcpbinding"></a>Sdílení portu mezi koncovým bodem služby a koncovým bodem mex pomocí nettcpbinding  
 Pokud zadáte základní adresu služby jako net.tcp://MyServer:8080/MyService a přidáte následující koncové body:  
  
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
  
 Zobrazí se chyba jako následující: Neošetřená výjimka: System.ServiceModel.AddressAlreadyInUseException: V koncovém bodě IP 0.0.0.0:9000 můžete tuto chybu obejít zadáním plně kvalifikované adresy URL s jiným portem pro koncového bodu MEX, jak je znázorněno v následujícím fragmentu konfigurace:  
  
```xml
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="net.tcp://localhost:9001/servicemodelsamples/mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
<a name="BK_MK99"></a>
## <a name="when-calling-a-wcf-web-http-application-from-a-wcf-soap-application-the-service-returns-the-following-error-405-method-not-allowed"></a>Při volání webové http aplikace WCF z aplikace WCF SOAP vrátí služba následující chybu: Metoda 405 není povolena.  
 Volání aplikace <xref:System.ServiceModel.WebHttpBinding> WCF Web HTTP (služba, <xref:System.ServiceModel.Description.WebHttpBehavior>která používá a ) ze služby WCF může generovat následující výjimku: ``Unhandled Exception: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: The remote server returned an unexpected response: (405) Method Not Allowed.`` K této výjimce dochází, protože WCF přepíše odchozí <xref:System.ServiceModel.OperationContext> s příchozí <xref:System.ServiceModel.OperationContext>. Chcete-li tento problém <xref:System.ServiceModel.OperationContextScope> vyřešit, vytvořte operaci služby WCF Web HTTP. Například:  
  
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
