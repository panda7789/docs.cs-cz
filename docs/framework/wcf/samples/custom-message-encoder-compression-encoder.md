---
title: 'Vlastní kodér zpráv: Kompresní kodér'
ms.date: 03/30/2017
ms.assetid: 57450b6c-89fe-4b8a-8376-3d794857bfd7
ms.openlocfilehash: b70875e385fa32256476f6d1ae53e8cc1f5ff9de
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44065021"
---
# <a name="custom-message-encoder-compression-encoder"></a>Vlastní kodér zpráv: Kompresní kodér
Tento příklad ukazuje, jak implementovat vlastní kodér na platformě Windows Communication Foundation (WCF).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Tento příklad se skládá z programu konzoly klienta (.exe), v místním prostředí služby konzolový program (.exe) a komprese zprávy kodér knihovny (.dll). Služba implementuje kontrakt, který definuje vzor komunikace požadavek odpověď. Smlouva je definován `ISampleServer` rozhraní, které zpřístupňuje základní řetězec přečtou operací (`Echo` a `BigEcho`). Klient podá synchronní žádosti pro danou operaci a odpovědi služby opakováním zprávy zpět do klienta. Činnost klienta a služby je viditelný v oknech konzoly. Záměrem tohoto příkladu je ukazují, jak psát vlastní kodér a předvádět dopady kompresi zpráv na lince. Přidat instrumentaci na kompresní kodér zprávy k výpočtu velikosti zpráv a doba zpracování.  
  
> [!NOTE]
>  V rozhraní .NET Framework 4 Automatická dekomprese byla zapnuta klienta WCF na serveru je odesílání zkomprimovanou odpověď (vytvořenou pomocí algoritmu, jako je například GZip nebo Deflate). Pokud je služba Web hostovaný v Internet Information Server (IIS), může služba IIS konfigurována na odeslání komprimované odpovědi služby. Tato ukázka je možné, pokud je požadavkem pro kompresi a dekompresi na klienta a služby, nebo jestli je služba v místním prostředí.  
  
 Vzorek ukazuje, jak sestavit a integrovat vlastní kodér zpráv do aplikace WCF. Knihovna GZipEncoder.dll se nasazuje s klientem a službou. Tato ukázka předvádí, dopad komprese zprávy. Kód v GZipEncoder.dll ukazuje následující:  
  
-   Vytváření vlastních encoder a kodér objekt pro vytváření.  
  
-   Vývoj element vazby pro vlastní kodér.  
  
-   Pomocí konfigurace vlastních vazeb pro integraci elementů vlastní vazby.  
  
-   Vývoj vlastní obslužnou rutinu umožní konfiguraci souboru vlastní prvek vazby.  
  
 Jak je uvedeno dříve, existuje několik vrstev, které jsou implementovány v vlastní kodér. Abychom vám lépe předvedli vztah mezi každou z těchto úrovní, zjednodušené pořadí událostí pro spuštění služby je v následujícím seznamu:  
  
1.  Spustí se server.  
  
2.  Informace o konfiguraci je pro čtení.  
  
    1.  Konfigurace služby registruje rutiny vlastní konfigurace.  
  
    2.  Hostitel služby je vytvořen a otevřít.  
  
    3.  Vlastní konfigurace pro element vytvoří a vrátí prvek vlastní vazby.  
  
    4.  Vlastní prvek vazby vytvoří a vrátí objekt pro vytváření kodéru zpráv.  
  
3.  Příjmu zprávy.  
  
4.  Objekt pro vytváření kodéru zpráv vrátí kodéru zprávy ve zprávě pro čtení a zápis odpovědi.  
  
5.  Kodér vrstvy je implementovaný jako objekt pro vytváření tříd. Pouze kodéru pro vytváření tříd musí být veřejně vystavené pro vlastní kodér. Objekt factory, který je vrácený element vazby při <xref:System.ServiceModel.ServiceHost> nebo <xref:System.ServiceModel.ChannelFactory%601> je vytvořen objekt. Zpráva kodérů můžou fungovat v režimu ve vyrovnávací paměti nebo datových proudů. Tato ukázka předvádí, jak ve vyrovnávací paměti režim a režim tvorby datového proudu.  
  
 Pro oba režimy existuje je v doprovodné `ReadMessage` a `WriteMessage` metoda abstract `MessageEncoder` třídy. Většina kódování práce probíhá v těchto metod. Ukázka zabalí existující text a zprávy v binární kodérů. To umožňuje vzorku pro delegování čtení a zápis síťové vyjádření zpráv do vnitřní kodér a kompresní kodér ke kompresi a dekompresi výsledky. Protože neexistuje žádný kanál pro kódování zprávy, jde o jediný model pro použití více kodérů ve službě WCF. Jakmile byl dekomprimován zprávy, se předá výslednou zprávu zásobníku do zásobníku kanál pro zpracování. Během komprese je výsledný komprimované zprávy zapisují přímo do datového proudu k dispozici.  
  
 Tato ukázka používá pomocné metody (`CompressBuffer` a `DecompressBuffer`) k provedení převodu z vyrovnávací paměti do datových proudů používat `GZipStream` třídy.  
  
 Ve vyrovnávací paměti `ReadMessage` a `WriteMessage` třídy Zkontrolujte použití `BufferManager` třídy. Kodér je přístupný pouze prostřednictvím kodér objekt pro vytváření. Abstraktní `MessageEncoderFactory` třída poskytuje vlastnost s názvem `Encoder` pro přístup k aktuální kodér a metodu s názvem `CreateSessionEncoder` pro vytvoření encoder, který podporuje relací. Takové kodéru lze použít ve scénáři, kde kanál podporuje relace, je seřazený a spolehlivosti. Tento scénář umožňuje optimalizace v obou relacích data zapsaná do přenosu. Pokud to není žádoucí, by neměl přetížit základní metodu. `Encoder` Vlastnost poskytuje mechanismus pro přístup k relaci bez kodér a výchozí implementaci `CreateSessionEncoder` vrátí metoda hodnotu vlastnosti. Protože vzorku zabalí existující encoder stanovit komprese, `MessageEncoderFactory` implementace přijímá `MessageEncoderFactory` , který představuje objekt factory vnitřní kodér.  
  
 Teď, když jsou definovány encoder a kodér objekt pro vytváření, můžete použít pomocí klienta WCF a služeb. Tyto kodéry však musíte přidat do zásobníku kanálu. Lze odvodit z třídy <xref:System.ServiceModel.ServiceHost> a <xref:System.ServiceModel.ChannelFactory%601> třídy a přepsat `OnInitialize` metody pro tento objekt pro vytváření kodér přidat ručně. Můžete také zveřejnit factory kodér prostřednictvím vlastní prvek vazby.  
  
 Chcete-li vytvořit nové vlastní prvek vazby, odvoďte třídu z <xref:System.ServiceModel.Channels.BindingElement> třídy. Existuje však několik typů elementů vazby. Aby bylo zajištěno, že je vlastní prvek vazby rozpoznán jako element vazby kódování zprávy, je také nutné implementovat <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>. <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> Zpřístupní metodu pro vytvoření nového factory kodéru zpráv (`CreateMessageEncoderFactory`), které je implementováno s cílem vrátit instanci objektu pro vytváření odpovídající kodéru zpráv. Kromě toho <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> má vlastnost, která má označení verze adresování. Protože tato ukázka zabalí existující kodérů, ukázková implementace také zabalí existující kodér elementů vazby a přebírá kodéru vnitřní element vazby jako parametr do konstruktoru a zpřístupní prostřednictvím vlastnosti. Následující ukázkový kód ukazuje implementaci `GZipMessageEncodingBindingElement` třídy.  
  
```  
public sealed class GZipMessageEncodingBindingElement   
                        : MessageEncodingBindingElement //BindingElement  
                        , IPolicyExportExtension  
{  
  
    //We use an inner binding element to store information   
    //required for the inner encoder.  
    MessageEncodingBindingElement innerBindingElement;  
  
        //By default, use the default text encoder as the inner encoder.  
        public GZipMessageEncodingBindingElement()  
            : this(new TextMessageEncodingBindingElement()) { }  
  
    public GZipMessageEncodingBindingElement(MessageEncodingBindingElement messageEncoderBindingElement)  
    {  
        this.innerBindingElement = messageEncoderBindingElement;  
    }  
  
    public MessageEncodingBindingElement InnerMessageEncodingBindingElement  
    {  
        get { return innerBindingElement; }  
        set { innerBindingElement = value; }  
    }  
  
    //Main entry point into the encoder binding element.   
    // Called by WCF to get the factory that creates the  
    //message encoder.  
    public override MessageEncoderFactory CreateMessageEncoderFactory()  
    {  
        return new   
GZipMessageEncoderFactory(innerBindingElement.CreateMessageEncoderFactory());  
    }  
  
    public override MessageVersion MessageVersion  
    {  
        get { return innerBindingElement.MessageVersion; }  
        set { innerBindingElement.MessageVersion = value; }  
    }  
  
    public override BindingElement Clone()  
    {  
        return new   
        GZipMessageEncodingBindingElement(this.innerBindingElement);  
    }  
  
    public override T GetProperty<T>(BindingContext context)  
    {  
        if (typeof(T) == typeof(XmlDictionaryReaderQuotas))  
        {  
            return innerBindingElement.GetProperty<T>(context);  
        }  
        else   
        {  
            return base.GetProperty<T>(context);  
        }  
    }  
  
    public override IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)  
    {  
        if (context == null)  
            throw new ArgumentNullException("context");  
  
        context.BindingParameters.Add(this);  
        return context.BuildInnerChannelFactory<TChannel>();  
    }  
  
    public override IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)  
    {  
        if (context == null)  
            throw new ArgumentNullException("context");  
  
        context.BindingParameters.Add(this);  
        return context.BuildInnerChannelListener<TChannel>();  
    }  
  
    public override bool CanBuildChannelListener<TChannel>(BindingContext context)  
    {  
        if (context == null)  
            throw new ArgumentNullException("context");  
  
        context.BindingParameters.Add(this);  
        return context.CanBuildInnerChannelListener<TChannel>();  
    }  
  
    void IPolicyExportExtension.ExportPolicy(MetadataExporter exporter, PolicyConversionContext policyContext)  
    {  
        if (policyContext == null)  
        {  
            throw new ArgumentNullException("policyContext");  
        }  
       XmlDocument document = new XmlDocument();  
       policyContext.GetBindingAssertions().Add(document.CreateElement(  
            GZipMessageEncodingPolicyConstants.GZipEncodingPrefix,  
            GZipMessageEncodingPolicyConstants.GZipEncodingName,  
            GZipMessageEncodingPolicyConstants.GZipEncodingNamespace));  
    }  
}  
```  
  
 Všimněte si, že `GZipMessageEncodingBindingElement` implementuje třída `IPolicyExportExtension` rozhraní, takže tento element vazby se dá exportovat jako zásady v metadatech, jak je znázorněno v následujícím příkladu.  
  
```xml  
<wsp:Policy wsu:Id="BufferedHttpSampleServer_ISampleServer_policy">  
    <wsp:ExactlyOne>  
      <wsp:All>  
        <gzip:text xmlns:gzip=  
        "http://schemas.microsoft.com/ws/06/2004/mspolicy/netgzip1" />   
       <wsaw:UsingAddressing />   
     </wsp:All>  
   </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 `GZipMessageEncodingBindingElementImporter` Implementuje třída `IPolicyImportExtension` rozhraní, tato třída Importuje zásady pro `GZipMessageEncodingBindingElement`. Nástroje svcutil.exe lze použít pro import zásady do konfiguračního souboru, zpracování `GZipMessageEncodingBindingElement`, následující měla být přidána do Svcutil.exe.config.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
        <add name="gzipMessageEncoding"   
          type=  
            "Microsoft.ServiceModel.Samples.GZipMessageEncodingElement, GZipEncoder, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </bindingElementExtensions>  
    </extensions>  
    <client>  
      <metadata>  
        <policyImporters>  
          <remove type=  
"System.ServiceModel.Channels.MessageEncodingBindingElementImporter, System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
          <extension type=  
"Microsoft.ServiceModel.Samples.GZipMessageEncodingBindingElementImporter, GZipEncoder, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 Teď, když je odpovídající prvek vazby pro kompresní kodér, ho můžete programově využívat do služby ani klienta vytváření nového objektu vlastní vazby a přidat vlastní prvek vazby, jak je znázorněno v následujícím ukázkovém kódu.  
  
```  
ICollection<BindingElement> bindingElements = new List<BindingElement>();  
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();  
GZipMessageEncodingBindingElement compBindingElement = new GZipMessageEncodingBindingElement ();  
bindingElements.Add(compBindingElement);  
bindingElements.Add(httpBindingElement);  
CustomBinding binding = new CustomBinding(bindingElements);  
binding.Name = "SampleBinding";  
binding.Namespace = "http://tempuri.org/bindings";  
```  
  
 To může být dostatečné pro většinu scénářů uživatelů, podpora soubor konfigurace je velmi důležité, pokud má být hostované webové služby. Pro podporu scénáři hostování webových, je třeba vytvořit obslužnou rutinu vlastní konfigurace na Povolit vlastní prvek vazby na umožňovat konfiguraci do souboru.  
  
 Můžete vytvářet obslužné rutiny konfiguračního pro element vazby na konfigurační systém poskytované [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)]. Obslužné rutiny konfiguračního elementu vazby musí být odvozen od <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> třídy. `BindingElementType` Vlastnost se používá k informování konfigurační systém typ elementu vazby k vytvoření této části. Všechny aspekty `BindingElement` , může být sada by měly být vystaveny jako vlastnosti <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> odvozené třídy. <xref:System.Configuration.ConfigurationPropertyAttribute> Je použít jako pomůcku při mapování atributů elementu konfigurace vlastností a nastavení výchozí hodnoty, pokud jsou chybějící atributy. Po hodnoty z konfigurace jsou načítány a použity k vlastnostem, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> metoda je volána, který převede na konkrétní instance elementu vazby vlastnosti. <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A> Metoda se používá pro převod vlastnosti na <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> do hodnoty, které mají být nastaven pro element vazby newlycreated odvozené třídy.  
  
 Následující ukázkový kód ukazuje implementaci `GZipMessageEncodingElement`.  
  
```  
public class GZipMessageEncodingElement : BindingElementExtensionElement  
{  
    public GZipMessageEncodingElement()  
    {  
    }  
  
//Called by the WCF to discover the type of binding element this   
//config section enables  
    public override Type BindingElementType  
    {  
        get { return typeof(GZipMessageEncodingBindingElement); }  
    }  
  
    //The only property we need to configure for our binding element is   
    //the type of inner encoder to use. Here, we support text and  
    //binary.  
    [ConfigurationProperty("innerMessageEncoding",   
                         DefaultValue = "textMessageEncoding")]  
    public string InnerMessageEncoding  
    {  
        get { return (string)base["innerMessageEncoding"]; }  
        set { base["innerMessageEncoding"] = value; }  
    }  
  
    //Called by the WCF to apply the configuration settings (the   
    //property above) to the binding element  
    public override void ApplyConfiguration(BindingElement bindingElement)  
    {  
        GZipMessageEncodingBindingElement binding =   
                (GZipMessageEncodingBindingElement)bindingElement;  
        PropertyInformationCollection propertyInfo =   
                    this.ElementInformation.Properties;  
        if (propertyInfo["innerMessageEncoding"].ValueOrigin !=   
                                     PropertyValueOrigin.Default)  
        {  
            switch (this.InnerMessageEncoding)  
            {  
                case "textMessageEncoding":  
                    binding.InnerMessageEncodingBindingElement =   
                      new TextMessageEncodingBindingElement();  
                    break;  
                case "binaryMessageEncoding":  
                    binding.InnerMessageEncodingBindingElement =   
                         new BinaryMessageEncodingBindingElement();  
                    break;  
            }  
        }  
    }  
  
    //Called by the WCF to create the binding element  
    protected override BindingElement CreateBindingElement()  
    {  
        GZipMessageEncodingBindingElement bindingElement =   
                new GZipMessageEncodingBindingElement();  
        this.ApplyConfiguration(bindingElement);  
        return bindingElement;  
    }  
}   
```  
  
 Tato obslužná rutina konfigurace mapuje následující reprezentaci v souboru App.config nebo Web.config pro službu nebo klienta.  
  
```xml  
<gzipMessageEncoding innerMessageEncoding="textMessageEncoding" />  
```  
  
 Pokud chcete použít tuto obslužnou rutinu konfigurace, je nutné jej zaregistrovat v rámci [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu, jak je znázorněno v následující ukázková konfigurace.  
  
```xml  
<extensions>  
    <bindingElementExtensions>  
       <add   
           name="gzipMessageEncoding"   
           type=  
           "Microsoft.ServiceModel.Samples.GZipMessageEncodingElement,  
           GZipEncoder, Version=1.0.0.0, Culture=neutral,   
           PublicKeyToken=null" />  
      </bindingElementExtensions>  
</extensions>  
```  
  
 Při spuštění serveru operace žádosti a odpovědi se zobrazí v okně konzoly. Stisknutím klávesy ENTER v okně pro vypnutí serveru.  
  
```  
Press Enter key to Exit.  
  
        Server Echo(string input) called:  
        Client message: Simple hello  
  
        Server BigEcho(string[] input) called:  
        64 client messages  
```  
  
 Když spustíte klienta, operace žádosti a odpovědi se zobrazí v okně konzoly. Stisknutím klávesy ENTER v okně Klient vypnutí klient.  
  
```  
Calling Echo(string):  
Server responds: Simple hello Simple hello  
  
Calling BigEcho(string[]):  
Server responds: Hello 0  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu:  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`  
  
## <a name="see-also"></a>Viz také
