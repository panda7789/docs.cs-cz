---
title: <bindingExtensions>
ms.date: 03/30/2017
ms.assetid: 8373f94d-d095-486f-8f1e-4ac2f72b58c7
ms.openlocfilehash: bd6aeb32e0994bceb9e56bcb1c6267f4cb64a5a4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73039148"
---
# \<bindingExtensions>

Tato část umožňuje použití uživatelsky definované vazby z počítače nebo konfiguračního souboru aplikace. Uživatelem definovanou vazbu k této kolekci můžete přidat pomocí `add` klíčového slova a nastavením `type` atributu elementu na uživatelem definovanou vazbu a také `name` atributem na název uživatelsky definované vazby.

Rozšíření vazby umožňují uživateli vytvořit uživatelsky definované vazby, které se použijí jako součást konfigurace koncového bodu. Programově je rozšíření vazby typu, který implementuje abstraktní třídu <xref:System.ServiceModel.Channels.Binding> .

V následujícím příkladu je použit `add` element a také `name` atribut pro přidání rozšíření vazby do `bindingExtensions` oddílu konfiguračního souboru:

```xml
<system.serviceModel>
  <extensions>
    <bindingExtensions>
      <add name="MyBinding"
           type="Microsoft.ServiceModel.Samples.MyBinding, MyBinding,
                 Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
    </bindingExtensions>
  </extensions>
</system.serviceModel>
```

Chcete-li do prvku přidat možnosti konfigurace, musí uživatel zapsat a zaregistrovat `bindingSection` element. Další informace najdete v <xref:System.Configuration> dokumentaci.

Po definování prvku a jeho typu konfigurace lze rozšíření použít jako součást koncového bodu, jak je znázorněno v následujícím příkladu:

```xml
<services>
  <service name="MyService">
    <endpoint address="myAddress"
              binding="MyBinding" />
  </service>
</services>
```

## <a name="see-also"></a>Viz také

- [Rozšíření vazeb](../../../wcf/extending/extending-bindings.md)
