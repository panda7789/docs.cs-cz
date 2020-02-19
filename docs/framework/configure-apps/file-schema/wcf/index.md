---
title: Konfigurační schéma služby WCF
ms.date: 03/30/2017
ms.assetid: c282aeb5-91f0-4522-8e2f-704c1ef3651f
ms.openlocfilehash: 866b0639f4391e1898bbe36e458df87e3c24bfff
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77448656"
---
# <a name="wcf-configuration-schema"></a><span data-ttu-id="83dfe-102">Konfigurační schéma služby WCF</span><span class="sxs-lookup"><span data-stu-id="83dfe-102">WCF Configuration Schema</span></span>
<span data-ttu-id="83dfe-103">Konfigurační prvky Windows Communication Foundation (WCF) umožňují nakonfigurovat službu WCF a klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="83dfe-103">Windows Communication Foundation (WCF) configuration elements enable you to configure WCF service and client applications.</span></span> <span data-ttu-id="83dfe-104">Pomocí [nástroje Configuration Editor (SvcConfigEditor. exe)](../../../wcf/configuration-editor-tool-svcconfigeditor-exe.md) můžete vytvářet a upravovat konfigurační soubory pro klienty a služby.</span><span class="sxs-lookup"><span data-stu-id="83dfe-104">You can use the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../wcf/configuration-editor-tool-svcconfigeditor-exe.md) to create and modify configuration files for clients and services.</span></span> <span data-ttu-id="83dfe-105">Vzhledem k tomu, že konfigurační soubory jsou formátovány jako XML, musíte být obeznámeni s XML, pokud je chcete ručně upravovat pomocí textového editoru.</span><span class="sxs-lookup"><span data-stu-id="83dfe-105">Since the configuration files are formatted as XML, you must be familiar with XML if you want to manually edit them using a text editor.</span></span> <span data-ttu-id="83dfe-106">Jinak můžete jej spustit do problémy jako k unfound značky elementu XML nebo atributu.</span><span class="sxs-lookup"><span data-stu-id="83dfe-106">Otherwise, you may run into issues such as an unfound XML element tag or attribute.</span></span> <span data-ttu-id="83dfe-107">Důvodem je, že značky elementu XML a atributy jsou malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="83dfe-107">This is because XML element tags and attributes are case-sensitive.</span></span>  
  
 <span data-ttu-id="83dfe-108">Konfigurační systém WCF je založený na oboru názvů <xref:System.Configuration>.</span><span class="sxs-lookup"><span data-stu-id="83dfe-108">The WCF configuration system is based on the <xref:System.Configuration> namespace.</span></span> <span data-ttu-id="83dfe-109">Proto můžete použít všechny standardní funkce poskytované oborem názvů <xref:System.Configuration>, například uzamykání konfigurace, šifrování a sloučení, a zvýšit tak zabezpečení vaší aplikace a její konfigurace.</span><span class="sxs-lookup"><span data-stu-id="83dfe-109">Therefore, you can use all the standard features provided by the <xref:System.Configuration> namespace, such as configuration locking, encryption and merging to increase the security of your application and its configuration.</span></span> <span data-ttu-id="83dfe-110">Další informace o těchto konceptech najdete v následujících tématech.</span><span class="sxs-lookup"><span data-stu-id="83dfe-110">For more information on these concepts, see the following topics.</span></span>  
  
 <span data-ttu-id="83dfe-111">[Šifrování informací o konfiguraci](https://docs.microsoft.com/previous-versions/aspnet/53tyfkaw(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="83dfe-111">[Encrypting Configuration Information](https://docs.microsoft.com/previous-versions/aspnet/53tyfkaw(v=vs.100))</span></span>  
  
 <span data-ttu-id="83dfe-112">[Uzamykání nastavení konfigurace](https://docs.microsoft.com/previous-versions/aspnet/55th21y4(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="83dfe-112">[Locking Configuration Settings](https://docs.microsoft.com/previous-versions/aspnet/55th21y4(v=vs.100))</span></span>  
  
 <span data-ttu-id="83dfe-113">Tato část popisuje všechny možné hodnoty každé položky konfigurace a způsob, jakým komunikuje s ostatními konfiguračními prvky služby WCF.</span><span class="sxs-lookup"><span data-stu-id="83dfe-113">This section describes all possible values of each configuration item, and how it interacts with other WCF configuration elements.</span></span> <span data-ttu-id="83dfe-114">Následující mapa znázorňuje schéma konfigurace WCF:</span><span class="sxs-lookup"><span data-stu-id="83dfe-114">The following map illustrates the WCF configuration schema:</span></span>  
  
 ![Diagram, který zobrazuje schéma konfigurace WCF.](./media/index/windows-communication-foundation-configuration-schema.gif)  
  
> [!CAUTION]
> <span data-ttu-id="83dfe-116">Měli byste chránit konfigurační oddíly WCF v konfiguračních souborech aplikace (App. config) pomocí příslušných seznamů Access Control (ACL), aby se předešlo potenciálním bezpečnostním hrozbám.</span><span class="sxs-lookup"><span data-stu-id="83dfe-116">You should protect WCF configuration sections in your application configuration files (app.config) with appropriate Access Control Lists (ACL) to prevent any potential security threats.</span></span>  <span data-ttu-id="83dfe-117">Měli byste se třeba ujistit, že k nastavení zabezpečení pro vazby aplikací nebo v oddílu modelu služby v konfiguračním souboru pro službu mají přístup jenom odpovídající uživatelé.</span><span class="sxs-lookup"><span data-stu-id="83dfe-117">For example, you should make sure that only the appropriate people can access or modify the security settings on application bindings, or the service model section of the configuration file for a service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="83dfe-118">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="83dfe-118">In This Section</span></span>  
 [<span data-ttu-id="83dfe-119">\<System. serviceModel ></span><span class="sxs-lookup"><span data-stu-id="83dfe-119">\<system.serviceModel></span></span>](system-servicemodel.md)  
 <span data-ttu-id="83dfe-120">Popisuje `ServiceModel` elementu.</span><span class="sxs-lookup"><span data-stu-id="83dfe-120">Describes the `ServiceModel` element.</span></span>  
  
 [<span data-ttu-id="83dfe-121">\<System. serviceModel. Activation ></span><span class="sxs-lookup"><span data-stu-id="83dfe-121">\<system.serviceModel.activation></span></span>](system-servicemodel-activation.md)  
 <span data-ttu-id="83dfe-122">Konfiguruje nástroj SMSvcHost. exe.</span><span class="sxs-lookup"><span data-stu-id="83dfe-122">Configures the SMSvcHost.exe tool.</span></span>  
  
 [<span data-ttu-id="83dfe-123">\<System. Runtime. Serialization ></span><span class="sxs-lookup"><span data-stu-id="83dfe-123">\<system.runtime.serialization></span></span>](system-runtime-serialization.md)  
 <span data-ttu-id="83dfe-124">Element nejvyšší úrovně pro nastavení možností při použití serializátorů, jako je <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="83dfe-124">The top-level element for setting options when using serializers such as the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="83dfe-125">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="83dfe-125">Related Sections</span></span>  
 [<span data-ttu-id="83dfe-126">Konfigurace aplikací Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="83dfe-126">Configuring Windows Communication Foundation Applications</span></span>](../../../wcf/configuring-services.md)  
 <span data-ttu-id="83dfe-127">Popisuje postup konfigurace služeb a klientů služby WCF.</span><span class="sxs-lookup"><span data-stu-id="83dfe-127">Describes how to configure WCF services and clients.</span></span>
