---
title: <dns>
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: ce12d0a82c8a443994559ed772496897f359b4e4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166670"
---
# <a name="dns"></a>\<dns>
Určuje očekávanou identitu serveru. Tato identita je platný pro X509 režim ověřování certifikátu, pokud certifikát serveru obsahuje DNS se stejnou hodnotou. Platí také pro režim ověřování systému Windows Pokud hlavní název služby má stejnou hodnotu.  
  
 Další informace o nastavení hodnoty prvku naleznete v tématu [identita a ověřování služby](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
 \<identity>  
\<dns>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|value|DNS certifikátu. DNS je standardní protokol slouží k vyhledání počítačů v síti na základě IP adresy. Uživatelé zapamatujete zobrazované názvy, například [ https://go.microsoft.com/fwlink/?prd=10929 ](https://go.microsoft.com/fwlink/?prd=10929) nebo [ https://go.microsoft.com/fwlink/?LinkID=96165 ](https://go.microsoft.com/fwlink/?LinkID=96165), jednodušší než adres na základě čísla, jako je například 207.46.131.137.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<identity>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Určuje identitu služby k ověření klienta.|  
  
## <a name="example"></a>Příklad  
 Následující kód konfigurace určuje DNS certifikát X.509, který se používá k ověření serveru.  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.DnsEndpointIdentity>
- [Identita a ověřování služby](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
