---
title: <exposedMethod>
ms.date: 03/30/2017
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
ms.openlocfilehash: 46f2872fb289c2793c356ea179deb3ce52e6d65e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855307"
---
# \<exposedMethod>
Představuje metodu COM+, která je vystavena v případě, že je rozhraní součásti modelu COM vystaveno jako webová služba.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<exposedMethods>**](exposedmethods.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<exposedMethod>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<comContracts>
  <comContract>
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|name|Řetězec obsahující metodu modelu COM+, která je vystavena v případě, že je rozhraní součásti modelu COM vystaveno jako webová služba.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<exposedMethods>](exposedmethods.md)|Kolekce [\<exposedMethod>](exposedmethod.md) prvků.|  
  
## <a name="remarks"></a>Poznámky  
 Nástroj pro konfiguraci integrace COM+ (ComSvcConfig. exe) se dá použít k přidání specifických metod z rozhraní modelu COM, které se zobrazí na vygenerované kontraktu služby.  
  
 Například můžete použít následující příkaz a přidat tři pojmenované metody z `IFinances` rozhraní COM na `ItemOrders` . Finanční komponenta k vygenerované smlouvě služby.  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 Při spuštění nástroje ComSvcConfig. exe pak vygeneruje následující kontrakt služby, který obsahuje výše zmíněné metody jako [\<exposedMethod>](exposedmethod.md) prvky.  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"
             name="IFinances"
             namespace="http://contoso.com/services/financial">
  <exposedMethod name="TransferFunds"/>
  <exposedMethod name="AddFunds"/>
  <exposedMethod name="RemoveFunds"/>
</comContract>
```  
  
 V okamžiku inicializace služby se modul runtime pokusí vygenerovat kontrakt služby tím, že se odrážejí a přidá pouze metody, které jsou obsaženy v seznamu [\<exposedMethod>](exposedmethod.md) prvků. Trasování se vytvoří pro každou metodu rozhraní, která není zahrnutá v kontraktu služby.  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.ComMethodElementCollection>
- <xref:System.ServiceModel.Configuration.ComMethodElement>
- [\<comContracts>](comcontracts.md)
- [Integrace s aplikacemi modelu COM+](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [Postupy: Konfigurace nastavení služby modelu COM+](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
