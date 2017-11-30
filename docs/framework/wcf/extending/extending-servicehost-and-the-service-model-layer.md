---
title: "Rozšíření ServiceHost a vrstva modelu služby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: extending service models [WCF]
ms.assetid: 954c138a-1cd0-45a0-8abe-e4d2b8ff5400
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1a1a439735375d96bee2d09f13d50e43783df964
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="extending-servicehost-and-the-service-model-layer"></a><span data-ttu-id="b8436-102">Rozšíření ServiceHost a vrstva modelu služby</span><span class="sxs-lookup"><span data-stu-id="b8436-102">Extending ServiceHost and the Service Model Layer</span></span>
<span data-ttu-id="b8436-103">Vrstva modelu služby je zodpovědná za stahování příchozí zprávy mimo základní kanály, převedena do volání metod v kódu aplikace a odesílání výsledky zpět k volajícímu.</span><span class="sxs-lookup"><span data-stu-id="b8436-103">The service model layer is responsible for pulling incoming messages out of the underlying channels, translating them into method invocations in application code, and sending the results back to the caller.</span></span> <span data-ttu-id="b8436-104">Rozšíření modelů služby upravit nebo jsou implementovány provádění nebo komunikace chování a funkce zahrnující klienta nebo dispečera funkce, vlastní chování, zprávu a parametr zachycení a další funkce rozšiřitelnost.</span><span class="sxs-lookup"><span data-stu-id="b8436-104">Service model extensions modify or implement execution or communication behavior and features involving client or dispatcher functionality, custom behaviors, message and parameter interception, and other extensibility functionality.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b8436-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b8436-105">In This Section</span></span>  
 [<span data-ttu-id="b8436-106">Rozšíření klientů</span><span class="sxs-lookup"><span data-stu-id="b8436-106">Extending Clients</span></span>](../../../../docs/framework/wcf/extending/extending-clients.md)  
 <span data-ttu-id="b8436-107">Popisuje rozhraní, které mohou zachytávat a upravit modul runtime klienta a také třídy, do kterých můžete vložit vlastními rozšířeními v klientských aplikacích.</span><span class="sxs-lookup"><span data-stu-id="b8436-107">Describes the interfaces that can intercept and modify the client runtime, as well as the classes into which you can insert your custom extensions in client applications.</span></span> <span data-ttu-id="b8436-108">Můžete například provést protokolování zpráv vlastní klienta, proveďte vlastní zprávu při serializaci a tak dále.</span><span class="sxs-lookup"><span data-stu-id="b8436-108">For example, you can perform custom client message logging, perform custom message serialization, and so on.</span></span>  
  
 [<span data-ttu-id="b8436-109">Rozšíření dispečerů</span><span class="sxs-lookup"><span data-stu-id="b8436-109">Extending Dispatchers</span></span>](../../../../docs/framework/wcf/extending/extending-dispatchers.md)  
 <span data-ttu-id="b8436-110">Popisuje rozhraní, které mohou zachytávat a upravit běh služby a také třídy, do kterých můžete vložit vlastní rozšíření aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="b8436-110">Describes the interfaces that can intercept and modify the service runtime, as well as the classes into which you can insert your custom extensions in service applications.</span></span> <span data-ttu-id="b8436-111">Například můžete provádět vlastní službu protokolování, ověření na straně služby zprávy, vlastní odeslání a podobně.</span><span class="sxs-lookup"><span data-stu-id="b8436-111">For example, you can perform custom service logging, service-side message validation, custom dispatching, and so on.</span></span>  
  
 [<span data-ttu-id="b8436-112">Rozšiřitelné objekty</span><span class="sxs-lookup"><span data-stu-id="b8436-112">Extensible Objects</span></span>](../../../../docs/framework/wcf/extending/extensible-objects.md)  
 <span data-ttu-id="b8436-113">Popisuje pět rozšiřitelné objekty a <xref:System.ServiceModel.IExtensibleObject%601> vzor.</span><span class="sxs-lookup"><span data-stu-id="b8436-113">Describes the five extensible objects and the <xref:System.ServiceModel.IExtensibleObject%601> pattern.</span></span> <span data-ttu-id="b8436-114">Vzor extensible objektu se používá buď rozšířit existující třídy runtime s novými funkcemi nebo přidat nový stav na objekt.</span><span class="sxs-lookup"><span data-stu-id="b8436-114">The extensible object pattern is used to either extend existing runtime classes with new functionality or to add new state to an object.</span></span> <span data-ttu-id="b8436-115">Rozšíření, které jsou připojené k jednomu rozšiřitelné objekty, aktivujte velmi různých fází zpracování pro přístup k sdílení stavu a funkce, které jsou připojené k běžné extensible objekt, který bude mít přístup k chování.</span><span class="sxs-lookup"><span data-stu-id="b8436-115">Extensions, attached to one of the extensible objects, enable behaviors at very different stages in processing to access shared state and functionality attached to a common extensible object that they can access.</span></span>  
  
 [<span data-ttu-id="b8436-116">Konfigurace a rozšíření modulu Runtime s chováním</span><span class="sxs-lookup"><span data-stu-id="b8436-116">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)  
 <span data-ttu-id="b8436-117">Pokud chcete změnit nastavení na nebo vložit rozšíření v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modul runtime, používáte chování.</span><span class="sxs-lookup"><span data-stu-id="b8436-117">To change settings on or insert extensions in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime, you use Behaviors.</span></span> <span data-ttu-id="b8436-118">WCF zahrnuje implementované systému chování pro řízení omezení, vytváření instancí a mnoho dalších aspektů služby a operace.</span><span class="sxs-lookup"><span data-stu-id="b8436-118">WCF includes system-implemented behaviors for controlling throttling, instancing, and many other aspects of services and operations.</span></span> <span data-ttu-id="b8436-119">Tato část popisuje postup vytvoření vlastního vlastní chování a jak je k dispozici pro použití obou prostřednictvím kódu programu a pomocí konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="b8436-119">This section describes how to create your own custom behaviors and how to make them available for use both programmatically and using configuration files.</span></span>  
  
 [<span data-ttu-id="b8436-120">Rozšíření hostování pomocí třídy ServiceHostFactory</span><span class="sxs-lookup"><span data-stu-id="b8436-120">Extending Hosting Using ServiceHostFactory</span></span>](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)  
 <span data-ttu-id="b8436-121">Popisuje, jak rozšířit <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>, <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>a použít <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> třídy k přizpůsobení hostitelské prostředí.</span><span class="sxs-lookup"><span data-stu-id="b8436-121">Describes how to extend <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>, <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>, and use the <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> classes to customize the host environment.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b8436-122">Odkaz</span><span class="sxs-lookup"><span data-stu-id="b8436-122">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b8436-123">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="b8436-123">Related Sections</span></span>
