---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: fdd6d83836c4ef31a4d7c8e68cb0cc050ac6bea4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "76787804"
---
# <a name="servicehost"></a><span data-ttu-id="aac09-101">\@Hostiteli</span><span class="sxs-lookup"><span data-stu-id="aac09-101">\@ServiceHost</span></span>

<span data-ttu-id="aac09-102">Přidruží továrnu, která se používá k vytváření hostitele služby pro hostování služby, a dalších aspektů programování potřebných pro přístup k nebo zkompilování hostujícího kódu, který je k dispozici v souboru. svc.</span><span class="sxs-lookup"><span data-stu-id="aac09-102">Associates the factory used to produce the service host with the service to be hosted and other programming aspects required to access or compile the hosting code provided in the .svc file.</span></span>

## <a name="syntax"></a><span data-ttu-id="aac09-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aac09-103">Syntax</span></span>

```xml
<% @ServiceHost
Service = "Service, ServiceNamespace"
Factory = "Factory, FactoryNamespace"
Debug = "Debug"
Language = "Language"
CodeBehind = "CodeBehind"
%>
```

## <a name="attributes"></a><span data-ttu-id="aac09-104">Atributy</span><span class="sxs-lookup"><span data-stu-id="aac09-104">Attributes</span></span>

### <a name="service"></a><span data-ttu-id="aac09-105">Služba</span><span class="sxs-lookup"><span data-stu-id="aac09-105">Service</span></span>

<span data-ttu-id="aac09-106">Název typu CLR hostované služby.</span><span class="sxs-lookup"><span data-stu-id="aac09-106">The CLR type name of the service hosted.</span></span> <span data-ttu-id="aac09-107">Mělo by se jednat o kvalifikovaný název typu, který implementuje jeden nebo více kontaktů služby.</span><span class="sxs-lookup"><span data-stu-id="aac09-107">This should be a qualified name of a type that implements one or more of the service contacts.</span></span>

### <a name="factory"></a><span data-ttu-id="aac09-108">Objekt pro vytváření</span><span class="sxs-lookup"><span data-stu-id="aac09-108">Factory</span></span>

<span data-ttu-id="aac09-109">Název typu CLR objektu pro vytváření hostitele služby, který se používá k vytvoření instance hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="aac09-109">The CLR type name of the service host factory used to instantiate the service host.</span></span> <span data-ttu-id="aac09-110">Tento atribut je nepovinný.</span><span class="sxs-lookup"><span data-stu-id="aac09-110">This attribute is optional.</span></span> <span data-ttu-id="aac09-111">Je-li tento parametr zadán, <xref:System.ServiceModel.Activation.ServiceHostFactory> je použita výchozí hodnota, která vrací instanci <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="aac09-111">If unspecified, the default <xref:System.ServiceModel.Activation.ServiceHostFactory> is used, which returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>

### <a name="debug"></a><span data-ttu-id="aac09-112">Ladění</span><span class="sxs-lookup"><span data-stu-id="aac09-112">Debug</span></span>

<span data-ttu-id="aac09-113">Určuje, zda má být služba Windows Communication Foundation (WCF) zkompilována se symboly ladění.</span><span class="sxs-lookup"><span data-stu-id="aac09-113">Indicates whether the Windows Communication Foundation (WCF) service should be compiled with debug symbols.</span></span> <span data-ttu-id="aac09-114">`true`Pokud má být služba WCF zkompilována se symboly ladění; v opačném případě `false` .</span><span class="sxs-lookup"><span data-stu-id="aac09-114">`true` if the WCF service should be compiled with debug symbols; otherwise, `false`.</span></span>

### <a name="language"></a><span data-ttu-id="aac09-115">Jazyk</span><span class="sxs-lookup"><span data-stu-id="aac09-115">Language</span></span>

<span data-ttu-id="aac09-116">Určuje jazyk použitý při kompilaci veškerého vloženého kódu v rámci souboru (. svc).</span><span class="sxs-lookup"><span data-stu-id="aac09-116">Specifies the language used when compiling all the inline code within file (.svc).</span></span> <span data-ttu-id="aac09-117">Hodnoty mohou představovat libovolný. NET – podporovaný jazyk, včetně `C#` , `VB` a `JS` , který odkazuje na C#, Visual Basic a JScript .NET, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="aac09-117">The values can represent any .NET-supported language, including `C#`, `VB`, and `JS`, which refer to C#, Visual Basic, and JScript .NET, respectively.</span></span> <span data-ttu-id="aac09-118">Tento atribut je nepovinný.</span><span class="sxs-lookup"><span data-stu-id="aac09-118">This attribute is optional.</span></span>

### <a name="codebehind"></a><span data-ttu-id="aac09-119">CodeBehind</span><span class="sxs-lookup"><span data-stu-id="aac09-119">CodeBehind</span></span>

<span data-ttu-id="aac09-120">Určuje zdrojový soubor, který implementuje webovou službu XML, pokud třída, která implementuje webovou službu XML, není umístěna ve stejném souboru a nebyla zkompilována do sestavení a umístěna do adresáře *\Bin* .</span><span class="sxs-lookup"><span data-stu-id="aac09-120">Specifies the source file that implements the XML Web service, when the class that implements the XML Web service does not reside in the same file and has not been compiled into an assembly and placed in the *\Bin* directory.</span></span>

## <a name="remarks"></a><span data-ttu-id="aac09-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aac09-121">Remarks</span></span>

<span data-ttu-id="aac09-122"><xref:System.ServiceModel.ServiceHost>Použití pro hostování služby je bod rozšíření v rámci programovacího modelu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="aac09-122">The <xref:System.ServiceModel.ServiceHost> used to host the service is a point of extensibility within the Windows Communication Foundation (WCF) programming model.</span></span> <span data-ttu-id="aac09-123">Model továrny se používá k vytvoření instance <xref:System.ServiceModel.ServiceHost> , protože je, potenciálně polymorfního typu, který by hostitelský prostředí nemělo vytvářet přímo.</span><span class="sxs-lookup"><span data-stu-id="aac09-123">A factory pattern is used to instantiate the <xref:System.ServiceModel.ServiceHost> because it is, potentially, a polymorphic type that the hosting environment should not instantiate directly.</span></span>

<span data-ttu-id="aac09-124">Výchozí implementace používá <xref:System.ServiceModel.Activation.ServiceHostFactory> k vytvoření instance <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="aac09-124">The default implementation uses <xref:System.ServiceModel.Activation.ServiceHostFactory> to create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="aac09-125">Můžete ale zadat vlastní továrnu (jednu, která vrací vašeho odvozeného hostitele) zadáním názvu typu CLR implementace výroby v `@ServiceHost` direktivě.</span><span class="sxs-lookup"><span data-stu-id="aac09-125">But you can provide your own factory (one that returns your derived host) by specifying the CLR type name of your factory implementation in the `@ServiceHost` directive.</span></span>

<span data-ttu-id="aac09-126">Pokud chcete použít vlastní objekt pro vytváření hostitele služby místo výchozí továrny, stačí zadat název typu v `@ServiceHost` direktivě následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="aac09-126">To use you own custom service host factory instead of the default factory, just provide the type name in the `@ServiceHost` directive as follows.</span></span>

```xml
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>
```

<span data-ttu-id="aac09-127">Udržujte implementace továrny co nejblíže.</span><span class="sxs-lookup"><span data-stu-id="aac09-127">Keep the factory implementations as light as possible.</span></span> <span data-ttu-id="aac09-128">Pokud máte spoustu vlastní logiky, váš kód je více použitelný, pokud tuto logiku vložíte do svého hostitele místo do objektu factory.</span><span class="sxs-lookup"><span data-stu-id="aac09-128">If you have lots of custom logic, your code is more reusable if you put that logic inside your host instead of inside the factory.</span></span>

<span data-ttu-id="aac09-129">Chcete-li například povolit koncový bod s povoleným AJAX pro `MyService` , zadejte <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> pro hodnotu `Factory` atributu místo výchozí <xref:System.ServiceModel.Activation.ServiceHostFactory> v `@ServiceHost` direktivě, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="aac09-129">For example, to enable an AJAX-enabled endpoint for `MyService`, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> for the value of the `Factory` attribute, instead of the default <xref:System.ServiceModel.Activation.ServiceHostFactory>, in the `@ServiceHost` directive as shown in the following example:</span></span>

```xml
<% @ServiceHost
Service="MyService"
Language="C#"
Debug="true"
Factory="WebScriptServiceHostFactory"
%>
```

## <a name="see-also"></a><span data-ttu-id="aac09-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="aac09-130">See also</span></span>

- [<span data-ttu-id="aac09-131">Vlastní hostitel služby</span><span class="sxs-lookup"><span data-stu-id="aac09-131">Custom Service Host</span></span>](../../../wcf/samples/custom-service-host.md)
