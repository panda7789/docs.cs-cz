---
title: Konfigurační schéma služby WCF
ms.date: 03/30/2017
ms.assetid: c282aeb5-91f0-4522-8e2f-704c1ef3651f
ms.openlocfilehash: baea1e49bce10054530afa5b6f282023d5ceb981
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2019
ms.locfileid: "58463329"
---
# <a name="wcf-configuration-schema"></a><span data-ttu-id="7389e-102">Konfigurační schéma služby WCF</span><span class="sxs-lookup"><span data-stu-id="7389e-102">WCF Configuration Schema</span></span>
<span data-ttu-id="7389e-103">Windows Communication Foundation (WCF) konfigurační prvky umožňují nakonfigurovat služeb a klientských aplikací WCF.</span><span class="sxs-lookup"><span data-stu-id="7389e-103">Windows Communication Foundation (WCF) configuration elements enable you to configure WCF service and client applications.</span></span> <span data-ttu-id="7389e-104">Můžete použít [nástroj Configuration Editor (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) vytvářet a upravovat konfigurační soubory pro klienty a služby.</span><span class="sxs-lookup"><span data-stu-id="7389e-104">You can use the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) to create and modify configuration files for clients and services.</span></span> <span data-ttu-id="7389e-105">Protože konfigurační soubory jsou formátovány jako XML, musíte znát XML Pokud budete chtít ručně upravovat pomocí textového editoru.</span><span class="sxs-lookup"><span data-stu-id="7389e-105">Since the configuration files are formatted as XML, you must be familiar with XML if you want to manually edit them using a text editor.</span></span> <span data-ttu-id="7389e-106">Jinak můžete jej spustit do problémy jako k unfound značky elementu XML nebo atributu.</span><span class="sxs-lookup"><span data-stu-id="7389e-106">Otherwise, you may run into issues such as an unfound XML element tag or attribute.</span></span> <span data-ttu-id="7389e-107">Důvodem je, že značky elementu XML a atributy jsou malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="7389e-107">This is because XML element tags and attributes are case-sensitive.</span></span>  
  
 <span data-ttu-id="7389e-108">Systém konfigurace WCF je založen na <xref:System.Configuration> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7389e-108">The WCF configuration system is based on the <xref:System.Configuration> namespace.</span></span> <span data-ttu-id="7389e-109">Proto můžete použít všechny funkce úrovně standard poskytuje <xref:System.Configuration> obor názvů, jako např. konfigurace zámku, šifrování a slučování ke zvýšení zabezpečení aplikace a její konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="7389e-109">Therefore, you can use all the standard features provided by the <xref:System.Configuration> namespace, such as configuration locking, encryption and merging to increase the security of your application and its configuration.</span></span> <span data-ttu-id="7389e-110">Další informace o těchto konceptech naleznete v následujících tématech.</span><span class="sxs-lookup"><span data-stu-id="7389e-110">For more information on these concepts, see the following topics.</span></span>  
  
 [<span data-ttu-id="7389e-111">Informace o konfiguraci šifrování</span><span class="sxs-lookup"><span data-stu-id="7389e-111">Encrypting Configuration Information</span></span>](https://go.microsoft.com/fwlink/?LinkId=95337)  
  
 [<span data-ttu-id="7389e-112">Nastavení uzamčení</span><span class="sxs-lookup"><span data-stu-id="7389e-112">Locking Configuration Settings</span></span>](https://go.microsoft.com/fwlink/?LinkId=95338)  
  
 <span data-ttu-id="7389e-113">Tato část popisuje všechny možné hodnoty každé položky konfigurace a interakci s ostatními prvky konfigurace WCF.</span><span class="sxs-lookup"><span data-stu-id="7389e-113">This section describes all possible values of each configuration item, and how it interacts with other WCF configuration elements.</span></span> <span data-ttu-id="7389e-114">Následující mapa znázorňuje schéma konfigurace služby WCF:</span><span class="sxs-lookup"><span data-stu-id="7389e-114">The following map illustrates the WCF configuration schema:</span></span>  
  
 ![Diagram zobrazující průběh konfigurační schéma služby WCF.](./media/index/windows-communication-foundation-configuration-schema.gif)  
  
> [!CAUTION]
>  <span data-ttu-id="7389e-116">Měli byste chránit WCF konfigurační oddíly funkce v konfigurační soubory aplikace (app.config) s odpovídající řízení přístupu jsou uvedeny (ACL) aby všechny potenciální ohrožení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7389e-116">You should protect WCF configuration sections in your application configuration files (app.config) with appropriate Access Control Lists (ACL) to prevent any potential security threats.</span></span>  <span data-ttu-id="7389e-117">Například by měl Ujistěte se, že pouze na příslušné osoby můžete upravit nebo přistoupit k nastavení zabezpečení v aplikaci vazby nebo model oddílu služby konfiguračního souboru pro službu.</span><span class="sxs-lookup"><span data-stu-id="7389e-117">For example, you should make sure that only the appropriate people can access or modify the security settings on application bindings, or the service model section of the configuration file for a service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7389e-118">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="7389e-118">In This Section</span></span>  
 [<span data-ttu-id="7389e-119">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7389e-119">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
 <span data-ttu-id="7389e-120">Popisuje `ServiceModel` elementu.</span><span class="sxs-lookup"><span data-stu-id="7389e-120">Describes the `ServiceModel` element.</span></span>  
  
 [<span data-ttu-id="7389e-121">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="7389e-121">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)  
 <span data-ttu-id="7389e-122">Konfiguruje nástroj SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="7389e-122">Configures the SMSvcHost.exe tool.</span></span>  
  
 [<span data-ttu-id="7389e-123">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="7389e-123">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
 <span data-ttu-id="7389e-124">Element nejvyšší úrovně pro nastavení možností při použití serializátory, jako <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="7389e-124">The top-level element for setting options when using serializers such as the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7389e-125">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="7389e-125">Related Sections</span></span>  
 [<span data-ttu-id="7389e-126">Konfigurace aplikací Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="7389e-126">Configuring Windows Communication Foundation Applications</span></span>](../../../wcf/configuring-services.md)  
 <span data-ttu-id="7389e-127">Popisuje postup konfigurace služby WCF a klienty.</span><span class="sxs-lookup"><span data-stu-id="7389e-127">Describes how to configure WCF services and clients.</span></span>
