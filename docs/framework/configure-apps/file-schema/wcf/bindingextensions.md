---
title: <bindingExtensions>
ms.date: 03/30/2017
ms.assetid: 8373f94d-d095-486f-8f1e-4ac2f72b58c7
ms.openlocfilehash: 34ba198de33ae4aa1882d13f74bd2d538999a0c9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919780"
---
# <a name="bindingextensions"></a><span data-ttu-id="b0b31-101">\<bindingExtensions ></span><span class="sxs-lookup"><span data-stu-id="b0b31-101">\<bindingExtensions></span></span>
<span data-ttu-id="b0b31-102">Tato část umožňuje použití uživatelsky definované vazby z počítače nebo konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="b0b31-102">This section enables the use of a user defined binding from a machine or application configuration file.</span></span> <span data-ttu-id="b0b31-103">Uživatelem definovanou vazbu k této kolekci můžete přidat pomocí `add` klíčového slova a `type` nastavením atributu elementu na uživatelem definovanou vazbu a také `name` atributem na název uživatelsky definované vazby.</span><span class="sxs-lookup"><span data-stu-id="b0b31-103">You can add a user defined binding to this collection by using the `add` keyword, and setting the `type` attribute of the element to a user defined binding, as well as the `name` attribute to the name of the user defined binding.</span></span>  
  
 <span data-ttu-id="b0b31-104">Rozšíření vazby umožňují uživateli vytvořit uživatelsky definované vazby, které se použijí jako součást konfigurace koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="b0b31-104">Binding extensions enable the user to create user-defined bindings for use as part an endpoint configuration.</span></span> <span data-ttu-id="b0b31-105">Programově je rozšíření vazby typu, který implementuje abstraktní třídu <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="b0b31-105">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.Binding>.</span></span>  
  
 <span data-ttu-id="b0b31-106">V následujícím příkladu se používá `add` element a také `name` atribut pro přidání rozšíření vazby do `bindingElementExtensions` oddílu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="b0b31-106">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingElementExtensions` section of the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="b0b31-107">Chcete-li do prvku přidat možnosti konfigurace, musí uživatel zapsat a zaregistrovat `bindingSection` element.</span><span class="sxs-lookup"><span data-stu-id="b0b31-107">To add configuration abilities to the element, the user needs to write and register a `bindingSection` element.</span></span> <span data-ttu-id="b0b31-108">Další informace najdete <xref:System.Configuration> v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="b0b31-108">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="b0b31-109">Po definování prvku a jeho typu konfigurace lze rozšíření použít jako součást koncového bodu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b0b31-109">After the element and its configuration type are defined, the extension can be used as part of an endpoint as shown in the following example.</span></span>  
  
```xml  
<services>
  <service name="MyService">
    <endpoint address="myAddress"
              binding="MyBinding" />
  </service>
</services>
```  
  
## <a name="see-also"></a><span data-ttu-id="b0b31-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b0b31-110">See also</span></span>

- [<span data-ttu-id="b0b31-111">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="b0b31-111">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
