---
title: '&lt;serviceActivations&gt;'
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: 5da05c7b6a9685b9e34b3181ce8e0bd31ccd052b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54704953"
---
# <a name="ltserviceactivationsgt"></a>&lt;serviceActivations&gt;
Konfigurace element, který slouží k přidání nastavení, jenž definuje nastavení aktivace virtuální služby, která je namapována na daný typ služby Windows Communication Foundation (WCF). To umožňuje aktivovat službám hostovaným ve WAS / IIS bez souboru .svc.  
  
 \<system.ServiceModel>  
\<serviceHostingEnvironment>  
\<serviceActivations>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<serviceHostingEnvironment>
  <serviceActivations>
    <add factory="String"
         service="String" />
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
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-serviceactivations.md)|Přidá prvek konfigurace, který určuje aktivace aplikace služby.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|Definuje typ, který vytvoří instanci hostitelským prostředím služby pro konkrétní přenos.|  
  
## <a name="remarks"></a>Poznámky  
 Následující příklad ukazuje, jak nakonfigurovat nastavení aktivace v souboru web.config.  
  
```xml  
<configuration>
  <system.serviceModel>
    <serviceHostingEnvironment>
      <serviceActivations>
        <add service="GreetingService" />
      </serviceActivations>
    </serviceHostingEnvironment>
  </system.serviceModel>
</configuration>
```  
  
 Pomocí této konfigurace, můžete aktivovat GreetingService bez použití souboru .svc.  
  
 Všimněte si, že `<serviceHostingEnvironment>` je konfigurace na úrovni aplikace. Je nutné umístit `web.config` obsahující konfiguraci v kořenu virtuální aplikace. Kromě toho `serviceHostingEnvironment` machinetoApplication odvoditelný oddíl. Když si zaregistrujete jedinou službou v kořenové složce na počítači, každá služba aplikace zdědí tuto službu.  
  
 Aktivace podle konfigurace podporuje aktivaci přes protokol http a jiným protokolem než http. Vyžaduje rozšíření v relatativeAddress, tj. .svc, XOML nebo .xamlx. Vlastní rozšíření můžete namapovat buildProviders ví, která vám pak umožní k aktivaci služby přes jakékoli rozšíření. Při konfliktu `<serviceActivations>` části přepíše .svc registrace.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
