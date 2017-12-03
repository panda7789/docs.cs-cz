---
title: '&lt;serviceActivations&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 43461f23476d1c387cec06f9aee893defa634201
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltserviceactivationsgt"></a>&lt;serviceActivations&gt;
Konfigurace element, který umožňuje přidat nastavení, které definují nastavení aktivace virtuální služby, pomocí které jsou namapovány na vaše [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] typů služeb. Díky tomu je možné aktivovat služby hostované v WAS nebo IIS bez souborů .svc.  
  
 \<systém. ServiceModel >  
\<serviceHostingEnvironment >  
\<serviceActivations >  
  
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
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Přidat >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-serviceactivations.md)|Přidá prvek konfigurace, který určuje aktivace aplikace služby.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|Definuje typ, který vytvoří instanci služby hostování prostředí konkrétního přenosu.|  
  
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
  
 Aktivace podle konfigurace podporuje aktivaci přes protokol http a jiným protokolem než http. To vyžaduje rozšíření v relatativeAddress tj .svc, XOML nebo .xamlx. Vlastní rozšíření můžete namapovat buildProviders přehled, který budete pak moci aktivace služby přes jakoukoli příponu. Při konfliktu `<serviceActivations>` části přepsání .svc registrace.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>
