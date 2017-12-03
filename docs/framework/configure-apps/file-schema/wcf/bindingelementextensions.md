---
title: '&lt;bindingElementExtensions&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb597fc0-c947-451c-afda-bf23d42f4f4d
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 71fdc7c68ff7e672a5adf044bbe0200563772a58
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltbindingelementextensionsgt"></a>&lt;bindingElementExtensions&gt;
Tato část umožňuje použití vlastní vazby element z počítače nebo konfiguračního souboru aplikace. Element vlastní vazby můžete přidat do této kolekce pomocí `add` – klíčové slovo a nastavení `type` atribut elementu vazby element rozšíření, a taky `name` atribut prvku vlastní vazby.  
  
 Vazba rozšíření zajistit, aby uživatel k vytváření prvků uživatelem definované vazby pro použití v rámci vlastní vazby. Prostřednictvím kódu programu, rozšíření vazby je typ, který implementuje abstraktní třídu <xref:System.ServiceModel.Channels.BindingElement>. V konfiguračním souboru `bindingElementExtensions` části se používá k definování element rozšíření.  
  
 Následující příklad používá `add` elementu, společně s `name` přidat příponu vazby do atribut `bindingElementExtensions` oddílu konfiguračního souboru.  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <bindingElementExtensions>  
           <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportSection, UdpTransport,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </bindingElementExtensions>  
    </extensions>  
</system.serviceModel>  
```  
  
 Přidat konfiguraci dalo k elementu, uživatel musí k zápisu a zaregistrovat `bindingElementExtensionSection` elementu. Další informace najdete v tématu <xref:System.Configuration> dokumentaci.  
  
 Po elementu a jeho typ konfigurace jsou definovány, rozšíření lze použít jako součást vlastní vazby, jak je znázorněno v následujícím příkladu.  
  
```xml  
<customBinding>  
     <binding name="test2">  
         <udpTransport />  
         <binaryMessageEncoding maxReadPoolSize="211" maxWritePoolSize="2132"  
             maxSessionSize="3141" />  
         </binding>  
</customBinding>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>  
 [Rozšiřování vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)
