---
title: Aktivace založená na konfiguraci v IIS a WAS
ms.date: 03/30/2017
ms.assetid: 6a927e1f-b905-4ee5-ad0f-78265da38238
ms.openlocfilehash: 5e1672f4dd67950178c95d3e043e16072fcd0ef4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593578"
---
# <a name="configuration-based-activation-in-iis-and-was"></a>Aktivace založená na konfiguraci v IIS a WAS

Normálně při hostování služby Windows Communication Foundation (WCF) v rámci služby Internetová informační služba (IIS) nebo aktivační služby procesů systému Windows (WAS) je nutné zadat soubor. svc. Soubor. svc obsahuje název služby a volitelný vlastní objekt pro hostování služby. Tento další soubor přináší režii spravovatelnosti. Funkce aktivace na základě konfigurace odebere požadavek na soubor. svc, a proto na přidruženou režii.

## <a name="configuration-based-activation"></a>Aktivace podle konfigurace

Aktivace na základě konfigurace přebírá metadata, která se používají k umístění do souboru. svc, a umístí je do souboru Web. config. V rámci `serviceHostingEnvironment` prvku<> je <`serviceActivations`> element. V rámci `serviceActivations` prvku <> je jeden nebo více <ch `add`> prvků, jeden pro každou hostovanou službu. Prvek <`add`> obsahuje atributy, které umožňují nastavit relativní adresu pro službu a typ služby nebo objekt pro vytváření hostitele služby. Následující příklad kódu konfigurace ukazuje, jak se tento oddíl používá.

> [!NOTE]
> Každý <`add`> elementu musí určovat atribut Service nebo Factory. Zadání atributů Service a Factory je povoleno.

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add relativeAddress="MyServiceAddress" service="Service" factory="MyServiceHostFactory"/>
  </serviceActivations>
</serviceHostingEnvironment>
```

 S tímto souborem v souboru Web. config můžete umístit zdrojový kód služby do adresáře App_Code aplikace nebo sestavení v souladu s v adresáři bin aplikace.

> [!NOTE]
>
> - Při použití aktivace na základě konfigurace není podporován vložený kód v souborech. svc.
> - `relativeAddress`Atribut musí být nastaven na relativní adresu, například " \<sub-directory> /Service.svc" nebo "~/ \< Sub-Directory/Service. svc".
> - Výjimka konfigurace je vyvolána, pokud zaregistrujete relativní adresu, která nemá známou příponu přidruženou ke službě WCF.
> - Zadaná relativní adresa je relativní vzhledem k kořenu virtuální aplikace.
> - Z důvodu hierarchického modelu konfigurace jsou zaregistrované relativní adresy na úrovni počítače a webu děděny virtuálními aplikacemi.
> - Registrace v konfiguračním souboru mají přednost před nastaveními v souboru. svc,. xamlx,. XOML nebo jiném souboru.
> - Všechna lomítka (zpětná lomítka) v identifikátoru URI odeslanému službě IIS/WAS se automaticky převádějí na lomítko (lomítko). Pokud přidáte relativní adresu obsahující "\" a odešlete identifikátor URI služby IIS, který používá relativní adresu, zpětné lomítko se převede na lomítko a služba IIS ji nemůže spárovat s relativní adresou. Služba IIS odesílá informace o trasování, které označují, že se nenašly žádné shody.

## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection.ServiceActivations%2A>
- [Služby hostování](../hosting-services.md)
- [Přehled hostování služeb pracovních postupů](hosting-workflow-services-overview.md)
- [\<serviceHostingEnvironment>](../../configure-apps/file-schema/wcf/servicehostingenvironment.md)
- [Funkce hostování technologie Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
