---
title: Porovnání webových služeb ASP.NET Web Services s technologií WCF z hlediska vývojových požadavků
ms.date: 03/30/2017
ms.assetid: f362d00e-ce82-484f-9d4f-27e579d5c320
ms.openlocfilehash: fcf2d204d9d59a29024ff09d92be2a7b9339fce9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-development"></a>Porovnání webových služeb ASP.NET Web Services s technologií WCF z hlediska vývojových požadavků
Windows Communication Foundation (WCF) má možnost režim kompatibility ASP.NET umožňují aplikacím WCF být naprogramovaný tak a nakonfigurovaný jako webových služeb ASP.NET a napodobovat jejich chování. V následujících částech porovnání webových služeb ASP.NET a WCF založený na co je potřeba k vývoji aplikací pomocí obou technologií.  
  
## <a name="data-representation"></a>Reprezentace dat  
 Vývoj webové služby pomocí ASP.NET se obvykle začíná definování všechny rozšířené datové typy, které má používat služba. ASP.NET spoléhá na <xref:System.Xml.Serialization.XmlSerializer> přeložit data reprezentována rozhraní .NET Framework typů XML pro přenos do nebo ze služby a překládat data přijatá ve formátu XML do objekty rozhraní .NET Framework. Definování komplexních datové typy, které je použití služby ASP.NET vyžaduje třídy definici rozhraní .NET Framework, který <xref:System.Xml.Serialization.XmlSerializer> může serializovat do a z XML. Těchto tříd lze zapsat ručně, nebo vytvořit z definice typů ve schématu XML pomocí příkazového řádku XML schémata a datových typů podporu nástroji pro xsd.exe.  
  
 Následuje seznam klíčů problémů vědět při definování rozhraní .NET Framework třída, která je <xref:System.Xml.Serialization.XmlSerializer> může serializovat do a z XML:  
  
-   Veřejná pole a vlastnosti objektů rozhraní .NET Framework se přeložit na XML.  
  
-   Instance třídy kolekce můžete serializován do souboru XML, pouze v případě, že třídy implementovat buď <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.ICollection> rozhraní.  
  
-   Třídy implementující <xref:System.Collections.IDictionary> rozhraní, jako například <xref:System.Collections.Hashtable>, nesmí být serializován do souboru XML.  
  
-   Dobře mnoho typů v atributu <xref:System.Xml.Serialization> oboru názvů lze přidat do třídy rozhraní .NET Framework a její členy k řízení zastoupení instancí třídy ve formátu XML.  
  
 Vývoj aplikací WCF obvykle také začíná definici komplexních typů. WCF lze používat stejné typy rozhraní .NET Framework jako webové služby ASP.NET.  
  
 WCF<xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> lze přidat na typy rozhraní .NET Framework, které určují, že instance typu se k serializaci do XML a které konkrétní pole nebo vlastnosti typu se k serializaci, jak je znázorněno v následujícím ukázkovém kódu.  
  
```  
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
  
 <xref:System.Runtime.Serialization.DataContractAttribute> Označuje, že nulový nebo nenulový počet typ pole nebo vlastnosti mají být serializován, při <xref:System.Runtime.Serialization.DataMemberAttribute> označuje, že pole nebo vlastnost je k serializaci. <xref:System.Runtime.Serialization.DataContractAttribute> Lze použít ke třídě nebo struktuře. <xref:System.Runtime.Serialization.DataMemberAttribute> Můžete použít pro pole nebo vlastnost a pole a vlastnosti, na které se použije atribut může být veřejné nebo soukromé. Instance typy, které mají <xref:System.Runtime.Serialization.DataContractAttribute> u nich se označuje jako měnící data ve službě WCF. Jsou serializován do souboru XML pomocí <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 Tady je seznam důležitých rozdílů mezi použitím <xref:System.Runtime.Serialization.DataContractSerializer> a pomocí <xref:System.Xml.Serialization.XmlSerializer> a různé atributy <xref:System.Xml.Serialization> oboru názvů.  
  
-   <xref:System.Xml.Serialization.XmlSerializer> a atributy <xref:System.Xml.Serialization> obor názvů jsou navržené tak, abyste mohli k mapování typů rozhraní .NET Framework na libovolný platný typ definovaná ve schématu XML, a proto poskytují velmi přesné kontrolu nad zastoupení typu v kódu XML. <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> poskytují velmi malé kontrolu nad zastoupení typu v kódu XML. Můžete zadat pouze obory názvů a názvy používá k reprezentování typ a příslušné pole a vlastnosti v souboru XML a pořadí, ve kterém polí a vlastností zobrazí v souboru XML:  
  
    ```  
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
  
     Všem ostatním o struktuře XML, který představuje typ rozhraní .NET je dáno <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
-   Díky tomu, že není možností řízení jak typu je možné vyjádřit v XML, stane vysoce předvídatelný pro proces serializace <xref:System.Runtime.Serialization.DataContractSerializer>a tím, snazší za účelem optimalizace. Praktické výhodou návrh <xref:System.Runtime.Serialization.DataContractSerializer> je lepší výkon, přibližně deset procent lepší výkon.  
  
-   Atributy pro použití s <xref:System.Xml.Serialization.XmlSerializer> neoznačují které pole nebo vlastnosti typu se serializován do souboru XML, zatímco <xref:System.Runtime.Serialization.DataMemberAttribute> pro použití s <xref:System.Runtime.Serialization.DataContractSerializer> explicitně zobrazuje vlastnosti nebo pole, které se serializují. Kontrakty dat jsou proto explicitní kontrakty o struktuře data, která aplikace je k odesílání a příjmu.  
  
-   <xref:System.Xml.Serialization.XmlSerializer> Může překládat pouze veřejné členy objektu .NET do souboru XML, <xref:System.Runtime.Serialization.DataContractSerializer> může překládat členy objektů do souboru XML bez ohledu na to modifikátory přístupu těchto členů.  
  
-   V důsledku schopnost serializovat neveřejným členy typy do souboru XML, <xref:System.Runtime.Serialization.DataContractSerializer> má méně omezení pro různé typy .NET, které mohou serializovat do souboru XML. Konkrétně může překládat do typy XML jako <xref:System.Collections.Hashtable> implementující <xref:System.Collections.IDictionary> rozhraní. <xref:System.Runtime.Serialization.DataContractSerializer> Je mnohem pravděpodobnější mohli k serializaci instancí všechny existující typ formátu .NET do XML bez nutnosti upravte definici typu nebo vývoj obálku pro ni.  
  
-   Jiné důsledkem <xref:System.Runtime.Serialization.DataContractSerializer> nebudete mít přístup k neveřejným členy typu je, že vyžaduje úplný vztah důvěryhodnosti, zatímco <xref:System.Xml.Serialization.XmlSerializer> neexistuje. Oprávnění úplný vztah důvěryhodnosti k kódu poskytuje úplný přístup ke všem prostředkům na počítači, který je přístupný pomocí přihlašovacích údajů, za kterých je prováděna kód. Tato možnost by měla použít dát pozor, jako plně důvěryhodný kód přistupuje k všechny prostředky ve vašem počítači.  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer> Zahrnuje některé podporu pro správu verzí:  
  
    -   <xref:System.Runtime.Serialization.DataMemberAttribute> Má <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> vlastnost, která může být přiřazena hodnota false pro členy, které jsou přidány do nové verze kontraktu dat, které nebyly v dřívějších verzích, a tím povolíte aplikací s novější verzí kontrakt jako schopna zpracovat starší verze.  
  
    -   Tak, že kontraktu dat implementovat <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní, jeden můžete povolit <xref:System.Runtime.Serialization.DataContractSerializer> předat členy definované v novější verze sady kontraktu dat prostřednictvím aplikací s předchozími verzemi smlouvy.  
  
 I přes všechny rozdíly, XML, do kterého <xref:System.Xml.Serialization.XmlSerializer> serializuje typu ve výchozím nastavení je sémanticky stejný jako soubor XML, do kterého <xref:System.Runtime.Serialization.DataContractSerializer> serializuje typu zadaný obor názvů pro soubor XML byl explicitně definován. Následující třídy, která má atributy pro použití s oběma serializátorů, je přeložit na sémanticky identické XML pomocí <xref:System.Xml.Serialization.XmlSerializer> a <xref:System.Runtime.Serialization.DataContractAttribute>:  
  
```  
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
  
 Windows software development kit (SDK) zahrnuje nástroj příkazového řádku volat [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Nástroj xsd.exe použít s webovými službami ASP.NET, jako například Svcutil.exe může generovat definice datových typů .NET ze schématu XML. Typy jsou kontrakty dat, pokud <xref:System.Runtime.Serialization.DataContractSerializer> můžete emitování XML ve formátu XML schéma definované; jinak, jsou určené pro použití serializace <xref:System.Xml.Serialization.XmlSerializer>. Svcutil.exe může také generovat schéma XML z kontrakty dat pomocí jeho `dataContractOnly` přepínače.  
  
> [!NOTE]
>  I když webových služeb ASP.NET použijte <xref:System.Xml.Serialization.XmlSerializer>a režim kompatibility WCF ASP.NET umožňuje služby WCF, které napodobují chování webových služeb ASP.NET, možnost kompatibility ASP.NET neomezuje jeden pomocí <xref:System.Xml.Serialization.XmlSerializer>. Stále můžete použít <xref:System.Runtime.Serialization.DataContractSerializer> do služeb spuštěných v režimu kompatibility ASP.NET.  
  
## <a name="service-development"></a>Vývoj pro služby  
 K vývoji služby pomocí ASP.NET, byla obvyklé přidat <xref:System.Web.Services.WebService> atribut na třídu a <xref:System.Web.Services.WebMethodAttribute> na některou z metod této třídy, které mají být operace služby:  
  
```  
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
  
```  
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
  
 Tato možnost je jako upřednostňované, protože rozhraní s <xref:System.Web.Services.WebService> atribut se považuje za kontraktu pro operace prováděné na službu, kterou lze opětovně použít s různými třídami, které může implementovat stejné kontraktu různými způsoby.  
  
 Služby WCF se poskytuje tak, že definujete jeden nebo více koncových bodů WCF. Koncový bod je definována adresy, vazby a kontraktu služby. Adresa definuje, kde se služba nachází. Vazba Určuje, jak se komunikovat se službou. Kontrakt služby definuje operace, které můžete provádět službu.  
  
 Kontrakt služby je obvykle definováno nejprve přidáním <xref:System.ServiceModel.ServiceContractAttribute> a <xref:System.ServiceModel.OperationContractAttribute> k rozhraní:  
  
```  
[ServiceContract]  
public interface IEcho  
{  
     [OperationContract]  
     string Echo(string input);  
}  
```  
  
 <xref:System.ServiceModel.ServiceContractAttribute> Určuje, že rozhraní definuje kontraktu služby WCF a <xref:System.ServiceModel.OperationContractAttribute> označuje, která, pokud existuje, metod rozhraní definuje operace kontrakt služby.  
  
 Po definování kontraktu služby, je implementována ve třídě, tak, že třída implementovat rozhraní, ve které je definováno kontrakt služby:  
  
```  
public class Service : IEcho  
{  
    public string Echo(string input)  
    {  
       return input;  
    }  
}  
```  
  
 Třídu, která implementuje kontraktu služby se označuje jako služba zadejte ve WCF.  
  
 Dalším krokem je adresu a vazbu přidružit typ služby. Která se obvykle provádí v konfiguračním souboru buď úpravou souboru přímo, nebo v editoru konfigurace zadat s použitím technologie WCF. Tady je příklad konfiguračního souboru.  
  
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
  
 Vazba určuje sadu protokolů pro komunikaci s aplikací. Následující tabulka uvádí vazby poskytované systémem, které reprezentují běžné možnosti.  
  
|Název|Účel|  
|----------|-------------|  
|BasicHttpBinding|Vzájemná funkční spolupráce s webovými službami a podpůrné služby WS-BasicProfile 1.1 a 1.0 profil základní zabezpečení klientů.|  
|WSHttpBinding|Vzájemná funkční spolupráce s webovými službami a klienty, kteří podporují WS-* protokoly prostřednictvím protokolu HTTP.|  
|– WSDualHttpBinding|Duplexní komunikaci pomocí protokolu HTTP, podle kterého příjemce úvodní zpráva není odpověď přímo do počáteční odesílatele, ale může přenášet libovolný počet odpovědi přes v časovém intervalu pomocí protokolu HTTP v souladu s WS-* protokoly.|  
|Wsfederationbinding –|Komunikaci pomocí protokolu HTTP, ve kterém lze řídit přístup k prostředkům služby založené na přihlašovací údaje vystavený poskytovatele explicitně identifikovat přihlašovacích údajů.|  
|NetTcpBinding|Bezpečné, spolehlivé a vysoce výkonné komunikace mezi WCF softwaru entity v síti.|  
|NetNamedPipeBinding|Bezpečné, spolehlivé a vysoce výkonné komunikaci mezi entitami softwaru WCF na stejném počítači.|  
|– NetMsmqBinding|Komunikace mezi entitami softwaru WCF pomocí služby MSMQ.|  
|MsmqIntegrationBinding|Komunikace mezi entity softwaru WCF a jinou entitou softwaru pomocí služby MSMQ.|  
|NetPeerTcpBinding|Komunikace mezi entitami softwaru WCF pomocí sítě Windows Peer-to-Peer.|  
  
 Vazby poskytované systémem <xref:System.ServiceModel.BasicHttpBinding>, zahrnuje sadu protokolů podporovaných webových služeb ASP.NET.  
  
 Vlastní vazby WCF aplikací jsou snadno definované jako kolekce tříd element vazby, které WCF používá k implementaci jednotlivých protokolů. Nové prvky vazby je možné zapsat do představují další protokoly.  
  
 Interní chování typů služeb lze upravit pomocí vlastností rodiny třídy názvem chování. Zde <xref:System.ServiceModel.ServiceBehaviorAttribute> třída se používá k určení, že je typ služby s více vlákny.  
  
```  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple]  
public class DerivativesCalculatorServiceType: IDerivativesCalculator  
```  
  
 Některé chování jako <xref:System.ServiceModel.ServiceBehaviorAttribute>, atributů. Ostatní těm, které jsou s vlastnostmi, které správce chtít nastavit, můžete změnit v konfiguraci aplikace.  
  
 V programování typů služeb, často využívání <xref:System.ServiceModel.OperationContext> třídy. Jeho statické <xref:System.ServiceModel.OperationContext.Current%2A> vlastnost poskytuje přístup k informacím o kontextu, ve kterém je spuštěna operace. <xref:System.ServiceModel.OperationContext> je podobná i <xref:System.Web.HttpContext> a <xref:System.EnterpriseServices.ContextUtil> třídy.  
  
## <a name="hosting"></a>Hostování  
 Webových služeb ASP.NET kompilovány do sestavení knihovny tříd. Soubor s názvem souboru služby je za předpokladu, že má .asmx rozšíření a obsahuje `@ WebService` direktiva, která identifikuje třídu, která obsahuje kód pro tuto službu a sestavení, ve kterém se nachází.  
  
```  
<%@ WebService Language="C#" Class="Service,ServiceAssembly" %>  
```  
  
 Soubor služby se zkopíruje do kořenový adresář aplikace ASP.NET v Internetové informační služby (IIS) a sestavení se zkopíruje do podadresáři \bin tento kořenový adresář aplikace. Aplikace je pak přístupné pomocí uniform resource locator (URL) souboru služby v kořenovém adresáři aplikace.  
  
 Služby WCF se dají snadno hostovat v rámci služby IIS 5.1 nebo 6.0, proces aktivace služby WAS (Windows), je dodáván jako součást služby IIS 7.0, a v rámci všech aplikací .NET. K hostování služby IIS 5.1 nebo 6.0, musíte službu používají protokol HTTP jako protokol pro přenos komunikace.  
  
 K hostování služby v rámci služby IIS 5.1, 6.0 nebo WAS, použijte postup následovně:  
  
1.  Zkompilujte typ služby do sestavení knihovny tříd.  
  
2.  Vytvoření služby souboru s příponou .svc s `@ ServiceHost` – direktiva k identifikaci typ služby:  
  
    ```  
    <%@ServiceHost language="c#" Service="MyService" %>  
    ```  
  
3.  Zkopírujte soubor služby do virtuálního adresáře a sestavení, v podadresáři \bin tento virtuální adresář.  
  
4.  Zkopírujte konfigurační soubor do virtuálního adresáře a název souboru Web.config.  
  
 Aplikace je pak přístupné pomocí adresu URL souboru služby v kořenovém adresáři aplikace.  
  
 K hostování služby WCF v rámci aplikace .NET, zkompilování typ služby do třídy knihovny sestavení odkazuje aplikace a aplikaci na hostitele služby pomocí <xref:System.ServiceModel.ServiceHost> třídy. Následuje příklad základní programování vyžaduje:  
  
```  
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
  
 Tento příklad ukazuje, jak jsou při sestavování zadané adresy pro jeden nebo více přenosové protokoly <xref:System.ServiceModel.ServiceHost>. Tyto adresy jsou označovány jako základní adresy.  
  
 Adresa zadaná pro libovolný koncový bod služby WCF je adresu relativně k základní adresa hostitele pro koncový bod. Hostitel může mít jeden základní adresa pro každý protokol pro přenos komunikace. V konfiguraci ukázka v předchozím konfiguračním souboru <xref:System.ServiceModel.BasicHttpBinding> vybrané pro používá koncový bod HTTP jako protokol pro přenos, takže adresa koncového bodu, `EchoService`, je relativní vzhledem k základní adresu HTTP hostitele. V případě hostitele v předchozím příkladu je základní adresu HTTP http://www.contoso.com:8000/. Pro služby hostované v rámci služby IIS nebo WAS základní adresa je adresa URL souboru služby, služby.  
  
 Pouze služby hostované ve službě IIS nebo WAS a které jsou nakonfigurované s protokolem HTTP jako přenosový protokol výhradně, lze použít možnost režim kompatibility WCF ASP.NET. Tuto možnost zapnete vyžaduje následující kroky.  
  
1.  Musíte přidat programátorů <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> atribut typu služby a určit, že režim kompatibility ASP.NET je buď povoleno nebo požadováno.  
  
    ```  
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
  
     Aplikace, WCF můžete nakonfigurovat také používat pro své služby souborů a nikoli .svc .asmx jako rozšíření.  
  
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
  
     Tuto možnost můžete uložit z museli změnit klienty, které jsou nakonfigurované na použití adresy URL služby souborů .asmx při úpravě služby Pokud chcete použít WCF.  
  
## <a name="client-development"></a>Vývoj pro klienta  
 Klienti pro ASP.NET Web services jsou generovány pomocí nástroje příkazového řádku, WSDL.exe, který obsahuje adresu URL souboru .asmx jako vstup. Nástroj odpovídající poskytované WCF je [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Vygeneruje kód modul s definici kontraktu služby a definice třídy klienta WCF. Také vytváří konfigurační soubor s adresou a vazby služby.  
  
 V programování klienta vzdálené služby je většinou vhodné programu podle asynchronní vzor. Kód vygenerovaný nástroj WSDL.exe vždy poskytuje pro synchronní a asynchronní vzor ve výchozím nastavení. Kód vygenerovaný [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) můžete zadat buď vzor. Poskytuje synchronní vzor ve výchozím nastavení. Pokud je nástroj spuštěn s `/async` přepínače, pak poskytuje generovaný kód pro asynchronní vzor.  
  
 Není zaručeno, že názvy v třídy klienta WCF generované ASP. Nástroj WSDL.exe NET je ve výchozím nastavení, odpovídat názvům v nástroje Svcutil.exe vygenerované třídy klienta WCF. Na konkrétní názvy vlastnosti tříd, které mají k serializaci pomocí <xref:System.Xml.Serialization.XmlSerializer> ve výchozím nastavení, mají v kód vygenerovaný nástroje Svcutil.exe, která není v případě s nástroj WSDL.exe příponu vlastnost.  
  
## <a name="message-representation"></a>Reprezentace zprávy  
 Hlavičky SOAP zpráv odesílaných i přijímaných v: webových služeb ASP.NET můžete přizpůsobit. Třída je odvozený od <xref:System.Web.Services.Protocols.SoapHeader> definovat strukturu hlavičky a potom <xref:System.Web.Services.Protocols.SoapHeaderAttribute> slouží k určení přítomnosti záhlaví.  
  
```  
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
  
 WCF poskytuje atributy, <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, a <xref:System.ServiceModel.MessageBodyMemberAttribute> k popisu struktury protokolu SOAP zprávy odeslané a přijaté službou.  
  
```  
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
  
 Tuto syntaxi vypočítá explicitní reprezentace strukturu zprávy, zatímco strukturu zprávy je zahrnuto v kódu webové služby technologie ASP.NET. Také v syntaxi ASP.NET hlavičky zpráv jsou reprezentovány jako vlastnosti služby, například `ProtocolHeader` vlastnost v předchozím příkladu, že v syntaxi WCF, jsou přesněji reprezentována jako vlastnosti zprávy. Navíc WCF umožňuje hlavičky zpráv, který se má přidat ke konfiguraci koncových bodů.  
  
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
  
 Možnost umožňuje vyhnout se všechny odkazy na infrastruktury protokolu hlavičky v kódu pro klienta služby nebo: hlavičky jsou přidány do zprávy z důvodu konfigurace koncového bodu.  
  
## <a name="service-description"></a>Popis služby  
 Vydání požadavku HTTP GET pro soubor .asmx ASP.NET webové služby s dotazem WSDL způsobí, že ASP.NET, aby generoval WSDL k popisu služby. Vrací, které WSDL jako odpověď na žádost.  
  
 ASP.NET 2.0 možné ověřit, jestli je kompatibilní s Basic Profile 1.1 organizace interoperabilita služby webové služby (WS-I) a vložit deklaraci, zda je služba kompatibilní do své WSDL. To znamená done pomocí `ConformsTo` a `EmitConformanceClaims` parametry <xref:System.Web.Services.WebServiceBindingAttribute> atribut.  
  
```  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 WSDL, který ASP.NET generuje pro službu lze přizpůsobit. Přizpůsobení probíhají vytvořením třídy odvozené z <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> k přidávání položek do schématu WSDL.  
  
 Vydání požadavku HTTP GET s dotazem WSDL pro soubor .svc služby WCF s hostovaným v rámci služby IIS 51 koncový bod protokolu HTTP, 6.0 nebo WAS způsobí, že chcete odpovídat WSDL k popisu služby WCF. Vydání požadavku HTTP GET s dotazem WSDL základní adresu HTTP služby hostované v rámci aplikace .NET má stejný účinek, pokud httpGetEnabled nastavena na hodnotu true.  
  
 WCF se však také odpovídá na požadavky služby WS-MetadataExchange s WSDL, který ho generuje k popisu služby. Webových služeb ASP.NET nemají integrovanou podporu pro WS-MetadataExchange požadavky.  
  
 WSDL, který generuje WCF lze hojně přizpůsobit. <xref:System.ServiceModel.Description.ServiceMetadataBehavior> Třída zajišťuje některé funkce pro přizpůsobení schématu WSDL. WCF můžete nakonfigurovat také v negeneruje WSDL, ale spíše na použití statických souborů WSDL na dané adrese URL.  
  
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
 Nezpracované výjimky jsou v webových služeb ASP.NET, vracené klientům. jako chyb SOAP. Můžete také explicitně vyvolat instance <xref:System.Web.Services.Protocols.SoapException> třídy a mít větší kontrolu nad obsah chybu protokolu SOAP, který získá odeslány klientovi.  
  
 Ve službách WCF nebudou zobrazeny neošetřených výjimek klientům jako chyb SOAP, aby se zabránilo citlivé informace, které můžou neúmyslně zpřístupnit prostřednictvím výjimky. Nastavení konfigurace je k dispozici do mají neošetřené výjimky vracené klientům. pro účely ladění.  
  
 Pokud chcete vrátit chyb SOAP klientům, můžete vyvolat instancí obecného typu <xref:System.ServiceModel.FaultException%601>pomocí kontraktu dat typu jako obecného typu. Můžete také přidat <xref:System.ServiceModel.FaultContractAttribute> atributů k operacím k určení chyb, které může yield operace.  
  
```  
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
  
 To tak, že má za následek možné chyby inzerovaných ve schématu WSDL pro službu, umožňuje tak klientským programátorům předvídat chyb, které můžete výsledkem operace a zápisu že odpovídající catch příkazy.  
  
```  
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
  
## <a name="state-management"></a>Stav správy  
 Třída, která slouží k implementaci ASP.NET webové služby může být odvozen od <xref:System.Web.Services.WebService>.  
  
```  
public class Service : WebService, IEcho  
{  
  
 public string Echo(string input)  
 {  
  return input;  
 }  
}  
```  
  
 V takovém případě třída může být naprogramovaný tak, aby použít <xref:System.Web.Services.WebService> základní kontext vlastnosti třídy se pro přístup k <xref:System.Web.HttpContext> objektu. <xref:System.Web.HttpContext> Objekt lze použít k aktualizaci a načíst informace o stavu aplikace pomocí jeho vlastnosti aplikace a slouží k aktualizaci a načíst informace o stavu relace pomocí jeho vlastnost relace.  
  
 Technologie ASP.NET poskytuje značnou kontrolu nad kde stavu relace informace přistupovat pomocí vlastnosti relace <xref:System.Web.HttpContext> je ve skutečnosti uložen. Může být uložená v souborech cookie, v databázi, v paměti aktuálního serveru nebo v paměti na určený server. Volba se provádí v konfiguračním souboru služby.  
  
 WCF poskytuje rozšiřitelné objekty pro správu stavu. Rozšiřitelné objekty jsou objekty, které implementují <xref:System.ServiceModel.IExtensibleObject%601>. Nejdůležitější rozšiřitelné objekty jsou <xref:System.ServiceModel.ServiceHostBase> a <xref:System.ServiceModel.InstanceContext>. `ServiceHostBase` umožňuje udržovat stav všech instancí služby všechny typy na stejném hostiteli mohou získat přístup, při `InstanceContext` umožňuje udržovat stav, který je přístupný pomocí žádný kód běžící v rámci stejné instance typu služby.  
  
 Tady, typ služby `TradingSystem`, má <xref:System.ServiceModel.ServiceBehaviorAttribute> určující, zda všechna volání ze stejné instance klienta WCF směrují na stejnou instanci typu služby.  
  
```  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]  
public class TradingSystem: ITradingService  
```  
  
 Třída, `DealData`, definuje stav, který je přístupný pomocí jakékoli kód spuštěný ve stejné instanci typu služby.  
  
```  
internal class DealData: IExtension<InstanceContext>  
{  
 public string DealIdentifier = null;  
 public Trade[] Trades = null;  
}  
```  
  
 V kódu typu služby, který implementuje některé z operací kontrakt služby `DealData` stav objektu se přidá do stavu aktuální instance typu služby.  
  
```  
string ITradingService.BeginDeal()  
{  
 string dealIdentifier = Guid.NewGuid().ToString();  
 DealData state = new DealData(dealIdentifier);  
 OperationContext.Current.InstanceContext.Extensions.Add(state);  
 return dealIdentifier;  
}  
```  
  
 Tento objekt stavu můžete pak načíst a upravovat kód, který implementuje jiné operace kontrakt služby.  
  
```  
void ITradingService.AddTrade(Trade trade)  
{  
 DealData dealData =  OperationContext.Current.InstanceContext.Extensions.Find<DealData>();  
 dealData.AddTrade(trade);  
}  
```  
  
 Zatímco technologie ASP.NET poskytuje ovládací prvek přes kde stavu informace v <xref:System.Web.HttpContext> třída je ve skutečnosti uložena, WCF, alespoň v jeho počáteční verze poskytuje žádnou kontrolu nad úložiště rozšiřitelné objekty. Která se považuje za velmi nejlepší důvod pro výběr režim kompatibility ASP.NET služby WCF. Pokud je nutné konfigurovat stav správy, pak pro režim kompatibility ASP.NET výslovném umožňuje používat zařízení <xref:System.Web.HttpContext> třída přesně tak, jak se používají v technologii ASP.NET a taky nakonfigurovat kde stavu informace, které jsou spravované pomocí <xref:System.Web.HttpContext> třída je uložena.  
  
## <a name="security"></a>Zabezpečení  
 Možnosti zabezpečení rozhraní ASP.NET Web služeb jsou pro zabezpečení všechny aplikace služby IIS. Protože WCF aplikace může být hostovaný pouze v rámci služby IIS, ale také v rámci všech spustitelný soubor rozhraní .NET, možnosti zabezpečení aplikací WCF musí být provedeny nezávislá funkce služby IIS. Zařízení, které jsou pro ASP.NET Web services jsou však také k dispozici pro spuštění v režimu kompatibility ASP.NET služby WCF.  
  
### <a name="security-authentication"></a>Zabezpečení: ověřování  
 Služba IIS poskytuje možnosti pro řízení přístupu k aplikacím, které můžete vybrat buď anonymní přístup, nebo různé režimy ověřování: ověřování systému Windows, ověřování hodnotou hash, základní ověřování a ověřování .NET Passport. Možnost ověřování systému Windows lze použít k řízení přístupu k webové služby ASP.NET. Nicméně když jsou aplikací služby WCF hostované v rámci služby IIS, IIS musí být nakonfigurovány tak, aby povolovala anonymní přístup k aplikaci, tak, že ověřování je možné spravovat pomocí WCF samostatně, který podporuje ověřování systému Windows mezi různé další možnosti. Další možnosti, které jsou integrované zahrnovat uživatelské jméno tokeny, certifikáty X.509, tokeny SAML a služba CardSpace karet, ale může být také definováno vlastních ověřovacích mechanismů.  
  
### <a name="security-impersonation"></a>Zabezpečení: zosobnění  
 Technologie ASP.NET poskytuje identity element který ASP.NET webové služby, můžete provést zosobnění konkrétní uživatele nebo přihlašovacích údajů uživatele podle toho, která jsou k dispozici s aktuální požadavek. Tento element slouží ke konfiguraci zosobnění v WCF aplikace spuštěné v režimu kompatibility ASP.NET.  
  
 Konfigurační systém WCF poskytuje vlastní element identity pro určení konkrétního uživatele k zosobnění. Navíc klienti WCF a služeb mohou být nezávisle konfigurovány pro zosobnění. Klienti lze nakonfigurovat k zosobnění s aktuálním uživatelem při odesílají žádosti.  
  
```xml  
<behaviors>  
     <behavior name="DerivativesCalculatorClientBehavior">  
      <clientCredentials>  
      <windows allowedImpersonationLevel="Impersonation"/>  
      </clientCredentials>  
     </behavior>  
</behaviors>  
```  
  
 Operace služby se dá nakonfigurovat k zosobnění přihlašovacích údajů uživatele podle toho, která jsou k dispozici s aktuální požadavek.  
  
```  
[OperationBehavior(Impersonation = ImpersonationOption.Required)]  
public void Receive(Message input)  
```  
  
### <a name="security-authorization-using-access-control-lists"></a>Zabezpečení: Autorizace pomocí seznamů řízení přístupu  
 Seznamy řízení přístupu (ACL) umožňuje omezit přístup k souborům .asmx. Seznamy ACL v souborů .svc WCF se ignorují, ale s výjimkou v režimu kompatibility ASP.NET.  
  
### <a name="security-role-based-authorization"></a>Zabezpečení: Ověření na základě Role  
 Možnost ověřování systému Windows služby IIS lze použít ve spojení s zadaný element autorizace podle jazyka konfigurace ASP.NET pro usnadnění autorizace na základě rolí pro webové služby ASP.NET podle skupiny systému Windows, k nimž uživatelé přiřazeni . ASP.NET 2.0 zavedená obecnější mechanismus ověřování na základě rolí: zprostředkovatelů rolí.  
  
 Zprostředkovatelé role jsou třídy, že všechny implementovat základní rozhraní pro dotazující o rolích, ke kterým je přiřazen uživatele, ale každý zprostředkovatele rolí umí k načtení těchto informací z jiného zdroje. ASP.NET 2.0 obsahuje role zprostředkovatele, který přiřazení rolí můžete načíst z databáze Microsoft SQL Server a další, které mohou načítat přiřazení rolí ze Správce autorizací systému Windows Server 2003.  
  
 Tento mechanismus role zprostředkovatele lze použít ve skutečnosti nezávisle na ASP.NET v jakékoli aplikaci .NET, včetně aplikace WCF. Následující ukázka konfigurace pro aplikaci WCF ukazuje způsob použití poskytovatele rolí prostředí ASP.NET je možnost vybraná prostřednictvím <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.  
  
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
  
### <a name="security-claims-based-authorization"></a>Zabezpečení: Autorizace založené na deklaracích identity  
 Jedním z nejdůležitějších inovace služby WCF je jeho důkladné podporu pro autorizaci přístupu k chráněným prostředkům na základě deklarací. Deklarace identity skládá z typu, doprava a hodnotu, licence ovladače, třeba. Umožňuje sadu deklarací identity o nosiče, z nichž jeden je držitele datum narození. Typ této deklarace identity je datum narození, když hodnota deklarace identity je datum narození ovladače. Oprávnění, který deklaraci identity svěřuje nosiče Určuje, co dělat s hodnotou deklarace identity nosiče. V případě deklarace identity ovladač datum narození, vpravo se u sebe: ovladač má, datum narození ale nejde, třeba, změnu. Na základě deklarace autorizace uzavře autorizace na základě rolí, protože role jsou typu deklarace identity.  
  
 Na základě deklarací autorizace provádí porovnávání sadu deklarací identity pro požadavky na přístup operace a to v závislosti na výsledku této porovnání, přidělování nebo odmítání přístupu pro operaci. Ve službě WCF, můžete zadat třídu se použije ke spuštění na základě deklarace autorizace znovu přiřazením hodnoty na `ServiceAuthorizationManager` vlastnost <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.  
  
```xml  
<behaviors>  
     <behavior name='ServiceBehavior'>  
     <serviceAuthorization   
     serviceAuthorizationManagerType=  
                   'Service.AccessChecker, Service' />  
     </behavior>  
</behaviors>  
```  
  
 Třídy používané ke spuštění ověření na základě deklarace identity musí být odvozeny od <xref:System.ServiceModel.ServiceAuthorizationManager>, který má jenom jednu metodu přepsat, `AccessCheck()`. WCF volá tuto metodu vždy, když je volána operace služby a poskytuje <xref:System.ServiceModel.OperationContext> objekt, který se má deklarace pro uživatele v jeho `ServiceSecurityContext.AuthorizationContext` vlastnost. WCF podporuje práci při sestavování deklarace identity o uživateli z tokenu jakoukoli zabezpečení uživatele zadaná pro ověřování, což ponechá úkolu vyhodnocení, zda tyto deklarace identity stačit pro operace.  
  
 Že WCF automaticky sestaví deklarace identity z jakéhokoli druhu zabezpečení token je vysoce významnou inovaci, protože umožňuje kód pro ověřování na základě deklarací zcela nezávislé na ověřovací mechanismus. Naopak autorizace pomocí seznamů řízení přístupu nebo role v ASP.NET úzce souvisí ověřování systému Windows.  
  
### <a name="security-confidentiality"></a>Zabezpečení: důvěrnost  
 Důvěrnost zprávy vyměňují s webovými službami ASP.NET můžete zajistit na úrovni přenosu konfigurace aplikace v rámci služby IIS pro používání zabezpečené protokol HTTPS (Hypertext Transfer). Pro aplikace WCF hostované v rámci služby IIS lze provést stejný. Aplikace WCF hostované mimo služby IIS však lze také nastavit pro použití protokolu zabezpečení přenosu. Důležitější, aplikace WCF je také možné nakonfigurovat zabezpečit zprávy předtím, než jsou přenosu, pomocí protokolu WS-zabezpečení. Zabezpečení právě tělo zprávy pomocí protokolu WS-Security umožňuje přenášet jako s důvěrnými napříč prostředníci před dosažením konečného cíle.  
  
## <a name="globalization"></a>Globalizace  
 Jazyk konfigurace ASP.NET můžete zadat jazykovou verzi pro jednotlivé služby. WCF nepodporuje toto nastavení konfigurace s výjimkou v režimu kompatibility ASP.NET. O lokalizaci služby WCF, který nepoužívá režim kompatibility ASP.NET, zkompilovat typ služby do sestavení specifické pro jazykovou verzi a mít samostatné koncové body specifické pro jazykovou verzi pro každé sestavení specifické pro jazykovou verzi.  
  
## <a name="see-also"></a>Viz také  
 [Porovnání webových služeb ASP.NET se službou WCF na základě účelu a používaných standardů](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
