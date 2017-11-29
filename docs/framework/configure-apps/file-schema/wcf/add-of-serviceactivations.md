---
title: "&lt;add&gt; – &lt;serviceActivations&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5166f7859bb3e914de8313de08427cda9bc06d6f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-ltserviceactivationsgt"></a>&lt;add&gt; – &lt;serviceActivations&gt;
Konfigurace element, který umožňuje definovat nastavení aktivace virtuální služby, pomocí které jsou namapovány na vaše [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] typů služeb. Díky tomu je možné aktivovat služby hostované v WAS nebo IIS bez souborů .svc.  
  
 \<systém. ServiceModel >  
\<ServiceHostingEnvironment >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<serviceHostingEnvironment>   
   <serviceActivations>  
      <add factory="String"  
           service="String"/>  
   </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|objekt pro vytváření|Řetězec, který určuje název typu CLR objekt factory, který generuje element aktivace služby.|  
|service|ServiceType, který implementuje službu (úplná kvalifikovaný Typename nebo krátké Typename (Pokud je umístěn ve složce App_Code).|  
|relativeAddress|Relativní adresa v aktuální aplikaci služby IIS – například "Service.svc". Tato relativní adresa WCF 4.0 musí obsahovat jeden z známé přípon (.svc, .xamlx,...). Žádný fyzický soubor musí existovat pro relativeUrl|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|Konfigurační oddíl, který popisuje nastavení aktivace.|  
  
## <a name="remarks"></a>Poznámky  
 Následující příklad ukazuje, jak nakonfigurovat nastavení aktivace v souboru web.config.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <serviceHostingEnvironment>  
      <serviceActivations>  
        <add service="GreetingService"/>  
      </serviceActivations>  
    </serviceHostingEnvironment>  
  </system.serviceModel>  
</configuration>  
```  
  
 Pomocí této konfigurace, můžete aktivovat GreetingService bez použití soubor SVC.  
  
 Všimněte si, že `<serviceHostingEnvironment>` je konfigurace na úrovni aplikace. Je nutné umístit `web.config` obsahující konfiguraci kořenovém virtuální aplikace. Kromě toho `serviceHostingEnvironment` je machinetoApplication zděditelné oddíl. Když si zaregistrujete jedné služby v kořenu počítače, zdědí všechny služby v aplikaci tuto službu.  
  
 Aktivace podle konfigurace podporuje aktivaci přes protokol http a jiným protokolem než http. To vyžaduje rozšíření v relatativeAddress, tj. .svc, XOML nebo .xamlx. Vlastní rozšíření můžete namapovat buildProviders přehled, který budete pak moci aktivace služby přes jakoukoli příponu. Při konfliktu `<serviceActivations>` části přepsání .svc registrace.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.ServiceActivationElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>
