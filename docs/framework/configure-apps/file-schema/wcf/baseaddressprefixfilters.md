---
title: <baseAddressPrefixFilters>
ms.date: 03/30/2017
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
ms.openlocfilehash: 378db238d647be2248c0303f45aece42f7ea5b31
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701005"
---
# <a name="baseaddressprefixfilters"></a>\<baseAddressPrefixFilters>
Představuje kolekci konfigurace, které prvky, které určují předávání filtry, které poskytují mechanismus pro výběr příslušné vazby Internetové informační služby (IIS) při hostování aplikace Windows Communication Foundation (WCF) ve službě IIS.  
  
> [!WARNING]
>  \<baseAddressPrefixFilters > neobsahuje rozpoznat "localhost", použijte místo toho plně kvalifikovaný název počítače.  
  
 \<system.ServiceModel>  
\<ServiceHostingEnvironment>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
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
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddressprefixfilter.md)|Přidá prvek konfigurace, který určuje předponu filtr pro základní adresy použité hostitelem služby.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|Definuje typ, který vytvoří instanci hostitelským prostředím služby pro konkrétní přenos.|  
  
## <a name="remarks"></a>Poznámky  
 Filtr předponu poskytuje způsob pro sdílené poskytovatele hostingu k určení, které identifikátory URI se používá služba. Umožňuje sdílené hostitele k hostování více aplikací s jinou bázové adresy pro stejné schéma na stejném místě.  
  
 Webové servery služby IIS jsou kontejnery pro virtuální aplikace, které obsahují virtuální adresáře. Aplikace v síti přístupné prostřednictvím jedné nebo více vazeb služby IIS. Vazby služby IIS poskytuje dva druhy údajů: protokol vazby a informace o vazbě. Vazba protokolu (třeba HTTP) definuje schéma, přes které probíhá komunikace a vazby informace (například IP adresy, portu, hostitel) obsahuje data sloužící k přístupu na web.  
  
 Služba IIS podporuje zadávání více vazeb služby IIS pro každou lokalitu, což vede k více bázové adresy pro každé schéma. Protože služby WCF hostované na webu umožňuje vytváření vazby na pouze jednu základní adresu pro každé schéma, můžete použít předponu funkce filtru pro výběr vyžaduje základní adresa hostované služby. Příchozí základní adresy poskytované službou IIS, jsou filtrované na základě seznamu filtru volitelné předpony.  
  
 Váš web může obsahovat například následující základní adresy.  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 Následující konfigurační soubor můžete použít k zadání předpony filtr na úrovni appdomain.  
  
```xml  
<system.serviceModel>
  <serviceHostingEnvironment>
    <baseAddressPrefixFilters>
      <add prefix="net.tcp://test1.fabrikam.com:8000" />
      <add prefix="http://test2.fabrikam.com:9000" />
    </baseAddressPrefixFilters>
  </serviceHostingEnvironment>
</system.serviceModel>
```  
  
 V tomto příkladu `net.tcp://test1.fabrikam.com:8000` a `http://test2.fabrikam.com:9000` jsou pouze bázové adresy pro příslušné schémata, které jsou povolené, které se budou předávat.  
  
 Ve výchozím nastavení Pokud není zadána předponu, všechny adresy se předaly. Určení předpona, která umožňuje pouze odpovídající základní adresa pro toto schéma, které se budou předávat.  
  
> [!NOTE]
>  Tento filtr nepodporuje žádné zástupné znaky. Kromě toho baseAddresses poskytované službou IIS pravděpodobně adresy, které jsou vázány na jiná schémata není k dispozici v `baseAddressPrefixFilters` seznamu. Tyto adresy nejsou odfiltrovány.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [Hostování](../../../../../docs/framework/wcf/feature-details/hosting.md)
