---
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 7aa3755be97a839cb576d53852b75cfe50e39276
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "72773937"
---
# \<client>
`client`Prvek definuje seznam koncových bodů, ke kterým se klient může připojit.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<client>**

## <a name="syntax"></a>Syntaxe

```xml
<system.serviceModel>
  <client>
    <endpoint>
    </endpoint>
    <metadata>
    </metadata>
  </client>
</system.serviceModel>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy
 Žádné

### <a name="child-elements"></a>Podřízené elementy

|Prvek|Description|
|-------------|-----------------|
|[\<endpoint>](endpoint-of-client.md)|Obsahuje kolekci elementů koncového bodu, které určují koncové body, ke kterým se může tento klient připojit.|
|[\<metadata>](metadata.md)|Obsahuje nastavení pro zpracování metadat.|

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Description|
|-------------|-----------------|
|[\<system.serviceModel>](system-servicemodel.md)|Kořenový element všech prvků konfigurace Windows Communication Foundation (WCF).|

## <a name="remarks"></a>Poznámky
 `client`Oddíl definuje seznam koncových bodů, ke kterým se klient může připojit. Každý koncový bod uvedený v části klienta definuje vlastní vazbu, chování a kontrakt. Je jednoznačně identifikován kombinací `name` `contract` atributů a. Kód klienta Určuje, že se má `name` připojit ke koncovému bodu pro službu, kterou klient implementuje. Pokud `name` je atribut vynechán, koncový bod funguje jako výchozí koncový bod pro kontrakt, který implementuje.

 Kromě toho tato část také určuje nastavení pro zpracování metadat.

## <a name="example"></a>Příklad

```xml
<client>
  <endpoint address="/HelloWorld/"
            bindingConfiguration="usingDefaults"
            name="MyBinding"
            binding="customBinding"
            contract="HelloWorld">
    <addressProperties actingAs="http://www.microsoft.com/TestActor"
                       identityData="BasicReadWrite"
                       identityType="Spn"
                       isAddressPrivate="false">
  </endpoint>
</client>
```

## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [Konfigurace klienta WCF](../../../wcf/feature-details/client-configuration.md)
- [Klienti](../../../wcf/feature-details/clients.md)
