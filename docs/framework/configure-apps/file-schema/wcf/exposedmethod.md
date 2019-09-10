---
title: <exposedMethod>
ms.date: 03/30/2017
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
ms.openlocfilehash: 46f2872fb289c2793c356ea179deb3ce52e6d65e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855307"
---
# <a name="exposedmethod"></a>\<Prvků exposedMethod >
Představuje metodu COM+, která je vystavena v případě, že je rozhraní součásti modelu COM vystaveno jako webová služba.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Konfigurační oddíl comContracts >** ](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comContract >** ](comcontract.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<exposedMethods >** ](exposedmethods.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Prvků exposedMethod >**  
  
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
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<exposedMethods >](exposedmethods.md)|Kolekce prvků exposedMethod prvků >. [ \<](exposedmethod.md)|  
  
## <a name="remarks"></a>Poznámky  
 Nástroj pro konfiguraci integrace COM+ (ComSvcConfig. exe) se dá použít k přidání specifických metod z rozhraní modelu COM, které se zobrazí na vygenerované kontraktu služby.  
  
 Například můžete použít následující příkaz a přidat tři pojmenované metody z `IFinances` rozhraní COM `ItemOrders`na. Finanční komponenta k vygenerované smlouvě služby.  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 Když spustíte také ComSvcConfig. exe, vygeneruje následující kontrakt služby, který uvádí dřív uvedené metody jako [ \<prvky prvků exposedMethod >](exposedmethod.md) .  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"
             name="IFinances"
             namespace="http://contoso.com/services/financial">
  <exposedMethod name="TransferFunds"/>
  <exposedMethod name="AddFunds"/>
  <exposedMethod name="RemoveFunds"/>
</comContract>
```  
  
 V okamžiku inicializace služby se modul runtime pokusí vygenerovat kontrakt služby tím, že se odrážejí a přidá jenom metody, které jsou uvedené v seznamu [ \<prvků exposedmethodch prvků >](exposedmethod.md) . Trasování se vytvoří pro každou metodu rozhraní, která není zahrnutá v kontraktu služby.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.ComMethodElementCollection>
- <xref:System.ServiceModel.Configuration.ComMethodElement>
- [\<comContracts>](comcontracts.md)
- [Integrace s aplikacemi modelu COM+](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [Postupy: Konfigurace nastavení služby modelu COM+](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
