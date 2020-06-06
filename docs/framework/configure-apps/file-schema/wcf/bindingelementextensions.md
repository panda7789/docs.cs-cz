---
title: <bindingElementExtensions>
ms.date: 03/30/2017
ms.assetid: bb597fc0-c947-451c-afda-bf23d42f4f4d
ms.openlocfilehash: c323a65ace332d2ecd1e03330dddbe7ca17ff5bd
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "69926372"
---
# \<bindingElementExtensions>
<span data-ttu-id="908c3-101">Tato část umožňuje použití vlastního prvku vazby z počítače nebo konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="908c3-101">This section enables the use of a custom binding element from a machine or application configuration file.</span></span> <span data-ttu-id="908c3-102">Do této kolekce můžete přidat vlastní prvek vazby pomocí `add` klíčového slova a nastavením `type` atributu elementu na rozšíření elementu vazby, jakož i `name` atribut pro vlastní element vazby.</span><span class="sxs-lookup"><span data-stu-id="908c3-102">You can add a custom binding element to this collection by using the `add` keyword, and setting the `type` attribute of the element to a binding element extension, as well as the `name` attribute to the custom binding element.</span></span>  
  
 <span data-ttu-id="908c3-103">Rozšíření vazby umožňují uživateli vytvořit uživatelsky definované prvky vazby pro použití jako součást vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="908c3-103">Binding extensions enable the user to create user-defined binding elements for use as part of custom bindings.</span></span> <span data-ttu-id="908c3-104">Programově je rozšíření vazby typu, který implementuje abstraktní třídu <xref:System.ServiceModel.Channels.BindingElement> .</span><span class="sxs-lookup"><span data-stu-id="908c3-104">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.BindingElement>.</span></span> <span data-ttu-id="908c3-105">V konfiguračním souboru `bindingElementExtensions` je oddíl použit k definování elementu rozšíření.</span><span class="sxs-lookup"><span data-stu-id="908c3-105">In the configuration file, the `bindingElementExtensions` section is used to define an extension element.</span></span>  
  
 <span data-ttu-id="908c3-106">V následujícím příkladu se používá `add` element a také `name` atribut pro přidání rozšíření vazby do `bindingElementExtensions` oddílu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="908c3-106">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingElementExtensions` section of the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="908c3-107">Chcete-li do prvku přidat možnosti konfigurace, musí uživatel zapsat a zaregistrovat `bindingElementExtensionSection` element.</span><span class="sxs-lookup"><span data-stu-id="908c3-107">To add configuration abilities to the element, the user needs to write and register a `bindingElementExtensionSection` element.</span></span> <span data-ttu-id="908c3-108">Další informace najdete v <xref:System.Configuration> dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="908c3-108">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="908c3-109">Po definování prvku a jeho typu konfigurace lze rozšíření použít jako součást vlastní vazby, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="908c3-109">After the element and its configuration type are defined, the extension can be used as part of a custom binding as shown in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="908c3-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="908c3-110">See also</span></span>

- <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>
- [<span data-ttu-id="908c3-111">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="908c3-111">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
