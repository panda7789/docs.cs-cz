---
title: <bindingExtensions>
ms.date: 03/30/2017
ms.assetid: 8373f94d-d095-486f-8f1e-4ac2f72b58c7
ms.openlocfilehash: 6eed4e8c549bccb06d8d425b084554a2ec7a1183
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55272757"
---
# <a name="bindingextensions"></a>\<bindingExtensions >
Tato část umožňuje použití uživatelem definované vazby z počítače nebo konfiguračního souboru aplikace. Můžete přidat uživatelem definovaného prvku vazby k této kolekci pomocí `add` – klíčové slovo a nastavení `type` atribut elementu do uživatelem definované vazby, stejně jako `name` definované vazby atributu na jméno uživatele.  
  
 Rozšíření vazby umožňují uživateli vytvořit uživatelem definované vazby pro použití v rámci konfigurace koncového bodu. Prostřednictvím kódu programu, rozšíření vazby je typ, který implementuje abstraktní třídu <xref:System.ServiceModel.Channels.Binding>.  
  
 V následujícím příkladu `add` element, stejně jako `name` atribut můžete přidat příponu vazby na `bindingElementExtensions` oddílu konfiguračního souboru.  
  
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
  
 Chcete-li přidat možnosti konfigurace na prvek, uživatel musí k zápisu a registrace `bindingSection` elementu. Další informace najdete v článku <xref:System.Configuration> dokumentaci.  
  
 Po definování elementu a jeho typ konfigurace rozšíření, je možné jako součást koncového bodu, jak je znázorněno v následujícím příkladu.  
  
```xml  
<services>
  <service name="MyService">
    <endpoint address="myAddress"
              binding="MyBinding" />
  </service>
</services>
```  
  
## <a name="see-also"></a>Viz také:
- [Rozšíření vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)
