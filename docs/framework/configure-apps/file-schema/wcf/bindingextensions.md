---
title: <bindingExtensions>
ms.date: 03/30/2017
ms.assetid: 8373f94d-d095-486f-8f1e-4ac2f72b58c7
ms.openlocfilehash: ed55701e45d8580e37cf4776de6b9c5241e0548c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113032"
---
# <a name="bindingextensions"></a><span data-ttu-id="bb21c-101">\<bindingExtensions ></span><span class="sxs-lookup"><span data-stu-id="bb21c-101">\<bindingExtensions></span></span>
<span data-ttu-id="bb21c-102">Tato část umožňuje použití uživatelem definované vazby z počítače nebo konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="bb21c-102">This section enables the use of a user defined binding from a machine or application configuration file.</span></span> <span data-ttu-id="bb21c-103">Můžete přidat uživatelem definovaného prvku vazby k této kolekci pomocí `add` – klíčové slovo a nastavení `type` atribut elementu do uživatelem definované vazby, stejně jako `name` definované vazby atributu na jméno uživatele.</span><span class="sxs-lookup"><span data-stu-id="bb21c-103">You can add a user defined binding to this collection by using the `add` keyword, and setting the `type` attribute of the element to a user defined binding, as well as the `name` attribute to the name of the user defined binding.</span></span>  
  
 <span data-ttu-id="bb21c-104">Rozšíření vazby umožňují uživateli vytvořit uživatelem definované vazby pro použití v rámci konfigurace koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="bb21c-104">Binding extensions enable the user to create user-defined bindings for use as part an endpoint configuration.</span></span> <span data-ttu-id="bb21c-105">Prostřednictvím kódu programu, rozšíření vazby je typ, který implementuje abstraktní třídu <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="bb21c-105">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.Binding>.</span></span>  
  
 <span data-ttu-id="bb21c-106">V následujícím příkladu `add` element, stejně jako `name` atribut můžete přidat příponu vazby na `bindingElementExtensions` oddílu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="bb21c-106">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingElementExtensions` section of the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="bb21c-107">Chcete-li přidat možnosti konfigurace na prvek, uživatel musí k zápisu a registrace `bindingSection` elementu.</span><span class="sxs-lookup"><span data-stu-id="bb21c-107">To add configuration abilities to the element, the user needs to write and register a `bindingSection` element.</span></span> <span data-ttu-id="bb21c-108">Další informace najdete v článku <xref:System.Configuration> dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="bb21c-108">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="bb21c-109">Po definování elementu a jeho typ konfigurace rozšíření, je možné jako součást koncového bodu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="bb21c-109">After the element and its configuration type are defined, the extension can be used as part of an endpoint as shown in the following example.</span></span>  
  
```xml  
<services>
  <service name="MyService">
    <endpoint address="myAddress"
              binding="MyBinding" />
  </service>
</services>
```  
  
## <a name="see-also"></a><span data-ttu-id="bb21c-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bb21c-110">See also</span></span>

- [<span data-ttu-id="bb21c-111">Rozšiřování vazeb</span><span class="sxs-lookup"><span data-stu-id="bb21c-111">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
