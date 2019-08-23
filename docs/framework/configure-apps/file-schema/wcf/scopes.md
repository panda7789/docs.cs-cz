---
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: dd6513930798e9e1ab263f75c9350511c2dcdcd5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935185"
---
# <a name="scopes"></a>\<> oborů
Obsahuje kolekci prvků konfigurace, které určují identifikátory URI vlastního oboru, které lze použít k filtrování koncových bodů služby během dotazu.  
  
\<system.ServiceModel>  
\<> chování  
\<endpointBehaviors>  
\<> chování  
\<endpointDiscovery>  
\<> oborů  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI" />
        </scopes>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|[\<add>](add-of-scopes.md)|Přidá informace o oboru pro koncový bod, který lze použít v porovnání kritérií pro hledání služeb.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<endpointDiscovery>](endpointdiscovery.md)|Určuje různá nastavení zjišťování pro koncový bod, například jeho zjistitelnost, obory a jakákoli vlastní rozšíření pro jeho metadata.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
