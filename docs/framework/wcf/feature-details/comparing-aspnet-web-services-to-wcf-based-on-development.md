---
title: Porovnání webových služeb ASP.NET Web Services s technologií WCF z hlediska vývojových požadavků
ms.date: 03/30/2017
ms.assetid: f362d00e-ce82-484f-9d4f-27e579d5c320
ms.openlocfilehash: c4c07d24ba322c957aac5ba9fa6ed3a5f337fb9a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53127365"
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-development"></a>Porovnání webových služeb ASP.NET Web Services s technologií WCF z hlediska vývojových požadavků
Windows Communication Foundation (WCF) je možnost režim kompatibility ASP.NET umožňují aplikacím naprogramovat a nakonfigurované stejně jako webové služby WCF a napodobení jejich chování. Následující části porovnávají webových služeb ASP.NET a WCF založená na co je potřeba k vývoji aplikací pomocí obou technologií.  
  
## <a name="data-representation"></a>Reprezentace dat  
 Vývoj webové služby s využitím technologie ASP.NET se obvykle začíná definování jakékoli komplexních datových typů, které se má používat služba. Technologie ASP.NET se může spolehnout <xref:System.Xml.Serialization.XmlSerializer> převodu dat reprezentovaný typy rozhraní .NET Framework do formátu XML pro přenos do nebo ze služby a pro převod data přijatá ve formátu XML do objektů .NET Framework. Definování komplexních datových typů, které se má používat službu ASP.NET vyžaduje definici rozhraní .NET Framework třída, která je <xref:System.Xml.Serialization.XmlSerializer> může serializovat do a ze souboru XML. Takové třídy napsané ručně, nebo generovány z definice typů ve schématu XML pomocí příkazového řádku XML schémat/dat typy podpory nástroje, xsd.exe.  
  
 Tady je seznam důležitých problémů vědět při definování rozhraní .NET Framework třída, která je <xref:System.Xml.Serialization.XmlSerializer> může serializovat do a ze souboru XML:  
  
-   Pouze veřejné polí a vlastností objektů v rozhraní .NET Framework jsou přeloženy do XML.  
  
-   Instance třídy kolekce lze serializovat do souboru XML, pouze v případě, že třídy implementovat buď <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.ICollection> rozhraní.  
  
-   Třídy, které implementují <xref:System.Collections.IDictionary> rozhraní, jako například <xref:System.Collections.Hashtable>, nejde serializovat do formátu XML.  
  
-   Velké typy v mnoha atributů <xref:System.Xml.Serialization> oboru názvů lze přidat do třídy rozhraní .NET Framework a jeho členy lze řídit, jak jsou reprezentovány instancí třídy ve formátu XML.  
  
 Vývoj aplikací WCF obvykle také začíná definice komplexních typů. WCF je třeba použít stejné typy rozhraní .NET Framework jako webové služby ASP.NET.  
  
 WCF<xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> lze přidat na typy rozhraní .NET Framework označuje, že se instance daného typu, je k serializaci do XML a které konkrétních polích nebo vlastnostech typu jsou serializovaná, jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 <xref:System.Runtime.Serialization.DataContractAttribute> Znamená, že nula nebo více polí a vlastností typu mají být serializován, zatímco <xref:System.Runtime.Serialization.DataMemberAttribute> označuje, že konkrétní pole nebo vlastnost má být serializován. <xref:System.Runtime.Serialization.DataContractAttribute> Lze použít u třídy nebo struktury. <xref:System.Runtime.Serialization.DataMemberAttribute> Lze použít u pole nebo vlastnost a pole a vlastnosti, ke kterým se atribut používá může být veřejné nebo soukromé. Instance typů, které mají <xref:System.Runtime.Serialization.DataContractAttribute> u nich, se nazývají data smluv ve službě WCF. Jsou serializován do souboru XML pomocí <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 Tady je seznam důležitých rozdílů mezi použitím nástrojů <xref:System.Runtime.Serialization.DataContractSerializer> a použití <xref:System.Xml.Serialization.XmlSerializer> a různé atributy <xref:System.Xml.Serialization> oboru názvů.  
  
-   <xref:System.Xml.Serialization.XmlSerializer> a atributy <xref:System.Xml.Serialization> obor názvů jsou navržené tak, aby bylo možné mapovat typy rozhraní .NET Framework na libovolný platný typ definovaný ve schématu XML a tak poskytovat velmi přesnou kontrolu nad zastoupení typu ve formátu XML. <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> poskytují velmi málo kontrolu nad zastoupení typu ve formátu XML. Můžete nastavit jenom obory názvů a názvů používaných ke znázornění typu a jeho pole nebo vlastnosti v souboru XML a pořadí, ve kterém polí a vlastností zobrazí v kódu XML:  
  
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
  
     Všechno ostatní o struktuře XML, který představuje typ formátu .NET je určeno <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
-   Tím, že není velkou kontrolu nad jak je typem a nelze je reprezentovat ve formátu XML, stane vysoce předvídatelné pro procesu serializace <xref:System.Runtime.Serialization.DataContractSerializer>a tím usnadňuje optimalizaci. Praktické výhodou návrh <xref:System.Runtime.Serialization.DataContractSerializer> je lepší výkon, přibližně deset procent lepší výkon.  
  
-   Atributy pro použití se službou <xref:System.Xml.Serialization.XmlSerializer> nevyplývá, pole nebo vlastnosti typu se serializovat do formátu XML, zatímco <xref:System.Runtime.Serialization.DataMemberAttribute> pro použití se službou <xref:System.Runtime.Serialization.DataContractSerializer> ukazuje explicitně pole nebo vlastnosti serializují. Kontrakty dat jsou proto explicitní smluv o struktuře dat, která aplikace je odesílat a přijímat.  
  
-   <xref:System.Xml.Serialization.XmlSerializer> Může překládat pouze veřejné členy objektu rozhraní .NET do formátu XML, <xref:System.Runtime.Serialization.DataContractSerializer> přeložit jako objekty její členové objektů do souboru XML bez ohledu na to modifikátory přístupu těchto členů.  
  
-   Následkem schopnost serializovat neveřejným členům typů do souboru XML, <xref:System.Runtime.Serialization.DataContractSerializer> má méně omezení pro různé typy .NET, které mohou serializovat do formátu XML. Zejména může překládat na typy XML jako <xref:System.Collections.Hashtable> , které implementují <xref:System.Collections.IDictionary> rozhraní. <xref:System.Runtime.Serialization.DataContractSerializer> Je mnohem pravděpodobnější lze serializovat instance všechny existující typ formátu .NET do formátu XML bez nutnosti změňte definici typu nebo vyvíjet obálku pro něj.  
  
-   Jiné důsledkem <xref:System.Runtime.Serialization.DataContractSerializer> nebudete mít přístup k neveřejným členům typu je, že vyžaduje úplný vztah důvěryhodnosti, že <xref:System.Xml.Serialization.XmlSerializer> nepodporuje. Přístupová oprávnění plné důvěryhodnosti kódu poskytuje úplný přístup ke všem prostředkům na počítači, který je přístupný pomocí přihlašovacích údajů, za kterých je kód spuštěn. Tato možnost by měla sloužit opatrně plně důvěryhodný kód přistupuje k všechny prostředky ve vašem počítači.  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer> Zahrnuje některé podpory pro správu verzí:  
  
    -   <xref:System.Runtime.Serialization.DataMemberAttribute> Má <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> vlastnost, která je možné přiřadit hodnotu false pro členy, které jsou přidány do nové verze kontraktu dat, které nebyly k dispozici v dřívějších verzích, a tím umožní aplikace s touto novou verzí smlouvy bude nelze zpracovat starší verze.  
  
    -   Tím, že implementace kontraktu dat <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní, jeden můžete povolit <xref:System.Runtime.Serialization.DataContractSerializer> předat členy definované v novějších verzích kontraktu dat prostřednictvím aplikací s předchozími verzemi smlouvy.  
  
 Bez ohledu na některé rozdíly, XML, do kterého <xref:System.Xml.Serialization.XmlSerializer> serializuje typu ve výchozím nastavení je sémanticky shodná s XML, do kterého <xref:System.Runtime.Serialization.DataContractSerializer> serializuje typu podle oboru názvů XML není výslovně uveden. Následující třídy, která má atributy pro použití s nástrojem serializátory, je přeložit na sémanticky identické XML pomocí <xref:System.Xml.Serialization.XmlSerializer> a <xref:System.Runtime.Serialization.DataContractAttribute>:  
  
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
  
 Sady Windows software development kit (SDK) zahrnuje nástroj příkazového řádku, volá se, [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Nástroj xsd.exe použitý s webovými službami ASP.NET, jako jsou Svcutil.exe lze generovat definice datových typů .NET ze schématu XML. Pokud jsou tyto typy kontraktů dat <xref:System.Runtime.Serialization.DataContractSerializer> může vysílat XML ve formátu definovaná pomocí schématu XML; v opačném případě jsou určeny pro použití serializace <xref:System.Xml.Serialization.XmlSerializer>. Svcutil.exe lze také generování schématu XML z kontraktů dat pomocí jeho `dataContractOnly` přepnout.  
  
> [!NOTE]
>  I když webových služeb ASP.NET použijte <xref:System.Xml.Serialization.XmlSerializer>a režim kompatibility WCF ASP.NET umožňuje služby WCF, které napodobují chování webových služeb ASP.NET, ASP.NET možnost kompatibility neomezuje z nich se má používat <xref:System.Xml.Serialization.XmlSerializer>. Stále můžete použít <xref:System.Runtime.Serialization.DataContractSerializer> pomocí služby spuštěné v režimu kompatibility ASP.NET.  
  
## <a name="service-development"></a>Vývoj služby  
 Pro vývoj služby pomocí ASP.NET, bylo běžné přidáte <xref:System.Web.Services.WebService> atribut třídy a <xref:System.Web.Services.WebMethodAttribute> k některé z metod této třídy, které mají být operace služby:  
  
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
  
 ASP.NET 2.0 zavedla možnost přidání atributu <xref:System.Web.Services.WebService> a <xref:System.Web.Services.WebMethodAttribute> rozhraní, nikoli třída a zápis třídu pro implementaci rozhraní:  
  
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
  
 Pomocí této možnosti má být upřednostňované, protože rozhraní s <xref:System.Web.Services.WebService> atributu tvoří kontrakt operace prováděné na službu, kterou lze opětovně použít s různými třídami, které mohou implementovat tento stejný kontrakt různými způsoby.  
  
 WCF service se poskytuje tak, že definujete jeden nebo více koncových bodů WCF. Koncový bod je definován tak, že adresa, vazba a kontrakt služby. Adresa definuje, ve kterém se služba nachází. Vazba Určuje, jak komunikovat se službou. Kontrakt služby definuje operace, které služby mohou provádět.  
  
 Kontrakt služby je obvykle definován jako první, tak, že přidáte <xref:System.ServiceModel.ServiceContractAttribute> a <xref:System.ServiceModel.OperationContractAttribute> rozhraní:  
  
```csharp  
[ServiceContract]  
public interface IEcho  
{  
     [OperationContract]  
     string Echo(string input);  
}  
```  
  
 <xref:System.ServiceModel.ServiceContractAttribute> Určuje, že rozhraní definuje kontrakt služby WCF a <xref:System.ServiceModel.OperationContractAttribute> označuje, která, pokud existuje, metod rozhraní definuje operace kontraktu služby.  
  
 Po definování kontraktu služby je implementována ve třídě, tím, že třída implementovat rozhraní, ve které je definováno kontraktu služby:  
  
```csharp  
public class Service : IEcho  
{  
    public string Echo(string input)  
    {  
       return input;  
    }  
}  
```  
  
 Třídu, která implementuje kontrakt služby se označuje jako služba typu ve službě WCF.  
  
 Dalším krokem je spojit adresu a vazbu s typem služby. Který se obvykle provádí v konfiguračním souboru, tak, že upravíte soubor přímo nebo pomocí editoru konfigurace s použitím technologie WCF k dispozici. Tady je příklad konfiguračního souboru.  
  
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
  
 Vazba určuje sadu protokolů pro komunikaci s aplikací. V následující tabulce jsou uvedeny vazeb poskytovaných systémem, které představují běžné možnosti.  
  
|Název|Účel|  
|----------|-------------|  
|BasicHttpBinding|Interoperabilita s Web services a klienti podporující WS-BasicProfile 1.1 a 1.0 profil základní zabezpečení.|  
|WSHttpBinding|Interoperabilita s Web services a klienti podporující WS-* protokolů přes protokol HTTP.|  
|WSDualHttpBinding|Duplexní komunikaci pomocí protokolu HTTP, podle kterého příjemce původní zprávu neodpovídejte přímo do počáteční odesílatele, ale může přenést libovolný počet odpovědí po určitou dobu pomocí protokolu HTTP v souladu s WS-* protokoly.|  
|Wsfederationbinding –|Komunikaci pomocí protokolu HTTP, ve kterém lze ovládat přístup k prostředkům služby na základě přihlašovacích údajů vydané poskytovatele přihlašovacích údajů explicitně identifikovat.|  
|NetTcpBinding|Bezpečné, spolehlivé a vysoce výkonné komunikace mezi entitami softwaru WCF přes síť.|  
|NetNamedPipeBinding|Bezpečné, spolehlivé a vysoce výkonné komunikace mezi entitami WCF software ve stejném počítači.|  
|netMsmqBinding|Komunikace mezi entitami WCF software pomocí služby MSMQ.|  
|MsmqIntegrationBinding|Komunikace mezi entitou softwaru WCF a jiné entity software pomocí služby MSMQ.|  
|NetPeerTcpBinding|Komunikace mezi entitami softwaru WCF pomocí sítě Peer-to-Peer Windows.|  
  
 Vazeb poskytovaných systémem <xref:System.ServiceModel.BasicHttpBinding>, zahrnuje sadu protokolů podporovaných webových služeb ASP.NET.  
  
 Vlastní vazby WCF aplikací se snadno definují jako kolekce tříd element vazby, které používá WCF k implementaci jednotlivých protokolů. Nové prvky vazby je možné zapisovat na představují další protokoly.  
  
 Vnitřní chování typů služeb je možné upravit pomocí vlastností rodinu tříd pojmenovanou chování. Tady <xref:System.ServiceModel.ServiceBehaviorAttribute> třída se používá k určení, že je typ služby s více vlákny.  
  
```csharp  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple]  
public class DerivativesCalculatorServiceType: IDerivativesCalculator  
```  
  
 Některá chování, jako jsou <xref:System.ServiceModel.ServiceBehaviorAttribute>, jsou atributy. Jiné, ty s vlastnostmi, které byste měli správci nastavit, lze upravit v konfiguraci aplikace.  
  
 V programovacích typy služeb, často používají tvoří <xref:System.ServiceModel.OperationContext> třídy. Jeho statické <xref:System.ServiceModel.OperationContext.Current%2A> vlastnost poskytuje přístup k informacím o kontextu, ve kterém je spuštěná operace. <xref:System.ServiceModel.OperationContext> je podobný i <xref:System.Web.HttpContext> a <xref:System.EnterpriseServices.ContextUtil> třídy.  
  
## <a name="hosting"></a>Hostování  
 Webové služby ASP.NET jsou kompilovány do sestavení knihovny tříd. Soubor s názvem souboru definice služby je za předpokladu, že má příponou .asmx a obsahuje `@ WebService` směrnice, identifikující třídu, která obsahuje kód pro službu a sestavení, ve kterém se nachází.  
  
```  
<%@ WebService Language="C#" Class="Service,ServiceAssembly" %>  
```  
  
 Služba soubor je zkopírován do kořenový adresář aplikace ASP.NET v Internetové informační služby (IIS) a sestavení je zkopírován do podadresáři \bin tento kořenový adresář aplikace. Aplikace je přístupná pak s použitím adresu uniform resource locator (URL) souboru služby v kořenovém adresáři aplikace.  
  
 V rámci služby IIS 5.1 a 6.0, Windows WAS Process Activation Service (), která je k dispozici jako součást služby IIS 7.0, a v rámci všech aplikací .NET, je možné snadno hostovat služby WCF. K hostování služby ve službě IIS 5.1 a 6.0, musíte použít službu HTTP jako protokol pro přenos komunikace.  
  
 K hostování služby IIS 5.1, 6.0 nebo v rámci WAS, použijte následující kroky:  
  
1.  Zkompilujte do sestavení knihovny tříd typ služby.  
  
2.  Vytvořte službu soubor s příponou .svc s `@ ServiceHost` směrnice identifikovat typ služby:  
  
    ```  
    <%@ServiceHost language="c#" Service="MyService" %>  
    ```  
  
3.  Zkopírujte soubor služby do virtuálního adresáře a sestavení, v podadresáři \bin daného virtuálního adresáře.  
  
4.  Zkopírujte konfigurační soubor do virtuálního adresáře a pojmenujte ho souboru Web.config.  
  
 Aplikace je přístupná pak pomocí adresy URL služby souborů v kořenovém adresáři aplikace.  
  
 K hostování služby WCF v rámci aplikace .NET, kompilovat typ služby do aplikace odkazuje sestavení knihovny tříd a aplikací na hostitele služby pomocí programu <xref:System.ServiceModel.ServiceHost> třídy. Následuje příklad základní programování vyžaduje:  
  
```csharp  
string httpBaseAddress = "http://www.contoso.com:8000/";  
string tcpBaseAddress = "net.tcp://www.contoso.com:8080/";  
  
Uri httpBaseAddressUri = new Uri(httpBaseAddress);  
Uri tcpBaseAddressUri = new Uri(tcpBaseAddress);  
  
Uri[] baseAdresses = new Uri[] {   
 httpBaseAddressUri,  
 tcpBaseAddressUri};  
  
using(ServiceHost host = new ServiceHost(  
typeof(Service), //"Service" is the name of the service type baseAdresses))  
{  
     host.Open();  
  
     […] //Wait to receive messages  
     host.Close();  
}  
```  
  
 Tento příklad ukazuje, jak jsou určené adresy pro jeden nebo více protokolů přenosu v procesu vytváření <xref:System.ServiceModel.ServiceHost>. Tyto adresy jsou označovány jako základní adresy.  
  
 Adresa zadaná pro libovolný koncový bod služby WCF je adresa relativní k základní adresa hostitele koncového bodu. Hostitel může mít jednu základní adresu pro každý protokol pro přenos komunikace. V ukázkové konfiguraci v konfiguračním souboru předchozí <xref:System.ServiceModel.BasicHttpBinding> vybrané pro koncový bod používá HTTP jako přenosový protokol, tak adresu koncového bodu, `EchoService`, je relativní vzhledem k základní adresu HTTP hostitele. V případě hostitele v předchozím příkladu je základní adresu HTTP `http://www.contoso.com:8000/`. Služby hostované v rámci služby IIS nebo WAS základní adresa je adresa URL služby souboru služby.  
  
 Pouze služby hostované v IIS nebo WAS a které jsou nakonfigurované s protokolem HTTP jako přenosový protokol výhradně, lze použít možnost režim kompatibility WCF ASP.NET. Zapnutí této možnosti vyžaduje následující kroky.  
  
1.  Musíte přidat programátor <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> atributu pro typ služby a určit, že režim kompatibility ASP.NET je buď povoleno nebo požadováno.  
  
    ```csharp  
    [System.ServiceModel.Activation.AspNetCompatibilityRequirements(  
          RequirementsMode=AspNetCompatbilityRequirementsMode.Require)]  
    public class DerivativesCalculatorServiceType: IDerivativesCalculator  
    ```  
  
2.  Správce musí nakonfigurovat aplikaci, aby používala režim kompatibility ASP.NET.  
  
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
  
     Aplikace WCF je také nakonfigurovat .asmx používat jako rozšíření pro jejich služby souborů a nikoli .svc.  
  
    ```xml  
    <system.web>  
         <compilation>  
          <compilation debug="true">  
          <buildProviders>  
           <remove extension=".asmx"/>  
           <add extension=".asmx"   
            type="System.ServiceModel.ServiceBuildProvider,   
            Systemm.ServiceModel,   
            Version=3.0.0.0,   
            Culture=neutral,   
            PublicKeyToken=b77a5c561934e089" />  
          </buildProviders>  
          </compilation>  
         </compilation>  
    </system.web>  
    ```  
  
     Tuto možnost můžete uložit z museli upravovat klienty, kteří jsou nakonfigurovány pro použití adresy URL služby souborů .asmx při úpravě službu používat WCF.  
  
## <a name="client-development"></a>Vývoj pro klientské  
 Klienti pro webových služeb ASP.NET se generují pomocí nástroje příkazového řádku, WSDL.exe, který obsahuje adresu URL souboru .asmx jako vstup. Nástroj odpovídající poskytované WCF je [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Generuje modul kódu s definicí kontraktu služby a definice třídy klienta WCF. Také generuje konfigurační soubor s adresou a vazby služby.  
  
 V programovacích klienta vzdálené služby je obecně vhodné program podle asynchronního zpracování. Kód generovaný nástrojem WSDL.exe vždy zajišťující synchronního a asynchronního zpracování ve výchozím nastavení. Kód vygenerovaný [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) můžete zadat buď vzor. Ve výchozím nastavení poskytuje pro synchronní vzor. Pokud je spuštěn nástroj `/async` přepnout, generovaný kód poskytuje pro asynchronní zpracování.  
  
 Neexistuje žádná záruka, že názvy tříd klienta WCF generovaných ASP. Nástroj WSDL.exe vaší sítě, ve výchozím nastavení, odpovídaly názvům v generované pomocí nástroje Svcutil.exe třídy klienta WCF. Zejména názvy vlastností třídy, které mají k serializaci pomocí <xref:System.Xml.Serialization.XmlSerializer> ve výchozím nastavení, disponují přípona vlastností v kódu generovaném nástrojem Svcutil.exe, což není případ nástrojem WSDL.exe.  
  
## <a name="message-representation"></a>Reprezentace zprávy  
 Záhlaví SOAP zpráv odesílaných i přijímaných webových služeb ASP.NET se dají přizpůsobit. Třída je odvozena z <xref:System.Web.Services.Protocols.SoapHeader> pro definici struktury hlavičky a pak <xref:System.Web.Services.Protocols.SoapHeaderAttribute> slouží k určení přítomnosti záhlaví.  
  
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
  
 WCF obsahuje atributy, <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, a <xref:System.ServiceModel.MessageBodyMemberAttribute> k popisu struktury protokolu SOAP zprávy odeslané a přijaté službou.  
  
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
public class ItemMesage  
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
  
 Tato syntaxe poskytuje reprezentaci explicitní konstrukce zprávy, že struktura zpráv, které je zahrnuto v kódu webové služby technologie ASP.NET. Také v syntaxi ASP.NET záhlaví zpráv jsou reprezentovány jako vlastnosti služby, například `ProtocolHeader` vlastnost v předchozím příkladu, zatímco ve WCF syntaxe jsou přesněji reprezentována jako vlastnosti zprávy. Navíc WCF umožňuje záhlaví zpráv, které mají být přidány do konfigurace koncových bodů.  
  
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
  
 Možnost umožňuje vyhnout se všechny odkazy na záhlaví infrastruktury protokolu v kódu klienta nebo služby: záhlaví jsou přidány do zprávy z důvodu konfigurace koncového bodu.  
  
## <a name="service-description"></a>Popis služby  
 Vydání požadavku HTTP GET pro soubor .asmx technologie ASP.NET webové služby s dotazem WSDL způsobí, že technologie ASP.NET generuje WSDL k popisu služby. Vrátí, na který WSDL jako odpověď na požadavek.  
  
 ASP.NET 2.0 možné ověřit, že je kompatibilní s Basic Profile 1.1 organizace Interoperability služby webové služby (WS-I) a pro vložení deklarace identity, že služba je kompatibilní s do své WSDL. To znamená dokončeno pomocí `ConformsTo` a `EmitConformanceClaims` parametry <xref:System.Web.Services.WebServiceBindingAttribute> atribut.  
  
```csharp  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 WSDL, který ASP.NET generuje pro službu se dají přizpůsobit. Přizpůsobení probíhají vytvořením odvozené třídy z <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> přidání položek do jazyka WSDL.  
  
 Vydání požadavku HTTP GET s dotazem WSDL souboru .svc služby WCF se nehostují ve službě IIS 51 koncový bod HTTP, 6.0 nebo WAS způsobí, že odpoví WSDL k popisu služby WCF. Vydání požadavku HTTP GET s dotazem WSDL na základní adresu HTTP služby hostované v rámci aplikace .NET má stejný účinek, pokud httpGetEnabled je nastavena na hodnotu true.  
  
 WCF se však také reaguje na požadavky WS-MetadataExchange WSDL, který generuje k popisu služby. Webové služby ASP.NET nemají integrovanou podporu pro WS-MetadataExchange požadavky.  
  
 WSDL, který generuje WCF je možné výrazně přizpůsobit. <xref:System.ServiceModel.Description.ServiceMetadataBehavior> Třída poskytuje některé funkce pro přizpůsobení jazyka WSDL. WCF je možné nakonfigurovat také negeneruje WSDL, ale závisí na použití statický soubor WSDL na dané adrese URL.  
  
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
 V rozhraní ASP.NET Web services jsou vráceny neošetřené výjimky klientům jako chyb SOAP. Můžete také explicitně vyvolat instance <xref:System.Web.Services.Protocols.SoapException> třídy a mít větší kontrolu nad obsahem chybu protokolu SOAP, který získá přenést do klienta.  
  
 Ve službách WCF nevrací neošetřené výjimky klientům jako chyb SOAP, aby se zabránilo neúmyslnému vystavení prostřednictvím výjimky citlivé informace. Konfigurace nastavení je dostupné na mají neošetřené výjimky vracené klientům pro účely ladění.  
  
 Pokud chcete vrátit chyby SOAP pro klienty, můžete vyvolat instance obecného typu <xref:System.ServiceModel.FaultException%601>s použitím kontraktu dat typu, Obecné. Můžete také přidat <xref:System.ServiceModel.FaultContractAttribute> atributy pro operace k určení chyb, které operace mohou zobrazit.  
  
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
  
 Proto za následek chyby je to možné, inzerované v jazyce WSDL pro službu, umožňuje tak klientským programátorům předvídat chyb, které můžete výsledkem operace a zápisu že odpovídající catch – příkazy.  
  
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
 Třída používaný k implementaci technologie ASP.NET webové služby může být odvozena z <xref:System.Web.Services.WebService>.  
  
```csharp  
public class Service : WebService, IEcho  
{  
  
 public string Echo(string input)  
 {  
  return input;  
 }  
}  
```  
  
 V takovém případě mohou být naprogramovány třídu použít <xref:System.Web.Services.WebService> základní třídy vlastnost kontextu pro přístup k <xref:System.Web.HttpContext> objektu. <xref:System.Web.HttpContext> Objektu lze použít k aktualizaci a získat informace o stavu aplikace pomocí vlastností aplikace a slouží k aktualizaci a načtení informací o stavu relace pomocí její vlastnosti relace.  
  
 Technologie ASP.NET poskytuje významnou kontrolu nad kde informace, které jsou přístupné pomocí vlastnosti relace stavu relace <xref:System.Web.HttpContext> skutečně uložená. Mohou být uložena v souborech cookie, databázi, do paměti jako aktuální server nebo paměti určený server. Volba se provádí v konfiguračním souboru služby.  
  
 WCF poskytuje rozšiřitelné objekty pro správu stavu. Rozšiřitelné objekty jsou objekty, které implementují <xref:System.ServiceModel.IExtensibleObject%601>. Nejdůležitější rozšiřitelné objekty jsou <xref:System.ServiceModel.ServiceHostBase> a <xref:System.ServiceModel.InstanceContext>. `ServiceHostBase` umožňuje udržovat stav všech instancí služby typy na stejném hostiteli přístup, zatímco `InstanceContext` umožňuje zachovat stav, který je přístupný libovolnému kódu v rámci stejné instance daného typu služby.  
  
 Tady, typ služby `TradingSystem`, má <xref:System.ServiceModel.ServiceBehaviorAttribute> , která určuje, že všechna volání ze stejné instance klienta WCF se směrují do stejné instance daného typu služby.  
  
```csharp  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]  
public class TradingSystem: ITradingService  
```  
  
 Třída, `DealData`, definuje stav, který je přístupný libovolnému kódu ve stejné instanci daného typu služby s.  
  
```csharp  
internal class DealData: IExtension<InstanceContext>  
{  
 public string DealIdentifier = null;  
 public Trade[] Trades = null;  
}  
```  
  
 V kódu, který implementuje jedné z operací kontraktu služby, typ služby `DealData` stav objektu se přidá do stavu aktuální instance daného typu služby.  
  
```csharp  
string ITradingService.BeginDeal()  
{  
 string dealIdentifier = Guid.NewGuid().ToString();  
 DealData state = new DealData(dealIdentifier);  
 OperationContext.Current.InstanceContext.Extensions.Add(state);  
 return dealIdentifier;  
}  
```  
  
 Tento objekt stavu jde pak načíst a upravovat kód, který implementuje jiné operace kontraktu služby.  
  
```csharp  
void ITradingService.AddTrade(Trade trade)  
{  
 DealData dealData =  OperationContext.Current.InstanceContext.Extensions.Find<DealData>();  
 dealData.AddTrade(trade);  
}  
```  
  
 Informace v stavu kde že technologie ASP.NET poskytuje ovládací prvek průběhu <xref:System.Web.HttpContext> třída je ve skutečnosti uložena, WCF, alespoň v jeho počáteční verze poskytuje žádnou kontrolu nad tím, kde jsou uložená rozšiřitelné objekty. Který představuje nejlepších důvod pro výběr režim kompatibility ASP.NET pro služby WCF. Pokud je nutné konfigurovat stav správy, pak vyžadují pro režim kompatibility ASP.NET umožňuje použít zařízení <xref:System.Web.HttpContext> třídy přesně tak, jak se používají v technologii ASP.NET a taky nakonfigurovat kde informace stavu společností <xref:System.Web.HttpContext> třída je uložena.  
  
## <a name="security"></a>Zabezpečení  
 Možnosti pro zabezpečení webové služby jsou pro zabezpečení všechny aplikace služby IIS. Protože aplikace WCF je možné hostovat nejen v rámci služby IIS, ale také v rámci žádného spustitelného souboru, .NET, možnosti pro zabezpečení aplikací WCF se musí provádět nezávisle na zařízení služby IIS. Zařízení k dispozici pro webové služby ASP.NET jsou ale také k dispozici pro spuštění v režimu kompatibility ASP.NET služby WCF.  
  
### <a name="security-authentication"></a>Zabezpečení: Ověřování  
 Služba IIS poskytuje funkce pro řízení přístupu k aplikacím, které můžete vybrat anonymní přístup nebo různé režimy ověřování: Ověřování Windows, ověřování hodnotou hash, základní ověřování a ověřování pomocí služby .NET Passport. Možnost ověřování Windows lze použít k řízení přístupu k webové služby ASP.NET. Když jsou aplikací služby WCF hostované v rámci služby IIS, služba IIS musí nakonfigurovat tak, aby povolovala anonymní přístup k aplikaci, tak, že ověřování je možné spravovat pomocí WCF, který podporuje ověřování Windows z různých dalších možností. Další možnosti, které jsou integrované zahrnovat uživatelské jméno tokenů, certifikáty X.509, tokeny SAML a služba CardSpace karty, ale je také možné definovat vlastní ověřovací mechanismy.  
  
### <a name="security-impersonation"></a>Zabezpečení: Zosobnění  
 Technologie ASP.NET poskytuje identity element pomocí technologie ASP.NET webové služby můžete provést zosobnění s určitým uživatelem nebo přihlašovacích údajů uživatele podle toho, která jsou součástí aktuálního požadavku. Tento element lze použít ke konfiguraci zosobnění v WCF aplikace běžící v režimu kompatibility ASP.NET.  
  
 Určování určitého uživatele k zosobnění, poskytuje tento systém konfigurace WCF vlastní element identity. Také klienti WCF a služeb můžete nezávisle na sobě nakonfigurovat pro zosobnění. Klienty můžete nakonfigurovat zosobnit aktuálního uživatele, když odesílají žádosti.  
  
```xml  
<behaviors>  
     <behavior name="DerivativesCalculatorClientBehavior">  
      <clientCredentials>  
      <windows allowedImpersonationLevel="Impersonation"/>  
      </clientCredentials>  
     </behavior>  
</behaviors>  
```  
  
 Operace služby je možné nakonfigurovat k zosobnění přihlašovacích údajů uživatele podle toho, která jsou součástí aktuálního požadavku.  
  
```csharp  
[OperationBehavior(Impersonation = ImpersonationOption.Required)]  
public void Receive(Message input)  
```  
  
### <a name="security-authorization-using-access-control-lists"></a>Zabezpečení: Autorizace pomocí seznamů řízení přístupu  
 Seznamy řízení přístupu (ACL) slouží k omezení přístupu k souborům .asmx. Seznamy ACL na hledání souborů .svc WCF se ignorují však s výjimkou v režim kompatibility ASP.NET.  
  
### <a name="security-role-based-authorization"></a>Zabezpečení: Autorizace na základě rolí  
 Možnost ověřování Windows služby IIS můžete použít ve spojení s elementem autorizace k dispozici v jazyce ASP.NET konfigurace usnadňuje ověřování na základě rolí pro webové služby ASP.NET na základě skupin Windows, ke kterým uživatelé jsou přiřazení . ASP.NET 2.0 zavedené obecnější mechanismus ověřování na základě role: role zprostředkovatele.  
  
 Zprostředkovatele rolí jsou třídy, že všechny základní rozhraní pro dotazující o rolích, které je uživatel přiřazenou implementovat, ale každý zprostředkovatele rolí ví, jak načítal příslušné informace z jiného zdroje. ASP.NET 2.0 obsahuje role poskytovatele, který lze načíst přiřazení rolí z databáze Microsoft SQL Server a další, které můžete načíst přiřazení role ze Správce autorizací systému Windows Server 2003.  
  
 Mechanismus poskytovatele role lze použít ve skutečnosti bez ohledu na jejich technologie ASP.NET v jakékoli aplikaci .NET, včetně aplikace WCF. Následující ukázková konfigurace pro aplikace WCF ukazuje, jak pomocí poskytovatele rolí prostředí ASP.NET je možnost vybraná prostřednictvím <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.  
  
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
  
### <a name="security-claims-based-authorization"></a>Zabezpečení: Autorizace na základě rolí  
 Jeden z vašich nejdůležitějších inovace služby WCF je důkladná podpora pro autorizaci přístupu k chráněným prostředkům na základě deklarací identity. Deklarace identity se skládají typu, práva a hodnotu, licence ovladače, třeba. Je sada deklarací o nosiče, z nichž jeden je držitele datum narození. Typ této deklarace identity je datum narození, když hodnota deklarace identity je datum narození ovladače. Pravé straně, který uděluje deklaraci identity nositele Určuje, co můžete dělat nositele hodnotou deklarace identity. V případě deklarace identity ovladače datum narození vpravo je vlastníkem: ovladač disponuje, datum narození ale nelze, například, ji změnit. Autorizace na základě rolí obklopuje autorizace na základě role, protože role jsou typu deklarace identity.  
  
 Autorizace na základě deklarací identity provádí porovnání sadu deklarací identity pro požadavky na přístup, operace a v závislosti na výsledku této porovnání, udělujete nebo odepíráte přístup k operaci. Ve službě WCF, můžete určit třídu se použije ke spuštění autorizace na základě rolí, znovu tak, že přiřadíte hodnotu, která `ServiceAuthorizationManager` vlastnost <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.  
  
```xml  
<behaviors>  
     <behavior name='ServiceBehavior'>  
     <serviceAuthorization   
     serviceAuthorizationManagerType=  
                   'Service.AccessChecker, Service' />  
     </behavior>  
</behaviors>  
```  
  
 Třídy používané pro spuštění ověřování na základě deklarace identity musí být odvozen z <xref:System.ServiceModel.ServiceAuthorizationManager>, který má pouze jednu metodu pro přepsání, `AccessCheck()`. WCF volá tuto metodu pokaždé, když se operace služby, je vyvolána a poskytuje <xref:System.ServiceModel.OperationContext> objektu, který má deklarace pro uživatele v jeho `ServiceSecurityContext.AuthorizationContext` vlastnost. WCF provádí kompletace deklarace identity o uživateli z libovolné tokenu zabezpečení uživatele pro ověřování, které zůstanou k dispozici úkolu vyhodnocení, jestli tyto deklarace identit postačovat pro příslušná operace.  
  
 WCF automaticky sestaví deklarace identity z nejrůznějších typů zabezpečení token je vysoce důležité inovace, protože je kód pro ověření na základě deklarací zcela nezávislé mechanismu ověřování. Naopak autorizace pomocí seznamů řízení přístupu nebo role v technologii ASP.NET je úzce vázané na ověřování Windows.  
  
### <a name="security-confidentiality"></a>Zabezpečení: Důvěrnost  
 Důvěrnost zpráv s webovými službami ASP.NET, které si vyměňují lze zajistit na úrovni přenosu tím, že nakonfigurujete aplikaci v rámci služby IIS, aby používala zabezpečený protokol HTTPS (Hypertext Transfer). Totéž lze provést aplikací služby WCF hostované v rámci služby IIS. Aplikace WCF hostované mimo službu IIS však lze také nastavit pomocí zabezpečeného přenosu protokolu. Důležitější, WCF aplikace lze také nakonfigurovat pro zabezpečení zpráv předtím, než se přenášejí, pomocí protokolu WS-Security. Zabezpečení tělo zprávy pomocí WS-Security umožňuje přenášet důvěrně napříč prostředníci před dosažením konečného cíle.  
  
## <a name="globalization"></a>Globalizace  
 Konfigurace jazyka ASP.NET můžete zadat jazykovou verzi pro jednotlivé služby. WCF nepodporuje toto nastavení konfigurace s výjimkou v režim kompatibility ASP.NET. Chcete-li lokalizovat služby WCF, která nepoužívá režim kompatibility ASP.NET, kompilaci typ služby do sestavení specifické pro jazykovou verzi a mít samostatné koncové body specifické pro jazykovou verzi pro každé sestavení specifické pro jazykovou verzi.  
  
## <a name="see-also"></a>Viz také  
 [Porovnání webových služeb ASP.NET se službou WCF na základě účelu a používaných standardů](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
