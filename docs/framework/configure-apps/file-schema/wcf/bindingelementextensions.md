---
title: '&lt;bindingElementExtensions&gt;'
ms.date: 03/30/2017
ms.assetid: bb597fc0-c947-451c-afda-bf23d42f4f4d
ms.openlocfilehash: a93474a4f86fac2a6b211652e3ddc86901cf197f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747746"
---
# <a name="ltbindingelementextensionsgt"></a><span data-ttu-id="2dab7-102">&lt;bindingElementExtensions&gt;</span><span class="sxs-lookup"><span data-stu-id="2dab7-102">&lt;bindingElementExtensions&gt;</span></span>
<span data-ttu-id="2dab7-103">Tato část umožňuje použití vlastní vazby element z počítače nebo konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="2dab7-103">This section enables the use of a custom binding element from a machine or application configuration file.</span></span> <span data-ttu-id="2dab7-104">Element vlastní vazby můžete přidat do této kolekce pomocí `add` – klíčové slovo a nastavení `type` atribut elementu vazby element rozšíření, a taky `name` atribut prvku vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="2dab7-104">You can add a custom binding element to this collection by using the `add` keyword, and setting the `type` attribute of the element to a binding element extension, as well as the `name` attribute to the custom binding element.</span></span>  
  
 <span data-ttu-id="2dab7-105">Vazba rozšíření zajistit, aby uživatel k vytváření prvků uživatelem definované vazby pro použití v rámci vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="2dab7-105">Binding extensions enable the user to create user-defined binding elements for use as part of custom bindings.</span></span> <span data-ttu-id="2dab7-106">Prostřednictvím kódu programu, rozšíření vazby je typ, který implementuje abstraktní třídu <xref:System.ServiceModel.Channels.BindingElement>.</span><span class="sxs-lookup"><span data-stu-id="2dab7-106">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.BindingElement>.</span></span> <span data-ttu-id="2dab7-107">V konfiguračním souboru `bindingElementExtensions` části se používá k definování element rozšíření.</span><span class="sxs-lookup"><span data-stu-id="2dab7-107">In the configuration file, the `bindingElementExtensions` section is used to define an extension element.</span></span>  
  
 <span data-ttu-id="2dab7-108">Následující příklad používá `add` elementu, společně s `name` přidat příponu vazby do atribut `bindingElementExtensions` oddílu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="2dab7-108">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingElementExtensions` section of the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="2dab7-109">Přidat konfiguraci dalo k elementu, uživatel musí k zápisu a zaregistrovat `bindingElementExtensionSection` elementu.</span><span class="sxs-lookup"><span data-stu-id="2dab7-109">To add configuration abilities to the element, the user needs to write and register a `bindingElementExtensionSection` element.</span></span> <span data-ttu-id="2dab7-110">Další informace najdete v tématu <xref:System.Configuration> dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="2dab7-110">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="2dab7-111">Po elementu a jeho typ konfigurace jsou definovány, rozšíření lze použít jako součást vlastní vazby, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2dab7-111">After the element and its configuration type are defined, the extension can be used as part of a custom binding as shown in the following example.</span></span>  
  
```xml  
<customBinding>  
     <binding name="test2">  
         <udpTransport />  
         <binaryMessageEncoding maxReadPoolSize="211" maxWritePoolSize="2132"  
             maxSessionSize="3141" />  
         </binding>  
</customBinding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2dab7-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="2dab7-112">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>  
 [<span data-ttu-id="2dab7-113">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="2dab7-113">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
