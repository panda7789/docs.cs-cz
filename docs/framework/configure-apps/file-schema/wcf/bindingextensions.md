---
title: '&lt;bindingExtensions&gt;'
ms.date: 03/30/2017
ms.assetid: 8373f94d-d095-486f-8f1e-4ac2f72b58c7
ms.openlocfilehash: f99b38ede66dbecb44f9e8e67f921943071672ca
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltbindingextensionsgt"></a><span data-ttu-id="ff7a9-102">&lt;bindingExtensions&gt;</span><span class="sxs-lookup"><span data-stu-id="ff7a9-102">&lt;bindingExtensions&gt;</span></span>
<span data-ttu-id="ff7a9-103">Tato část umožňuje použití definované uživatelem vazby z počítače nebo konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="ff7a9-103">This section enables the use of a user defined binding from a machine or application configuration file.</span></span> <span data-ttu-id="ff7a9-104">Můžete přidat definované uživatelem vazby k této kolekci pomocí `add` – klíčové slovo a nastavení `type` atribut elementu uživatelem definované vazby, společně s `name` vazby definován atribut na jméno uživatele.</span><span class="sxs-lookup"><span data-stu-id="ff7a9-104">You can add a user defined binding to this collection by using the `add` keyword, and setting the `type` attribute of the element to a user defined binding, as well as the `name` attribute to the name of the user defined binding.</span></span>  
  
 <span data-ttu-id="ff7a9-105">Vazba rozšíření umožňují uživatelům vytvořit uživatelem definované vazby pro použití v rámci konfigurace koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="ff7a9-105">Binding extensions enable the user to create user-defined bindings for use as part an endpoint configuration.</span></span> <span data-ttu-id="ff7a9-106">Prostřednictvím kódu programu, rozšíření vazby je typ, který implementuje abstraktní třídu <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="ff7a9-106">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.Binding>.</span></span>  
  
 <span data-ttu-id="ff7a9-107">Následující příklad používá `add` elementu, společně s `name` přidat příponu vazby do atribut `bindingElementExtensions` oddílu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="ff7a9-107">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingElementExtensions` section of the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="ff7a9-108">Přidat konfiguraci dalo k elementu, uživatel musí k zápisu a zaregistrovat `bindingSection` elementu.</span><span class="sxs-lookup"><span data-stu-id="ff7a9-108">To add configuration abilities to the element, the user needs to write and register a `bindingSection` element.</span></span> <span data-ttu-id="ff7a9-109">Další informace najdete v tématu <xref:System.Configuration> dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="ff7a9-109">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="ff7a9-110">Po elementu a jeho typ konfigurace jsou definovány, rozšíření lze použít jako součást koncový bod, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ff7a9-110">After the element and its configuration type are defined, the extension can be used as part of an endpoint as shown in the following example.</span></span>  
  
```xml  
<services>  
    <service name="MyService">  
        <endpoint address="myAddress" binding="MyBinding" />  
    </service>  
</services>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ff7a9-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff7a9-111">See Also</span></span>  
 [<span data-ttu-id="ff7a9-112">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="ff7a9-112">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
