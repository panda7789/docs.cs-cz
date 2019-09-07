---
title: <transport> z <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: 95cfa076f62f767af431ff5a0bcc2ca31b824e30
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399246"
---
# <a name="transport-of-wshttpbinding"></a>\<> přenosu > \<WSHttpBinding

Definuje nastavení ověřování pro přenos HTTP.

[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsHttpBinding >** ](wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpečení**](security-of-wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> přenosu**  

## <a name="syntax"></a>Syntaxe

```xml
<wsHttpBinding>
  <binding>
    <security mode="None|Transport|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="Basic|Certificate|Digest|None|Ntlm|Windows"
                 proxyCredentialType="Basic|Digest|None|Ntlm|Windows"
                 realm="string" />
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</wsHttpBinding>
```

## <a name="type"></a>type

<xref:System.ServiceModel.HttpTransportSecurity>

## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`clientCredentialType`|Určuje přihlašovací údaje, které se používají k ověření klienta ke službě. Tento atribut je typu <xref:System.ServiceModel.HttpClientCredentialType>.|
|`proxyCredentialType`|Určuje přihlašovací údaje, které se používají k ověření klienta na proxy doméně. Tento atribut je typu <xref:System.ServiceModel.HttpProxyCredentialType>.|
|`realm`|Řetězec, který určuje sféru ověřování pro ověřování algoritmem Digest nebo základního ověřování. Výchozí hodnota je prázdný řetězec.<br /><br /> Sféra ověřování určuje alespoň název hostitele, který provádí ověřování. Může také určit kolekci uživatelů, kteří mají přístup. Uživatel může zadat dotaz na sféru ověření, aby bylo možné zjistit, který z několika možných uživatelských jmen a hesel lze použít.|
|`policyEnforcement`|Tento výčet Určuje, kdy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> se má vyhovět.<br /><br /> 1.  Nikdy – zásada se nikdy vynutila (Rozšířená ochrana je zakázaná).<br />2.  WhenSupported – zásada se vynutila jenom v případě, že klient podporuje rozšířenou ochranu.<br />3.  Always – zásada se vždycky vynutila. Nepůjde ověřit klienty, kteří nepodporují rozšířenou ochranu.|

## <a name="clientcredentialtype-attribute"></a>clientCredentialType – atribut

|Value|Popis|
|-----------|-----------------|
|`None`|Zabezpečení je zakázané.|
|`Basic`|Používá základní ověřování.|
|`Digest`|Používá ověřování hodnotou hash.|
|`Ntlm`|Používá ověřování NTLM jako zálohu v doméně systému Windows.|
|`Windows`|Používá integrované ověřování systému Windows.|
|`Certificate`|Pomocí certifikátů X. 509 ověří klienta.|

## <a name="proxycredentialtype-attribute"></a>proxyCredentialType – atribut

|Value|Popis|
|-----------|-----------------|
|`None`|Zabezpečení je zakázané.|
|`Basic`|Používá základní ověřování.|
|`Digest`|Používá ověřování hodnotou hash.|
|`Ntlm`|Používá protokol NTLM jako zálohu s doménou systému Windows.|
|`Windows`|Používá integrované ověřování systému Windows.|
|`Certificate`|Pomocí certifikátů X. 509 ověří klienta.|

### <a name="child-elements"></a>Podřízené elementy

Žádné

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Popis|
|-------------|-----------------|
|[\<> zabezpečení](security-of-wshttpbinding.md)|Představuje možnosti [ \<zabezpečení wsHttpBinding >](wshttpbinding.md).|

## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<> vazby](../../../misc/binding.md)
