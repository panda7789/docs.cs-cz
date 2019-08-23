---
title: <serviceActivations>
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: fb7c699612ef12aae39aaeadaf170d0e8f2553cd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936445"
---
# <a name="serviceactivations"></a>\<serviceActivations>

Prvek konfigurace, který umožňuje přidat nastavení definující nastavení aktivace virtuální služby, která jsou namapována na vaše typy služeb Windows Communication Foundation (WCF). Díky tomu je možné aktivovat služby hostované v rámci služby/IIS bez souboru. svc.

\<system.ServiceModel>\
\<serviceHostingEnvironment>\
\<serviceActivations>

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

|Prvek|Popis|
|-------------|-----------------|
|[\<add>](add-of-serviceactivations.md)|Přidá prvek konfigurace, který určuje aktivaci aplikace služby.|

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Popis|
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

Všimněte si `<serviceHostingEnvironment>` , že je konfigurace na úrovni aplikace. Je nutné umístit `web.config` konfiguraci obsahující konfiguraci do kořenového adresáře virtuální aplikace. Kromě toho `serviceHostingEnvironment` je machineToApplication dědičná část. Pokud v kořenovém adresáři počítače zaregistrujete jednu službu, bude tato služba dědit všechny služby v aplikaci.

Aktivace založená na konfiguraci podporuje aktivaci prostřednictvím protokolu HTTP i jiného typu než HTTP. Vyžaduje rozšíření v adresa relativeAddress, tj. svc,. XOML nebo. xamlx. Můžete namapovat vlastní rozšíření na know buildProviders, které vám pak umožní aktivovat službu přes jakékoli rozšíření. Po konfliktu `<serviceActivations>` oddíl přepíše registraci. svc.

## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
