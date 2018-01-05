---
title: '@ServiceHost'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 027debb311a3f9547623b6dff778e82b7e475327
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="servicehost"></a>@ServiceHost
<span data-ttu-id="8a466-101">Přidruží objekt pro vytváření použitý k vytvoření hostitele služby se službou pro hostování a ostatní programovací aspekty vyžaduje přístup k nebo zkompilovat kód hostování zadaný v souboru .svc.</span><span class="sxs-lookup"><span data-stu-id="8a466-101">Associates the factory used to produce the service host with the service to be hosted and other programming aspects required to access or compile the hosting code provided in the .svc file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a466-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a466-102">Syntax</span></span>  
  
```  
<% @ServiceHost   
Service = "Service, ServiceNamespace"   
Factory = "Factory, FactoryNamespace"  
Debug = "Debug"  
Language = "Language"   
CodeBehind = "CodeBehind"%>  
```  
  
## <a name="attributes"></a><span data-ttu-id="8a466-103">Atributy</span><span class="sxs-lookup"><span data-stu-id="8a466-103">Attributes</span></span>  
  
#### <a name="service"></a><span data-ttu-id="8a466-104">Služba</span><span class="sxs-lookup"><span data-stu-id="8a466-104">Service</span></span>  
 <span data-ttu-id="8a466-105">Název typu CLR hostované služby.</span><span class="sxs-lookup"><span data-stu-id="8a466-105">The CLR type name of the service hosted.</span></span> <span data-ttu-id="8a466-106">To by měl být kvalifikovaný název typu, který implementuje jeden nebo více kontaktů služby.</span><span class="sxs-lookup"><span data-stu-id="8a466-106">This should be a qualified name of a type that implements one or more of the service contacts.</span></span>  
  
#### <a name="factory"></a><span data-ttu-id="8a466-107">objekt pro vytváření</span><span class="sxs-lookup"><span data-stu-id="8a466-107">Factory</span></span>  
 <span data-ttu-id="8a466-108">Název typu CLR objektu pro vytváření hostitele služby použít k vytvoření instance hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="8a466-108">The CLR type name of the service host factory used to instantiate the service host.</span></span> <span data-ttu-id="8a466-109">Tento atribut je volitelné.</span><span class="sxs-lookup"><span data-stu-id="8a466-109">This attribute is optional.</span></span> <span data-ttu-id="8a466-110">Pokud tento parametr nezadáte, výchozí <xref:System.ServiceModel.Activation.ServiceHostFactory> se používá, které vrací instanci třídy <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="8a466-110">If unspecified, the default <xref:System.ServiceModel.Activation.ServiceHostFactory> is used, which returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
#### <a name="debug"></a><span data-ttu-id="8a466-111">Ladit</span><span class="sxs-lookup"><span data-stu-id="8a466-111">Debug</span></span>  
 <span data-ttu-id="8a466-112">Určuje, zda [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] služby má kompilovat s ladicími symboly.</span><span class="sxs-lookup"><span data-stu-id="8a466-112">Indicates whether the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service should be compiled with debug symbols.</span></span> <span data-ttu-id="8a466-113">`true`Pokud [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služby by měl být kompilované s ladicími symboly, jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="8a466-113">`true` if the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service should be compiled with debug symbols; otherwise, `false`.</span></span>  
  
#### <a name="language"></a><span data-ttu-id="8a466-114">Jazyk</span><span class="sxs-lookup"><span data-stu-id="8a466-114">Language</span></span>  
 <span data-ttu-id="8a466-115">Určuje jazyk použitý ke zkompilování všech vloženého kódu v rámci tohoto souboru (.svc).</span><span class="sxs-lookup"><span data-stu-id="8a466-115">Specifies the language used when compiling all the inline code within file (.svc).</span></span> <span data-ttu-id="8a466-116">Hodnoty může představovat žádné. NET podporován jazyk, včetně C#, VB a Node.js na C#, Visual Basic .NET a JScript .NET.</span><span class="sxs-lookup"><span data-stu-id="8a466-116">The values can represent any .NET-supported language, including C#, VB, and JS, which refer to C#, Visual Basic .NET, and JScript .NET, respectively.</span></span> <span data-ttu-id="8a466-117">Tento atribut je volitelné.</span><span class="sxs-lookup"><span data-stu-id="8a466-117">This attribute is optional.</span></span>  
  
#### <a name="codebehind"></a><span data-ttu-id="8a466-118">CodeBehind</span><span class="sxs-lookup"><span data-stu-id="8a466-118">CodeBehind</span></span>  
 <span data-ttu-id="8a466-119">Určuje zdrojový soubor, který implementuje webové služby XML, jakmile třídu, která implementuje webové služby XML nenachází ve stejném souboru nebyl byl zkompilován do sestavení a umístěn v adresáři \Bin.</span><span class="sxs-lookup"><span data-stu-id="8a466-119">Specifies the source file that implements the XML Web service, when the class that implements the XML Web service does not reside in the same file and has not been compiled into an assembly and placed in the \Bin directory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a466-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8a466-120">Remarks</span></span>  
 <span data-ttu-id="8a466-121"><xref:System.ServiceModel.ServiceHost> Použít k hostování služby je bod rozšiřitelnost v rámci [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] programovací model.</span><span class="sxs-lookup"><span data-stu-id="8a466-121">The <xref:System.ServiceModel.ServiceHost> used to host the service is a point of extensibility within the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] programming model.</span></span> <span data-ttu-id="8a466-122">Vzor factory slouží k vytváření instancí <xref:System.ServiceModel.ServiceHost> protože se jedná, případně polymorfní typ, který by neměl hostitelské prostředí doložit přímo.</span><span class="sxs-lookup"><span data-stu-id="8a466-122">A factory pattern is used to instantiate the <xref:System.ServiceModel.ServiceHost> because it is, potentially, a polymorphic type that the hosting environment should not instantiate directly.</span></span>  
  
 <span data-ttu-id="8a466-123">Výchozí implementace používá <xref:System.ServiceModel.Activation.ServiceHostFactory> k vytvoření instance <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="8a466-123">The default implementation uses <xref:System.ServiceModel.Activation.ServiceHostFactory> to create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="8a466-124">Ale můžete zadat vlastní objekt pro vytváření (ten, který vrátí odvozené hostiteli) tak, že zadáte název vaší implementace objektu factory v typu CLR [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) – direktiva.</span><span class="sxs-lookup"><span data-stu-id="8a466-124">But you can provide your own factory (one that returns your derived host) by specifying the CLR type name of your factory implementation in the [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive.</span></span>  
  
 <span data-ttu-id="8a466-125">Pokud chcete používat vlastní služby vlastní objekt pro vytváření hostitele místo výchozí objekt pro vytváření, stačí zadat název typu ve [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) – direktiva následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="8a466-125">To use you own custom service host factory instead of the default factory, just provide the type name in the [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive as follows:</span></span>  
  
```xml  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 <span data-ttu-id="8a466-126">Zachovat co nejlehčí factory implementace.</span><span class="sxs-lookup"><span data-stu-id="8a466-126">Keep the factory implementations as light as possible.</span></span> <span data-ttu-id="8a466-127">Pokud máte velké množství vlastní logiky, je váš kód více opakovaně použitelný, když vložíte tuto logiku v hostiteli místo uvnitř objektu pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="8a466-127">If you have lots of custom logic, your code is more reusable if you put that logic inside your host instead of inside the factory.</span></span>  
  
 <span data-ttu-id="8a466-128">Například pro povolení koncového bodu technologie AJAX pro `MyService`, zadejte <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> pro hodnotu `Factory` atribut místo výchozího <xref:System.ServiceModel.Activation.ServiceHostFactory>v [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) direktivy jako Následující příklad ukazuje.</span><span class="sxs-lookup"><span data-stu-id="8a466-128">For example, to enable an AJAX-enabled endpoint for `MyService`, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> for the value of the `Factory` attribute, instead of the default <xref:System.ServiceModel.Activation.ServiceHostFactory>, in the [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a466-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="8a466-129">Example</span></span>  
  
```  
<% @ServiceHost   
Service="MyService"  
Language="C#"  
Debug="true"  
Factory="WebScriptServiceHostFactory"  
%>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8a466-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="8a466-130">See Also</span></span>  
 [<span data-ttu-id="8a466-131">Vlastní hostitel služby</span><span class="sxs-lookup"><span data-stu-id="8a466-131">Custom Service Host</span></span>](../../../../../docs/framework/wcf/samples/custom-service-host.md)
