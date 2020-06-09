---
title: Porovnání webových služeb ASP.NET Web Services s technologií WCF z hlediska vývojových požadavků
ms.date: 03/30/2017
ms.assetid: f362d00e-ce82-484f-9d4f-27e579d5c320
ms.openlocfilehash: c6e83bb234751dc477776f0fa540ffa8688dc667
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597589"
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-development"></a>Porovnání webových služeb ASP.NET Web Services s technologií WCF z hlediska vývojových požadavků

Windows Communication Foundation (WCF) má možnost režimu kompatibility ASP.NET, která umožňuje programové použití aplikací WCF a jejich konfiguraci, jako jsou webové služby ASP.NET, a napodobuje jejich chování. V následujících částech jsou porovnávány webové služby ASP.NET a WCF na základě toho, co je potřeba pro vývoj aplikací pomocí obou technologií.

## <a name="data-representation"></a>Reprezentace dat

Vývoj webové služby pomocí ASP.NET obvykle začíná definováním jakýchkoli složitých datových typů, které služba používá. ASP.NET spoléhá na rozhraní, <xref:System.Xml.Serialization.XmlSerializer> aby přeložilo data reprezentovaná .NET Framework typy do XML pro přenos do nebo ze služby a k překladu dat přijatých jako XML do objektů .NET Framework. Definování komplexních datových typů, které musí služba ASP.NET použít, vyžaduje definici .NET Framework třídy, které <xref:System.Xml.Serialization.XmlSerializer> může serializovat a z XML. Takové třídy lze zapsat ručně nebo vygenerovat z definic typů ve schématu XML pomocí nástroje příkazového řádku XML Schemas/data types support Utility, XSD. exe.

Následuje seznam klíčových problémů, které je potřeba znát při definování .NET Framework tříd, které <xref:System.Xml.Serialization.XmlSerializer> může serializovat do a z XML:

- Pouze veřejná pole a vlastnosti objektů .NET Framework jsou přeloženy do XML.

- Instance tříd kolekcí mohou být serializovány do XML pouze v případě, že třídy implementují <xref:System.Collections.IEnumerable> <xref:System.Collections.ICollection> rozhraní nebo.

- Třídy, které implementují <xref:System.Collections.IDictionary> rozhraní, například <xref:System.Collections.Hashtable> , se nedají SERIALIZOVAT do XML.

- Skvělé množství typů atributů v <xref:System.Xml.Serialization> oboru názvů lze přidat do .NET Framework třídy a jejích členů pro řízení, jak jsou instance třídy zastoupeny v XML.

Vývoj aplikací WCF obvykle začíná také definicí komplexních typů. WCF je možné použít pro použití stejných typů .NET Framework jako ASP.NET webové služby.

WCF <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> lze jej přidat do .NET Framework typů pro indikaci, že instance typu mají být serializovány do XML a které konkrétní pole nebo vlastnosti tohoto typu mají být serializovány, jak je znázorněno v následujícím ukázkovém kódu.

```csharp
//Example One:
[DataContract]
public class LineItem
{
    [DataMember]
    public string ItemNumber;
    [DataMember]
    public decimal Quantity;
    [DataMember]
    public decimal UnitPrice;
}

//Example Two:
public class LineItem
{
    [DataMember]
    private string itemNumber;
    [DataMember]
    private decimal quantity;
    [DataMember]
    private decimal unitPrice;

    public string ItemNumber
    {
      get
      {
          return this.itemNumber;
      }

      set
      {
          this.itemNumber = value;
      }
    }

    public decimal Quantity
    {
        get
        {
            return this.quantity;
        }

        set
        {
            this.quantity = value;
        }
    }

    public decimal UnitPrice
    {
      get
      {
          return this.unitPrice;
      }

      set
      {
          this.unitPrice = value;
      }
    }
}

//Example Three:
public class LineItem
{
     private string itemNumber;
     private decimal quantity;
     private decimal unitPrice;

     [DataMember]
     public string ItemNumber
     {
       get
       {
          return this.itemNumber;
       }

       set
       {
           this.itemNumber = value;
       }
     }

     [DataMember]
     public decimal Quantity
     {
          get
          {
              return this.quantity;
          }

          set
          {
             this.quantity = value;
          }
     }

     [DataMember]
     public decimal UnitPrice
     {
          get
          {
              return this.unitPrice;
          }

          set
          {
              this.unitPrice = value;
          }
     }
}
```

To <xref:System.Runtime.Serialization.DataContractAttribute> znamená, že nula nebo více polí nebo vlastností typu musí být serializován, zatímco <xref:System.Runtime.Serialization.DataMemberAttribute> vlastnost označuje, že konkrétní pole nebo vlastnost má být serializována. <xref:System.Runtime.Serialization.DataContractAttribute>Lze použít pro třídu nebo strukturu. <xref:System.Runtime.Serialization.DataMemberAttribute>Lze použít na pole nebo vlastnost a pole a vlastnosti, na které je atribut použit, mohou být buď veřejné, nebo soukromé. Instance typů, které mají <xref:System.Runtime.Serialization.DataContractAttribute> použitou, jsou v rámci WCF označovány jako kontrakty dat. Jsou serializovány do XML pomocí <xref:System.Runtime.Serialization.DataContractSerializer> .

Následuje seznam důležitých rozdílů mezi použitím <xref:System.Runtime.Serialization.DataContractSerializer> a pomocí <xref:System.Xml.Serialization.XmlSerializer> a různých atributů <xref:System.Xml.Serialization> oboru názvů.

- <xref:System.Xml.Serialization.XmlSerializer>A atributy <xref:System.Xml.Serialization> oboru názvů jsou navrženy tak, aby vám umožnily namapovat .NET Framework typy na libovolný platný typ definovaný ve schématu XML, a tak, aby poskytovaly velmi přesnou kontrolu nad tím, jak je typ REPREZENTOVÁN v XML. <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.DataContractAttribute> A <xref:System.Runtime.Serialization.DataMemberAttribute> poskytuje velmi malou kontrolu nad tím, jak je typ reprezentován v XML. Můžete zadat pouze obory názvů a názvy používané pro reprezentaci typu a jeho polí nebo vlastností v XML a pořadí, ve kterém se pole a vlastnosti zobrazí v souboru XML:

  ```csharp
  [DataContract(
  Namespace="urn:Contoso:2006:January:29",
  Name="LineItem")]
  public class LineItem
  {
        [DataMember(Name="ItemNumber",IsRequired=true,Order=0)]
        public string itemNumber;
        [DataMember(Name="Quantity",IsRequired=false,Order = 1)]
        public decimal quantity;
        [DataMember(Name="Price",IsRequired=false,Order = 2)]
        public decimal unitPrice;
  }
  ```

  Všechno ostatní o struktuře XML, která se používá k reprezentaci typu .NET, je určena <xref:System.Runtime.Serialization.DataContractSerializer> .

- Neumožňuje velkou kontrolu nad tím, jak je typ reprezentován v kódu XML, proces serializace je vysoce předvídatelný pro <xref:System.Runtime.Serialization.DataContractSerializer> , a, a, a je tak snazší ho optimalizovat. Praktická výhoda pro návrh <xref:System.Runtime.Serialization.DataContractSerializer> je vyšší výkon, přibližně 10 procent vyšší výkon.

- Atributy pro použití s parametrem <xref:System.Xml.Serialization.XmlSerializer> neoznačuje, která pole nebo vlastnosti tohoto typu jsou serializovány do XML, zatímco <xref:System.Runtime.Serialization.DataMemberAttribute> pro použití s parametrem je <xref:System.Runtime.Serialization.DataContractSerializer> explicitně zobrazen, která pole nebo vlastnosti jsou serializovány. Proto jsou kontrakty dat explicitní smlouvou o struktuře dat, která aplikace odesílá a přijímá.

- <xref:System.Xml.Serialization.XmlSerializer>Může přeložit pouze veřejné členy objektu .NET do kódu XML, <xref:System.Runtime.Serialization.DataContractSerializer> lze převést členy objektů do formátu XML bez ohledu na modifikátory přístupu těchto členů.

- V důsledku toho, že je možné serializovat neveřejné členy typů do XML, <xref:System.Runtime.Serialization.DataContractSerializer> má méně omezení na nejrůznější typy .NET, které může serializovat do XML. Konkrétně se může překládat na typy XML, jako by <xref:System.Collections.Hashtable> to implementovalo <xref:System.Collections.IDictionary> rozhraní. <xref:System.Runtime.Serialization.DataContractSerializer>Je mnohem více pravděpodobné, že je možné serializovat instance všech existujících typů rozhraní .NET do XML, aniž by bylo nutné buď upravit definici typu, nebo vytvořit obálku pro něj.

- Další důsledky, <xref:System.Runtime.Serialization.DataContractSerializer> jak mít přístup k neveřejným členům typu, je to, že vyžaduje úplný vztah důvěryhodnosti, zatímco to <xref:System.Xml.Serialization.XmlSerializer> není. Oprávnění pro přístup k kódu s úplným vztahem důvěryhodnosti poskytuje úplný přístup ke všem prostředkům v počítači, ke kterým lze přistupovat pomocí přihlašovacích údajů, na jejichž základě se kód spouští. Tato možnost by se měla používat společně s plně důvěryhodným kódem k přístupu ke všem prostředkům na vašem počítači.

- <xref:System.Runtime.Serialization.DataContractSerializer>Zahrnuje určitou podporu pro správu verzí:

  - <xref:System.Runtime.Serialization.DataMemberAttribute>Má <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> vlastnost, která se dá přiřadit hodnotě false pro členy, kteří jsou přidaní do nových verzí kontraktu dat, které nebyly přítomny v dřívějších verzích, takže aplikace s novější verzí kontraktu budou moci zpracovat předchozí verze.

  - Díky tomu, že kontrakt data implementuje <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní, může jeden dovolit <xref:System.Runtime.Serialization.DataContractSerializer> předat členům definovaným v novějších verzích kontraktu dat prostřednictvím aplikací s dřívějšími verzemi smlouvy.

Navzdory všem rozdílům je soubor XML, na který jsou <xref:System.Xml.Serialization.XmlSerializer> serializace typu, ve výchozím nastavení sémanticky totožný s kódem XML, do kterého <xref:System.Runtime.Serialization.DataContractSerializer> serializace typ, za předpokladu, že obor názvů XML je explicitně definován. Následující třída, která má atributy pro použití s oběma serializátory, je přeložena do sémanticky identického XML pomocí <xref:System.Xml.Serialization.XmlSerializer> a <xref:System.Runtime.Serialization.DataContractAttribute> :

```csharp
[Serializable]
[XmlRoot(Namespace="urn:Contoso:2006:January:29")]
[DataContract(Namespace="urn:Contoso:2006:January:29")]
public class LineItem
{
     [DataMember]
     public string ItemNumber;
     [DataMember]
     public decimal Quantity;
     [DataMember]
     public decimal UnitPrice;
}
```

Sada Windows Software Development Kit (SDK) obsahuje nástroj příkazového řádku, který se nazývá nástroj pro tvorbu [metadat ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md). Podobně jako nástroj XSD. exe, který se používá pro webové služby ASP.NET, může Svcutil. exe generovat definice datových typů .NET ze schématu XML. Typy jsou kontrakty dat, pokud <xref:System.Runtime.Serialization.DataContractSerializer> může generovat XML ve formátu definovaném schématem XML; v opačném případě jsou určeny pro serializaci pomocí <xref:System.Xml.Serialization.XmlSerializer> . Svcutil. exe může také vygenerovat schéma XML z kontraktů dat pomocí jeho `dataContractOnly` přepínače.

> [!NOTE]
> I když webové služby ASP.NET používají <xref:System.Xml.Serialization.XmlSerializer> , a režim kompatibility ASP.NET WCF způsobuje, že služby WCF napodobují chování webových služeb ASP.NET, možnost kompatibility ASP.NET neomezuje jednu na použití <xref:System.Xml.Serialization.XmlSerializer> . Ten může stále používat <xref:System.Runtime.Serialization.DataContractSerializer> se službami běžícími v režimu kompatibility ASP.NET.

## <a name="service-development"></a>Vývoj služeb

Chcete-li vyvinout službu pomocí ASP.NET, je vlastní pro přidání <xref:System.Web.Services.WebService> atributu do třídy a <xref:System.Web.Services.WebMethodAttribute> do libovolné metody třídy, které mají být operace služby:

```csharp
[WebService]
public class Service : T:System.Web.Services.WebService
{
    [WebMethod]
    public string Echo(string input)
    {
       return input;
    }
}
```

ASP.NET 2,0 představil možnost přidání atributu <xref:System.Web.Services.WebService> a <xref:System.Web.Services.WebMethodAttribute> rozhraní, nikoli třídy, a zápis třídy pro implementaci rozhraní:

```csharp
[WebService]
public interface IEcho
{
    [WebMethod]
    string Echo(string input);
}

public class Service : IEcho
{

   public string Echo(string input)
   {
        return input;
    }
}
```

Použití této možnosti je upřednostňováno, protože rozhraní s <xref:System.Web.Services.WebService> atributem představuje kontrakt pro operace prováděné službou, které lze znovu použít s různými třídami, které mohou implementovat stejný kontrakt různými způsoby.

Služba WCF je poskytována definováním jednoho nebo více koncových bodů WCF. Koncový bod je definovaný adresou, vazbou a kontraktem služby. Adresa určuje, kde se služba nachází. Vazba určuje, jak komunikovat se službou. Kontrakt služby definuje operace, které může služba provádět.

Kontrakt služby je obvykle definován jako první, a to přidáním <xref:System.ServiceModel.ServiceContractAttribute> a <xref:System.ServiceModel.OperationContractAttribute> k rozhraní:

```csharp
[ServiceContract]
public interface IEcho
{
     [OperationContract]
     string Echo(string input);
}
```

<xref:System.ServiceModel.ServiceContractAttribute>Určuje, že rozhraní definuje kontrakt služby WCF, a <xref:System.ServiceModel.OperationContractAttribute> označuje, které metody rozhraní definují operace kontraktu služby.

Po definování kontraktu služby je implementován ve třídě, tím, že třída implementuje rozhraní, pomocí kterého je definována kontrakt služby:

```csharp
public class Service : IEcho
{
    public string Echo(string input)
    {
       return input;
    }
}
```

Třída, která implementuje kontrakt služby, se na WCF označuje jako typ služby.

Dalším krokem je přidružení adresy a vazby k typu služby. To se obvykle provádí v konfiguračním souboru, a to buď úpravou souboru přímo, nebo pomocí editoru konfigurace, který je součástí služby WCF. Tady je příklad konfiguračního souboru.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
     <system.serviceModel>
      <services>
      <service name="Service ">
       <endpoint
        address="EchoService"
        binding="basicHttpBinding"
        contract="IEchoService "/>
      </service>
      </services>
     </system.serviceModel>
</configuration>
```

Vazba určuje sadu protokolů pro komunikaci s aplikací. V následující tabulce jsou uvedené systémové vazby, které reprezentují běžné možnosti.

|Name|Účel|
|----------|-------------|
|BasicHttpBinding|Interoperabilita s webovými službami a klienty, které podporují profil zabezpečení WS-BasicProfile 1,1 a Basic 1,0.|
|WSHttpBinding|Interoperabilita s webovými službami a klienty, které podporují protokoly WS-* přes protokol HTTP.|
|WSDualHttpBinding|Duplexní komunikace HTTP, kterou příjemce úvodní zprávy přímo neodpoví počátečnímu odesílateli, ale může přenést libovolný počet odpovědí v časovém intervalu pomocí protokolu HTTP v souladu s protokoly WS-*.|
|WSFederationBinding|Komunikace HTTP, při které se dá přístup k prostředkům služby řídit na základě přihlašovacích údajů vydaných výslovně identifikovaným poskytovatelem přihlašovacích údajů.|
|NetTcpBinding|Zabezpečená, spolehlivá a vysoce výkonná komunikace mezi softwarovými entitami WCF v síti.|
|NetNamedPipeBinding|Zabezpečená, spolehlivá a vysoce výkonná komunikace mezi entitami softwaru WCF ve stejném počítači.|
|NetMsmqBinding|Komunikace mezi softwarovými entitami WCF pomocí služby MSMQ.|
|MsmqIntegrationBinding|Komunikace mezi entitou softwaru WCF a jinou softwarovou entitou pomocí služby MSMQ.|
|NetPeerTcpBinding|Komunikace mezi softwarovými entitami WCF pomocí sítě Windows peer-to-peer.|

Vazba poskytovaná systémem <xref:System.ServiceModel.BasicHttpBinding> zahrnuje sadu protokolů podporovaných ASP.NET webovými službami.

Vlastní vazby pro aplikace WCF jsou snadno definovány jako kolekce tříd prvků vazby, které WCF používá k implementaci jednotlivých protokolů. Můžete napsat nové prvky vazby, které budou představovat další protokoly.

Vnitřní chování typů služeb lze upravit pomocí vlastností rodiny tříd nazvaných chování. Zde je <xref:System.ServiceModel.ServiceBehaviorAttribute> třída použita k určení, zda má být typ služby vícevláknový.

```csharp
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple)]
public class DerivativesCalculatorServiceType: IDerivativesCalculator
```

Některá chování, například <xref:System.ServiceModel.ServiceBehaviorAttribute> , jsou atributy. Ostatní, ty, které by správci chtěli nastavit, je možné upravit v konfiguraci aplikace.

V typech programovacích služeb je časté použití <xref:System.ServiceModel.OperationContext> třídy vytvořeno. Jeho statická <xref:System.ServiceModel.OperationContext.Current%2A> vlastnost poskytuje přístup k informacím o kontextu, ve kterém je operace spuštěná. <xref:System.ServiceModel.OperationContext>je podobná <xref:System.Web.HttpContext> <xref:System.EnterpriseServices.ContextUtil> třídám a.

## <a name="hosting"></a>Hosting

Webové služby ASP.NET jsou kompilovány do sestavení knihovny tříd. K dispozici je soubor s názvem soubor služby s příponou. asmx a obsahuje `@ WebService` direktivu, která identifikuje třídu, která obsahuje kód pro službu a sestavení, ve kterém se nachází.

`<%@ WebService Language="C#" Class="Service,ServiceAssembly" %>`

Soubor služby je zkopírován do kořenového adresáře aplikace ASP.NET v Internetová informační služba (IIS) a sestavení je zkopírováno do podadresáře \Bin kořenového adresáře aplikace. Aplikace je pak přístupná pomocí adresy URL (Uniform Resource Locator) souboru služby v kořenovém adresáři aplikace.

Služby WCF je možné snadno hostovat v rámci služby IIS 5,1 nebo 6,0, což je služba WAS (Windows Process Activation Service), která se poskytuje jako součást služby IIS 7,0, a v rámci libovolné aplikace .NET. Aby mohla služba hostovat službu ve službě IIS 5,1 nebo 6,0, musí jako komunikační transportní protokol používat protokol HTTP.

Chcete-li hostovat službu ve službě IIS 5,1, 6,0 nebo v nástroji, postupujte podle následujících kroků:

1. Zkompilujte typ služby do sestavení knihovny tříd.

2. Vytvořte soubor služby s příponou. svc s `@ ServiceHost` direktivou pro identifikaci typu služby:

    `<%@ServiceHost language="c#" Service="MyService" %>`

3. Zkopírujte soubor služby do virtuálního adresáře a sestavení do podadresáře \Bin tohoto virtuálního adresáře.

4. Zkopírujte konfigurační soubor do virtuálního adresáře a pojmenujte ho Web. config.

Aplikace je pak přístupná pomocí adresy URL souboru služby v kořenovém adresáři aplikace.

Chcete-li hostovat službu WCF v rámci aplikace .NET, zkompilujte typ služby do sestavení knihovny tříd, na které odkazuje aplikace, a Programujte aplikaci pro hostování služby pomocí <xref:System.ServiceModel.ServiceHost> třídy. Následuje příklad základního vyžadovaného programování:

```csharp
string httpBaseAddress = "http://www.contoso.com:8000/";
string tcpBaseAddress = "net.tcp://www.contoso.com:8080/";

Uri httpBaseAddressUri = new Uri(httpBaseAddress);
Uri tcpBaseAddressUri = new Uri(tcpBaseAddress);

Uri[] baseAddresses = new Uri[] {
 httpBaseAddressUri,
 tcpBaseAddressUri};

using(ServiceHost host = new ServiceHost(
typeof(Service), //"Service" is the name of the service type baseAddresses))
{
     host.Open();

     […] //Wait to receive messages
     host.Close();
}
```

Tento příklad ukazuje, jak jsou zadány adresy jednoho nebo více přenosových protokolů v konstrukci <xref:System.ServiceModel.ServiceHost> . Tyto adresy se označují jako základní adresy.

Adresa zadaná pro libovolný koncový bod služby WCF je adresa relativní k základní adrese hostitele koncového bodu. Hostitel může mít jednu základní adresu pro každý komunikační transportní protokol. V ukázkové konfiguraci v předchozím konfiguračním souboru <xref:System.ServiceModel.BasicHttpBinding> používá vybraný koncový bod HTTP jako transportní protokol, takže adresa koncového bodu `EchoService` je relativní vzhledem k základní adrese http hostitele. V případě hostitele v předchozím příkladu je základní adresa HTTP `http://www.contoso.com:8000/` . V případě služby hostované v rámci služby IIS nebo WAS je základní adresou adresa URL souboru služby služby.

Pro použití možnosti režimu kompatibility WCF ASP.NET je možné použít jenom služby hostované ve službě IIS nebo WAS a které jsou nakonfigurované s HTTP jako transportní protokol. Zapnutí této možnosti vyžaduje následující kroky.

1. Programátor musí přidat <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> atribut do typu služby a určit, že režim kompatibility ASP.NET je buď povolený, nebo povinný.

    ```csharp
    [System.ServiceModel.Activation.AspNetCompatibilityRequirements(
          RequirementsMode=AspNetCompatibilityRequirementsMode.Require)]
    public class DerivativesCalculatorServiceType: IDerivativesCalculator
    ```

2. Správce musí aplikaci nakonfigurovat tak, aby používala režim kompatibility ASP.NET.

    ```xml
    <configuration>
         <system.serviceModel>
          <services>
          […]
          </services>
          <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
        </system.serviceModel>
    </configuration>
    ```

    Aplikace WCF je také možné nakonfigurovat tak, aby používaly. asmx jako přípona svých souborů služby, nikoli. svc.

    ```xml
    <system.web>
         <compilation>
          <compilation debug="true">
          <buildProviders>
           <remove extension=".asmx"/>
           <add extension=".asmx"
            type="System.ServiceModel.ServiceBuildProvider,
            System.ServiceModel,
            Version=3.0.0.0,
            Culture=neutral,
            PublicKeyToken=b77a5c561934e089" />
          </buildProviders>
          </compilation>
         </compilation>
    </system.web>
    ```

    Tato možnost vám může ušetřit při úpravách klientů, kteří jsou nakonfigurováni na používání adres URL souborů služby. asmx při úpravě služby na použití WCF.

## <a name="client-development"></a>Vývoj klienta

Klienti pro webové služby ASP.NET se generují pomocí nástroje příkazového řádku WSDL. exe, který jako vstup poskytuje adresu URL souboru. asmx. Odpovídající nástroj poskytovaný službou WCF je [Nástroj pro nástroj pro metadata ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md). Generuje modul kódu s definicí kontraktu služby a definicí třídy klienta WCF. Také generuje konfigurační soubor s adresou a vazbou služby.

Při programování klienta vzdálené služby je obecně vhodné programovat podle asynchronního vzoru. Kód vygenerovaný nástrojem WSDL. exe vždy poskytuje synchronní i asynchronní vzor ve výchozím nastavení. Kód vygenerovaný nástrojem pro dodávání [metadat ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) může poskytovat buď vzorek. Ve výchozím nastavení poskytuje synchronní vzor. Pokud je nástroj spuštěn s `/async` přepínačem, pak generovaný kód poskytne asynchronní vzorek.

Není zaručeno, že názvy v třídách klienta WCF vygenerovaných ASP. Nástroj WSDL. exe nástroje NET standardně odpovídá názvům ve třídách klienta WCF vygenerovaných nástrojem Svcutil. exe. Konkrétně názvy vlastností tříd, které musí být serializovány pomocí <xref:System.Xml.Serialization.XmlSerializer> , jsou ve výchozím nastavení uděleny vlastnosti přípona v kódu generovaném nástrojem Svcutil. exe, který není v případě nástroje WSDL. exe.

## <a name="message-representation"></a>Reprezentace zprávy

Hlavičky zpráv SOAP odesílaných a přijímaných webovými službami ASP.NET se dají přizpůsobit. Třída je odvozena z <xref:System.Web.Services.Protocols.SoapHeader> pro definování struktury záhlaví a pak <xref:System.Web.Services.Protocols.SoapHeaderAttribute> slouží k označení přítomnosti záhlaví.

```csharp
public class SomeProtocol : SoapHeader
{
     public long CurrentValue;
     public long Total;
}

[WebService]
public interface IEcho
{
     SomeProtocol ProtocolHeader
     {
      get;
     set;
     }

     [WebMethod]
     [SoapHeader("ProtocolHeader")]
     string PlaceOrders(PurchaseOrderType order);
}

public class Service: WebService, IEcho
{
     private SomeProtocol protocolHeader;

     public SomeProtocol ProtocolHeader
     {
         get
         {
              return this.protocolHeader;
         }

         set
         {
              this.protocolHeader = value;
         }
     }

     string PlaceOrders(PurchaseOrderType order)
     {
         long currentValue = this.protocolHeader.CurrentValue;
     }
}
```

Služba WCF poskytuje atributy,, <xref:System.ServiceModel.MessageContractAttribute> <xref:System.ServiceModel.MessageHeaderAttribute> a <xref:System.ServiceModel.MessageBodyMemberAttribute> pro popis struktury zpráv SOAP odesílaných a přijímaných službou.

```csharp
[DataContract]
public class SomeProtocol
{
     [DataMember]
     public long CurrentValue;
     [DataMember]
     public long Total;
}

[DataContract]
public class Item
{
     [DataMember]
     public string ItemNumber;
     [DataMember]
     public decimal Quantity;
     [DataMember]
     public decimal UnitPrice;
}

[MessageContract]
public class ItemMessage
{
     [MessageHeader]
     public SomeProtocol ProtocolHeader;
     [MessageBody]
     public Item Content;
}

[ServiceContract]
public interface IItemService
{
     [OperationContract]
     public void DeliverItem(ItemMessage itemMessage);
}
```

Tato syntaxe poskytuje explicitní reprezentace struktury zpráv, zatímco struktura zpráv je odvozena kódem webové služby ASP.NET. Také v syntaxi ASP.NET jsou hlavičky zpráv reprezentovány jako vlastnosti služby, jako je například `ProtocolHeader` vlastnost v předchozím příkladu, zatímco v syntaxi služby WCF jsou přesněji reprezentovány jako vlastnosti zpráv. WCF také umožňuje přidání záhlaví zpráv do konfigurace koncových bodů.

```xml
<service name="Service ">
     <endpoint
      address="EchoService"
      binding="basicHttpBinding"
      contract="IEchoService ">
      <headers>
      <dsig:X509Certificate
       xmlns:dsig="http://www.w3.org/2000/09/xmldsig#">
       ...
      </dsig:X509Certificate>
      </headers>
     </endpoint>
</service>
```

Tato možnost umožňuje vyhnout se jakémukoli odkazu na záhlaví protokolu infrastruktury v kódu pro klienta nebo službu: záhlaví jsou přidána do zpráv z důvodu konfigurace koncového bodu.

## <a name="service-description"></a>Popis služby

Vydání požadavku HTTP GET pro soubor. asmx webové služby ASP.NET s dotazem WSDL způsobí, že ASP.NET generuje WSDL pro popis služby. Vrátí tento prvek WSDL jako odpověď na požadavek.

ASP.NET 2,0 umožňuje ověřit, jestli je služba kompatibilní se základním profilem 1,1 organizace pro interoperabilitu webových služeb (WS-I) a jestli se má do svého rozhraní WSDL vložit deklarace identity, kterou služba dodržuje. To se provádí pomocí `ConformsTo` parametrů a `EmitConformanceClaims` <xref:System.Web.Services.WebServiceBindingAttribute> atributu.

```csharp
[WebService(Namespace = "http://tempuri.org/")]
[WebServiceBinding(
     ConformsTo = WsiProfiles.BasicProfile1_1,
     EmitConformanceClaims=true)]
public interface IEcho
```

Rozhraní WSDL, které ASP.NET generuje pro službu, lze přizpůsobit. Vlastní nastavení se provádí vytvořením odvozené třídy <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> pro přidání položek do WSDL.

Vydání požadavku HTTP GET s dotazem WSDL pro soubor. svc služby WCF s koncovým bodem HTTP hostovaným ve službě IIS 51, 6,0 nebo způsobilo, že WCF reaguje na jazyk WSDL, aby popisoval službu. Vydání požadavku HTTP GET s dotazem WSDL na základní adresu HTTP služby hostované v aplikaci .NET má stejný účinek, pokud je httpGetEnabled nastaveno na hodnotu true.

WCF ale také reaguje na požadavky WS-MetadataExchange s WSDL, které generuje pro popis služby. Webové služby ASP.NET nemají integrovanou podporu pro požadavky WS-MetadataExchange.

WSDL, kterou WCF generuje, může být výrazně přizpůsobená. <xref:System.ServiceModel.Description.ServiceMetadataBehavior>Třída poskytuje určitá zařízení pro přizpůsobení rozhraní WSDL. WCF je také možné nakonfigurovat tak, aby negenerovalo WSDL, ale místo toho používat statický soubor WSDL v dané adrese URL.

```xml
<behaviors>
     <behavior name="DescriptionBehavior">
     <metadataPublishing
      enableMetadataExchange="true"
      enableGetWsdl="true"
      enableHelpPage="true"
      metadataLocation=
      "http://localhost/DerivativesCalculatorService/Service.WSDL"/>
     </behavior>
</behaviors>
```

## <a name="exception-handling"></a>Zpracování výjimek

V ASP.NET webové služby se neošetřené výjimky vrátí klientům jako chyby protokolu SOAP. Můžete také explicitně vyvolat instance <xref:System.Web.Services.Protocols.SoapException> třídy a mít větší kontrolu nad obsahem chyby protokolu SOAP, která se přenáší klientovi.

Ve službách WCF nejsou neošetřené výjimky vraceny klientům jako chyby protokolu SOAP, aby se zabránilo neúmyslnému zveřejnění citlivých informací prostřednictvím výjimek. Nastavení konfigurace je k dispozici, aby byly neošetřené výjimky vraceny klientům pro účely ladění.

Chcete-li vrátit chyby protokolu SOAP klientům, můžete vyvolat instance obecného typu <xref:System.ServiceModel.FaultException%601> pomocí typu kontraktu dat jako obecného typu. Můžete také přidat <xref:System.ServiceModel.FaultContractAttribute> atributy do operací a určit tak chyby, které může operace vracet.

```csharp
[DataContract]
public class MathFault
{
     [DataMember]
     public string operation;
     [DataMember]
     public string problemType;
}

[ServiceContract]
public interface ICalculator
{
     [OperationContract]
     [FaultContract(typeof(MathFault))]
     int Divide(int n1, int n2);
}
```

Výsledkem je, že jsou možné chyby inzerované v rozhraní WSDL pro službu, což umožňuje programátorům v klientských chybách odhadnout, které chyby mohou být výsledkem operace, a zapsat příslušné příkazy Catch.

```csharp
try
{
     result = client.Divide(value1, value2);
}
catch (FaultException<MathFault> e)
{
 Console.WriteLine("FaultException<MathFault>: Math fault while doing "
  + e.Detail.operation
  + ". Problem: "
  + e.Detail.problemType);
}
```

## <a name="state-management"></a>Správa stavu

Třída použitá k implementaci webové služby ASP.NET může být odvozena z <xref:System.Web.Services.WebService> .

```csharp
public class Service : WebService, IEcho
{

 public string Echo(string input)
 {
  return input;
 }
}
```

V takovém případě může být třída naprogramována tak, aby <xref:System.Web.Services.WebService> pro přístup k objektu použila kontextovou vlastnost základní třídy <xref:System.Web.HttpContext> . <xref:System.Web.HttpContext>Objekt lze použít k aktualizaci a načtení informací o stavu aplikace pomocí jeho vlastnosti aplikace a lze jej použít k aktualizaci a načtení informací o stavu relace pomocí vlastnosti relace.

ASP.NET poskytuje značnou kontrolu nad tím, kde jsou informace o stavu relace, ke kterým se přistupovaly pomocí vlastnosti relace ve <xref:System.Web.HttpContext> skutečnosti uložené. Může být uložen v souborech cookie, v databázi, v paměti aktuálního serveru nebo v paměti určeného serveru. Tato volba se provádí v konfiguračním souboru služby.

WCF poskytuje rozšiřitelné objekty pro správu stavů. Rozšiřitelné objekty jsou objekty, které implementují <xref:System.ServiceModel.IExtensibleObject%601> . Nejdůležitější rozšiřitelné objekty jsou <xref:System.ServiceModel.ServiceHostBase> a <xref:System.ServiceModel.InstanceContext> . `ServiceHostBase`umožňuje zachovat stav, ke kterému mají přístup všechny instance všech typů služeb na stejném hostiteli, a `InstanceContext` umožňuje zachovat stav, ke kterému může přistupovat jakýkoli kód spuštěný ve stejné instanci typu služby.

Zde je typ služby, `TradingSystem` , má, <xref:System.ServiceModel.ServiceBehaviorAttribute> který určuje, že všechna volání ze stejné instance klienta služby WCF jsou směrována do stejné instance typu služby.

```csharp
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]
public class TradingSystem: ITradingService
```

Třída `DealData` definuje stav, ke kterému lze přistupovat jakýkoli kód spuštěný ve stejné instanci typu služby.

```csharp
internal class DealData: IExtension<InstanceContext>
{
 public string DealIdentifier = null;
 public Trade[] Trades = null;
}
```

V kódu typu služby, který implementuje jednu z operací kontraktu služby, `DealData` je objekt stavu přidán do stavu aktuální instance typu služby.

```csharp
string ITradingService.BeginDeal()
{
 string dealIdentifier = Guid.NewGuid().ToString();
 DealData state = new DealData(dealIdentifier);
 OperationContext.Current.InstanceContext.Extensions.Add(state);
 return dealIdentifier;
}
```

Tento stavový objekt lze poté načíst a upravit pomocí kódu, který implementuje jinou operaci kontraktu služby.

```csharp
void ITradingService.AddTrade(Trade trade)
{
 DealData dealData =  OperationContext.Current.InstanceContext.Extensions.Find<DealData>();
 dealData.AddTrade(trade);
}
```

Zatímco ASP.NET poskytuje kontrolu nad tím, kde jsou ve skutečnosti uložené informace o stavu ve <xref:System.Web.HttpContext> třídě, WCF, alespoň v její počáteční verzi, neposkytuje žádnou kontrolu nad tím, kde jsou uložené rozšiřitelné objekty. To představuje velmi nejlepší důvod pro výběr režimu kompatibility ASP.NET pro službu WCF. Pokud je konfigurovatelná Správa stavu nevyhnutelná a potom se rozhodnete, že režim kompatibility ASP.NET umožňuje používat zařízení <xref:System.Web.HttpContext> třídy přesně tak, jak se používají v ASP.NET, a také nakonfigurovat, kde jsou informace o stavu spravované pomocí <xref:System.Web.HttpContext> třídy uložené.

## <a name="security"></a>Zabezpečení

Možnosti zabezpečení webových služeb ASP.NET jsou ty, které slouží k zabezpečení libovolné aplikace IIS. Vzhledem k tomu, že aplikace WCF lze hostovat nejen v rámci služby IIS, ale také v jakémkoli spustitelném souboru .NET, je nutné, aby byly možnosti pro zabezpečení aplikací WCF nezávislé na zařízeních služby IIS. Zařízení, která jsou poskytována pro webové služby ASP.NET, jsou však k dispozici také pro služby WCF spuštěné v režimu kompatibility ASP.NET.

### <a name="security-authentication"></a>Zabezpečení: ověřování

Služba IIS poskytuje zařízení pro řízení přístupu k aplikacím, pomocí kterých můžete vybrat buď anonymní přístup, nebo nejrůznější režimy ověřování: ověřování systému Windows, ověřování hodnotou hash, základní ověřování a ověřování pomocí služby .NET Passport. Možnost ověřování systému Windows se dá použít k řízení přístupu k ASP.NET webovým službám. Pokud jsou však aplikace WCF hostovány v rámci služby IIS, je nutné nakonfigurovat službu IIS tak, aby povolovala anonymní přístup k aplikaci, aby bylo možné ověřování spravovat samotným WCF, které podporuje ověřování systému Windows mezi různými dalšími možnostmi. Mezi další předdefinované možnosti patří tokeny uživatelského jména, certifikáty X. 509, tokeny SAML a karta CardSpace, ale je možné definovat i vlastní mechanismy ověřování.

### <a name="security-impersonation"></a>Zabezpečení: zosobnění

ASP.NET poskytuje prvek identity, pomocí kterého může být vytvořena webová služba ASP.NET k zosobnění konkrétního uživatele nebo pověření uživatele s aktuální žádostí. Tento element lze použít ke konfiguraci zosobnění v aplikacích WCF běžících v režimu kompatibility ASP.NET.

Konfigurační systém WCF poskytuje vlastní prvek identity pro určení konkrétního uživatele k zosobnění. Klienti a služby WCF taky můžou být pro zosobnění nezávisle nakonfigurované. Klienty lze nakonfigurovat k zosobnění aktuálního uživatele při odesílání požadavků.

```xml
<behaviors>
     <behavior name="DerivativesCalculatorClientBehavior">
      <clientCredentials>
      <windows allowedImpersonationLevel="Impersonation"/>
      </clientCredentials>
     </behavior>
</behaviors>
```

Operace služby se dají nakonfigurovat k zosobnění přihlašovacích údajů uživatele s aktuální žádostí.

```csharp
[OperationBehavior(Impersonation = ImpersonationOption.Required)]
public void Receive(Message input)
```

### <a name="security-authorization-using-access-control-lists"></a>Zabezpečení: autorizace pomocí seznamů Access Control

Seznamy Access Control (ACL) lze použít k omezení přístupu k souborům. asmx. Seznamy ACL v souborech WCF. svc se ale ignorují s výjimkou v režimu kompatibility ASP.NET.

### <a name="security-role-based-authorization"></a>Zabezpečení: autorizace na základě rolí

Možnost ověřování systému Windows ve službě IIS lze použít ve spojení s elementem autorizace poskytovaným konfiguračním jazykem ASP.NET pro usnadnění ověřování na základě rolí pro webové služby ASP.NET na základě skupin systému Windows, ke kterým jsou uživatelé přiřazeni. ASP.NET 2,0 představil obecnější mechanizmus ověřování na základě rolí: poskytovatelé rolí.

Poskytovatelé rolí jsou třídy, které všechny implementují základní rozhraní pro dotazování na role, ke kterým je uživatel přiřazený, ale každý poskytovatel rolí ví, jak tyto informace načíst z jiného zdroje. ASP.NET 2,0 poskytuje poskytovatele rolí, který může načítat přiřazení rolí z databáze Microsoft SQL Server, a druhý, který může načíst přiřazení rolí z Správce autorizací systému Windows Server 2003.

Mechanismus poskytovatele rolí se dá ve skutečnosti použít nezávisle na ASP.NET v jakékoli aplikaci .NET, včetně aplikace WCF. Následující ukázková konfigurace pro aplikaci WCF ukazuje, jak je možné použít poskytovatele rolí ASP.NET jako možnost vybranou prostřednictvím <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> .

```xml
<system.serviceModel>
     <services>
         <service name="Service.ResourceAccessServiceType"
             behaviorConfiguration="ServiceBehavior">
             <endpoint
              address="ResourceAccessService"
              binding="wsHttpBinding"
              contract="Service.IResourceAccessContract"/>
         </service>
     </services>
     <behaviors>
       <behavior name="ServiceBehavior">
       <serviceAuthorization principalPermissionMode="UseAspNetRoles"/>
      </behavior>
     </behaviors>
</system.serviceModel>
```

### <a name="security-claims-based-authorization"></a>Zabezpečení: ověřování na základě deklarací identity

Jednou z nejdůležitějších inovací služby WCF je důkladná podpora pro autorizaci přístupu k chráněným prostředkům na základě deklarací identity. Deklarace identity se skládají z typu, práva a hodnoty, licence na ovladače, například. Poskytuje sadu deklarací identity, z nichž jeden je držitelem data narození. Typ deklarace identity je datum narození, přičemž hodnota deklarace identity je datum narození ovladače. Právo, které udělí nárok na nosiči, určuje, co má nosič s hodnotou deklarace identity. V případě nároku na datum narození řidiče je práva k dispozici: ovladač má toto datum narození, ale nemůže ho například změnit. Ověřování založené na deklaracích obklopuje autorizaci na základě rolí, protože role představují typ deklarace identity.

Autorizaci založenou na deklaracích je možné provést porovnáním sady deklarací s požadavky na přístup k požadavkům operace a v závislosti na výsledku tohoto porovnání, udělení nebo odepření přístupu k této operaci. V rámci WCF můžete určit třídu, která se má použít ke spuštění autorizace založené na deklaracích, a to znovu přiřazením hodnoty `ServiceAuthorizationManager` vlastnosti třídy <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> .

```xml
<behaviors>
     <behavior name='ServiceBehavior'>
     <serviceAuthorization
     serviceAuthorizationManagerType=
                   'Service.AccessChecker, Service' />
     </behavior>
</behaviors>
```

Třídy používané ke spouštění autorizace založené na deklaracích musí být odvozeny z <xref:System.ServiceModel.ServiceAuthorizationManager> , který má pouze jednu metodu, která má být přepsána `AccessCheck()` . Služba WCF volá tuto metodu vždy, když je vyvolána operace služby a poskytuje <xref:System.ServiceModel.OperationContext> objekt, který má deklarace pro uživatele ve své `ServiceSecurityContext.AuthorizationContext` Vlastnosti. WCF provádí sestavování deklarací identity uživatele z libovolného tokenu zabezpečení, který uživatel zadal pro ověřování, což ponechá úkol vyhodnotit, zda tyto deklarace pro danou operaci postačují.

Tato technologie WCF automaticky sestavuje deklarace z jakéhokoli typu tokenu zabezpečení, protože způsobuje autorizaci kódu na základě deklarace zcela nezávisle na ověřovacím mechanismu. Naproti tomu autorizace pomocí seznamů ACL nebo rolí v ASP.NET je úzce spjata s ověřováním systému Windows.

### <a name="security-confidentiality"></a>Zabezpečení: důvěrnost

Důvěrnost zpráv vyměňovaných s ASP.NET webovými službami se dá zajistit na úrovni přenosu tím, že v rámci služby IIS nakonfigurujete aplikaci tak, aby používala protokol HTTPS (Secure Hypertext Transfer Protocol). Totéž lze provést pro aplikace WCF hostované v rámci služby IIS. Aplikace WCF hostované mimo službu IIS ale můžou být nakonfigurované tak, aby používaly zabezpečený transportní protokol. Důležitější je, že aplikace WCF je taky možné nakonfigurovat tak, aby se zprávy před jejich přečtením používaly pomocí protokolu WS-Security. Zabezpečení pouze těla zprávy pomocí WS-Security umožňuje, aby je bylo možné před dosažením konečného cíle přenést do všech dodavatelů.

## <a name="globalization"></a>Globalizace

Jazyk konfigurace ASP.NET umožňuje zadat jazykovou verzi pro jednotlivé služby. WCF nepodporuje toto nastavení konfigurace, s výjimkou v režimu kompatibility ASP.NET. Chcete-li lokalizovat službu WCF, která nepoužívá režim kompatibility ASP.NET, zkompilujte typ služby do sestavení specifických pro jazykovou verzi a pro každé sestavení specifické pro jazykovou verzi použijte samostatné koncové body specifické pro jazykovou verzi.

## <a name="see-also"></a>Viz také

- [Porovnání webových služeb ASP.NET se službou WCF na základě účelu a používaných standardů](comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
