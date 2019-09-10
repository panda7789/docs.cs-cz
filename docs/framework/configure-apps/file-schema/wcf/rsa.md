---
title: <rsa>
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: 0e1651f563bdb2b2b24eacacf7bfe387e33a82c7
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855043"
---
# <a name="rsa"></a>\<rsa>
Zabezpečený klient WCF, který se připojí ke koncovému bodu s touto identitou, ověří, že deklarace prezentované serverem obsahují deklaraci identity, která obsahuje veřejný klíč RSA používaný k vytvoření této identity.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> klienta**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> koncového bodu**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> identity**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> RSA**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<rsa value="String" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|value|Volitelný řetězec. Hodnota veřejného klíče RSA, která má být porovnána s klientem.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<identity>](identity.md)|Určuje identitu služby, kterou má klient ověřit.|  
  
## <a name="remarks"></a>Poznámky  
 Pomocí kontroly RSA můžete výslovně omezit ověřování na jeden certifikát na základě jeho klíče RSA nebo vygenerovat vlastní hodnotu klíče RSA. To umožňuje striktní ověřování konkrétního klíče RSA za cenu služby, která už nepracuje se stávajícími klienty, pokud se změní hodnota klíče RSA.  
  
 Další informace o použití identity k ověření služby klientovi najdete v tématu [identita služby a ověřování](../../../wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="example"></a>Příklad  
 Následující konfigurační kód určuje hodnotu veřejného klíče certifikátu X. 509, který se používá k ověření serveru.  
  
```xml  
<identity>
  <rsa value="0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" />
</identity>
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.RsaEndpointIdentity>
- [Identita a ověřování služby](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
