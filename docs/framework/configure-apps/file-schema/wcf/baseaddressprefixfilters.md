---
title: '&lt;baseAddressPrefixFilters&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 39ceaf3377f1da7f3f953024e1207618df84bf1d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltbaseaddressprefixfiltersgt"></a>&lt;baseAddressPrefixFilters&gt;
Představuje kolekci elementů konfigurace, které určují průchodu přes filtrů, které poskytují mechanismus vyberte odpovídající vazby Internetové informační služby (IIS), při hostování [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] aplikace ve službě IIS.  
  
> [!WARNING]
>  \<baseAddressPrefixFilters > neobsahuje rozpoznat "localhost", místo toho použijte název plně kvalifikovaný počítače.  
  
 \<systém. ServiceModel >  
\<ServiceHostingEnvironment >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="string"/>  
     </baseAddressPrefixFilters>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Přidat >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddressprefixfilter.md)|Přidá element konfigurace, který určuje předponu filtr pro základní adresy používané hostitele služby.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|Definuje typ, který vytvoří instanci služby hostování prostředí konkrétního přenosu.|  
  
## <a name="remarks"></a>Poznámky  
 Předpona filtr poskytuje způsob, jak sdílené poskytovatelům hostingu zadejte identifikátory, které mají být použita služba. Umožňuje sdílené hostitele k hostování více aplikací s jiné základní adresy pro stejné schéma ve stejné lokalitě.  
  
 Webové servery služby IIS jsou kontejnery pro virtuální aplikace, které obsahují virtuální adresáře. Aplikace v síti je přístupná přes jeden nebo více vazby služby IIS. Vazby služby IIS poskytují dva kusy informací: protokol vazby a informace o vazbě. Vazba protokol (například HTTP) definuje schéma, přes který probíhá komunikace a vazby informace (například IP adresu, Port, hostitel) obsahuje data používá pro přístup k webu.  
  
 Služba IIS podporuje zadání více vazby služby IIS pro každou lokalitu, což vede k více základní adresy pro každé schéma. Protože [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služba hostovaná na webu umožňuje vazby pouze jeden základní adresu pro každé schéma, můžete použít funkci filtru předponu a vyberte požadované základní adresu hostované služby. Příchozí základní adresy poskytované službou IIS, jsou filtrovány na základě seznamu filtru volitelné předponu.  
  
 Například váš web může obsahovat následující základní adresy.  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 Následující konfigurační soubor můžete použít k zadání předpony filtru na úrovni domény aplikace.  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="net.tcp://test1.fabrikam.com:8000"/>  
        <add prefix="http://test2.fabrikam.com:9000"/>  
    </baseAddressPrefixFilters>  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 V tomto příkladu `net.tcp://test1.fabrikam.com:8000` a `http://test2.fabrikam.com:9000` jsou pouze základní adresy pro příslušné schémat, které mohou být předána.  
  
 Ve výchozím nastavení Pokud není zadána předponu, všechny adresy se předaly. Umožňuje zadat předponu pouze odpovídající základní adresu pro tento schéma, které se budou předávat.  
  
> [!NOTE]
>  Filtr nepodporuje žádné zástupné znaky. Kromě toho baseAddresses poskytované službou IIS pravděpodobně adresy vázaný na jiná schémata nejsou k dispozici v `baseAddressPrefixFilters` seznamu. Tyto adresy nejsou odfiltrována.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [Hostování](../../../../../docs/framework/wcf/feature-details/hosting.md)
