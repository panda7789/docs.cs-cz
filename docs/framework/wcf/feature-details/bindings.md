---
title: Vazby WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF [WCF], bindings
- Windows Communication Foundation [WCF], bindings
- bindings [WCF]
ms.assetid: 83639133-89f7-43f0-b4ef-8d9e57c08d25
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 22b7b8f568b3350972ace128fdc3164c4f3ba179
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="windows-communcation-foundation-bindings"></a><span data-ttu-id="b144a-102">Vazby WCF</span><span class="sxs-lookup"><span data-stu-id="b144a-102">Windows Communcation Foundation Bindings</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="b144a-103">odděluje postup zápisu softwaru pro aplikaci z jak komunikuje s jiným softwarem.</span><span class="sxs-lookup"><span data-stu-id="b144a-103"> separates how the software for an application is written from how it communicates with other software.</span></span> <span data-ttu-id="b144a-104">Vazby slouží k určení přenosu, kódování a podrobnosti protokolu povinné pro klienty a služby pro komunikaci mezi sebou.</span><span class="sxs-lookup"><span data-stu-id="b144a-104">Bindings are used to specify the transport, encoding, and protocol details required for clients and services to communicate with each other.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="b144a-105">vazby se používá ke generování základní síťové vyjádření koncového bodu, takže většina podrobnosti vazba musí schválit strany, které komunikují.</span><span class="sxs-lookup"><span data-stu-id="b144a-105"> uses bindings to generate the underlying wire representation of the endpoint, so most of the binding details must be agreed upon by the parties that are communicating.</span></span> <span data-ttu-id="b144a-106">Nejjednodušší způsob, jak dosáhnout je pro klientům služby používat stejnou vazbu, která koncový bod služby používá.</span><span class="sxs-lookup"><span data-stu-id="b144a-106">The easiest way to achieve this is for clients of a service to use the same binding that the endpoint for the service uses.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="b144a-107">jak to udělat, najdete v části [pomocí vazby na klienty a konfiguraci služby Windows Communication Foundation](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb).</span><span class="sxs-lookup"><span data-stu-id="b144a-107"> how to do this, see [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb).</span></span>  
  
 <span data-ttu-id="b144a-108">Vazba se skládá z kolekce elementů vazby.</span><span class="sxs-lookup"><span data-stu-id="b144a-108">A binding is made up of a collection of binding elements.</span></span> <span data-ttu-id="b144a-109">Každý prvek popisuje určitý aspekt jak koncový bod komunikuje s klienty.</span><span class="sxs-lookup"><span data-stu-id="b144a-109">Each element describes some aspect of how the endpoint communicates with clients.</span></span> <span data-ttu-id="b144a-110">Vazba musí obsahovat alespoň jeden element vazby přenosu, alespoň jeden kódování zpráv prvku vazby (což element vazby přenosu může zajistit ve výchozím nastavení) a libovolný počet dalších protokol prvky vazeb.</span><span class="sxs-lookup"><span data-stu-id="b144a-110">A binding must include at least one transport binding element, at least one message-encoding binding element (which the transport binding element can provide by default), and any number of other protocol binding elements.</span></span> <span data-ttu-id="b144a-111">Proces, který sestaví runtime mimo tento popis umožňuje každého prvku vazby přispívání kód pro tento modul runtime.</span><span class="sxs-lookup"><span data-stu-id="b144a-111">The process that builds a runtime out of this description allows each binding element to contribute code to that runtime.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="b144a-112">poskytuje vazby, které obsahují běžné možnosti elementů vazby.</span><span class="sxs-lookup"><span data-stu-id="b144a-112"> provides bindings that contain common selections of binding elements.</span></span> <span data-ttu-id="b144a-113">Ty mohou být použity ve výchozím nastavení, nebo můžete upravit tyto výchozí hodnoty podle požadavků uživatelů.</span><span class="sxs-lookup"><span data-stu-id="b144a-113">These can be used with their default settings or you can modify those default values according to user requirements.</span></span> <span data-ttu-id="b144a-114">Tyto vazby poskytované systémem mít vlastnosti, které umožňují přímou kontrolu nad prvky vazby a jejich nastavení.</span><span class="sxs-lookup"><span data-stu-id="b144a-114">These system-provided bindings have properties that allow direct control over the binding elements and their settings.</span></span> <span data-ttu-id="b144a-115">Můžete také snadno pracovat souběžného s více verzemi vazby tím, že každou verzi vazby svůj vlastní název.</span><span class="sxs-lookup"><span data-stu-id="b144a-115">You can also easily work side-by-side with multiple versions of a binding by giving each version of the binding its own name.</span></span> <span data-ttu-id="b144a-116">Podrobnosti najdete v tématu [Configuring System-Provided vazby](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="b144a-116">For details, see [Configuring System-Provided Bindings](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md).</span></span>  
  
 <span data-ttu-id="b144a-117">Pokud potřebujete kolekce elementů vazby není poskytovaný jednu z těchto vazeb poskytovaných systémem můžete vytvořit vlastní vazby, která se skládá z kolekce elementů požadované vazby.</span><span class="sxs-lookup"><span data-stu-id="b144a-117">If you need a collection of binding elements not provided by one of these system-provided bindings, you can create a custom binding that consists of the collection of binding elements required.</span></span> <span data-ttu-id="b144a-118">Tyto vlastních vazeb se dají snadno vytvářet a provádět nevyžadují novou třídu, ale není zadejte vlastnosti pro řízení prvky vazby nebo jejich nastavení.</span><span class="sxs-lookup"><span data-stu-id="b144a-118">These custom bindings are easy to create and do not require a new class, but they do not provide properties for controlling the binding elements or their settings.</span></span> <span data-ttu-id="b144a-119">Můžete používat prvky vazby a změnit jejich nastavení prostřednictvím kolekce, která obsahuje je.</span><span class="sxs-lookup"><span data-stu-id="b144a-119">You can access the binding elements and modify their settings through the collection that contains them.</span></span> <span data-ttu-id="b144a-120">Podrobnosti najdete v tématu [vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="b144a-120">For details, see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b144a-121">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b144a-121">In This Section</span></span>  
 [<span data-ttu-id="b144a-122">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="b144a-122">Configuring System-Provided Bindings</span></span>](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 <span data-ttu-id="b144a-123">Popisuje, jak používat a upravovat vazby, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] poskytuje pro podporu běžné scénáře.</span><span class="sxs-lookup"><span data-stu-id="b144a-123">Describes how to use and modify the bindings that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides to support common scenarios.</span></span>  
  
 [<span data-ttu-id="b144a-124">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="b144a-124">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 <span data-ttu-id="b144a-125">Popisuje, jak definovat [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vazeb pro služby a klienti imperativní v kódu a deklarativně pomocí konfigurace.</span><span class="sxs-lookup"><span data-stu-id="b144a-125">Describes how to define [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] bindings for services and clients imperatively in code and declaratively using configuration.</span></span>  
  
 [<span data-ttu-id="b144a-126">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="b144a-126">Custom Bindings</span></span>](../../../../docs/framework/wcf/extending/custom-bindings.md)  
 <span data-ttu-id="b144a-127">Popisuje, co <xref:System.ServiceModel.Channels.CustomBinding> je a pokud se používá.</span><span class="sxs-lookup"><span data-stu-id="b144a-127">Describes what a <xref:System.ServiceModel.Channels.CustomBinding> is and when it is used.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b144a-128">Odkaz</span><span class="sxs-lookup"><span data-stu-id="b144a-128">Reference</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
  
 <xref:System.ServiceModel.Channels.BindingElement>  
  
 <xref:System.ServiceModel.Channels.CustomBinding>  
  
## <a name="related-sections"></a><span data-ttu-id="b144a-129">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="b144a-129">Related Sections</span></span>  
 [<span data-ttu-id="b144a-130">Rozšiřování vazeb</span><span class="sxs-lookup"><span data-stu-id="b144a-130">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)
