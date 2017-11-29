---
title: "Práce s víc verzemi současně ve třídě WorkflowServiceHost"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 60887eed-df40-4412-b812-41e1dd329d15
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 68b0bea0253e32384291e5e73cc81367b0fb3305
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="side-by-side-versioning-in-workflowservicehost"></a><span data-ttu-id="6c536-102">Práce s víc verzemi současně ve třídě WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="6c536-102">Side by Side Versioning in WorkflowServiceHost</span></span>
<span data-ttu-id="6c536-103"><xref:System.ServiceModel.Activities.WorkflowServiceHost> Vedle sebe verze byla zavedená v [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] poskytuje možnosti pro hostování více verzí služby pracovních postupů na jeden koncový bod.</span><span class="sxs-lookup"><span data-stu-id="6c536-103">The <xref:System.ServiceModel.Activities.WorkflowServiceHost> side-by-side versioning introduced in [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] provides the capability to host multiple versions of a workflow service on a single endpoint.</span></span> <span data-ttu-id="6c536-104">Souběžně sdílená funkce poskytované umožňuje nakonfigurovat tak, aby nové instance služby pracovního postupu se vytvářejí pomocí nové definice pracovního postupu, při spuštění instance dokončení pomocí stávající definici pracovního postupu služby.</span><span class="sxs-lookup"><span data-stu-id="6c536-104">The side-by-side functionality provided allows a workflow service to be configured so that new instances of the workflow service are created using the new workflow definition, while running instances complete using the existing definition.</span></span> <span data-ttu-id="6c536-105">Toto téma obsahuje přehled používání vedle sebe spuštění pracovního postupu služby <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="6c536-105">This topic provides an overview of workflow service side-by-side execution using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6c536-106">Stáhněte si ukázku a podívejte se video s návodem verze vedle sebe služby pracovního postupu najdete v tématu [vedle sebe Správa verzí pomocí služby pracovních postupů Xamlx Web-Hosted](http://go.microsoft.com/fwlink/?LinkId=393746).</span><span class="sxs-lookup"><span data-stu-id="6c536-106">To download a sample and watch a video walkthrough of workflow service side-by-side versioning, see [Side by Side Versioning with a Web-Hosted Xamlx Workflow Service](http://go.microsoft.com/fwlink/?LinkId=393746).</span></span>  
  
## <a name="hosting-multiple-versions-in-a-workflow-service"></a><span data-ttu-id="6c536-107">Hostování více verzí v služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="6c536-107">Hosting Multiple Versions in a Workflow Service</span></span>  
 <span data-ttu-id="6c536-108"><xref:System.ServiceModel.Activities.WorkflowServiceHost>obsahuje dvě vlastnosti, které můžete nakonfigurovat tak, aby více verzí pracovní postup provést vedle sebe: <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> a <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="6c536-108"><xref:System.ServiceModel.Activities.WorkflowServiceHost> contains two properties that can be configured to allow multiple versions of a workflow to execute side-by-side: <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> and <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span> <span data-ttu-id="6c536-109"><xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A>obsahuje podporovaných verzích služby pracovního postupu a <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> slouží k jednoznačné identifikaci jednotlivých služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6c536-109"><xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> contains the supported versions of the workflow service, and <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is used to uniquely identify each workflow service.</span></span> <span data-ttu-id="6c536-110">K tomu je potřeba přidružení <xref:System.Activities.WorkflowIdentity> službou pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6c536-110">This is done by associating a <xref:System.Activities.WorkflowIdentity> with the workflow service.</span></span> <span data-ttu-id="6c536-111">A <xref:System.Activities.WorkflowIdentity> obsahuje tři identifikační údaje.</span><span class="sxs-lookup"><span data-stu-id="6c536-111">A <xref:System.Activities.WorkflowIdentity> contains three identifying pieces of information.</span></span> <span data-ttu-id="6c536-112"><xref:System.Activities.WorkflowIdentity.Name%2A>a <xref:System.Activities.WorkflowIdentity.Version%2A> obsahovat název a <xref:System.Version> a jsou povinné, a <xref:System.Activities.WorkflowIdentity.Package%2A> je volitelný a může sloužit k určení požadovaných další řetězec obsahující informace, jako je název sestavení nebo jiné informace.</span><span class="sxs-lookup"><span data-stu-id="6c536-112"><xref:System.Activities.WorkflowIdentity.Name%2A> and <xref:System.Activities.WorkflowIdentity.Version%2A> contain a name and a <xref:System.Version> and are required, and <xref:System.Activities.WorkflowIdentity.Package%2A> is optional and can be used to specify an additional string containing information such as assembly name or other desired information.</span></span> <span data-ttu-id="6c536-113">Každý služby pracovního postupu, který je součástí <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekce musí mít jedinečnou <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="6c536-113">Each workflow service contained in the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection must have a unique <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="6c536-114">A <xref:System.Activities.WorkflowIdentity> je jedinečný, pokud jsou některé jeho vlastnosti tři liší od jiného <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="6c536-114">A <xref:System.Activities.WorkflowIdentity> is unique if any of its three properties are different from another <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="6c536-115">A `null` <xref:System.Activities.WorkflowIdentity> je povolená hodnota pro <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, ale mohou mít pouze jeden předchozí verzi služby pracovního postupu `null` <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="6c536-115">A `null` <xref:System.Activities.WorkflowIdentity> is an allowable value for <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, but only one previous version of a workflow service may have a `null` <xref:System.Activities.WorkflowIdentity>.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6c536-116">A <xref:System.Activities.WorkflowIdentity> nesmí obsahovat žádné identifikovatelné osobní údaje (PII).</span><span class="sxs-lookup"><span data-stu-id="6c536-116">A <xref:System.Activities.WorkflowIdentity> should not contain any personally identifiable information (PII).</span></span> <span data-ttu-id="6c536-117"><xref:System.Activities.WorkflowIdentity>se skládá ze tří částí: <xref:System.Activities.WorkflowIdentity.Name%2A> (<xref:System.String>), <xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>) a <xref:System.Activities.WorkflowIdentity.Package%2A> (<xref:System.String>).</span><span class="sxs-lookup"><span data-stu-id="6c536-117"><xref:System.Activities.WorkflowIdentity> is composed of three parts: a <xref:System.Activities.WorkflowIdentity.Name%2A> (<xref:System.String>), a <xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>), and a <xref:System.Activities.WorkflowIdentity.Package%2A> (<xref:System.String>).</span></span> <span data-ttu-id="6c536-118">Informace o <xref:System.Activities.WorkflowIdentity> použít k vytvoření instance je pro všechny nakonfigurované sledování životního cyklu služeb v několika různých místech aktivity vygenerované modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="6c536-118">Information about the <xref:System.Activities.WorkflowIdentity> used to create an instance is emitted to any configured tracking services at several different points of the activity life-cycle by the runtime.</span></span> <span data-ttu-id="6c536-119">WF sledování nemá žádný mechanismus skrýt PII (citlivé uživatelských dat).</span><span class="sxs-lookup"><span data-stu-id="6c536-119">WF Tracking does not have any mechanism to hide PII (sensitive user data).</span></span> <span data-ttu-id="6c536-120">Proto <xref:System.Activities.WorkflowIdentity> instance nesmí obsahovat žádná data PII tak, jak bude vygenerované modulem runtime v sledování záznamů a mohou být viditelná pro každý, kdo má přístup k zobrazení záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="6c536-120">Therefore, a <xref:System.Activities.WorkflowIdentity> instance should not contain any PII data as it will be emitted by the runtime in tracking records and may be visible to anyone with access to view the tracking records.</span></span>  
  
### <a name="rules-for-hosting-multiple-versions-of-a-workflow-service"></a><span data-ttu-id="6c536-121">Pravidla pro hostování více verzí služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="6c536-121">Rules for Hosting Multiple Versions of a Workflow Service</span></span>  
 <span data-ttu-id="6c536-122">Pokud uživatel přidá další verzi <xref:System.ServiceModel.Activities.WorkflowServiceHost>, existuje několik podmínek, které je nutné splnit, aby služby pracovního postupu pro hostování se stejnou sadu koncových bodů a popis.</span><span class="sxs-lookup"><span data-stu-id="6c536-122">When a user adds an additional version to the <xref:System.ServiceModel.Activities.WorkflowServiceHost>, there are several conditions that must be met in order for a workflow service to be hosted with the same set of endpoints and description.</span></span> <span data-ttu-id="6c536-123">Pokud některý z dalších verzí selže ke splnění těchto podmínek <xref:System.ServiceModel.Activities.WorkflowServiceHost> vyvolá výjimku při `Open` je volána.</span><span class="sxs-lookup"><span data-stu-id="6c536-123">If any of the additional versions fail to meet these conditions, the <xref:System.ServiceModel.Activities.WorkflowServiceHost> throws an exception when `Open` is called.</span></span> <span data-ttu-id="6c536-124">Každý zadaná hostitele jako další verze definice pracovního postupu musí splňovat následující požadavky (kde primární verze je definice služby pracovního postupu, který je zadán pro konstruktor hostitele).</span><span class="sxs-lookup"><span data-stu-id="6c536-124">Each workflow definition provided to the host as an additional version must meet the following requirements (where the primary version is the workflow service definition that is provided to the host constructor).</span></span> <span data-ttu-id="6c536-125">Musí být verze další pracovního postupu:</span><span class="sxs-lookup"><span data-stu-id="6c536-125">The additional workflow version must:</span></span>  
  
-   <span data-ttu-id="6c536-126">Mít stejnou <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> jako primární verzi služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6c536-126">Have the same the <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> as the primary version of the workflow service.</span></span>  
  
-   <span data-ttu-id="6c536-127">Nesmí mít žádné <xref:System.ServiceModel.Activities.Receive> nebo <xref:System.ServiceModel.Activities.SendReply> aktivity v jeho <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> které nejsou v primární verzi, a musí odpovídat kontrakt operaci.</span><span class="sxs-lookup"><span data-stu-id="6c536-127">Must not have any <xref:System.ServiceModel.Activities.Receive> or <xref:System.ServiceModel.Activities.SendReply> activities in its <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> that are not in the primary version, and they must match the operation contract.</span></span>  
  
-   <span data-ttu-id="6c536-128">Mít jedinečnou <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="6c536-128">Have a unique <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span> <span data-ttu-id="6c536-129">Může mít pouze jednu definici pracovního postupu `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="6c536-129">One and only one workflow definition may have a `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span>  
  
 <span data-ttu-id="6c536-130">Některé změny nejsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="6c536-130">Some changes are permitted.</span></span> <span data-ttu-id="6c536-131">Následující položky se můžou lišit mezi verzemi:</span><span class="sxs-lookup"><span data-stu-id="6c536-131">The following items may be different between the versions:</span></span>  
  
-   <span data-ttu-id="6c536-132"><xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> Může mít jiný název a balíček než primární verze.</span><span class="sxs-lookup"><span data-stu-id="6c536-132">The <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> may have a different Name and Package than the primary version.</span></span>  
  
-   <span data-ttu-id="6c536-133"><xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> Hodnota může být jiný než primární verze.</span><span class="sxs-lookup"><span data-stu-id="6c536-133">The <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> value may be different than the primary version.</span></span>  
  
-   <span data-ttu-id="6c536-134"><xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> Může být jiný než primární verze.</span><span class="sxs-lookup"><span data-stu-id="6c536-134">The <xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> may be different than the primary version.</span></span>  
  
-   <span data-ttu-id="6c536-135"><xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> Může být jiný než primární verze.</span><span class="sxs-lookup"><span data-stu-id="6c536-135">The <xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> may be different than the primary version.</span></span>  
  
### <a name="configuring-the-definitionidentity"></a><span data-ttu-id="6c536-136">Konfigurace DefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="6c536-136">Configuring the DefinitionIdentity</span></span>  
 <span data-ttu-id="6c536-137">Při vytvoření služby pracovních postupů pomocí návrháře pracovních postupů <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> se nastavuje pomocí **vlastnosti** okno.</span><span class="sxs-lookup"><span data-stu-id="6c536-137">When a workflow service is created using the workflow designer, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is set using the **Properties** window.</span></span> <span data-ttu-id="6c536-138">Klikněte na tlačítko mimo služby kořenové aktivity v Návrháři vyberte služby pracovního postupu, a vyberte **vlastnosti – okno** z **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="6c536-138">Click outside of the service’s root activity in the designer to select the workflow service, and choose **Properties Window** from the **View** menu.</span></span> <span data-ttu-id="6c536-139">Vyberte **WorkflowIdentity** ze seznamu rozevíracího seznamu, který se zobrazí vedle **DefinitionIdentity** vlastnost a potom rozbalte položku a zadejte požadovanou <xref:System.Activities.WorkflowIdentity> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6c536-139">Select **WorkflowIdentity** from the drop-down list that appears beside the **DefinitionIdentity** property, and then expand and specify the desired <xref:System.Activities.WorkflowIdentity> properties.</span></span> <span data-ttu-id="6c536-140">V následujícím příkladu <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> nastavena <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` a <xref:System.Activities.WorkflowIdentity.Version%2A> z `1.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="6c536-140">In the following example the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured with the <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Version%2A> of `1.0.0.0`.</span></span> <span data-ttu-id="6c536-141"><xref:System.Activities.WorkflowIdentity.Package%2A>je volitelný a v tomto příkladu je `null`.</span><span class="sxs-lookup"><span data-stu-id="6c536-141"><xref:System.Activities.WorkflowIdentity.Package%2A> is optional and in this example is `null`.</span></span>  
  
 <span data-ttu-id="6c536-142">![DefinitionIdentity](../../../../docs/framework/wcf/feature-details/media/workflowservicedefinitionidentityv1.bmp "WorkflowServiceDefinitionIdentityv1")</span><span class="sxs-lookup"><span data-stu-id="6c536-142">![DefinitionIdentity](../../../../docs/framework/wcf/feature-details/media/workflowservicedefinitionidentityv1.bmp "WorkflowServiceDefinitionIdentityv1")</span></span>  
  
 <span data-ttu-id="6c536-143">Po samoobslužné hostované služby pracovních postupů <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> je nakonfigurován, když se služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6c536-143">When a workflow service is self-hosted, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured when the workflow service is constructed.</span></span> <span data-ttu-id="6c536-144">V následujícím příkladu <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> stejné hodnoty jako předchozí příklad, nakonfigurované s <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` a <xref:System.Activities.WorkflowIdentity.Name%2A> z `1.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="6c536-144">In the following example, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured with the same values as the previous example, with the <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Name%2A> of `1.0.0.0`.</span></span>  
  
```csharp  
WorkflowService service = new WorkflowService  
{  
    Name = "MortgageWorkflowService",  
    Body = new MortgageWorkflow(),  
    DefinitionIdentity = new WorkflowIdentity  
    {  
        Name = "MortgageWorkflow",  
        Version = new Version(1, 0, 0, 0)  
    }  
};  
```  
  
```vb  
Dim service As New WorkflowService  
With service  
    .Name = "MortgageWorkflowService"  
    .Body = New MortgageWorkflow  
    .DefinitionIdentity = New WorkflowIdentity With _  
    { _  
        .Name = "MortgageWorkflow", _  
        .Version = New Version(1, 0, 0, 0) _  
    }  
End With  
```  
  
 <span data-ttu-id="6c536-145">A <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> není vyžadována, i když může mít jenom jednu verzi služby pracovního postupu **null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="6c536-145">A <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is not required, although only one version of the workflow service may have a **null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6c536-146">To je užitečné, pokud je služba nasazená původně bez <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> nakonfigurovaná, a pak se vytvoří aktualizovaná verze.</span><span class="sxs-lookup"><span data-stu-id="6c536-146">This is useful if the service was deployed initially without a <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> configured, and then an updated version is created.</span></span>  
  
### <a name="adding-a-new-version-to-a-web-hosted-workflow-service"></a><span data-ttu-id="6c536-147">Přidání nové verze do pracovního postupu hostované webové služby</span><span class="sxs-lookup"><span data-stu-id="6c536-147">Adding a New Version to a Web-hosted Workflow Service</span></span>  
 <span data-ttu-id="6c536-148">Prvním krokem při konfiguraci nové verze služby pracovního procesu ve webové hostované služby je vytvořte novou složku v `App_Code` složky, která má stejný název jako soubor služby.</span><span class="sxs-lookup"><span data-stu-id="6c536-148">The first step in configuring a new version of a workflow service in a web-hosted service is to create a new folder in the `App_Code` folder that has the same name as the service file.</span></span> <span data-ttu-id="6c536-149">Pokud služby `xamlx` název souboru je `MortgageWorkflow.xamlx`, pak musí mít název složky `MortgageWorkflow`.</span><span class="sxs-lookup"><span data-stu-id="6c536-149">If the service’s `xamlx` file is named `MortgageWorkflow.xamlx`, then the folder must be named `MortgageWorkflow`.</span></span> <span data-ttu-id="6c536-150">Umístěte kopii původní službu `xamlx` souborů do této složky a přejmenujte jej na nový název, například `MortgageWorkflowV1.xamlx`.</span><span class="sxs-lookup"><span data-stu-id="6c536-150">Place a copy of the original service’s `xamlx` file into this folder and rename it to a new name, such as `MortgageWorkflowV1.xamlx`.</span></span> <span data-ttu-id="6c536-151">Proveďte požadované změny do primární služby, aktualizujte jeho <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>a poté nasaďte službu.</span><span class="sxs-lookup"><span data-stu-id="6c536-151">Make the desired changes to the primary service, update its <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, and then deploy the service.</span></span> <span data-ttu-id="6c536-152">V následujícím příkladu <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> bylo aktualizováno <xref:System.Activities.WorkflowIdentity.Name%2A> z `MortageWorkflow` a <xref:System.Activities.WorkflowIdentity.Version%2A> z `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="6c536-152">In the following example the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> has been updated with a <xref:System.Activities.WorkflowIdentity.Name%2A> of `MortageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Version%2A> of `2.0.0.0`.</span></span>  
  
 <span data-ttu-id="6c536-153">![DefinitionIdentity](../../../../docs/framework/wcf/feature-details/media/workflowservicedefinitionidentityv2.bmp "WorkflowServiceDefinitionIdentityv2")</span><span class="sxs-lookup"><span data-stu-id="6c536-153">![DefinitionIdentity](../../../../docs/framework/wcf/feature-details/media/workflowservicedefinitionidentityv2.bmp "WorkflowServiceDefinitionIdentityv2")</span></span>  
  
 <span data-ttu-id="6c536-154">Po restartování služby předchozí verze automaticky přidá do <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekce vzhledem k tomu, že se nachází v určené `App_Code` podsložky.</span><span class="sxs-lookup"><span data-stu-id="6c536-154">When the service restarts, the previous version will automatically be added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection because it is located in the designated `App_Code` subfolder.</span></span> <span data-ttu-id="6c536-155">Všimněte si, že pokud má primární verzi služby pracovního postupu `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> nepřidají předchozí verze.</span><span class="sxs-lookup"><span data-stu-id="6c536-155">Note that if the primary version of the workflow service has a `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> the previous versions will not be added.</span></span> <span data-ttu-id="6c536-156">Může mít jednu verzi `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, ale pokud existuje více verzí primární verze nesmí být ten se `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> nebo jinak předchozí verze nepřidají k <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="6c536-156">One version may have a `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, but if there are multiple versions the primary version must not be the one with the `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> or else the previous versions will not be added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span>  
  
### <a name="adding-a-new-version-to-a-self-hosted-workflow-service"></a><span data-ttu-id="6c536-157">Přidání nové verze službě samoobslužné hostovaných pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="6c536-157">Adding a New Version to a Self-hosted Workflow Service</span></span>  
 <span data-ttu-id="6c536-158">Při přidávání nové verze službě vlastním hostováním pracovního postupu, <xref:System.ServiceModel.Activities.WorkflowServiceHost> je nakonfigurován s primární verzí služby pracovního postupu a předchozí verze musí být explicitně přidán <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="6c536-158">When adding a new version to a self-hosted workflow service, the <xref:System.ServiceModel.Activities.WorkflowServiceHost> is configured with the primary version of the workflow service, and previous versions must be explicitly added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span> <span data-ttu-id="6c536-159">V následujícím příkladu <xref:System.ServiceModel.Activities.WorkflowServiceHost> je nakonfigurován pomocí služby primární pracovního postupu, který používá `MortgageWorkflowV2` definice pracovního postupu a nakonfigurované služby pracovních postupů `MortgageWorkflowV1` definice pracovního postupu se přidá do <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="6c536-159">In the following example, a <xref:System.ServiceModel.Activities.WorkflowServiceHost> is configured with a primary workflow service that uses a `MortgageWorkflowV2` workflow definition, and a workflow service configured with a `MortgageWorkflowV1` workflow definition is added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span> <span data-ttu-id="6c536-160">Každý pracovní postup služba je nakonfigurována s jedinečným <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> s odpovídajícími verze definice pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6c536-160">Each workflow service is configured with a unique <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> that reflects the version of the workflow definition.</span></span>  
  
```csharp  
// Create the primary version of the workflow service.  
WorkflowService serviceV2 = new WorkflowService  
{  
    Name = "MortgageWorkflowService",  
    Body = new MortgageWorkflowV2(),  
    DefinitionIdentity = new WorkflowIdentity  
    {  
        Name = "MortgageWorkflow",  
        Version = new Version(2, 0, 0, 0)  
    }  
};  
  
// Configure the WorkflowServiceHost with the current version  
// of the workflow service. This code requires Administrator  
// privileges to function correctly. If running from Visual  
// Studio, Visual Studio must be run with Administrator privileges.  
WorkflowServiceHost host = new WorkflowServiceHost(serviceV2,   
    new Uri("http://localhost:8080/MortgageWorkflowService"));  
  
// Create the previous version of the workflow service.  
WorkflowService serviceV1 = new WorkflowService  
{  
    Name = "MortgageWorkflowService",  
    Body = new MortgageWorkflowV1(),  
    DefinitionIdentity = new WorkflowIdentity  
    {  
        Name = "MortgageWorkflow",  
        Version = new Version(1, 0, 0, 0)  
    }  
};  
  
// Add the previous version of the service to the SupportedVersions collection.  
host.SupportedVersions.Add(serviceV1);  
```  
  
```vb  
'Create the primary version of the workflow service  
Dim serviceV2 As New WorkflowService  
With serviceV2  
    .Name = "MortgageWorkflowService"  
    .Body = New MortgageWorkflowV2  
    .DefinitionIdentity = New WorkflowIdentity With _  
    { _  
        .Name = "MortgageWorkflow", _  
        .Version = New Version(2, 0, 0, 0) _  
    }  
End With  
  
'Configure the WorkflowServiceHost with the current version  
'of the workflow service. This code requires Administrator  
'privileges to function correctly. If running from Visual  
'Studio, Visual Studio must be run with Administrator privileges.  
  
Dim host As New WorkflowServiceHost(serviceV2, _  
    New Uri("http://localhost:8080/MortgageWorkflowService"))  
  
'Create the previous version of the workflow service.  
Dim serviceV1 As New WorkflowService  
With serviceV1  
    .Name = "MortgageWorkflowService"  
    .Body = New MortgageWorkflowV1  
    .DefinitionIdentity = New WorkflowIdentity With _  
    { _  
        .Name = "MortgageWorkflow", _  
        .Version = New Version(1, 0, 0, 0) _  
    }  
End With  
  
'Add the previous version of the service to the SupportedVersions collection.  
host.SupportedVersions.Add(serviceV1)  
```
