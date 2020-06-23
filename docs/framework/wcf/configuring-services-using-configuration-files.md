---
title: Konfigurace služeb pomocí konfiguračních souborů
description: Přečtěte si, jak konfigurační soubor pro službu WCF poskytuje flexibilitu při poskytování dat o chování koncových bodů a služeb během nasazení.
ms.date: 03/30/2017
helpviewer_keywords:
- configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
ms.openlocfilehash: 1a3266ad8890436c9be9d0f2b231aeaca0f9236e
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245424"
---
# <a name="configuring-services-using-configuration-files"></a>Konfigurace služeb pomocí konfiguračních souborů
Konfigurace služby Windows Communication Foundation (WCF) pomocí konfiguračního souboru vám poskytne flexibilitu při poskytování dat o chování koncových bodů a služeb v bodě nasazení místo v době návrhu. Toto téma popisuje primární techniky k dispozici.  
  
 Služba WCF se dá konfigurovat pomocí technologie konfigurace .NET Framework. Nejčastěji se prvky XML přidávají do souboru Web.config pro web Internetová informační služba (IIS), který je hostitelem služby WCF. Tyto prvky umožňují změnit podrobnosti, jako jsou adresy koncových bodů (skutečné adresy používané ke komunikaci se službou) na počítačích jednotlivých počítačů. Kromě toho WCF zahrnuje několik prvků poskytovaných systémem, které umožňují rychle vybrat základní funkce pro službu. Počínaje .NET Framework 4 přichází WCF k dispozici nový výchozí konfigurační model, který zjednodušuje požadavky na konfiguraci WCF. Pokud neposkytnete konfiguraci služby WCF pro konkrétní službu, modul runtime automaticky nakonfiguruje vaši službu s některými standardními koncovými body a výchozí vazbou/chování. V praxi je psaní konfigurace hlavní součástí programování aplikací WCF.  
  
 Další informace najdete v tématu [Konfigurace vazeb pro služby](configuring-bindings-for-wcf-services.md). Seznam nejčastěji používaných prvků najdete v tématu [vazby poskytované systémem](system-provided-bindings.md). Další informace o výchozích koncových bodech, vazbách a chování najdete v tématu [zjednodušená konfigurace](simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](./samples/simplified-configuration-for-wcf-services.md).  
  
> [!IMPORTANT]
> Při nasazování souběžných scénářů, kde jsou nasazeny dvě různé verze služby, je nutné zadat částečné názvy sestavení, na které se odkazuje v konfiguračních souborech. Je to proto, že konfigurační soubor je sdílen napříč všemi verzemi služby a mohl by být spuštěn v různých verzích .NET Framework.  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a>System.Configuration: Web.config a App.config  
 WCF používá konfigurační systém System.Configuration .NET Framework.  
  
 Při konfiguraci služby v aplikaci Visual Studio použijte k zadání nastavení buď soubor Web.config, nebo App.config soubor. Volba názvu konfiguračního souboru je určena hostujícím prostředím, které jste si zvolili pro službu. Pokud používáte službu IIS k hostování vaší služby, použijte soubor Web.config. Pokud používáte jiné hostitelské prostředí, použijte soubor App.config.  
  
 V aplikaci Visual Studio se k vytvoření finálního konfiguračního souboru používá soubor s názvem App.config. Konečný název, který je ve skutečnosti použitý pro konfiguraci, závisí na názvu sestavení. Například sestavení s názvem "Cohowinery.exe" má konečný název konfiguračního souboru "Cohowinery.exe.config". Je však třeba upravit soubor App.config. Změny provedené v tomto souboru jsou automaticky provedeny v konečném konfiguračním souboru aplikace v době kompilace.  
  
 V části použití App.config se zaznamená, že konfigurační systém sloučí App.config soubor s obsahem Machine.config souboru při spuštění aplikace a použije se konfigurace. Tento mechanismus umožňuje definovat nastavení pro všechny počítače v souboru Machine.config. Soubor App.config lze použít k přepsání nastavení Machine.config souboru; Můžete také uzamknout nastavení v souboru Machine.config tak, aby se používala. V případě Web.config konfigurační systém sloučí Web.config soubory ve všech adresářích až do adresáře aplikace do konfigurace, která se použije. Další informace o konfiguraci a prioritách nastavení naleznete v tématech v <xref:System.Configuration> oboru názvů.  
  
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
> Části vazby a chování jsou volitelné a jsou zahrnuty pouze v případě potřeby.  
  
### <a name="the-services-element"></a>\<services>Element  
 `services`Element obsahuje specifikace pro všechny služby, které jsou hostiteli aplikace. Počínaje zjednodušeným modelem konfigurace v .NET Framework 4 je tato část volitelná.  
  
 [\<services>](../configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a>\<service>Element  
 Každá služba má tyto atributy:  
  
- `name`. Určuje typ, který poskytuje implementaci kontraktu služby. Toto je plně kvalifikovaný název, který se skládá z oboru názvů, tečky a názvu typu. Například `"MyNameSpace.myServiceType"`.  
  
- `behaviorConfiguration`. Určuje název jednoho z `behavior` prvků nalezených v `behaviors` elementu. Zadané chování řídí akce, například zda služba umožňuje zosobnění. Pokud je jeho hodnota prázdný název, nebo není zadána žádná, bude `behaviorConfiguration` do služby přidána výchozí sada chování služby.  
  
- [\<service>](../configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a>\<endpoint>Element  
 Každý koncový bod vyžaduje adresu, vazbu a kontrakt, které jsou reprezentované následujícími atributy:  
  
- `address`. Určuje identifikátor URI (Uniform Resource Identifier) služby, který může být absolutní adresa nebo jedna z nich relativní vzhledem k základní adrese služby. Pokud je parametr nastaven na prázdný řetězec, znamená to, že koncový bod je k dispozici na základní adrese, která je určena při vytváření <xref:System.ServiceModel.ServiceHost> služby pro službu.  
  
- `binding`. Obvykle určuje systémovou vazbu <xref:System.ServiceModel.WSHttpBinding> , jako je, ale může také specifikovat uživatelsky definované vazby. Zadaná vazba určuje typ přenosu, zabezpečení a používaného kódování a to, jestli jsou podporované nebo povolené spolehlivé relace, transakce nebo streamování.  
  
- `bindingConfiguration`. Pokud je nutné upravit výchozí hodnoty vazby, lze to provést nakonfigurováním příslušného `binding` prvku v `bindings` elementu. Tento atribut by měl mít stejnou hodnotu jako `name` atribut `binding` prvku, který se používá ke změně výchozích hodnot. Pokud není zadán žádný název nebo pokud není `bindingConfiguration` zadána žádná vazba, je v tomto koncovém bodu použita výchozí vazba typu vazby.  
  
- `contract`. Určuje rozhraní, které definuje kontrakt. Toto je rozhraní implementované v typu modulu CLR (Common Language Runtime) určeném `name` atributem `service` elementu.  
  
- [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md)  
  
### <a name="the-bindings-element"></a>\<bindings>Element  
 `bindings`Element obsahuje specifikace pro všechny vazby, které mohou být použity jakýmkoli koncovým bodem definovaným v jakékoli službě.  
  
 [\<bindings>](../configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a>\<binding>Element  
 `binding`Prvky obsažené v `bindings` elementu mohou být buď jedna z těchto vazeb poskytovaných systémem (viz téma [vazby poskytnuté systémem](system-provided-bindings.md)) nebo vlastní vazba (viz [vlastní vazby](./extending/custom-bindings.md)). `binding`Element má `name` atribut, který koreluje vazbu s koncovým bodem zadaným v `bindingConfiguration` atributu `endpoint` elementu. Pokud název není zadán, bude tato vazba odpovídat výchozímu typu vazby.  
  
Další informace o konfiguraci služeb a klientů najdete v tématu [Konfigurace služeb WCF](configuring-services.md).
  
 [\<binding>](../configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-behaviors-element"></a>\<behaviors>Element  
 Toto je prvek kontejneru pro `behavior` prvky, které definují chování pro službu.  
  
 [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a>\<behavior>Element  
 Každý `behavior` element je identifikován `name` atributem a poskytuje buď chování poskytované systémem, například <`throttling`> nebo vlastní chování. Pokud název není zadán, bude tento prvek chování odpovídat výchozímu chování služby nebo koncového bodu.  
  
 [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a>Jak používat konfigurace vazeb a chování  
 Technologie WCF usnadňuje sdílení konfigurací mezi koncovými body pomocí referenčního systému v konfiguraci. Místo přímého přiřazování hodnot konfigurace koncovému bodu jsou konfigurační hodnoty související s vazbami seskupeny do `bindingConfiguration` prvků v `<binding>` oddílu. Konfigurace vazby je pojmenovaná skupina nastavení pro vazbu. Koncové body pak mohou odkazovat `bindingConfiguration` podle názvu.  
  
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
  
 `name` `bindingConfiguration` Je nastaven v `<binding>` elementu. `name`Musí být jedinečný řetězec v rámci oboru typu vazby – v tomto případě [<\> BasicHttpBinding](../configure-apps/file-schema/wcf/basichttpbinding.md)nebo prázdná hodnota pro odkazování na výchozí vazbu. Koncový bod odkazuje na konfiguraci nastavením `bindingConfiguration` atributu na tento řetězec.  
  
 A `behaviorConfiguration` je implementován stejným způsobem, jak je znázorněno v následující ukázce.  
  
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
  
 Všimněte si, že se do služby přidala výchozí sada chování služby. Tento systém umožňuje koncovým bodům sdílet společné konfigurace bez předefinování nastavení. Je-li požadován obor v rámci rozsahu počítače, vytvořte v Machine.config konfiguraci vazby nebo chování. Konfigurační nastavení jsou k dispozici ve všech App.config souborech. [Nástroj Editor konfigurací (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md) usnadňuje vytváření konfigurací.  
  
## <a name="behavior-merge"></a>Sloučení chování  
 Funkce sloučení chování usnadňuje správu chování, když chcete, aby se sada běžných chování používala konzistentně. Tato funkce umožňuje zadat chování na různých úrovních konfigurační hierarchie a mít služby dědění chování z více úrovní konfigurační hierarchie. K tomu, abyste se vypředpokládali, jak to funguje, máte ve službě IIS následující rozložení virtuálních adresářů:  
  
 `~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc`
  
 A `~\Web.config` soubor má následující obsah:  
  
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
  
 A máte podřízený Web.config nacházející se v umístění ~\Child\Web.config s následujícím obsahem:  
  
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
  
 Služba, která se nachází na ~ \Child\Service.svc, se bude chovat, jako by se jednalo o chování serviceDebug a oddílu serviceMetadata. Služba nacházející se na ~ \Service.svc bude mít pouze chování serviceDebug. K tomu dochází, když se sloučí dvě kolekce chování se stejným názvem (v tomto případě je to prázdný řetězec).  
  
 Můžete také vymazat kolekce chování pomocí \<clear> značky a odebrat jednotlivá chování z kolekce pomocí \<remove> značky. Například následující dvě výsledky konfigurace v podřízené službě mají pouze chování oddílu serviceMetadata:  
  
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
  
 Sloučení chování je provedeno pro kolekce chování Nameless, jak je uvedeno výše, a pojmenované kolekce chování také.  
  
 Sloučení chování funguje v hostitelském prostředí služby IIS, ve kterém se Web.config soubory sloučí hierarchicky s kořenovým Web.config souborem a machine.config. Ale funguje i v prostředí aplikace, kde se machine.config můžou sloučit se souborem App.config.  
  
 Sloučení chování se aplikuje na chování koncového bodu i na chování služby v konfiguraci.  
  
 Pokud kolekce podřízených chování obsahuje chování, které již je přítomno v nadřazené kolekci chování, podřízené chování přepíše nadřazený objekt. Takže pokud kolekce nadřazených chování měla `<serviceMetadata httpGetEnabled="False" />` a podřízená kolekce chování měla `<serviceMetadata httpGetEnabled="True" />` , může podřízené chování přepsat nadřazené chování v kolekci chování a HttpGetEnabled by byla "true".  
  
## <a name="see-also"></a>Viz také

- [Zjednodušená konfigurace](simplified-configuration.md)
- [Konfigurace služeb WCF](configuring-services.md)
- [\<service>](../configure-apps/file-schema/wcf/service.md)
- [\<binding>](../configure-apps/file-schema/wcf/bindings.md)
