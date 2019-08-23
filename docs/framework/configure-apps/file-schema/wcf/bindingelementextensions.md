---
title: <bindingElementExtensions>
ms.date: 03/30/2017
ms.assetid: bb597fc0-c947-451c-afda-bf23d42f4f4d
ms.openlocfilehash: c323a65ace332d2ecd1e03330dddbe7ca17ff5bd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926372"
---
# <a name="bindingelementextensions"></a>\<bindingElementExtensions >
Tato část umožňuje použití vlastního prvku vazby z počítače nebo konfiguračního souboru aplikace. Do této kolekce můžete přidat vlastní prvek vazby pomocí `add` klíčového slova a `type` nastavením atributu elementu na rozšíření elementu vazby `name` , jakož i atribut pro vlastní element vazby.  
  
 Rozšíření vazby umožňují uživateli vytvořit uživatelsky definované prvky vazby pro použití jako součást vlastních vazeb. Programově je rozšíření vazby typu, který implementuje abstraktní třídu <xref:System.ServiceModel.Channels.BindingElement>. V konfiguračním souboru `bindingElementExtensions` je oddíl použit k definování elementu rozšíření.  
  
 V následujícím příkladu se používá `add` element a také `name` atribut pro přidání rozšíření vazby do `bindingElementExtensions` oddílu konfiguračního souboru.  
  
```xml  
<system.serviceModel>
  <extensions>
    <bindingElementExtensions>
      <add name="udpTransport"
           type="Microsoft.ServiceModel.Samples.UdpTransportSection, UdpTransport,
                 Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
    </bindingElementExtensions>
  </extensions>
</system.serviceModel>
```  
  
 Chcete-li do prvku přidat možnosti konfigurace, musí uživatel zapsat a zaregistrovat `bindingElementExtensionSection` element. Další informace najdete <xref:System.Configuration> v dokumentaci.  
  
 Po definování prvku a jeho typu konfigurace lze rozšíření použít jako součást vlastní vazby, jak je znázorněno v následujícím příkladu.  
  
```xml  
<customBinding>
  <binding name="test2">
    <udpTransport />
    <binaryMessageEncoding maxReadPoolSize="211"
                           maxWritePoolSize="2132"
                           maxSessionSize="3141" />
  </binding>
</customBinding>
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>
- [Rozšíření vazeb](../../../wcf/extending/extending-bindings.md)
