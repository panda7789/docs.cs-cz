---
title: Konfigurace služeb pomocí konfiguračních souborů
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
caps.latest.revision: 29
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e5ad91fa70a743b7135648cb10c7c519e3559bdb
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="configuring-services-using-configuration-files"></a>Konfigurace služeb pomocí konfiguračních souborů
Konfigurace [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] služby s konfiguračním souborem vám umožní poskytovat chování data koncový bod a služby v okamžiku nasazení místo v době návrhu. Toto téma popisuje primární techniky, které jsou k dispozici.  
  
 A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služba je konfigurovatelná pomocí [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] technologie konfigurace. Nejčastěji, jsou přidány elementy XML v souboru Web.config pro stránku Internetové informační služby (IIS), který je hostitelem [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby. Prvky umožňují změnit podrobnosti, například adresy koncových bodů (skutečná adresami používaný ke komunikaci se službou) na základě počítače podle počítače. Kromě toho [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] obsahuje několik poskytované systémem prvky, které vám umožní rychle vybrat nejzákladnější funkce pro služby. Počínaje [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] se dodává s nový model výchozí konfigurace, který zjednodušuje [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] požadavky na konfiguraci. Pokud nezadáte žádné [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] konfigurace pro konkrétní službu, modul runtime automaticky nakonfiguruje vaši službu s některými standardní koncové body a výchozí chování nebo vazby. V praxi, zápis konfigurace je hlavní část programování [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikací.  
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Konfigurace vazeb pro služby](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md). Seznam nejčastějších běžně používané elementy, najdete v části [System-Provided vazby](../../../docs/framework/wcf/system-provided-bindings.md). [!INCLUDE[crabout](../../../includes/crabout-md.md)] výchozí koncové body, vazby a chování, viz [zjednodušená konfigurace](../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
> [!IMPORTANT]
>  Při nasazení scénářů vedle sebe, kde se nasadí dvě různé verze služby, je nutné zadat částečné názvy sestavení odkazovaných v konfiguračních souborech. Je to proto, že konfigurační soubor je sdílena mezi všemi verzemi služby a může být spuštěno různé verze rozhraní .NET Framework.  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a>System.Configuration: Soubor Web.config a App.config  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] používá System.Configuration konfigurace systému [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
 Při konfiguraci služby v [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], použijte soubor Web.config nebo soubor App.config a zadejte nastavení. Volba název konfiguračního souboru je určen podle hostitelského prostředí, které zvolíte pro službu. Pokud používáte k hostování služby IIS, použijte soubor Web.config. Pokud používáte jiné hostitelské prostředí, můžete používejte soubor App.config.  
  
 V [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], soubor s názvem souboru App.config se používá k vytvoření konečné konfiguračního souboru. Název poslední ve skutečnosti použili při konfiguraci závisí na název sestavení. Například sestavení s názvem "Cohowinery.exe" má název souboru finální konfiguraci "Cohowinery.exe.config". Ale stačí pro změnu souboru App.config. Změny provedené v souboru jsou automaticky vytvářeny do konfiguračního souboru konečné aplikace v době kompilace.  
  
 Pomocí App.config, soubor konfigurační systém při spuštění aplikace a používá konfiguraci sloučí soubor App.config s obsahem souboru Machine.config. Tento mechanismus umožňuje celého systému a jak jsou definovány v souboru Machine.config. Použít soubor App.config pro přepsání nastavení souboru Machine.config; tak, aby získat používají, můžete uzamknout nastavení v souboru Machine.config. V případě Web.config sloučí konfigurační systém souborů Web.config ve všech adresářích vedoucí k adresáři aplikace do konfigurace, který se použije. [!INCLUDE[crabout](../../../includes/crabout-md.md)] Konfigurace a nastavení priority, najdete v tématech v <xref:System.Configuration> oboru názvů.  
  
## <a name="major-sections-of-the-configuration-file"></a>Hlavní části konfiguračního souboru  
 Hlavní části v konfiguračním souboru zahrnují následující prvky.  
  
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
>  Vazby a chování částech jsou volitelné a jsou zahrnuty pouze v případě potřeby.  
  
### <a name="the-services-element"></a>\<Services > – Element  
 `services` Element obsahuje specifikace pro všechny služby hostitelů aplikací. Počínaje zjednodušené konfigurační model v [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], v této části je volitelný.  
  
 [\<služby >](../../../docs/framework/configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a>\<Služby > elementu  
 Každá služba má tyto atributy:  
  
-   `name`. Určuje typ, který poskytuje implementaci kontraktu služby. Toto je plně kvalifikovaný název, který se skládá z oboru názvů, dobou a název typu. Například `"MyNameSpace.myServiceType"`.  
  
-   `behaviorConfiguration`. Určuje název jednoho z `behavior` elementy v nalezen `behaviors` element. Zadané chování řídí akce, například zda služba umožňuje zosobnění. Pokud je jeho hodnota prázdná název nebo Ne `behaviorConfiguration` je k dispozici potom sadu výchozí chování služby je přidán ke službě.  
  
-   [\<service>](../../../docs/framework/configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a>\<Endpoint > – Element  
 Každý koncový bod vyžaduje adresy, vazby a kontraktu, které jsou reprezentované pomocí následující atributy:  
  
-   `address`. Určuje služby identifikátor URI (Uniform Resource), které mohou být absolutní adresu nebo ten, který je uveden relativně k základní adresa služby. Pokud nastavit na prázdný řetězec, se označuje, že koncový bod je k dispozici na základní adrese, která je zadána při vytváření <xref:System.ServiceModel.ServiceHost> pro službu.  
  
-   `binding`. Obvykle určuje vazby poskytované systémem jako <xref:System.ServiceModel.WSHttpBinding>, ale můžete také určit, uživatelem definované vazby. Zadaná vazba Určuje typ přenosu, zabezpečení a kódování použité a toho, jestli spolehlivé relace, transakce nebo vysílání datového proudu podporován nebo povoleno.  
  
-   `bindingConfiguration`. Pokud je třeba upravit výchozí hodnoty vazby, to lze provést tak, že nakonfigurujete odpovídající `binding` element v `bindings` elementu. Tento atribut by měly mít stejnou hodnotu jako `name` atribut `binding` element, který se používá, chcete-li změnit výchozí hodnoty. Pokud není zadán název, nebo žádný `bindingConfiguration` je zadán vazba, vazba výchozí typ vazby se používá v koncovém bodě.  
  
-   `contract`. Určuje rozhraní, které definuje kontrakt. Toto je rozhraní implementované v běžné typ language runtime (CLR) určeného `name` atribut `service` elementu.  
  
-   [\<koncový bod > odkaz na element](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017)  
  
### <a name="the-bindings-element"></a>\<Vazby > elementu  
 `bindings` Element obsahuje specifikace pro všechny vazby, které můžete používat libovolný koncový bod definované v jakékoli služby.  
  
 [\<vazby >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a>\<Vazby > elementu  
 `binding` Elementů obsažených v `bindings` prvek může být buď jedné vazby poskytované systémem (najdete v části [System-Provided vazby](../../../docs/framework/wcf/system-provided-bindings.md)) nebo vlastní vazby (najdete v části [vlastní vazby](../../../docs/framework/wcf/extending/custom-bindings.md)). `binding` Element má `name` atribut, který korelaci vazba s zadaného v koncového bodu `bindingConfiguration` atribut `endpoint` elementu. Pokud není zadán žádný název, potom vazbou odpovídá na výchozí hodnoty tohoto typu vazby.  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)] Konfigurace služeb a klientů, najdete v části [konfigurace Windows Communication Foundation aplikací](http://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a).  
  
 [\<Vazba >](../../../docs/framework/misc/binding.md)  
  
### <a name="the-behaviors-element"></a>\<Chování > elementu  
 Toto je kontejnerový element pro `behavior` prvky, které definují chování pro službu.  
  
 [\<chování >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a>\<Chování > elementu  
 Každý `behavior` element je identifikována `name` atribut a poskytuje buď poskytované systémem chování, například <`throttling`>, nebo vlastní chování. Pokud není zadán název tohoto chování prvku odpovídá výchozí chování služba nebo koncový bod.  
  
 [\<chování >](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a>Jak používat vazby a konfigurace chování  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] umožňuje snadno sdílet konfigurace mezi koncovými body pomocí referenčního systému v konfiguraci. Namísto přímo přiřazení hodnoty konfigurace pro koncový bod, konfigurace související se vazby hodnoty jsou seskupené v `bindingConfiguration` elementů v `<binding>` oddílu. Konfigurace vazeb je pojmenovanou skupinu nastavení u vazby. Koncové body pak můžete odkazovat `bindingConfiguration` podle názvu.  
  
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
  
 `name` z `bindingConfiguration` je nastavena v `<binding>` elementu. `name` Musí být jedinečné řetězce v rámci oboru typ vazby – v takovém případě [< basicHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), nebo prázdná hodnota k odkazování na výchozí vazby. Koncový bod odkazy na konfiguraci nastavením `bindingConfiguration` atribut tento řetězec.  
  
 A `behaviorConfiguration` je implementována stejným způsobem, jak ukazuje následující příklad.  
  
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
  
 Všimněte si, že sada výchozí chování služby jsou přidány do služby. Tento systém umožňuje koncové body k sdílejí společné konfigurace bez opětovná definice nastavení. Pokud celého systému obor je požadován, vytvořte vazbu nebo chování konfiguraci v souboru Machine.config. Nastavení konfigurace jsou k dispozici ve všech souborů v souboru App.config. [Nástroj Configuration Editor (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) usnadňuje vytvoření konfigurací.  
  
## <a name="behavior-merge"></a>Chování sloučení  
 Funkci sloučení chování usnadňuje správu chování, pokud chcete sadu společné chování, který se má použít konzistentně. Tato funkce umožňuje zadat chování na různých úrovních v konfigurační hierarchii a máte služby dědit chování z několika úrovní v konfigurační hierarchii. Pro ilustraci jak toto funguje předpokládá, že máte následující rozložení virtuální adresář ve službě IIS:  
  
 ~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc  
  
 A souboru ~\Web.config má následující obsah:  
  
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
  
 A máte podřízený, které se nachází soubor Web.config v ~\Child\Web.config s tímto obsahem:  
  
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
  
 Služby umístěné v ~\Child\Service.svc se bude chovat, jako kdyby bylo serviceDebug i serviceMetadata chování. Služba nachází v ~\Service.svc budou mít pouze serviceDebug chování. Co se stane, je, že jsou sloučit dva chování kolekce se stejným názvem (v tomto případě prázdný řetězec).  
  
 Můžete také vymazat chování kolekce pomocí \<vymazat > značky a odebrat jednotlivé chování z kolekce pomocí \<odebrat > značky. Například následující dvě konfigurace výsledky v podřízeném služby s pouze serviceMetadata chování:  
  
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
  
 Chování sloučení se provádí pro kolekce nameless chování jako v příkladu nahoře a s názvem také kolekce chování.  
  
 Chování sloučení funguje ve službě IIS hostování prostředí, ve které sloučení souborů Web.config hierarchicky s souboru machine.config a kořenovém souboru Web.config. Ale spolupracuje také v prostředí aplikace, kde můžete sloučit machine.config pomocí souboru App.config.  
  
 Chování sloučení se vztahuje na koncový bod chování a chování služby v konfiguraci.  
  
 Pokud podřízené chování kolekce obsahuje chování, které se již nachází v kolekci chování nadřazené, přepíše chování podřízené nadřazený. Ano, pokud kolekce chování nadřazené měli `<serviceMetadata httpGetEnabled="False" />` a podřízené chování kolekce musí `<serviceMetadata httpGetEnabled="True" />`, podřízené chování by se mělo přepsat chování nadřazené v kolekci chování a httpGetEnabled by "true".  
  
## <a name="see-also"></a>Viz také  
 [Zjednodušená konfigurace](../../../docs/framework/wcf/simplified-configuration.md)  
 [Konfigurace aplikací pro Windows Communication Foundation](http://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a)  
 [\<service>](../../../docs/framework/configure-apps/file-schema/wcf/service.md)  
 [\<Vazba >](../../../docs/framework/misc/binding.md)
