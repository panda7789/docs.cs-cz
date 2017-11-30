---
title: "Vlastní kodér zpráv: Kompresní kodér"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57450b6c-89fe-4b8a-8376-3d794857bfd7
caps.latest.revision: "37"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 09566625b6159fb8ce6da6ef347e2d1ddecce1db
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="custom-message-encoder-compression-encoder"></a>Vlastní kodér zpráv: Kompresní kodér
Tento příklad ukazuje, jak implementovat vlastní kodér pomocí [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] platformy.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Tato ukázka se skládá z konzoly programu klienta (.exe), služba s vlastním hostováním program konzoly (.exe) a knihovny kodér zpráv komprese (.dll). Služba se implementuje kontrakt, který definuje komunikační vzor požadavku a odpovědi. Kontrakt je definována `ISampleServer` rozhraní, které zpřístupňuje základní řetězec zobrazování operací (`Echo` a `BigEcho`). Klient zadává synchronní požadavků pro danou operaci a odpovědi služby opakováním zprávy zpět do klienta. Činnost klienta a služby je viditelná v konzole windows. Účelem této ukázce je ukazují, jak psát vlastní kodér a předvedení dopad komprese zprávy v drátové síti. Instrumentace můžete přidat do kompresní kodér zpráv vypočítat velikost zprávy, doba zpracování nebo obojí.  
  
> [!NOTE]
>  V rozhraní .NET Framework 4, byla zapnuta automatickou dekompresi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienty, pokud server, který odesílá odpověď komprimované (vytvořeny pomocí algoritmu, například GZip a Deflate). Pokud služba je Web hostovaný v Internet Information Server (IIS), může služba IIS konfigurována pro službu pro odeslání komprimované odpovědi. Tato ukázka lze použít, pokud je požadavkem udělat komprese a dekomprese na klienta a služby, nebo pokud služba se hostuje sama.  
  
 Ukázka ukazuje, jak vytvořit a integrovat vlastní kodér zpráv do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace. Knihovna GZipEncoder.dll je nasazeno pomocí klienta a služby. Tento příklad také znázorňuje dopad kompresi zprávy. Kód v GZipEncoder.dll ukazuje následující:  
  
-   Vytváření vlastní kodér a kodér objekt pro vytváření.  
  
-   Vývoj pro vlastní kodér prvku vazby.  
  
-   Pomocí konfigurace vlastních vazeb pro integraci prvky vlastní vazby.  
  
-   Vývoj vlastní konfigurace obslužná rutina umožní konfiguraci souboru elementu vlastní vazby.  
  
 Jak je uvedeno dříve, existuje několik vrstev, které jsou implementované v vlastní kodér. Abychom vám lépe předvedli vztah mezi každou z těchto úrovní, zjednodušené pořadí událostí, pro spuštění služby je v následujícím seznamu:  
  
1.  Server se spustí.  
  
2.  Informace o konfiguraci je pro čtení.  
  
    1.  Konfigurace služby zaregistruje obslužná rutina vlastní konfigurace.  
  
    2.  Hostitel služby je vytvořen a otevřít.  
  
    3.  Vlastní konfigurace element vytvoří a vrátí prvek vlastní vazby.  
  
    4.  Vlastní vazby element vytvoří a vrátí objekt pro vytváření kodér zpráv.  
  
3.  Je přijata zpráva.  
  
4.  Objekt pro vytváření zpráv kodér vrátí kodéru zprávy pro čtení ve zprávě a zápis na odpověď.  
  
5.  Kodér vrstvy je implementovaný jako objekt pro vytváření tříd. Pouze factory kodér – třída musí být veřejně zpřístupněny pro vlastní kodér. Vrátí objekt factory prvku vazby při <xref:System.ServiceModel.ServiceHost> nebo <xref:System.ServiceModel.ChannelFactory%601> je vytvořen objekt. Zpráva kodéry můžou fungovat v režimu ve vyrovnávací paměti nebo streamování. Tento příklad znázorňuje režim s vyrovnávací pamětí a streamování režimu.  
  
 Pro každý režim je doplňujícími `ReadMessage` a `WriteMessage` metoda na abstraktní `MessageEncoder` třídy. Většina práce kódování probíhá v těchto metod. Ukázka zabalí existující text a zprávy v binární kodérů. To umožňuje vzorku, který se delegovat čtení a zápis síťové vyjádření zpráv vnitřní kodéru a umožňuje kompresní kodér komprimovat nebo dekomprimovat výsledky. Protože neexistuje žádný kanál pro kódování zpráv, jedná se o pouze model pro používání více kodéry v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Jakmile zpráva byla dekomprimovat, Výsledná zpráva je přidána na zásobník pro zásobník kanálu pro zpracování. Během komprese je výsledný komprimované zpráva zapsána přímo na zadaný datový proud.  
  
 Tato ukázka používá pomocné metody (`CompressBuffer` a `DecompressBuffer`) provést převod z vyrovnávací paměti do datových proudů používat `GZipStream` třídy.  
  
 Ve vyrovnávací paměti `ReadMessage` a `WriteMessage` třídy Zkontrolujte použití `BufferManager` třídy. Kodér je dostupné pouze prostřednictvím objektu pro vytváření kodér. Abstraktní `MessageEncoderFactory` třída poskytuje vlastnost s názvem `Encoder` pro přístup k aktuální kodér a metodu s názvem `CreateSessionEncoder` pro vytvoření kodér, který podporuje relací. Takové kodér lze ve scénáři, kde kanál podporuje relací, se seřadí a je spolehlivé. Tento scénář umožňuje optimalizace v každé relaci data zapsaná do sítě. Pokud to není žádoucí, základní metody by neměla být přetížený. `Encoder` Vlastnost poskytuje mechanismus pro přístup k méně relace kodér a výchozí implementaci `CreateSessionEncoder` vrátí metoda hodnotu vlastnosti. Protože ukázku zabalí existující kodér zajistit kompresi, `MessageEncoderFactory` implementace přijme `MessageEncoderFactory` představující kodér vnitřní objekt pro vytváření.  
  
 Teď, když jsou definovány kodér a objektu pro vytváření kodér, dá použít s [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta a služby. Tyto kodéry však musí být přidaný do zásobníku kanálu. Můžete odvození třídy z <xref:System.ServiceModel.ServiceHost> a <xref:System.ServiceModel.ChannelFactory%601> třídy a přepsání `OnInitialize` metody pro tento objekt pro vytváření kodér přidat ručně. Můžete také vystavit objektu pro vytváření kodér prostřednictvím vlastní vazby elementu.  
  
 Pokud chcete vytvořit nové vlastní vazby element, odvození třídy z <xref:System.ServiceModel.Channels.BindingElement> třídy. Existuje však několik typů elementů vazby. Aby se zajistilo, že element vlastní vazby rozpoznán jako element vazby kódování zprávy, je také nutné implementovat <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>. <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> Zpřístupní metodu pro vytvoření nového vytváření kodér zpráv (`CreateMessageEncoderFactory`), které je implementováno vrátit instanci objektu pro vytváření odpovídající kodér zpráv. Kromě toho <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> má vlastnost označující adresování verze. Protože tato ukázka zabalí existující kodéry, Vzorová implementace také zabalí existující kodér elementů vazby a trvá vnitřní kodér vazby element jako parametr pro konstruktor a zpřístupňuje prostřednictvím vlastnosti. Následující vzorový kód ukazuje implementaci `GZipMessageEncodingBindingElement` třídy.  
  
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
  
 Všimněte si, že `GZipMessageEncodingBindingElement` třída implementuje `IPolicyExportExtension` rozhraní, tak, aby tento element vazeb se dá vyexportovat jako zásada v metadatech, jak je znázorněno v následujícím příkladu.  
  
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
  
 `GZipMessageEncodingBindingElementImporter` Třída implementuje `IPolicyImportExtension` rozhraní, tato třída Importuje zásady pro `GZipMessageEncodingBindingElement`. Nástroje svcutil.exe lze použít pro import zásady do konfiguračního souboru pro zpracování `GZipMessageEncodingBindingElement`, následující musí být přidaní do Svcutil.exe.config.  
  
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
  
 Teď, když je odpovídající element vazby pro kompresní kodér, ho můžete prostřednictvím kódu programu jazyka do provozu nebo klienta vytváření nový objekt, který vlastní vazby a přidáním prvku vlastní vazby, jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 To může být dostatečné pro většinu scénářů uživatele, podpora souboru konfigurace je velmi důležité, pokud má být hostované webové služby. Podporuje scénář hostuje Web, je třeba vytvořit vlastní konfigurace obslužná rutina umožňuje konfigurovat vlastní vazby element v souboru.  
  
 Můžete vytvořit obslužnou rutinu konfigurace pro element vazby nad konfigurační systém poskytované [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)]. Konfigurace obslužné rutiny pro element vazby musí být odvozeny od <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> třídy. `BindingElementType` Vlastnost se používá k informování konfigurační systém typu vazby elementu, který chcete vytvořit pro tento oddíl. Všechny aspekty `BindingElement` , může být sada by měly být vystaveny jako vlastnosti <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> odvozené třídy. <xref:System.Configuration.ConfigurationPropertyAttribute> Se používá pro mapování atributů elementu konfigurace pro vlastnosti a nastavení výchozí hodnoty, pokud chybí atributy. Po hodnoty z konfigurace načíst a použít na vlastnosti <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> metoda je volána, který převede vlastnosti na konkrétní instanci prvku vazby. <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A> Metoda se používá pro převod vlastnosti na <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> odvozené třídy do hodnoty, které mají být nastavené u elementu newlycreated vazby.  
  
 Následující vzorový kód ukazuje implementaci `GZipMessageEncodingElement`.  
  
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
  
 Tato obslužná rutina konfigurace mapuje následující reprezentace v souboru App.config nebo Web.config pro službu nebo klienta.  
  
```xml  
<gzipMessageEncoding innerMessageEncoding="textMessageEncoding" />  
```  
  
 Pokud chcete použít tuto konfiguraci obslužnou rutinu, musí být zaregistrován v rámci [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu, jak je znázorněno v následující ukázka konfigurace.  
  
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
  
 Při spuštění serveru operaci požadavky a odpovědi se zobrazí v okně konzoly. Stisknutím klávesy ENTER v okně vypnout server.  
  
```  
Press Enter key to Exit.  
  
        Server Echo(string input) called:  
        Client message: Simple hello  
  
        Server BigEcho(string[] input) called:  
        64 client messages  
```  
  
 Při spuštění klienta operaci požadavky a odpovědi se zobrazí v okně konzoly. Stisknutím klávesy ENTER v okně klienta vypnout klienta.  
  
```  
Calling Echo(string):  
Server responds: Simple hello Simple hello  
  
Calling BigEcho(string[]):  
Server responds: Hello 0  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu:  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`  
  
## <a name="see-also"></a>Viz také
