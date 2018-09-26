---
title: Aktivace založená na konfiguraci v IIS a WAS
ms.date: 03/30/2017
ms.assetid: 6a927e1f-b905-4ee5-ad0f-78265da38238
ms.openlocfilehash: da98d237c066b70398d3238a75500e8a3abbe887
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47114993"
---
# <a name="configuration-based-activation-in-iis-and-was"></a>Aktivace založená na konfiguraci v IIS a WAS

Obvykle při hostování služby Windows Communication Foundation (WCF) v rámci Internetové informační služby (IIS) nebo Windows Process Activation Service (WAS), je nutné zadat soubor SVC. Souboru SVC obsahuje název služby a objektu pro vytváření hostitele volitelné vlastní služby. Tento přidaný soubor přidává režijní náklady na správu. Funkce aktivace podle konfigurace eliminuje nutnost mít souboru .svc a proto přidružené režie.

## <a name="configuration-based-activation"></a>Aktivace podle konfigurace

Aktivace podle konfigurace používá metadata, která používá budou umístěny v souboru svc a umístí jej do souboru Web.config. V rámci <`serviceHostingEnvironment`> element neexistuje <`serviceActivations`> element. V rámci <`serviceActivations`> element jsou jeden nebo více <`add`> elementy, jeden pro každý hostovanou službu. <`add`> Element obsahuje atributy, které umožňují nastavit relativní adresu pro službu a typ služby nebo objekt pro vytváření hostitele služby. Následující příklad kódu konfigurace ukazuje, jak se používá v této části.

> [!NOTE]
>  Každý <`add`> element musí určovat atribut factory nebo služby. Zadání služba a výrobce atributy je povoleno.

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add relativeAddress="MyServiceAddress" service="Service" factory="MyServiceHostFactory"/>
  </serviceActivations>
</serviceHostingEnvironment>
```

 S tímto v souboru Web.config můžete umístit služby zdrojový kód v adresáři App_Code splněny sestavení v adresáři Bin aplikace nebo aplikace.

> [!NOTE]
> - Při použití aktivace prostřednictvím konfigurace, vložení kódu za hledání souborů .svc se nepodporuje.
> - `relativeAddress` Atribut musí být nastaven na relativní adresu, jako například "\<podadresář > / service.svc" nebo "~ /\<directory dílčí, service.svc".
> - Když si zaregistrujete relativní adresa, na kterém není známá přípona přidružená k WCF, je vyvolána výjimka v konfiguraci.
> - Zadaná relativní adresa je relativní vzhledem k kořen virtuální aplikace.
> - Z důvodu hierarchický model konfigurace registrované relativní adresy na úrovni počítače a serveru jsou děděné virtuální aplikace.
> - Registrace v konfiguračním souboru mají přednost před nastavením v .svc, .xamlx, XOML nebo jiný soubor.
> - Žádné ' \' (zpětná lomítka) v identifikátoru URI odeslané do služby IIS / WAS se automaticky převedou na "/" (lomítko). Pokud je relativní adresa se přidá, který obsahuje "\" a odeslat služby IIS, který používá relativní adresu URI, zpětné lomítko je převedeno na dopředné lomítko a služby IIS nesmí odpovídat na relativní adresu. Služba IIS odesílá informace o trasování, která označuje, že nejsou nalezeny žádné odpovídající položky.

## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection.ServiceActivations%2A>
- [Služby hostování](../../../../docs/framework/wcf/hosting-services.md)
- [Přehled hostování služeb pracovních postupů](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)
- [\<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)
- [Hostování funkcí systému Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201276)