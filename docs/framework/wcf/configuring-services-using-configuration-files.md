---
title: Konfigurace služeb pomocí konfiguračních souborů
ms.date: 03/30/2017
helpviewer_keywords:
- configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
ms.openlocfilehash: caf6e238ca286e5e712c0273e10502655fd7ff4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174794"
---
# <a name="configuring-services-using-configuration-files"></a>Konfigurace služeb pomocí konfiguračních souborů
Konfigurace služby WCF (Windows Communication Foundation) s konfiguračním souborem poskytuje data o chování koncového bodu a služby v okamžiku nasazení namísto v době návrhu. Toto téma popisuje primární techniky, které jsou k dispozici.  
  
 Služba WCF je konfigurovatelná pomocí konfigurační technologie rozhraní .NET Framework. Nejčastěji jsou prvky XML přidány do souboru Web.config pro web Internetové informační služby (IIS), který je hostitelem služby WCF. Prvky umožňují změnit podrobnosti, jako jsou adresy koncového bodu (skutečné adresy používané ke komunikaci se službou) na základě strojpo počítači. WCF navíc obsahuje několik prvků poskytovaných systémem, které umožňují rychle vybrat nejzákladnější funkce pro službu. Počínaje rozhraním .NET Framework 4 je wcf dodáván s novým výchozím konfiguračním modelem, který zjednodušuje požadavky na konfiguraci WCF. Pokud nezadáte žádnou konfiguraci WCF pro konkrétní službu, runtime automaticky nakonfiguruje službu s některými standardními koncovými body a výchozí vazbou/chováním. V praxi je konfigurace zápisu hlavní součástí programování aplikací WCF.  
  
 Další informace naleznete [v tématu Konfigurace vazeb pro služby](configuring-bindings-for-wcf-services.md). Seznam nejčastěji používaných prvků naleznete v tématu [Vazby poskytované systémem](system-provided-bindings.md). Další informace o výchozích koncových bodech, vazbách a chování naleznete v [tématu Zjednodušená konfigurace](simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](./samples/simplified-configuration-for-wcf-services.md).  
  
> [!IMPORTANT]
> Při nasazování souběžných scénářů, kde jsou nasazeny dvě různé verze služby, je nutné zadat částečné názvy sestavení odkazovaných v konfiguračních souborech. Důvodem je, že konfigurační soubor je sdílen ve všech verzích služby a mohou být spuštěny v různých verzích rozhraní .NET Framework.  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a>System.Configuration: Web.config a App.config  
 WCF používá konfigurační systém System.Configuration rozhraní .NET Framework.  
  
 Při konfiguraci služby v sadě Visual Studio určete nastavení pomocí souboru Web.config nebo souboru App.config. Volba názvu konfiguračního souboru je určena hostitelským prostředím, které zvolíte pro službu. Pokud používáte službu IIS k hostování služby, použijte soubor Web.config. Pokud používáte jiné hostitelské prostředí, použijte soubor App.config.  
  
 V sadě Visual Studio se soubor s názvem App.config používá k vytvoření konečného konfiguračního souboru. Konečný název skutečně použitý pro konfiguraci závisí na názvu sestavení. Například sestavení s názvem "Cohowinery.exe" má konečný název konfiguračního souboru "Cohowinery.exe.config". Je však třeba upravit pouze soubor App.config. Změny provedené v tomto souboru jsou automaticky provedeny do konečného konfiguračního souboru aplikace v době kompilace.  
  
 Při použití souboru App.config sloučí soubor Konfigurace souboru App.config s obsahem souboru Machine.config při spuštění aplikace a použití konfigurace. Tento mechanismus umožňuje nastavení celého počítače, které mají být definovány v souboru Machine.config. Soubor App.config lze použít k přepsání nastavení souboru Machine.config; můžete také zamknout v nastavení v souboru Machine.config tak, aby si zvykli. V případě Web.config sloučí konfigurační systém soubory Web.config ve všech adresářích, které vedou k adresáři aplikace, do konfigurace, která bude použita. Další informace o konfiguraci a prioritách <xref:System.Configuration> nastavení naleznete v tématech v oboru názvů.  
  
## <a name="major-sections-of-the-configuration-file"></a>Hlavní části konfiguračního souboru  
 Hlavní části konfiguračního souboru obsahují následující prvky.  
  
```xml  
<system.ServiceModel>  
  
   <services>  
   <!-- Define the service endpoints. This section is optional in the new  
    default configuration model in .NET Framework 4. -->  
      <service>  
         <endpoint/>  
      </service>  
   </services>  
  
   <bindings>  
   <!-- Specify one or more of the system-provided binding elements,  
    for example, <basicHttpBinding> -->
   <!-- Alternatively, <customBinding> elements. -->  
      <binding>  
      <!-- For example, a <BasicHttpBinding> element. -->  
      </binding>  
   </bindings>  
  
   <behaviors>  
   <!-- One or more of the system-provided or custom behavior elements. -->  
      <behavior>  
      <!-- For example, a <throttling> element. -->  
      </behavior>  
   </behaviors>  
  
</system.ServiceModel>  
```  
  
> [!NOTE]
> Vazby a chování oddíly jsou volitelné a jsou zahrnuty pouze v případě potřeby.  
  
### <a name="the-services-element"></a>Služby \<> Element  
 Prvek `services` obsahuje specifikace pro všechny služby, které aplikace hostuje. Počínaje zjednodušeným konfiguračním modelem v rozhraní .NET Framework 4 je tato část volitelná.  
  
 [\<služby>](../configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a>Služba \<> Element  
 Každá služba má tyto atributy:  
  
- `name`. Určuje typ, který poskytuje implementaci servisní smlouvy. Toto je plně kvalifikovaný název, který se skládá z oboru názvů, tečky a potom názvu typu. Například `"MyNameSpace.myServiceType"`.  
  
- `behaviorConfiguration`. Určuje název jednoho z `behavior` prvků nalezených `behaviors` v prvku. Zadané chování řídí akce, jako je například zda služba umožňuje zosobnění. Pokud je jeho hodnota prázdný `behaviorConfiguration` název nebo ne je k dispozici, pak je do služby přidána výchozí sada chování služby.  
  
- [\<servisní>](../configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a>Koncový \<bod> element  
 Každý koncový bod vyžaduje adresu, vazbu a smlouvu, které jsou reprezentovány následujícími atributy:  
  
- `address`. Určuje identifikátor URI (Uniform Resource Identifier) služby, což může být absolutní adresa nebo adresa, která je dána vzhledem k základní adrese služby. Pokud je nastavena na prázdný řetězec, znamená to, že koncový bod <xref:System.ServiceModel.ServiceHost> je k dispozici na základní adrese, která je určena při vytváření pro službu.  
  
- `binding`. Obvykle určuje systémem poskytované <xref:System.ServiceModel.WSHttpBinding>vazby jako , ale můžete také určit uživatelem definované vazby. Zadaná vazba určuje typ přenosu, zabezpečení a kódování a zda jsou podporovány nebo povoleny spolehlivé relace, transakce nebo streamování.  
  
- `bindingConfiguration`. Pokud musí být změněny výchozí hodnoty vazby, lze to `binding` provést `bindings` konfigurací příslušného prvku v elementu. Tento atribut by měl mít `name` stejnou hodnotu jako atribut `binding` prvku, který se používá ke změně výchozích hodnot. Pokud není zadán žádný `bindingConfiguration` název nebo není zadán žádný ve vazbě, použije se v koncovém bodě výchozí vazba typu vazby.  
  
- `contract`. Určuje rozhraní, které definuje smlouvu. Toto je rozhraní implementované v typu CLR (CLR) jazyka určeného `name` atributem `service` prvku.  
  
- [\<>koncového bodu](../configure-apps/file-schema/wcf/endpoint-element.md)  
  
### <a name="the-bindings-element"></a>Vazby \<> Element  
 Prvek `bindings` obsahuje specifikace pro všechny vazby, které lze použít libovolný koncový bod definovaný v libovolné službě.  
  
 [\<vázání>](../configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a>Vazba \<> Element  
 Prvky `binding` obsažené v `bindings` prvku může být buď jeden ze systémem poskytované vazby (viz [System-Provided Vazby)](system-provided-bindings.md)nebo vlastní vazby (viz [vlastní vazby).](./extending/custom-bindings.md) Prvek `binding` má `name` atribut, který koreluje vazbu s `bindingConfiguration` koncovým `endpoint` bodem zadaným v atributu prvku. Pokud není zadán žádný název, pak tato vazba odpovídá výchozí mu typ vazby.  
  
Další informace o konfiguraci služeb a klientů naleznete v [tématu Konfigurace služeb WCF](configuring-services.md).
  
 [\<závazné>](../configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-behaviors-element"></a>Chování \<> Element  
 Toto je prvek `behavior` kontejneru pro prvky, které definují chování pro službu.  
  
 [\<chování>](../configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a>Chování \<> Element  
 Každý `behavior` prvek je `name` identifikován atributem a poskytuje buď systémové `throttling` chování, například <> nebo vlastní chování. Pokud není uveden žádný název, pak tento prvek chování odpovídá výchozí službě nebo chování koncového bodu.  
  
 [\<chování>](../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a>Použití konfigurace vazby a chování  
 WCF usnadňuje sdílení konfigurací mezi koncovými body pomocí referenčního systému v konfiguraci. Spíše než přímo přiřazení konfiguračních hodnot ke koncovému `bindingConfiguration` bodu, `<binding>` hodnoty konfigurace související s vazbou jsou seskupeny do prvků v části. Konfigurace vazby je pojmenovaná skupina nastavení na vazbě. Koncové body pak `bindingConfiguration` mohou odkazovat na název podle.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
 <system.serviceModel>  
  <bindings>  
    <basicHttpBinding>  
     <binding name="myBindingConfiguration1" closeTimeout="00:01:00" />  
     <binding name="myBindingConfiguration2" closeTimeout="00:02:00" />  
     <binding closeTimeout="00:03:00" />  <!-- Default binding for basicHttpBinding -->  
    </basicHttpBinding>  
     </bindings>  
     <services>  
      <service name="MyNamespace.myServiceType">  
       <endpoint
          address="myAddress" binding="basicHttpBinding"
          bindingConfiguration="myBindingConfiguration1"  
          contract="MyContract"  />  
       <endpoint
          address="myAddress2" binding="basicHttpBinding"
          bindingConfiguration="myBindingConfiguration2"  
          contract="MyContract" />  
       <endpoint
          address="myAddress3" binding="basicHttpBinding"
          contract="MyContract" />  
       </service>  
      </services>  
    </system.serviceModel>  
</configuration>  
```  
  
 `bindingConfiguration` `<binding>` Je `name` nastavena v prvku. Musí `name` být jedinečný řetězec v rámci oboru typu vazby – v tomto případě [<basicHttpBinding\>](../configure-apps/file-schema/wcf/basichttpbinding.md)nebo prázdnou hodnotu odkazovat na výchozí vazbu. Koncový bod odkazuje na konfiguraci `bindingConfiguration` nastavením atributu na tento řetězec.  
  
 A `behaviorConfiguration` je implementována stejným způsobem, jak je znázorněno v následující ukázce.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="myBehavior">  
           <callbackDebug includeExceptionDetailInFaults="true" />  
         </behavior>  
      </endpointBehaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="true" />  
        </behavior>  
      </serviceBehaviors>  
  
    </behaviors>  
    <services>  
     <service name="NewServiceType">  
       <endpoint
          address="myAddress3" behaviorConfiguration="myBehavior"  
          binding="basicHttpBinding"  
          contract="MyContract" />  
      </service>  
    </services>  
   </system.serviceModel>  
</configuration>  
```  
  
 Všimněte si, že výchozí sada chování služby jsou přidány do služby. Tento systém umožňuje koncovým bodům sdílet běžné konfigurace bez předefinování nastavení. Pokud je vyžadován obor celého počítače, vytvořte konfiguraci vazby nebo chování v souboru Machine.config. Nastavení konfigurace jsou k dispozici ve všech souborech App.config. [Nástroj Editor konfigurace (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md) usnadňuje vytváření konfigurací.  
  
## <a name="behavior-merge"></a>Sloučení chování  
 Funkce sloučení chování usnadňuje správu chování, pokud chcete, aby sada běžných chování byla použita konzistentně. Tato funkce umožňuje určit chování na různých úrovních hierarchie konfigurace a nechat služby dědit chování z více úrovní hierarchie konfigurace. Pro ilustraci, jak to funguje, předpokládáte, že máte ve službě IIS následující rozložení virtuálního adresáře:  
  
 `~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc`
  
 A `~\Web.config` váš soubor má následující obsah:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceDebug includeExceptionDetailInFaults="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 A máte podřízený web.config umístěný na adrese ~\Child\Web.config s následujícím obsahem:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 Služba umístěná na adrese ~\Child\Service.svc se bude chovat, jako by měla chování ladění a metadat služby. Služba umístěná na adrese ~\Service.svc bude mít pouze chování serviceDebug. Co se stane, je, že dvě kolekce chování se stejným názvem (v tomto případě prázdný řetězec) jsou sloučeny.  
  
 Kolekce chování můžete také vymazat \<pomocí značky clear> a odebráním \<jednotlivých chování z kolekce pomocí značky remove>. Například následující dvě konfigurace výsledky v podřízené služby s pouze serviceMetadata chování:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <remove name="serviceDebug"/>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <clear/>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 Sloučení chování se provádí pro bezejmenné kolekce chování, jak je uvedeno výše a pojmenované kolekce chování také.  
  
 Sloučení chování funguje v hostitelském prostředí služby IIS, ve kterém se soubory Web.config hierarchicky slučují s kořenovým souborem Web.config a machine.config. Ale funguje také v aplikačním prostředí, kde machine.config může sloučit se souborem App.config.  
  
 Sloučení chování platí pro chování koncového bodu a chování služby v konfiguraci.  
  
 Pokud kolekce podřízené chování obsahuje chování, které je již k dispozici v nadřazené kolekci chování, podřízené chování přepíše nadřazené. Takže pokud nadřazené kolekce chování měl `<serviceMetadata httpGetEnabled="False" />` a podřízené chování kolekce měla `<serviceMetadata httpGetEnabled="True" />`, podřízené chování by přepsat nadřazené chování v kolekci chování a httpGetEnabled by být "true".  
  
## <a name="see-also"></a>Viz také

- [Zjednodušená konfigurace](simplified-configuration.md)
- [Konfigurace služeb WCF](configuring-services.md)
- [\<servisní>](../configure-apps/file-schema/wcf/service.md)
- [\<závazné>](../configure-apps/file-schema/wcf/bindings.md)
