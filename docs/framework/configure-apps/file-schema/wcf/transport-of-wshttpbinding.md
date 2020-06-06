---
title: <transport> z <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: 1afeed62fcbf3b083d69a7cedb7eb80b81f5c17b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73732734"
---
# <a name="transport-of-wshttpbinding"></a>\<transport> z \<wsHttpBinding>

Definuje nastavení ověřování pro přenos HTTP.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  

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

## <a name="type"></a>Typ

<xref:System.ServiceModel.HttpTransportSecurity>

## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`clientCredentialType`|Určuje přihlašovací údaje, které se používají k ověření klienta ke službě. Tento atribut je typu <xref:System.ServiceModel.HttpClientCredentialType> .|
|`proxyCredentialType`|Určuje přihlašovací údaje, které se používají k ověření klienta na proxy doméně. Tento atribut je typu <xref:System.ServiceModel.HttpProxyCredentialType> .|
|`realm`|Řetězec, který určuje sféru ověřování pro ověřování algoritmem Digest nebo základního ověřování. Výchozí hodnota je prázdný řetězec.<br /><br /> Sféra ověřování určuje alespoň název hostitele, který provádí ověřování. Může také určit kolekci uživatelů, kteří mají přístup. Uživatel může zadat dotaz na sféru ověření, aby bylo možné zjistit, který z několika možných uživatelských jmen a hesel lze použít.|
|`policyEnforcement`|Tento výčet Určuje, kdy se <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> má vyhovět.<br /><br /> 1. nikdy – zásada se nikdy vynutila (Rozšířená ochrana je zakázaná).<br />2. WhenSupported – zásada se vynutila jenom v případě, že klient podporuje rozšířenou ochranu.<br />3. Always – zásada se vždycky vynutila. Nepůjde ověřit klienty, kteří nepodporují rozšířenou ochranu.|

## <a name="clientcredentialtype-attribute"></a>clientCredentialType – atribut

|Hodnota|Description|
|-----------|-----------------|
|`None`|Zabezpečení je zakázané.|
|`Basic`|Používá základní ověřování.|
|`Digest`|Používá ověřování hodnotou hash.|
|`Ntlm`|Používá ověřování NTLM jako zálohu v doméně systému Windows.|
|`Windows`|Používá integrované ověřování systému Windows.|
|`Certificate`|Pomocí certifikátů X. 509 ověří klienta.|

## <a name="proxycredentialtype-attribute"></a>proxyCredentialType – atribut

|Hodnota|Description|
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

|Prvek|Description|
|-------------|-----------------|
|[\<security>](security-of-wshttpbinding.md)|Představuje možnosti zabezpečení [\<wsHttpBinding>](wshttpbinding.md) .|

## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
