---
title: '&lt;bindingExtensions&gt;'
ms.date: 03/30/2017
ms.assetid: 8373f94d-d095-486f-8f1e-4ac2f72b58c7
ms.openlocfilehash: f99b38ede66dbecb44f9e8e67f921943071672ca
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750772"
---
# <a name="ltbindingextensionsgt"></a>&lt;bindingExtensions&gt;
Tato část umožňuje použití definované uživatelem vazby z počítače nebo konfiguračního souboru aplikace. Můžete přidat definované uživatelem vazby k této kolekci pomocí `add` – klíčové slovo a nastavení `type` atribut elementu uživatelem definované vazby, společně s `name` vazby definován atribut na jméno uživatele.  
  
 Vazba rozšíření umožňují uživatelům vytvořit uživatelem definované vazby pro použití v rámci konfigurace koncového bodu. Prostřednictvím kódu programu, rozšíření vazby je typ, který implementuje abstraktní třídu <xref:System.ServiceModel.Channels.Binding>.  
  
 Následující příklad používá `add` elementu, společně s `name` přidat příponu vazby do atribut `bindingElementExtensions` oddílu konfiguračního souboru.  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <bindingExtensions>  
           <add name="MyBinding" type="Microsoft.ServiceModel.Samples.MyBinding, MyBinding,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </bindingExtensions>  
    </extensions>  
</system.serviceModel>  
```  
  
 Přidat konfiguraci dalo k elementu, uživatel musí k zápisu a zaregistrovat `bindingSection` elementu. Další informace najdete v tématu <xref:System.Configuration> dokumentaci.  
  
 Po elementu a jeho typ konfigurace jsou definovány, rozšíření lze použít jako součást koncový bod, jak je znázorněno v následujícím příkladu.  
  
```xml  
<services>  
    <service name="MyService">  
        <endpoint address="myAddress" binding="MyBinding" />  
    </service>  
</services>  
```  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)
