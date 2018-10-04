---
title: Používání standardních koncových bodů
ms.date: 03/30/2017
ms.assetid: ecd6a62f-9619-4778-a497-6f888087a9ea
ms.openlocfilehash: 5502d42d6a576509c826e05c8781662d374fbff4
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48584283"
---
# <a name="usage-of-standard-endpoints"></a>Používání standardních koncových bodů

Tato ukázka demonstruje použití standardních koncových bodů v konfiguračních souborech služby. Standardní koncový bod umožňuje uživatelům zjednodušit definic koncových bodů s použitím jedné vlastnosti k popisu adresa, vazba a kontrakt kombinaci s další vlastnosti přidružené k němu. Tato ukázka předvádí, jak definovat a implementovat vlastní standardní koncový bod a tom, jak definovat konkrétní vlastnosti v koncovém bodě.

## <a name="sample-details"></a>Ukázka podrobnosti

Koncové body služby je možné zadat tak poskytuje tři parametry: adresa, vazba a kontrakt. Další parametry, které může být zadán zahrnují konfiguraci chování, záhlaví, identifikátor URI příposlechu a tak dále. V některých případech, některé nebo všechny adresy vazby a kontrakty mají hodnoty, které nelze změnit. Z tohoto důvodu je možné použít standardní koncové body. Mezi příklady těchto koncových bodů patří koncové body metadat systému exchange a zjišťování koncových bodů. Standardní koncové body také zlepšit použitelnost tím, že konfigurace koncových bodů služby bez nutnosti poskytnout informace, které pevné nebo vytvořte svoje vlastní standardní koncové body, například použitelnosti zadáním přiměřené sadu výchozí hodnoty a snížit tak množství podrobností konfigurační soubory.

Tento příklad se skládá ze dvou projektů: služba, která definuje dva standardní koncové body a klienta, který komunikuje se službou. Způsob, jakým jsou definovány standardních koncových bodů služby v konfiguračním souboru se zobrazuje v následujícím příkladu.

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

První koncový bod definovaný pro službu je druhu `customEndpoint`, jejichž definice si můžete prohlédnout ve `<standardEndpoints>` oddílu, ve kterém vlastnost `property` přiřazena hodnota `true`. To platí koncový bod přizpůsobit pomocí nové vlastnosti. Druhý koncový bod odpovídá koncový bod metadat, ve kterém jsou pevné hodnoty adresa, vazba a kontrakt.

K definování elementu koncový bod standard, která je odvozena z třídy `StandardEndpointElement` musí být vytvořeny. V případě této ukázce `CustomEndpointElement` třída je definována, jak je znázorněno v následujícím příkladu.

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

V `CreateServiceEndpoint` funkce, `CustomEndpoint` je vytvořen objekt. Jeho definice můžete vidět v následujícím příkladu:

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

 K provedení komunikace mezi klienta a služby, se vytvoří odkaz na službu klienta ke službě. Při ukázku je sestavení a spuštění, spustí služba a klient komunikuje s ním. Všimněte si, že by měl pokaždé, když se některé změny ve službě aktualizovat odkaz na službu.

#### <a name="to-use-this-sample"></a>Pro fungování této ukázky

1.  Pomocí sady Visual Studio 2012, otevřete soubor StandardEndpoints.sln.

2.  Povolte více projektů se spustí.

    1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na řešení standardních koncových bodů a potom vyberte **vlastnosti**.

    2.  V **společné vlastnosti**vyberte **spouštěný projekt**a potom klikněte na tlačítko **více projektů po spuštění**.

    3.  Přesunout projekt služby na začátku seznamu, s **akce** nastavena na **Start**.

    4.  Přesunout projektu klienta po projekt služby také s **akce** nastavena na **Start**.

         Toto nastavení určuje, že klientský projekt je proveden po projekt služby.

3.  Abyste mohli spustit řešení, stiskněte klávesu F5.

> [!NOTE]
> Pokud tyto kroky nefungují, ujistěte se, že vaše prostředí je správně nastavený, pomocí následujících kroků:
>
> 1. Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).
> 2. Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](building-the-samples.md).
> 3. Spusťte ukázku v jedné nebo více konfigurací počítače, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](running-the-samples.md).

> [!IMPORTANT]
> Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\StandardEndpoints`
