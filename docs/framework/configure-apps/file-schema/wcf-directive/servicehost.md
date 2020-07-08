---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: cb425d9f4dadd97e93946a2b4cd9d059ea8504ce
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051360"
---
# <a name="servicehost"></a><span data-ttu-id="d94e2-101">\@Hostiteli</span><span class="sxs-lookup"><span data-stu-id="d94e2-101">\@ServiceHost</span></span>

<span data-ttu-id="d94e2-102">Přidruží továrnu, která se používá k vytváření hostitele služby pro hostování služby, a dalších aspektů programování potřebných pro přístup k nebo zkompilování hostujícího kódu, který je k dispozici v souboru. svc.</span><span class="sxs-lookup"><span data-stu-id="d94e2-102">Associates the factory used to produce the service host with the service to be hosted and other programming aspects required to access or compile the hosting code provided in the .svc file.</span></span>

## <a name="syntax"></a><span data-ttu-id="d94e2-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="d94e2-103">Syntax</span></span>

```aspx-csharp
<% @ServiceHost
Service = "Service, ServiceNamespace"
Factory = "Factory, FactoryNamespace"
Debug = "Debug"
Language = "Language"
CodeBehind = "CodeBehind"
%>
```

## <a name="attributes"></a><span data-ttu-id="d94e2-104">Atributy</span><span class="sxs-lookup"><span data-stu-id="d94e2-104">Attributes</span></span>

### <a name="service"></a><span data-ttu-id="d94e2-105">Služba</span><span class="sxs-lookup"><span data-stu-id="d94e2-105">Service</span></span>

<span data-ttu-id="d94e2-106">Název typu CLR hostované služby.</span><span class="sxs-lookup"><span data-stu-id="d94e2-106">The CLR type name of the service hosted.</span></span> <span data-ttu-id="d94e2-107">Mělo by se jednat o kvalifikovaný název typu, který implementuje jeden nebo více kontaktů služby.</span><span class="sxs-lookup"><span data-stu-id="d94e2-107">This should be a qualified name of a type that implements one or more of the service contacts.</span></span>

### <a name="factory"></a><span data-ttu-id="d94e2-108">Objekt pro vytváření</span><span class="sxs-lookup"><span data-stu-id="d94e2-108">Factory</span></span>

<span data-ttu-id="d94e2-109">Název typu CLR objektu pro vytváření hostitele služby, který se používá k vytvoření instance hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="d94e2-109">The CLR type name of the service host factory used to instantiate the service host.</span></span> <span data-ttu-id="d94e2-110">Tento atribut je nepovinný.</span><span class="sxs-lookup"><span data-stu-id="d94e2-110">This attribute is optional.</span></span> <span data-ttu-id="d94e2-111">Je-li tento parametr zadán, <xref:System.ServiceModel.Activation.ServiceHostFactory> je použita výchozí hodnota, která vrací instanci <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="d94e2-111">If unspecified, the default <xref:System.ServiceModel.Activation.ServiceHostFactory> is used, which returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>

### <a name="debug"></a><span data-ttu-id="d94e2-112">Ladit</span><span class="sxs-lookup"><span data-stu-id="d94e2-112">Debug</span></span>

<span data-ttu-id="d94e2-113">Určuje, zda má být služba Windows Communication Foundation (WCF) zkompilována se symboly ladění.</span><span class="sxs-lookup"><span data-stu-id="d94e2-113">Indicates whether the Windows Communication Foundation (WCF) service should be compiled with debug symbols.</span></span> <span data-ttu-id="d94e2-114">`true`Pokud má být služba WCF zkompilována se symboly ladění; v opačném případě `false` .</span><span class="sxs-lookup"><span data-stu-id="d94e2-114">`true` if the WCF service should be compiled with debug symbols; otherwise, `false`.</span></span>

### <a name="language"></a><span data-ttu-id="d94e2-115">Jazyk</span><span class="sxs-lookup"><span data-stu-id="d94e2-115">Language</span></span>

<span data-ttu-id="d94e2-116">Určuje jazyk použitý při kompilaci veškerého vloženého kódu v rámci souboru (. svc).</span><span class="sxs-lookup"><span data-stu-id="d94e2-116">Specifies the language used when compiling all the inline code within file (.svc).</span></span> <span data-ttu-id="d94e2-117">Hodnoty mohou představovat libovolný. NET – podporovaný jazyk, včetně `C#` , `VB` a `JS` , který odkazuje na C#, Visual Basic a JScript .NET, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="d94e2-117">The values can represent any .NET-supported language, including `C#`, `VB`, and `JS`, which refer to C#, Visual Basic, and JScript .NET, respectively.</span></span> <span data-ttu-id="d94e2-118">Tento atribut je nepovinný.</span><span class="sxs-lookup"><span data-stu-id="d94e2-118">This attribute is optional.</span></span>

### <a name="codebehind"></a><span data-ttu-id="d94e2-119">CodeBehind</span><span class="sxs-lookup"><span data-stu-id="d94e2-119">CodeBehind</span></span>

<span data-ttu-id="d94e2-120">Určuje zdrojový soubor, který implementuje webovou službu XML, pokud třída, která implementuje webovou službu XML, není umístěna ve stejném souboru a nebyla zkompilována do sestavení a umístěna do adresáře *\Bin* .</span><span class="sxs-lookup"><span data-stu-id="d94e2-120">Specifies the source file that implements the XML Web service, when the class that implements the XML Web service does not reside in the same file and has not been compiled into an assembly and placed in the *\Bin* directory.</span></span>

## <a name="remarks"></a><span data-ttu-id="d94e2-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d94e2-121">Remarks</span></span>

<span data-ttu-id="d94e2-122"><xref:System.ServiceModel.ServiceHost>Použití pro hostování služby je bod rozšíření v rámci programovacího modelu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d94e2-122">The <xref:System.ServiceModel.ServiceHost> used to host the service is a point of extensibility within the Windows Communication Foundation (WCF) programming model.</span></span> <span data-ttu-id="d94e2-123">Model továrny se používá k vytvoření instance <xref:System.ServiceModel.ServiceHost> , protože je, potenciálně polymorfního typu, který by hostitelský prostředí nemělo vytvářet přímo.</span><span class="sxs-lookup"><span data-stu-id="d94e2-123">A factory pattern is used to instantiate the <xref:System.ServiceModel.ServiceHost> because it is, potentially, a polymorphic type that the hosting environment should not instantiate directly.</span></span>

<span data-ttu-id="d94e2-124">Výchozí implementace používá <xref:System.ServiceModel.Activation.ServiceHostFactory> k vytvoření instance <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="d94e2-124">The default implementation uses <xref:System.ServiceModel.Activation.ServiceHostFactory> to create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="d94e2-125">Můžete ale zadat vlastní továrnu (jednu, která vrací vašeho odvozeného hostitele) zadáním názvu typu CLR implementace výroby v `@ServiceHost` direktivě.</span><span class="sxs-lookup"><span data-stu-id="d94e2-125">But you can provide your own factory (one that returns your derived host) by specifying the CLR type name of your factory implementation in the `@ServiceHost` directive.</span></span>

<span data-ttu-id="d94e2-126">Pokud chcete použít vlastní objekt pro vytváření hostitele služby místo výchozí továrny, stačí zadat název typu v `@ServiceHost` direktivě následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="d94e2-126">To use you own custom service host factory instead of the default factory, just provide the type name in the `@ServiceHost` directive as follows.</span></span>

```xml
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>
```

<span data-ttu-id="d94e2-127">Udržujte implementace továrny co nejblíže.</span><span class="sxs-lookup"><span data-stu-id="d94e2-127">Keep the factory implementations as light as possible.</span></span> <span data-ttu-id="d94e2-128">Pokud máte spoustu vlastní logiky, váš kód je více použitelný, pokud tuto logiku vložíte do svého hostitele místo do objektu factory.</span><span class="sxs-lookup"><span data-stu-id="d94e2-128">If you have lots of custom logic, your code is more reusable if you put that logic inside your host instead of inside the factory.</span></span>

<span data-ttu-id="d94e2-129">Chcete-li například povolit koncový bod s povoleným AJAX pro `MyService` , zadejte <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> pro hodnotu `Factory` atributu místo výchozí <xref:System.ServiceModel.Activation.ServiceHostFactory> v `@ServiceHost` direktivě, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="d94e2-129">For example, to enable an AJAX-enabled endpoint for `MyService`, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> for the value of the `Factory` attribute, instead of the default <xref:System.ServiceModel.Activation.ServiceHostFactory>, in the `@ServiceHost` directive as shown in the following example:</span></span>

```aspx-csharp
<% @ServiceHost
Service="MyService"
Language="C#"
Debug="true"
Factory="WebScriptServiceHostFactory"
%>
```

## <a name="see-also"></a><span data-ttu-id="d94e2-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="d94e2-130">See also</span></span>

- [<span data-ttu-id="d94e2-131">Vlastní hostitel služby</span><span class="sxs-lookup"><span data-stu-id="d94e2-131">Custom Service Host</span></span>](../../../wcf/samples/custom-service-host.md)
