---
title: '&lt;exposedMethod&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ecef8049a980f662cce4c421f62ccd3703400d69
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltexposedmethodgt"></a>&lt;exposedMethod&gt;
Představuje metodu modelu COM +, který je zveřejněný, pokud je jako webovou službu vystavený rozhraní komponenty modelu COM +.  
  
 \<systém. ServiceModel >  
\<comContracts >  
\<comContract >  
\<metody >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<comContracts>  
  <comContract>  
      <exposedMethods>  
         <exposedMethod name="string" />  
      </exposedMethods>  
  </comContract>  
</comContracts>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|name|Řetězec, který obsahuje metodu modelu COM +, který je zveřejněný, pokud je jako webovou službu vystavený rozhraní komponenty modelu COM +.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<exposedMethods >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethods.md)|Kolekce [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elementy.|  
  
## <a name="remarks"></a>Poznámky  
 Modelu COM + integrace nástroje configuration (ComSvcConfig.exe) můžete použít k přidání konkrétních metod z rozhraní modelu COM se objevily na kontrakt generovaný služby.  
  
 Například následující příkaz můžete přidat tři metody s názvem z `IFinances` rozhraní modelu COM na `ItemOrders`. Finanční komponenta generovaného servisní smlouvou.  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 Když spustíte také ComSvcConfig.exe, pak generuje následující kontrakt služby výpis výše uvedených metod jako [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elementy.  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}" name="IFinances" namespace="http://contoso.com/services/financial">  
    <exposedMethod name="TransferFunds"/>  
    <exposedMethod name="AddFunds"/>  
    <exposedMethod name="RemoveFunds"/>  
</comContract>  
```  
  
 Během inicializace služby modulu runtime pokusí generovat kontraktu služby odrážející přes a přidáním pouze metody, které jsou uvedené v seznamu [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elementy. Trasování se vytvoří pro každou metodu rozhraní, která není součástí kontraktu služby.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.ComMethodElementCollection>  
 <xref:System.ServiceModel.Configuration.ComMethodElement>  
 [\<comContracts >](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [Integrace s aplikacemi modelu COM +](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [Postupy: Konfigurace nastavení služby COM +](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
