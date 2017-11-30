---
title: "Používání standardních koncových bodů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ecd6a62f-9619-4778-a497-6f888087a9ea
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 85dda1619fe3a77c4716806de2467cb96287b2f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="usage-of-standard-endpoints"></a>Používání standardních koncových bodů
Tento příklad znázorňuje postup používání standardních koncových bodů v konfiguračních souborech na služby. Koncový bod standardní umožňuje uživateli pomocí jedné vlastnosti popis adresu, kombinace vazby a kontraktu s další vlastnosti přidružené k němu zjednodušit definice koncových bodů. Tento příklad znázorňuje, jak definovat a implementovat vlastní standardní koncového bodu a jak definovat specifické vlastnosti v koncovém bodě.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Koncové body služby lze zadat zadáním tři parametry: adresy, vazby a smlouvy. Další parametry, které lze zadat zahrnují konfigurace chování, záhlaví, naslouchání URI a tak dále. V některých případech, některé nebo všechny adresy vazby a kontrakty obsahují hodnoty, které nelze změnit. Z tohoto důvodu je možné použít standardní koncové body. Příkladem takových koncových bodů může být koncové body metadat exchange a zjišťování koncových bodů. Standardní koncové body také zlepšují použitelnost tím, že se konfigurace koncových bodů služby bez nutnosti poskytnout informace, které pevné nebo vytvořte svoje vlastní standardní koncových bodů, např. Chcete-li zlepšit použitelnost poskytováním přiměřené sadu výchozí hodnoty a snížit tak množství podrobností konfigurační soubory.  
  
 Tato ukázka se skládá ze dvou projektů: služba, která definuje dva standardní koncové body a klienta, který komunikuje se službou. Způsob, jakým standardní koncové body jsou definovány pro službu v konfiguračním souboru je zobrazit v následujícím příkladu.  
  
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
  
 První koncový bod pro službu je typu definována `customEndpoint`, jejichž definice si můžete prohlédnout ve `<standardEndpoints>` části, ve kterém vlastnost `property` je zadána hodnota `true`. Toto je malá koncový bod přizpůsobit pomocí novou vlastnost. Druhý odpovídá koncový bod metadat, ve kterém jsou pevné hodnoty adresy, vazby a kontrakt.  
  
 Můžete definovat standardní koncový bod elementu, třída odvozená z `StandardEndpointElement` musí být vytvořen. V případě této ukázce `CustomEndpointElement` má byla třída definována, jak je znázorněno v následujícím příkladu.  
  
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
  
 V `CreateServiceEndpoint` funkce, `CustomEndpoint` je vytvořen objekt. V následujícím příkladu se zobrazí jeho definice.  
  
```  
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
  
 K provedení komunikace mezi klienta a služby, vytvoří se v klientovi služby odkazu na službu. Když ukázce je vytvořen a provést, spustí službu a klient naváže komunikaci s ním. Všimněte si, že odkaz na službu je třeba aktualizovat pokaždé, když je některé změny ve službě.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete soubor StandardEndpoints.sln.  
  
2.  Povolte více projektů, aby bylo možné spustit.  
  
    1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na řešení standardních koncových bodů a pak vyberte **vlastnosti**.  
  
    2.  V **společných vlastností**, vyberte **spouštěný projekt**a potom klikněte na **více projektů po spuštění**.  
  
    3.  Projekt služby přesunout na začátek seznamu, s **akce** nastavena na **spustit**.  
  
    4.  Přesunout projektu klienta po projekt služby, také s **akce** nastavena na **spustit**.  
  
         Určuje, že projektu klienta se spustí až po projektu služby.  
  
3.  Pokud chcete spustit řešení, stisknutím klávesy F5.  
  
> [!NOTE]
>  Pokud tyto kroky nefungují, ujistěte se, že vaše prostředí správně nastavený, pomocí následujících kroků.  
>   
>  1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
> 2.  Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
> 3.  Spustit ukázku v jedné nebo více konfigurací počítače, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\StandardEndpoints`  
  
## <a name="see-also"></a>Viz také
