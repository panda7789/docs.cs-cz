---
title: <serviceActivations>
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: 64ae0bfd90ae941fc78515c7936c998201c87485
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855131"
---
# \<serviceActivations>

Prvek konfigurace, který umožňuje přidat nastavení definující nastavení aktivace virtuální služby, která jsou namapována na vaše typy služeb Windows Communication Foundation (WCF). Díky tomu je možné aktivovat služby hostované v rámci služby/IIS bez souboru. svc.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceActivations>**  

## <a name="syntax"></a>Syntaxe

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

Žádné

### <a name="child-elements"></a>Podřízené elementy

|Prvek|Description|
|-------------|-----------------|
|[\<add>](add-of-serviceactivations.md)|Přidá prvek konfigurace, který určuje aktivaci aplikace služby.|

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Description|
|-------------|-----------------|
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|Definuje typ, který hostující prostředí služby vytvoří pro konkrétní přenos.|

## <a name="remarks"></a>Poznámky

Následující příklad ukazuje, jak nakonfigurovat nastavení aktivace v souboru Web. config.

```xml
<configuration>
  <system.serviceModel>
    <serviceHostingEnvironment>
      <serviceActivations>
        <add service="GreetingService" />
      </serviceActivations>
    </serviceHostingEnvironment>
  </system.serviceModel>
</configuration>
```

Pomocí této konfigurace můžete aktivovat GreetingService bez použití souboru. svc.

Všimněte si, že `<serviceHostingEnvironment>` je konfigurace na úrovni aplikace. Je nutné umístit `web.config` konfiguraci obsahující konfiguraci do kořenového adresáře virtuální aplikace. Kromě toho `serviceHostingEnvironment` je machineToApplication dědičná část. Pokud v kořenovém adresáři počítače zaregistrujete jednu službu, bude tato služba dědit všechny služby v aplikaci.

Aktivace založená na konfiguraci podporuje aktivaci prostřednictvím protokolu HTTP i jiného typu než HTTP. Vyžaduje rozšíření v adresa relativeAddress, tj.. svc,. XOML nebo. xamlx. Můžete namapovat vlastní rozšíření na know buildProviders, které vám pak umožní aktivovat službu přes jakékoli rozšíření. Po konfliktu `<serviceActivations>` oddíl přepíše registraci. svc.

## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
