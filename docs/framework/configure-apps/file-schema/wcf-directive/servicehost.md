---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: 730b1188a95d0e35d7431d43884e867e5520585e
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2018
ms.locfileid: "44365073"
---
# <a name="servicehost"></a><span data-ttu-id="a2ae8-101">\@Hostitel služby</span><span class="sxs-lookup"><span data-stu-id="a2ae8-101">\@ServiceHost</span></span>
<span data-ttu-id="a2ae8-102">Přidruží objekt pro vytváření použitý k vytvoření hostitele služby pomocí ní zajistit také jejich hostování a ostatní programovací aspekty vyžaduje přístup k nebo zkompilovat kód hostování zadaný v souboru SVC.</span><span class="sxs-lookup"><span data-stu-id="a2ae8-102">Associates the factory used to produce the service host with the service to be hosted and other programming aspects required to access or compile the hosting code provided in the .svc file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2ae8-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2ae8-103">Syntax</span></span>  
  
```  
<% @ServiceHost   
Service = "Service, ServiceNamespace"   
Factory = "Factory, FactoryNamespace"  
Debug = "Debug"  
Language = "Language"   
CodeBehind = "CodeBehind"%>  
```  
  
## <a name="attributes"></a><span data-ttu-id="a2ae8-104">Atributy</span><span class="sxs-lookup"><span data-stu-id="a2ae8-104">Attributes</span></span>  
  
#### <a name="service"></a><span data-ttu-id="a2ae8-105">Služba</span><span class="sxs-lookup"><span data-stu-id="a2ae8-105">Service</span></span>  
 <span data-ttu-id="a2ae8-106">Název typu CLR hostované služby.</span><span class="sxs-lookup"><span data-stu-id="a2ae8-106">The CLR type name of the service hosted.</span></span> <span data-ttu-id="a2ae8-107">To by měl být úplný název typu, který implementuje jednu nebo více kontakty ke službě.</span><span class="sxs-lookup"><span data-stu-id="a2ae8-107">This should be a qualified name of a type that implements one or more of the service contacts.</span></span>  
  
#### <a name="factory"></a><span data-ttu-id="a2ae8-108">objekt pro vytváření</span><span class="sxs-lookup"><span data-stu-id="a2ae8-108">Factory</span></span>  
 <span data-ttu-id="a2ae8-109">Název typu CLR objektu pro vytváření hostitele služby použít k vytvoření instance hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="a2ae8-109">The CLR type name of the service host factory used to instantiate the service host.</span></span> <span data-ttu-id="a2ae8-110">Tento atribut je volitelný.</span><span class="sxs-lookup"><span data-stu-id="a2ae8-110">This attribute is optional.</span></span> <span data-ttu-id="a2ae8-111">Pokud tento parametr zadán, výchozí <xref:System.ServiceModel.Activation.ServiceHostFactory> se používá, která vrací instanci <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="a2ae8-111">If unspecified, the default <xref:System.ServiceModel.Activation.ServiceHostFactory> is used, which returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
#### <a name="debug"></a><span data-ttu-id="a2ae8-112">Ladit</span><span class="sxs-lookup"><span data-stu-id="a2ae8-112">Debug</span></span>  
 <span data-ttu-id="a2ae8-113">Určuje, zda služby Windows Communication Foundation (WCF) by měl být kompilována se symboly ladění.</span><span class="sxs-lookup"><span data-stu-id="a2ae8-113">Indicates whether the Windows Communication Foundation (WCF) service should be compiled with debug symbols.</span></span> <span data-ttu-id="a2ae8-114">`true` Pokud se služba WCF by měl být kompilována se symboly ladění; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="a2ae8-114">`true` if the WCF service should be compiled with debug symbols; otherwise, `false`.</span></span>  
  
#### <a name="language"></a><span data-ttu-id="a2ae8-115">Jazyk</span><span class="sxs-lookup"><span data-stu-id="a2ae8-115">Language</span></span>  
 <span data-ttu-id="a2ae8-116">Určuje jazyk použitý při kompilaci všech vložených kódu v souboru (.svc).</span><span class="sxs-lookup"><span data-stu-id="a2ae8-116">Specifies the language used when compiling all the inline code within file (.svc).</span></span> <span data-ttu-id="a2ae8-117">Hodnoty mohou představovat všechny. NET – podporované jazyky, včetně C#, VB a JS, které se odkazují na C#, Visual Basic .NET a JScript .NET, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="a2ae8-117">The values can represent any .NET-supported language, including C#, VB, and JS, which refer to C#, Visual Basic .NET, and JScript .NET, respectively.</span></span> <span data-ttu-id="a2ae8-118">Tento atribut je volitelný.</span><span class="sxs-lookup"><span data-stu-id="a2ae8-118">This attribute is optional.</span></span>  
  
#### <a name="codebehind"></a><span data-ttu-id="a2ae8-119">CodeBehind</span><span class="sxs-lookup"><span data-stu-id="a2ae8-119">CodeBehind</span></span>  
 <span data-ttu-id="a2ae8-120">Určuje zdrojový soubor, který implementuje webové služby XML, třídy, která implementuje webové služby XML není umístěný ve stejném souboru a nebyl po kompilovány do sestavení a umístěn v adresáři \Bin.</span><span class="sxs-lookup"><span data-stu-id="a2ae8-120">Specifies the source file that implements the XML Web service, when the class that implements the XML Web service does not reside in the same file and has not been compiled into an assembly and placed in the \Bin directory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2ae8-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a2ae8-121">Remarks</span></span>  
 <span data-ttu-id="a2ae8-122"><xref:System.ServiceModel.ServiceHost> Použít k hostování služby je bodu rozšiřitelnosti v rámci programovací model Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a2ae8-122">The <xref:System.ServiceModel.ServiceHost> used to host the service is a point of extensibility within the Windows Communication Foundation (WCF) programming model.</span></span> <span data-ttu-id="a2ae8-123">Objekt pro vytváření vzorek se používá k vytvoření instance <xref:System.ServiceModel.ServiceHost> protože se jedná, případně polymorfní typ, který by neměl přímo vytvořit instanci hostitelského prostředí.</span><span class="sxs-lookup"><span data-stu-id="a2ae8-123">A factory pattern is used to instantiate the <xref:System.ServiceModel.ServiceHost> because it is, potentially, a polymorphic type that the hosting environment should not instantiate directly.</span></span>  
  
 <span data-ttu-id="a2ae8-124">Výchozí implementace používá <xref:System.ServiceModel.Activation.ServiceHostFactory> k vytvoření instance <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="a2ae8-124">The default implementation uses <xref:System.ServiceModel.Activation.ServiceHostFactory> to create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="a2ae8-125">Ale můžete zadat vlastní objekt pro vytváření (jedna, která vrací odvozené hostitelů) tak, že zadáte název typu CLR továrny implementace v [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) směrnice.</span><span class="sxs-lookup"><span data-stu-id="a2ae8-125">But you can provide your own factory (one that returns your derived host) by specifying the CLR type name of your factory implementation in the [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive.</span></span>  
  
 <span data-ttu-id="a2ae8-126">Pokud chcete použít objekt pro vytváření hostitele služby vlastní vlastní místo výchozí objekt pro vytváření, stačí zadat název typu v [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) směrnice následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="a2ae8-126">To use you own custom service host factory instead of the default factory, just provide the type name in the [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive as follows:</span></span>  
  
```xml  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 <span data-ttu-id="a2ae8-127">Udržujte co nejlehčí factory implementace.</span><span class="sxs-lookup"><span data-stu-id="a2ae8-127">Keep the factory implementations as light as possible.</span></span> <span data-ttu-id="a2ae8-128">Pokud máte velké množství vlastní logiku, váš kód je více opakovaně použitelné, pokud jste tuto logiku umístěte hostitele místo uvnitř objekt pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="a2ae8-128">If you have lots of custom logic, your code is more reusable if you put that logic inside your host instead of inside the factory.</span></span>  
  
 <span data-ttu-id="a2ae8-129">Například pro povolení koncového bodu s povoleným AJAX pro `MyService`, zadejte <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> pro hodnotu vlastnosti `Factory` atribut místo výchozího <xref:System.ServiceModel.Activation.ServiceHostFactory>v [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) direktiv jako je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a2ae8-129">For example, to enable an AJAX-enabled endpoint for `MyService`, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> for the value of the `Factory` attribute, instead of the default <xref:System.ServiceModel.Activation.ServiceHostFactory>, in the [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2ae8-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="a2ae8-130">Example</span></span>  
  
```  
<% @ServiceHost   
Service="MyService"  
Language="C#"  
Debug="true"  
Factory="WebScriptServiceHostFactory"  
%>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a2ae8-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="a2ae8-131">See Also</span></span>  
 [<span data-ttu-id="a2ae8-132">Vlastní hostitel služby</span><span class="sxs-lookup"><span data-stu-id="a2ae8-132">Custom Service Host</span></span>](../../../../../docs/framework/wcf/samples/custom-service-host.md)
