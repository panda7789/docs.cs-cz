---
title: <clientCertificate> z <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
ms.openlocfilehash: a8a78bbfcd9dfbf6975503a845d5bb4e2d24b13d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398141"
---
# <a name="clientcertificate-of-servicecredentials"></a>\<clientCertificate> z \<serviceCredentials>
Definuje certifikát X. 509, který se používá k podpisu a šifrování zpráv na straně klienta ve formě duplexního komunikačního vzoru.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientCertificate>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<clientCertificate>
  <certificate />
  <authentication />
</clientCertificate>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<authentication>](authentication-of-clientcertificate-element.md)|Určuje možnosti ověřování pro klientský certifikát.|  
|[\<certificate>](certificate-of-clientcertificate-element.md)|Určuje certifikát, který se má použít.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|Určuje přihlašovací údaje, které se mají použít při ověřování služby, a nastavení související s ověřováním přihlašovacích údajů klienta.|  
  
## <a name="remarks"></a>Poznámky  
 Tento prvek se používá v případě, že služba musí mít certifikát klienta předem pro zabezpečenou komunikaci s klientem. K tomu dochází při použití duplexního způsobu komunikace. V typickém vzoru požadavků a odpovědí klient zahrne svůj certifikát do žádosti, kterou služba používá k šifrování a podepsání své odpovědi zpět do klienta. Ve způsobu duplexního přenosu však služba nemá požadavek od klienta, a proto potřebuje certifikát klienta předem, aby bylo možné zprávu zabezpečit klientovi. Proto je nutné získat certifikát klienta při vzdáleném vyjednávání a zadat certifikát pomocí tohoto prvku. Další informace o duplexních službách najdete v tématu [Postupy: Vytvoření duplexního kontraktu](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
 Certifikát nastavený v tomto elementu se používá k šifrování zpráv klientovi jenom pro vazby, které jsou nakonfigurované s `MutualCertificateDuplex` režimem ověřování zabezpečení zprávy.  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>
- [Postupy: Vytvoření duplexního kontraktu](../../../wcf/feature-details/how-to-create-a-duplex-contract.md)
- [Chování zabezpečení](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md)
