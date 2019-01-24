---
title: '&lt;bindingExtensions&gt;'
ms.date: 03/30/2017
ms.assetid: 8373f94d-d095-486f-8f1e-4ac2f72b58c7
ms.openlocfilehash: 2b0e3fe417d76a08b7dd3295b68a179c3d9acefc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672887"
---
# <a name="ltbindingextensionsgt"></a><span data-ttu-id="8156b-102">&lt;bindingExtensions&gt;</span><span class="sxs-lookup"><span data-stu-id="8156b-102">&lt;bindingExtensions&gt;</span></span>
<span data-ttu-id="8156b-103">Tato část umožňuje použití uživatelem definované vazby z počítače nebo konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="8156b-103">This section enables the use of a user defined binding from a machine or application configuration file.</span></span> <span data-ttu-id="8156b-104">Můžete přidat uživatelem definovaného prvku vazby k této kolekci pomocí `add` – klíčové slovo a nastavení `type` atribut elementu do uživatelem definované vazby, stejně jako `name` definované vazby atributu na jméno uživatele.</span><span class="sxs-lookup"><span data-stu-id="8156b-104">You can add a user defined binding to this collection by using the `add` keyword, and setting the `type` attribute of the element to a user defined binding, as well as the `name` attribute to the name of the user defined binding.</span></span>  
  
 <span data-ttu-id="8156b-105">Rozšíření vazby umožňují uživateli vytvořit uživatelem definované vazby pro použití v rámci konfigurace koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="8156b-105">Binding extensions enable the user to create user-defined bindings for use as part an endpoint configuration.</span></span> <span data-ttu-id="8156b-106">Prostřednictvím kódu programu, rozšíření vazby je typ, který implementuje abstraktní třídu <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="8156b-106">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.Binding>.</span></span>  
  
 <span data-ttu-id="8156b-107">V následujícím příkladu `add` element, stejně jako `name` atribut můžete přidat příponu vazby na `bindingElementExtensions` oddílu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="8156b-107">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingElementExtensions` section of the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="8156b-108">Chcete-li přidat možnosti konfigurace na prvek, uživatel musí k zápisu a registrace `bindingSection` elementu.</span><span class="sxs-lookup"><span data-stu-id="8156b-108">To add configuration abilities to the element, the user needs to write and register a `bindingSection` element.</span></span> <span data-ttu-id="8156b-109">Další informace najdete v článku <xref:System.Configuration> dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="8156b-109">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="8156b-110">Po definování elementu a jeho typ konfigurace rozšíření, je možné jako součást koncového bodu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8156b-110">After the element and its configuration type are defined, the extension can be used as part of an endpoint as shown in the following example.</span></span>  
  
```xml  
<services>
  <service name="MyService">
    <endpoint address="myAddress"
              binding="MyBinding" />
  </service>
</services>
```  
  
## <a name="see-also"></a><span data-ttu-id="8156b-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8156b-111">See also</span></span>
- [<span data-ttu-id="8156b-112">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="8156b-112">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
