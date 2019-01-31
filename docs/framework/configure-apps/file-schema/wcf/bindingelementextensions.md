---
title: <bindingElementExtensions>
ms.date: 03/30/2017
ms.assetid: bb597fc0-c947-451c-afda-bf23d42f4f4d
ms.openlocfilehash: 9a2a3af093949c1d724fdea13655bbb80fe71048
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270459"
---
# <a name="bindingelementextensions"></a><span data-ttu-id="66418-101">\<bindingElementExtensions ></span><span class="sxs-lookup"><span data-stu-id="66418-101">\<bindingElementExtensions></span></span>
<span data-ttu-id="66418-102">Tato část umožňuje používat vlastní prvek vazby z počítače nebo konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="66418-102">This section enables the use of a custom binding element from a machine or application configuration file.</span></span> <span data-ttu-id="66418-103">Vlastní prvek vazby můžete přidat do této kolekce pomocí `add` – klíčové slovo a nastavení `type` atribut elementu, který chcete rozšíření elementu vazby, stejně jako `name` atribut na prvek vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="66418-103">You can add a custom binding element to this collection by using the `add` keyword, and setting the `type` attribute of the element to a binding element extension, as well as the `name` attribute to the custom binding element.</span></span>  
  
 <span data-ttu-id="66418-104">Rozšíření vazby umožňují uživateli vytvořit uživatelem definované vazby prvky pro použití jako součást vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="66418-104">Binding extensions enable the user to create user-defined binding elements for use as part of custom bindings.</span></span> <span data-ttu-id="66418-105">Prostřednictvím kódu programu, rozšíření vazby je typ, který implementuje abstraktní třídu <xref:System.ServiceModel.Channels.BindingElement>.</span><span class="sxs-lookup"><span data-stu-id="66418-105">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.BindingElement>.</span></span> <span data-ttu-id="66418-106">V konfiguračním souboru `bindingElementExtensions` oddíl se používá k definování element rozšíření.</span><span class="sxs-lookup"><span data-stu-id="66418-106">In the configuration file, the `bindingElementExtensions` section is used to define an extension element.</span></span>  
  
 <span data-ttu-id="66418-107">V následujícím příkladu `add` element, stejně jako `name` atribut můžete přidat příponu vazby na `bindingElementExtensions` oddílu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="66418-107">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingElementExtensions` section of the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="66418-108">Chcete-li přidat možnosti konfigurace na prvek, uživatel musí k zápisu a registrace `bindingElementExtensionSection` elementu.</span><span class="sxs-lookup"><span data-stu-id="66418-108">To add configuration abilities to the element, the user needs to write and register a `bindingElementExtensionSection` element.</span></span> <span data-ttu-id="66418-109">Další informace najdete v článku <xref:System.Configuration> dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="66418-109">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="66418-110">Po definování elementu a jeho typ konfigurace rozšíření, je možné jako součást vlastní vazby, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="66418-110">After the element and its configuration type are defined, the extension can be used as part of a custom binding as shown in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="66418-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="66418-111">See also</span></span>
- <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>
- [<span data-ttu-id="66418-112">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="66418-112">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
