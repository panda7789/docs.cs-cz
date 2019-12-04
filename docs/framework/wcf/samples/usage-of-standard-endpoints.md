---
title: Používání standardních koncových bodů
ms.date: 03/30/2017
ms.assetid: ecd6a62f-9619-4778-a497-6f888087a9ea
ms.openlocfilehash: 2b210bfe683669aeebf54a1701f07d492e6abdb4
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715349"
---
# <a name="usage-of-standard-endpoints"></a>Používání standardních koncových bodů

Tato ukázka předvádí, jak používat standardní koncové body v konfiguračních souborech služby. Standardní koncový bod umožňuje uživateli zjednodušit definice koncových bodů pomocí jedné vlastnosti pro popis kombinace adresy, vazby a kontraktu s dalšími vlastnostmi, které jsou k ní přidružené. Tato ukázka předvádí, jak definovat a implementovat vlastní koncový bod Standard a jak definovat konkrétní vlastnosti v koncovém bodu.

## <a name="sample-details"></a>Podrobnosti ukázky

Koncové body služby je možné zadat zadáním tří parametrů: adresa, vazba a kontrakt. Mezi další parametry, které lze zadat, patří konfigurace chování, hlavičky, identifikátor URI naslouchání atd. V některých případech mají některé nebo všechny adresy, vazby a kontrakty hodnoty, které se nedají změnit. Z tohoto důvodu je možné použít standardní koncové body. Mezi příklady takových koncových bodů patří koncové body výměny metadat a koncové body zjišťování. Standardní koncové body také zlepšují použitelnost tím, že umožňují konfiguraci koncových bodů služby bez nutnosti poskytovat informace o pevné povaze nebo vytvářet vlastní standardní koncové body, například pro zlepšení použitelnosti poskytnutím přiměřené sady výchozích hodnoty, čímž se sníží úroveň podrobností konfiguračních souborů.

Tato ukázka se skládá ze dvou projektů: služby, která definuje dva standardní koncové body a klienta, který komunikuje se službou. Způsob definování standardních koncových bodů pro službu v konfiguračním souboru je znázorněno v následujícím příkladu.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <extensions>
      <endpointExtensions>
        <add name="customEndpoint" type="Microsoft.Samples.StandardEndpoints.CustomEndpointCollectionElement, service" />
      </endpointExtensions>
    </extensions>
    <services>
      <service name="Microsoft.Samples.StandardEndpoints.CalculatorService">
        <endpoint address="http://localhost:8000/Samples/Service.svc/customEndpoint" contract="Microsoft.Samples.StandardEndpoints.ICalculator" kind="customEndpoint" />
        <endpoint kind="mexEndpoint" />
      </service>
    </services>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <serviceMetadata httpGetEnabled="True"/>
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <standardEndpoints>
      <customEndpoint>
        <standardEndpoint property="True" />
      </customEndpoint>
    </standardEndpoints>
  </system.serviceModel>
</configuration>
```

Prvním koncovým bodem definovaným pro službu je `customEndpoint`, jehož definici lze zobrazit v části `<standardEndpoints>`, ve které je `property` vlastnosti přiřazena hodnota `true`. Jedná se o případ přizpůsobený koncovému bodu s novou vlastností. Druhý koncový bod odpovídá koncovému bodu metadat, ve kterém jsou opraveny hodnoty adresy, vazby a kontraktu.

Pro definování elementu standardního koncového bodu musí být vytvořena třída, která je odvozena od `StandardEndpointElement`. V případě této ukázky byla definována třída `CustomEndpointElement`, jak je znázorněno v následujícím příkladu.

```csharp
public class CustomEndpointElement : StandardEndpointElement
{
    public bool Property
    {
        get { return (bool)base["property"]; }
        set { base["property"] = value; }
    }

    protected override ConfigurationPropertyCollection Properties
    {
        get
        {
            ConfigurationPropertyCollection properties = base.Properties;
            properties.Add(new ConfigurationProperty("property", typeof(bool), false, ConfigurationPropertyOptions.None));
            return properties;
        }
    }

    protected override Type EndpointType
    {
        get { return typeof(CustomEndpoint); }
    }

    protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contract)
    {
        return new CustomEndpoint();
    }

    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)
    {
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;
        customEndpoint.Property = this.Property;
    }

    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)
    {
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;
        customEndpoint.Property = this.Property;
    }

    protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)
    {
    }

    protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)
    {
    }
}
```

Ve funkci `CreateServiceEndpoint` je vytvořen objekt `CustomEndpoint`. Jeho definice je uvedena v následujícím příkladu:

```csharp
public class CustomEndpoint : ServiceEndpoint
{
    public CustomEndpoint()
        : this(string.Empty)
    {
    }

    public CustomEndpoint(string address)
        : this(address, ContractDescription.GetContract(typeof(ICalculator)))
    {
    }

    public CustomEndpoint(string address, ContractDescription contract)
        : base(contract)
    {
        this.Binding = new BasicHttpBinding();
        this.IsSystemEndpoint = false;
    }

    public bool Property
    {
        get;
        set;
    }
}
```

 K provedení komunikace mezi službou a klientem se v klientovi vytvoří odkaz na službu. Při sestavení a spuštění ukázky se služba spustí a klient s ním komunikuje. Všimněte si, že odkaz na službu by se měl aktualizovat při každé změně ve službě.

#### <a name="to-use-this-sample"></a>Použití této ukázky

1. Pomocí sady Visual Studio 2012 otevřete soubor oddílu StandardEndpoints. sln.

2. Povolit spuštění více projektů.

    1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na standardní řešení koncových bodů a pak vyberte **vlastnosti**.

    2. V nabídce **běžné vlastnosti**vyberte možnost **projekt po spuštění**a pak klikněte na **více projektů po spuštění**.

    3. Přesuňte projekt služby na začátek seznamu a **akci** nastavte na **Spustit**.

    4. Přesuňte klientský projekt po projektu služby a **akci** nastavte na **Spustit**.

         To určuje, že projekt klienta je proveden po projektu služby.

3. Pokud chcete řešení spustit, stiskněte klávesu F5.

> [!NOTE]
> Pokud tyto kroky nefungují, ujistěte se, že máte správně nastavené prostředí, a to pomocí následujících kroků:
>
> 1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).
> 2. Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).
> 3. Chcete-li spustit ukázku v jedné nebo více konfiguracích počítačů, postupujte podle pokynů v [části spuštění ukázek Windows Communication Foundation](running-the-samples.md).

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\StandardEndpoints`
