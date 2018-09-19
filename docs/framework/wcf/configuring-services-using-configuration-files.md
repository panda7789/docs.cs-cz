---
title: Konfigurace služeb pomocí konfiguračních souborů
ms.date: 03/30/2017
helpviewer_keywords:
- configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
ms.openlocfilehash: 904abff4f3cae5873fe3cc9705dee84f73e2a523
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46004507"
---
# <a name="configuring-services-using-configuration-files"></a>Konfigurace služeb pomocí konfiguračních souborů
Konfigurace služby Windows Communication Foundation (WCF) s konfiguračním souborem dává možnost poskytovat koncový bod a data o chování služby Přejme během nasazení místo v době návrhu. Toto téma popisuje primární techniky, které jsou k dispozici.  
  
 Služba WCF se dají konfigurovat pomocí [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] technologie konfigurace. Nejčastěji jsou přidány elementy XML v souboru Web.config pro web Internetové informační služby (IIS), který je hostitelem služby WCF. Prvky umožňují změnit podrobnosti, jako jsou adresy koncových bodů (skutečné adresy používaný ke komunikaci se službou service) pro počítače podle počítače. Kromě toho WCF obsahuje několik elementů poskytované systémem, které umožňují rychle vybrat většina základních funkcí pro službu. Počínaje [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], WCF se dodává s novou výchozí konfiguraci modelu, která zjednodušuje požadavky na konfiguraci WCF. Pokud nezadáte žádnou konfiguraci WCF pro konkrétní službu, modul runtime automaticky nakonfiguruje vaše služba se některé standardní koncové body a výchozí vazby a chování. V praxi, zápis konfigurace je velkou část programování WCF aplikací.  
  
 Další informace najdete v tématu [Konfigurace vazeb pro služby](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md). Seznam nejčastějších běžně používají elementy, najdete v části [System-Provided vazby](../../../docs/framework/wcf/system-provided-bindings.md). Další informace o výchozí koncové body, vazby a chování najdete v tématu [zjednodušená konfigurace](../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
> [!IMPORTANT]
>  Při nasazení vedle sebe scénáře, ve které jsou nasazené dvě různé verze služby, je nutné zadat částečné názvy sestavení odkazovaná v konfiguračních souborech. Je to proto, že konfigurační soubor se sdílí mezi všemi verzemi služby a mohl být spuštěn v různých verzích rozhraní .NET Framework.  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a>System.Configuration: Soubor Web.config a App.config  
 WCF používá systém konfigurace System.Configuration [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
 Při konfiguraci služby v sadě Visual Studio, použijte k určení nastavení souboru Web.config nebo App.config soubor. Volba název konfiguračního souboru určuje hostitelské prostředí, které jste vybrali pro službu. Pokud používáte k hostování vaší služby IIS, použijte soubor Web.config. Pokud používáte jiné hostitelské prostředí, pomocí souboru App.config.  
  
 V sadě Visual Studio soubor s názvem souboru App.config slouží k vytvoření konečného konfiguračního souboru. Poslední název ve skutečnosti využívá ke konfiguraci závisí na názvu sestavení. Například sestavení s názvem "Cohowinery.exe" má název souboru, konečnou konfiguraci "Cohowinery.exe.config". Však stačí změnit soubor App.config. Změny provedené v tomto souboru jsou automaticky provedeny do konfiguračního souboru konečné aplikace v době kompilace.  
  
 Pomocí App.config, sloučí soubor konfigurační systém souboru App.config s obsahem souboru Machine.config při spuštění aplikace a tato konfigurace používá. Tento mechanismus umožňuje nastavení platná pro celý počítač byly definovány v souboru Machine.config. Souboru App.config můžete použít k přepsání nastavení souboru Machine.config. Můžete také uzamknout v nastavení v souboru Machine.config tak, aby získat použít. V případě souboru Web.config sloučí konfigurační systém souborů Web.config ve všech adresářích vedoucí do adresáře aplikace do konfigurace, který se použije. Další informace o konfiguraci a nastavení priorit, najdete v tématech v <xref:System.Configuration> oboru názvů.  
  
## <a name="major-sections-of-the-configuration-file"></a>Hlavní části konfiguračního souboru  
 Hlavní části v konfiguračním souboru obsahují následující prvky.  
  
```xml  
<system.ServiceModel>  
  
   <services>  
   <!—- Define the service endpoints. This section is optional in the new  
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
>  Vazby a chování oddíly jsou volitelné a jsou zahrnuty pouze v případě vyžaduje.  
  
### <a name="the-services-element"></a>\<Services > – Element  
 `services` Prvek obsahuje specifikace pro všechny služby hostitelů aplikací. Počínaje zjednodušené konfigurační model v [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], tato část je nepovinná.  
  
 [\<služby >](../../../docs/framework/configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a>\<Služby > – Element  
 Každá služba má tyto atributy:  
  
-   `name`. Určuje typ, který poskytuje implementaci kontraktu služby. Toto je plně kvalifikovaný název, který se skládá z oboru názvů, tečku a název typu. Například `"MyNameSpace.myServiceType"`.  
  
-   `behaviorConfiguration`. Určuje název jedné z `behavior` součástí prvky `behaviors` elementu. Zadané chování se řídí akce, například zda služba umožňuje zosobnění. Pokud je jeho hodnota prázdný název nebo žádnou instanci `behaviorConfiguration` je k dispozici potom výchozí sadu chování služby je přidán do služby.  
  
-   [\<service>](../../../docs/framework/configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a>\<Endpoint > – Element  
 Každý koncový bod požaduje adresu vazba a kontrakt, které jsou znázorněny následující atributy:  
  
-   `address`. Určuje služby identifikátor URI (Uniform Resource), což může být absolutní adresa nebo ten, který je zadána relativní k základní adresu služby. Pokud nastavit na prázdný řetězec znamená, že koncový bod je k dispozici na základní adrese, který je určen při vytváření <xref:System.ServiceModel.ServiceHost> pro službu.  
  
-   `binding`. Obvykle určuje vazeb poskytovaných systémem jako <xref:System.ServiceModel.WSHttpBinding>, ale můžete také určit uživatelem definované vazby. Zadaná vazba Určuje typ přenosu, zabezpečení a kódování použité a určuje, zda je podporována nebo povolené spolehlivé relace, transakcí nebo datové proudy.  
  
-   `bindingConfiguration`. Pokud výchozí hodnoty vazby musí být změněny, to můžete udělat pomocí konfigurace odpovídající `binding` prvek `bindings` element. Tento atribut by měly mít stejnou hodnotu jako `name` atribut `binding` element, který umožňuje změnit výchozí nastavení. Pokud není zadán název, nebo žádný `bindingConfiguration` je zadaná ve vazbě, koncový bod je použita výchozí vazbu typu vazby.  
  
-   `contract`. Určuje rozhraní definuje kontrakt. Toto je rozhraní implementované v společný typ language runtime (CLR) určené `name` atribut `service` elementu.  
  
-   [\<koncový bod > referenční dokumentace elementu](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017)  
  
### <a name="the-bindings-element"></a>\<Vazby > – Element  
 `bindings` Prvek obsahuje specifikace pro všechny vazby, které může používat libovolný koncový bod definovaný v libovolnou službu.  
  
 [\<vazby >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a>\<Vazby > – Element  
 `binding` Elementů obsažených v `bindings` element může být buď jeden vazeb poskytovaných systémem (naleznete v tématu [System-Provided vazby](../../../docs/framework/wcf/system-provided-bindings.md)) nebo vlastní vazby (naleznete v tématu [vlastních vazeb](../../../docs/framework/wcf/extending/custom-bindings.md)). `binding` Element má `name` atributů, které souvisí s koncového bodu určeného v vazbu `bindingConfiguration` atribut `endpoint` elementu. Pokud není zadán žádný název, pak je, že vazba odpovídá na výchozí hodnotu tohoto typu vazby.  
  
 Další informace o konfiguraci služeb a klientů najdete v tématu [konfigurace Windows Communication Foundation aplikací](https://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a).  
  
 [\<Vytvoření vazby >](../../../docs/framework/misc/binding.md)  
  
### <a name="the-behaviors-element"></a>\<Chování > – Element  
 Toto je prvek kontejneru pro `behavior` prvky, které definují chování pro službu.  
  
 [\<chování >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a>\<Chování > – Element  
 Každý `behavior` element je identifikován `name` atribut a poskytuje buď poskytnuté systémem chování, například <`throttling`>, nebo vlastní chování. Pokud není zadán název prvku chování odpovídá výchozí chování služby nebo koncového bodu.  
  
 [\<chování >](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a>Jak používat vazby a chování konfigurace  
 WCF umožňuje snadno sdílet konfigurace mezi koncovými body pomocí referenčního systému v konfiguraci. Místo toho přímo konfigurační hodnoty pro koncový bod, související vazby konfigurační hodnoty jsou seskupené ve `bindingConfiguration` prvky `<binding>` části. Konfigurace vazby je pojmenovaná skupina nastavení na vazbu. Koncové body můžete odkázat `bindingConfiguration` podle názvu.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
 <system.serviceModel>  
  <bindings>  
    <basicHttpBinding>  
     <binding name="myBindingConfiguration1" closeTimeout="00:01:00" />  
     <binding name="myBindingConfiguration2" closeTimeout="00:02:00" />  
     <binding closeTimeout="00:03:00" />  <!—- Default binding for basicHttpBinding -->  
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
  
 `name` z `bindingConfiguration` je nastavena v `<binding>` elementu. `name` Musí být jedinečný řetězec v rámci oboru typ vazby – v tomto případě [< basicHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), nebo prázdná hodnota pro odkazování na výchozí vazby. Koncový bod odkazy na konfiguraci tak, že nastavíte `bindingConfiguration` atributu na řetězec.  
  
 A `behaviorConfiguration` je implementováno stejným způsobem, jak je znázorněno v následujícím příkladu.  
  
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
  
 Všimněte si, že výchozí sadu chování služby jsou přidány do služby. Tento systém umožňuje koncové body sdílení obvyklé konfigurace bez předefinování nastavení. Pokud celý počítač obor je požadován, vytvoření vazby nebo chování konfigurace v souboru Machine.config. Nastavení konfigurace jsou k dispozici ve všech souborech App.config. [Nástroj Configuration Editor (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) usnadňuje vytvoření konfigurací.  
  
## <a name="behavior-merge"></a>Chování sloučení  
 Slučovací funkce chování usnadňuje správu chování, pokud chcete sadu společné chování, který se má použít konzistentně. Tato funkce umožňuje určit chování na různých úrovních hierarchie configuration a služby dědit z více úrovní hierarchie konfigurace chování. Pro ilustraci jak tohle funguje Předpokládejme, že máte následující virtuální adresář rozložení ve službě IIS:  
  
 ~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc  
  
 A ~\Web.config soubor má následující obsah:  
  
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
  
 A jste dítě tohoto souboru Web.config umístěný v ~\Child\Web.config s následujícím obsahem:  
  
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
  
 Služby umístěné v ~\Child\Service.svc se bude chovat, jako by byl serviceDebug i serviceMetadata chování. Chování serviceDebug bude mít jenom služby umístěné v ~\Service.svc. Co se stane, je, že se sloučí dvě chování kolekce se stejným názvem (v tomto případě prázdný řetězec).  
  
 Chování kolekce můžete také zrušit pomocí \<vymazat > Označit a odebrat jednotlivé chování z kolekce pomocí \<odebrat > značky. Například následující dvě konfigurace výsledky v podřízeném služeb s pouze serviceMetadata chování:  
  
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
  
 Chování sloučení je Hotovo nameless chování kolekcí, jak je znázorněno výše a s názvem také kolekce chování.  
  
 Sloučení chování funguje ve službě IIS hostitelské prostředí, ve které sloučit soubory Web.config hierarchicky s kořenový soubor Web.config a souboru machine.config. Funguje to ovšem i v prostředí aplikace, kde můžete machine.config sloučit s soubor App.config.  
  
 Sloučení chování platí pro chování koncového bodu a chování služby v konfiguraci.  
  
 Pokud podřízená kolekce chování obsahuje chování, které je již v kolekci chování nadřazeného, podřízené chování potlačuje nadřazené. Ano, pokud kolekce chování nadřazených `<serviceMetadata httpGetEnabled="False" />` a podřízené kolekce chování měli `<serviceMetadata httpGetEnabled="True" />`podřízené chování by se mělo přepsat chování nadřazené v kolekci chování a httpGetEnabled by být "true".  
  
## <a name="see-also"></a>Viz také  
 [Zjednodušená konfigurace](../../../docs/framework/wcf/simplified-configuration.md)  
 [Konfigurace aplikací Windows Communication Foundation](https://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a)  
 [\<service>](../../../docs/framework/configure-apps/file-schema/wcf/service.md)  
 [\<Vytvoření vazby >](../../../docs/framework/misc/binding.md)
