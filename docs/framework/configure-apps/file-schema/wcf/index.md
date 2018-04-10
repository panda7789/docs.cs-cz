---
title: Konfigurační schéma služby WCF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c282aeb5-91f0-4522-8e2f-704c1ef3651f
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7286793d6b2ad94c656dd37cdcc5fe1b0ab85660
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="wcf-configuration-schema"></a><span data-ttu-id="204fd-102">Konfigurační schéma služby WCF</span><span class="sxs-lookup"><span data-stu-id="204fd-102">WCF Configuration Schema</span></span>
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="204fd-103">konfigurace – elementy umožňují nakonfigurovat [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služby a klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="204fd-103"> configuration elements enable you to configure [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service and client applications.</span></span> <span data-ttu-id="204fd-104">Můžete použít [nástroj Configuration Editor (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) vytvářet a upravovat konfigurační soubory pro klienty a služby.</span><span class="sxs-lookup"><span data-stu-id="204fd-104">You can use the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) to create and modify configuration files for clients and services.</span></span> <span data-ttu-id="204fd-105">Vzhledem k tomu, že konfigurační soubory, které jsou formátovány jako XML, musí být nebude znají XML Pokud chcete ručně upravovat pomocí textového editoru.</span><span class="sxs-lookup"><span data-stu-id="204fd-105">Since the configuration files are formatted as XML, you must be familiar with XML if you want to manually edit them using a text editor.</span></span> <span data-ttu-id="204fd-106">Jinak můžete jej spustit do problémy jako k unfound značky elementu XML nebo atributu.</span><span class="sxs-lookup"><span data-stu-id="204fd-106">Otherwise, you may run into issues such as an unfound XML element tag or attribute.</span></span> <span data-ttu-id="204fd-107">Důvodem je, že značky elementu XML a atributy jsou malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="204fd-107">This is because XML element tags and attributes are case-sensitive.</span></span>  
  
 <span data-ttu-id="204fd-108">[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Podle konfigurace systému <xref:System.Configuration> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="204fd-108">The [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] configuration system is based on the <xref:System.Configuration> namespace.</span></span> <span data-ttu-id="204fd-109">Proto můžete použít standardní funkce poskytované službou <xref:System.Configuration> oboru názvů, jako např. konfigurace zámku, šifrování a slučování ke zvýšení zabezpečení vaší aplikace a její konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="204fd-109">Therefore, you can use all the standard features provided by the <xref:System.Configuration> namespace, such as configuration locking, encryption and merging to increase the security of your application and its configuration.</span></span> <span data-ttu-id="204fd-110">Další informace o těchto konceptech naleznete v následujících tématech.</span><span class="sxs-lookup"><span data-stu-id="204fd-110">For more information on these concepts, see the following topics.</span></span>  
  
 [<span data-ttu-id="204fd-111">Informace o konfiguraci šifrování</span><span class="sxs-lookup"><span data-stu-id="204fd-111">Encrypting Configuration Information</span></span>](http://go.microsoft.com/fwlink/?LinkId=95337)  
  
 [<span data-ttu-id="204fd-112">Nastavení uzamčení</span><span class="sxs-lookup"><span data-stu-id="204fd-112">Locking Configuration Settings</span></span>](http://go.microsoft.com/fwlink/?LinkId=95338)  
  
 <span data-ttu-id="204fd-113">Tato část popisuje všechny možné hodnoty každé položky konfigurace a jak komunikuje s jinými prvky konfigurace WCF.</span><span class="sxs-lookup"><span data-stu-id="204fd-113">This section describes all possible values of each configuration item, and how it interacts with other WCF configuration elements.</span></span> <span data-ttu-id="204fd-114">Následující mapa znázorňuje schéma konfigurace WCF.</span><span class="sxs-lookup"><span data-stu-id="204fd-114">The following map illustrates the WCF configuration schema.</span></span>  
  
 <span data-ttu-id="204fd-115">![WCF Configuration Schema](../../../../../docs/framework/configure-apps/file-schema/wcf/media/orcasconfigschema.gif "OrcasConfigSchema")</span><span class="sxs-lookup"><span data-stu-id="204fd-115">![WCF Configuration Schema](../../../../../docs/framework/configure-apps/file-schema/wcf/media/orcasconfigschema.gif "OrcasConfigSchema")</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="204fd-116">Měli byste chránit [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] konfigurační oddíly funkce v konfigurační soubory aplikace (app.config) s odpovídající řízení přístupu jsou uvedené (ACL) aby se zabránilo všechny potenciální bezpečnostní hrozby.</span><span class="sxs-lookup"><span data-stu-id="204fd-116">You should protect [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] configuration sections in your application configuration files (app.config) with appropriate Access Control Lists (ACL) to prevent any potential security threats.</span></span>  <span data-ttu-id="204fd-117">Měli byste si například ověřit, že pouze na příslušné osoby lze zobrazit nebo upravit nastavení zabezpečení na vazby aplikace nebo v části modelu služby konfiguračního souboru pro službu.</span><span class="sxs-lookup"><span data-stu-id="204fd-117">For example, you should make sure that only the appropriate people can access or modify the security settings on application bindings, or the service model section of the configuration file for a service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="204fd-118">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="204fd-118">In This Section</span></span>  
 [<span data-ttu-id="204fd-119">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="204fd-119">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
 <span data-ttu-id="204fd-120">Popisuje `ServiceModel` elementu.</span><span class="sxs-lookup"><span data-stu-id="204fd-120">Describes the `ServiceModel` element.</span></span>  
  
 [<span data-ttu-id="204fd-121">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="204fd-121">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)  
 <span data-ttu-id="204fd-122">Konfiguruje nástroj SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="204fd-122">Configures the SMSvcHost.exe tool.</span></span>  
  
 [<span data-ttu-id="204fd-123">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="204fd-123">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
 <span data-ttu-id="204fd-124">Element nejvyšší úrovně pro nastavení možností při použití serializátorů, jako <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="204fd-124">The top-level element for setting options when using serializers such as the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="204fd-125">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="204fd-125">Related Sections</span></span>  
 [<span data-ttu-id="204fd-126">Konfigurace aplikací pro Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="204fd-126">Configuring Windows Communication Foundation Applications</span></span>](http://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a)  
 <span data-ttu-id="204fd-127">Popisuje postup konfigurace [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služeb a klientů.</span><span class="sxs-lookup"><span data-stu-id="204fd-127">Describes how to configure [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services and clients.</span></span>
