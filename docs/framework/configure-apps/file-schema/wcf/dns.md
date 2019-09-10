---
title: <dns>
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: c68cabd03eca71b41a0d0acce26897fa2653f4d3
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855376"
---
# <a name="dns"></a>\<dns>
Určuje očekávanou identitu serveru. Tato identita je platná pro režim ověřování certifikátu x509, pokud certifikát serveru obsahuje DNS se stejnou hodnotou. Je také platný pro režim ověřování systému Windows, pokud má hlavní název služby stejnou hodnotu.  
  
Další informace o nastavení hodnoty prvku naleznete v tématu [identity a ověřování služby](../../../wcf/feature-details/service-identity-and-authentication.md).  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> klienta**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> koncového bodu**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> identity**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> DNS**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|value|DNS certifikátu. DNS je standardní protokol, který se používá k nalezení počítačů v síti založené na protokolu IP. Uživatelé si můžou pamatovat zobrazované názvy, <https://go.microsoft.com/fwlink/?prd=10929> například [https://go.microsoft.com/fwlink/?LinkID=96165](https://go.microsoft.com/fwlink/?LinkID=96165)nebo, jednodušší než adresy založené na číslech, jako je například 207.46.131.137.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<identity>](identity.md)|Určuje identitu služby, kterou má klient ověřit.|  
  
## <a name="example"></a>Příklad  
 Následující konfigurační kód určuje DNS certifikátu X. 509, který se používá k ověření serveru.  
  
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
- [Identita a ověřování služby](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
