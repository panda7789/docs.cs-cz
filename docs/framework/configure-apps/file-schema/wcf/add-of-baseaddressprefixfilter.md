---
title: "&lt;add&gt; – &lt;baseAddressPrefixFilter&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b226bede-8459-4de9-b2ac-3d39604ce2bc
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7d4c509a710637e335f80257fb3984f164d83a51
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-ltbaseaddressprefixfiltergt"></a>&lt;add&gt; – &lt;baseAddressPrefixFilter&gt;
Reprezentuje element konfigurace, který určuje průchozí filtr, který poskytuje mechanismus pro hostování vyberte odpovídající vazby Internetové informační služby (IIS) [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] aplikace ve službě IIS.  
  
 \<systém. ServiceModel >  
\<ServiceHostingEnvironment >  
\<baseAddressPrefixFilters >  
\<Přidat >  
  
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
  
|Atribut|Popis|  
|---------------|-----------------|  
|Předpona|Identifikátor URI, který se používá k porovnání součástí základní adresu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<baseAddressPrefixFilters >](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)|Kolekci elementů konfigurace, které určují průchozí filtrů, které poskytují mechanismus při hostování vyberte odpovídající vazby služby IIS [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] aplikace ve službě IIS.|  
  
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
  
 V tomto příkladu `net.tcp://test1.fabrikam.com:8000` a `http://test2.fabrikam.com:9000` jsou pouze základní adresy pro jejich příslušných systémů, které mohou být předána.  
  
 Ve výchozím nastavení Pokud není zadána předponu, všechny adresy se předaly. Umožňuje zadat předponu pouze odpovídající základní adresu pro tento schéma, které se budou předávat.  
  
> [!NOTE]
>  Filtr nepodporuje žádné zástupné znaky. Kromě toho baseAddresses poskytované službou IIS pravděpodobně adresy vázaný na jiná schémata nejsou k dispozici v `baseAddressPrefixFilters` seznamu. Tyto adresy nejsou odfiltrována.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [Hostování](../../../../../docs/framework/wcf/feature-details/hosting.md)
