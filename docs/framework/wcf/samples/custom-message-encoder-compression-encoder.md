---
title: 'Vlastní kodér zpráv: Kompresní kodér'
ms.date: 03/30/2017
ms.assetid: 57450b6c-89fe-4b8a-8376-3d794857bfd7
ms.openlocfilehash: 84afb060e98a5936b24c5446ff543fd627864102
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971990"
---
# <a name="custom-message-encoder-compression-encoder"></a>Vlastní kodér zpráv: Kompresní kodér

Tato ukázka předvádí, jak implementovat vlastní kodér pomocí platformy Windows Communication Foundation (WCF).

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`

## <a name="sample-details"></a>Podrobnosti ukázky

Tato ukázka se skládá z programu klientské konzoly (. exe), samoobslužného programu konzoly služby (. exe) a knihovny kodéru kompresního kodéru (. dll). Služba implementuje kontrakt definující způsob komunikace požadavek-odpověď. Kontrakt je definován `ISampleServer` rozhraním, které zveřejňuje základní operace s odezvou řetězce (`Echo` a `BigEcho`). Klient provádí synchronní požadavky na danou operaci a odpověď služby, a to opakováním zprávy zpátky klientovi. Aktivita klientů a služeb je viditelná v oknech konzoly. Záměrem této ukázky je Ukázat, jak napsat vlastní kodér a Ukázat dopad komprimace zprávy na kabel. Můžete přidat instrumentaci do kodéru kompresních zpráv, abyste mohli vypočítat velikost zprávy, čas zpracování nebo obojí.

> [!NOTE]
> V .NET Framework 4 byla na klientovi WCF povolena automatická dekomprese, pokud server odesílá komprimovanou odpověď (vytvořenou pomocí algoritmu, jako je GZip nebo deflate). Pokud je služba hostitelem webu v rámci služby IIS (Internet Information Server), je možné službu IIS nakonfigurovat tak, aby odesílala komprimovanou odpověď. Tato ukázka se dá použít, pokud je potřeba provést kompresi a dekompresi jak v klientovi, tak ve službě, nebo pokud je tato služba v místním prostředí hostovaná.

Ukázka ukazuje, jak sestavit a integrovat vlastní kodér zpráv do aplikace WCF. Knihovna GZipEncoder. dll je nasazena s klientem i službou. Tato ukázka také ukazuje dopad komprimace zpráv. Kód v souboru GZipEncoder. dll ukazuje následující:

- Vytváření vlastního kodéru a továrny kodéru

- Vývoj prvku vazby pro vlastní kodér.

- Použití vlastní konfigurace vazeb pro integraci vlastních elementů vazby.

- Vývoj vlastní obslužné rutiny konfigurace umožňující konfiguraci souboru vlastního elementu vazby.

Jak bylo uvedeno dříve, existuje několik vrstev, které jsou implementovány ve vlastním kodéru. Pro lepší ilustraci vztahu mezi jednotlivými vrstvami je v následujícím seznamu zjednodušené pořadí událostí pro spuštění služby:

1. Spustí se server.

2. Informace o konfiguraci jsou čteny.

    1. Konfigurace služby registruje obslužnou rutinu vlastní konfigurace.

    2. Hostitel služby je vytvořen a otevřen.

    3. Vlastní prvek konfigurace vytvoří a vrátí vlastní prvek vazby.

    4. Vlastní prvek vazby vytvoří a vrátí objekt pro vytváření kodéru zpráv.

3. Byla přijata zpráva.

4. Objekt pro vytváření kodéru zpráv vrátí kodér zpráv pro čtení ve zprávě a vypíše odpověď.

5. Vrstva kodéru je implementována jako objekt pro vytváření tříd. Pouze objekt pro vytváření tříd kodéru musí být veřejně vystavený pro vlastní kodér. Objekt factory je vrácen elementem vazby při <xref:System.ServiceModel.ServiceHost> vytvoření objektu or. <xref:System.ServiceModel.ChannelFactory%601> Kodéry zpráv mohou pracovat v režimu vyrovnávací paměti nebo streamování. Tato ukázka demonstruje režim vyrovnávací paměti i režim streamování.

Pro každý režim je k dispozici `ReadMessage` doprovodný `WriteMessage` objekt a metoda pro `MessageEncoder` abstraktní třídu. Většina práce kódování probíhá v těchto metodách. Ukázka zalomí stávající textové a binární kodéry zpráv. To umožňuje, aby vzorek mohl delegovat čtení a zápis kabelových reprezentace zpráv do vnitřního kodéru a umožňuje kompresnímu kodéru komprimaci nebo dekomprimaci výsledků. Vzhledem k tomu, že není k dispozici žádný kanál pro kódování zpráv, je to jediný model pro použití více kodérů ve službě WCF. Jakmile se zpráva dekomprimuje, Výsledná zpráva se předá zásobníku pro zpracování zásobníku kanálů. Během komprese se výsledná komprimovaná zpráva zapisuje přímo do poskytnutého datového proudu.

Tato ukázka používá pomocné metody (`CompressBuffer` a `DecompressBuffer`) k provedení převodu z vyrovnávací paměti `GZipStream` na datové proudy pro použití třídy.

Vyrovnávací paměť `ReadMessage` a `WriteMessage` třídyvyužívajítřídu.`BufferManager` Kodér je přístupný jenom přes objekt pro vytváření kodéru. Abstraktní `MessageEncoderFactory` Třída poskytuje vlastnost s názvem `Encoder` pro přístup k aktuálnímu kodéru a metodu pojmenovanou `CreateSessionEncoder` pro vytvoření kodéru, který podporuje relace. Takový kodér se dá použít ve scénáři, kde kanál podporuje relace, je uspořádaný a spolehlivý. Tento scénář umožňuje optimalizaci v každé relaci dat zapsaných do tohoto drátu. Pokud to není žádoucí, základní metoda by neměla být přetížena. Vlastnost poskytuje mechanismus pro přístup k kodéru bez relací a výchozí implementace `CreateSessionEncoder` metody vrací hodnotu vlastnosti. `Encoder` Vzhledem k tomu, že ukázka zabalí existující kodér, aby poskytoval `MessageEncoderFactory` kompresi, implementace `MessageEncoderFactory` akceptuje, která představuje objekt pro vytváření vnitřních kodérů.

Teď, když je definice kodéru a kodéru definovaná, se dají použít spolu s klientem a službou WCF. Tyto kodéry však musí být přidány do zásobníku kanálů. Můžete odvodit třídy z <xref:System.ServiceModel.ServiceHost> tříd a <xref:System.ServiceModel.ChannelFactory%601> a přepsat `OnInitialize` metody pro přidání této továrny kodéru ručně. Objekt pro vytváření kodéru můžete také zveřejnit pomocí vlastního elementu vazby.

Chcete-li vytvořit nový vlastní element vazby, odvodit třídu z <xref:System.ServiceModel.Channels.BindingElement> třídy. Existuje však několik typů prvků vazby. Chcete-li zajistit, aby byl prvek vlastní vazby rozpoznán jako prvek vazby kódování zprávy, je také nutné implementovat <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>. Zpřístupňuje metodu pro vytvoření nového objektu pro vytváření nových zpráv (`CreateMessageEncoderFactory`), který je implementován pro vrácení instance odpovídajícího objektu pro vytváření kodéru zpráv. <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> Kromě toho <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> má vlastnost k označení verze adresování. Vzhledem k tomu, že tato ukázka zabalí existující kodéry, ukázková implementace také zalomí existující prvky vazby kodéru a převezme prvek vazby vnitřního kodéru jako parametr konstruktoru a zpřístupní jej prostřednictvím vlastnosti. Následující vzorový kód ukazuje implementaci `GZipMessageEncodingBindingElement` třídy.

```csharp
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

Všimněte si `GZipMessageEncodingBindingElement` , že třída `IPolicyExportExtension` implementuje rozhraní, takže tento prvek vazby lze exportovat jako zásadu v metadatech, jak je znázorněno v následujícím příkladu.

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

Třída implementuje rozhraní, tato třída importuje zásady pro `GZipMessageEncodingBindingElement`. `GZipMessageEncodingBindingElementImporter` `IPolicyImportExtension` Nástroj Svcutil. exe lze použít k importu zásad do konfiguračního souboru, aby bylo možné zpracovat `GZipMessageEncodingBindingElement`, do Svcutil. exe. config je třeba přidat následující.

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

Nyní, když existuje odpovídající element vazby kompresního kodéru, lze programově připojit ke službě nebo klientovi pomocí vytvoření nového vlastního objektu vazby a přidáním vlastního elementu vazby, jak je znázorněno v následujícím ukázkovém kódu.

```csharp
ICollection<BindingElement> bindingElements = new List<BindingElement>();
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();
GZipMessageEncodingBindingElement compBindingElement = new GZipMessageEncodingBindingElement ();
bindingElements.Add(compBindingElement);
bindingElements.Add(httpBindingElement);
CustomBinding binding = new CustomBinding(bindingElements);
binding.Name = "SampleBinding";
binding.Namespace = "http://tempuri.org/bindings";
```

I když je to pro většinu scénářů uživatelů dostačující, podpora konfigurace souboru je kritická, pokud by služba byla hostována na webu. Aby bylo možné podporovat scénář pro hostování webu, je nutné vyvinout vlastní obslužnou rutinu konfigurace, aby bylo možné v souboru konfigurovat vlastní prvek vazby.

Můžete vytvořit obslužnou rutinu konfigurace pro element vazby na vrcholu konfiguračního systému. Obslužná rutina konfigurace elementu vazby musí být odvozena od <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> třídy. <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.BindingElementType?displayProperty=nameWithType> Informuje konfigurační systém typu elementu vazby, který se má pro tento oddíl vytvořit. Všechny aspekty `BindingElement` , které lze nastavit, by měly být zveřejněny jako vlastnosti <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> v odvozené třídě. <xref:System.Configuration.ConfigurationPropertyAttribute> Pomoc při mapování atributů elementů konfigurace na vlastnosti a nastavení výchozích hodnot v případě, že chybí atributy. Poté, co jsou hodnoty z konfigurace načteny a aplikovány na vlastnosti <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A?displayProperty=nameWithType> , je volána metoda, která převede vlastnosti na konkrétní instanci elementu vazby. Metoda slouží k převodu vlastností <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> odvozené třídy na hodnoty, které mají být nastaveny u nově vytvořeného prvku vazby. <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A?displayProperty=nameWithType>

Následující vzorový kód ukazuje implementaci rozhraní `GZipMessageEncodingElement`.

```csharp
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

Tato obslužná rutina konfigurace mapuje následující reprezentace v App. config nebo Web. config pro službu nebo klienta.

```xml
<gzipMessageEncoding innerMessageEncoding="textMessageEncoding" />
```

Chcete-li použít tuto obslužnou rutinu konfigurace, musí být registrována v rámci [ \<prvku System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) , jak je znázorněno v následující ukázkové konfiguraci.

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

Při spuštění serveru se v okně konzoly zobrazí požadavky na operace a odpovědi. V okně stiskněte klávesu ENTER, aby se server vypnul.

```
Press Enter key to Exit.

        Server Echo(string input) called:
        Client message: Simple hello

        Server BigEcho(string[] input) called:
        64 client messages
```

Když spustíte klienta nástroje, v okně konzoly se zobrazí požadavky na operace a odpovědi. V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.

```
Calling Echo(string):
Server responds: Simple hello Simple hello

Calling BigEcho(string[]):
Server responds: Hello 0

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Pomocí následujícího příkazu nainstalujte ASP.NET 4,0:

    ```
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

3. Při sestavování řešení postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

4. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`
