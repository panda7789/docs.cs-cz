---
title: Práce s víc verzemi současně ve třídě WorkflowServiceHost
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 60887eed-df40-4412-b812-41e1dd329d15
ms.openlocfilehash: bc662e51c96a06737e1bd6fd78d5f70f3922d080
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184464"
---
# <a name="side-by-side-versioning-in-workflowservicehost"></a><span data-ttu-id="2a7d2-102">Práce s víc verzemi současně ve třídě WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="2a7d2-102">Side by Side Versioning in WorkflowServiceHost</span></span>
<span data-ttu-id="2a7d2-103">Souběžná <xref:System.ServiceModel.Activities.WorkflowServiceHost> správa verzí zavedená v rozhraní .NET Framework 4.5 poskytuje možnost hostovat více verzí služby pracovního postupu v jednom koncovém bodě.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-103">The <xref:System.ServiceModel.Activities.WorkflowServiceHost> side-by-side versioning introduced in .NET Framework 4.5 provides the capability to host multiple versions of a workflow service on a single endpoint.</span></span> <span data-ttu-id="2a7d2-104">Poskytovaná funkce vedle sebe umožňuje konfiguraci služby pracovního postupu tak, aby byly vytvořeny nové instance služby pracovního postupu pomocí nové definice pracovního postupu, zatímco spuštěné instance byly dokončeny pomocí existující definice.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-104">The side-by-side functionality provided allows a workflow service to be configured so that new instances of the workflow service are created using the new workflow definition, while running instances complete using the existing definition.</span></span> <span data-ttu-id="2a7d2-105">Toto téma obsahuje přehled služby pracovního <xref:System.ServiceModel.Activities.WorkflowServiceHost>postupu souběžné spuštění pomocí .</span><span class="sxs-lookup"><span data-stu-id="2a7d2-105">This topic provides an overview of workflow service side-by-side execution using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2a7d2-106">Chcete-li stáhnout ukázku a podívat se na video návod ke službě pracovního postupu vedle sebe, přečtěte si informace [o správě verzí vedle sebe pomocí služby Xamlx Workflow Service hostované na webu](https://go.microsoft.com/fwlink/?LinkId=393746).</span><span class="sxs-lookup"><span data-stu-id="2a7d2-106">To download a sample and watch a video walkthrough of workflow service side-by-side versioning, see [Side by Side Versioning with a Web-Hosted Xamlx Workflow Service](https://go.microsoft.com/fwlink/?LinkId=393746).</span></span>  
  
## <a name="hosting-multiple-versions-in-a-workflow-service"></a><span data-ttu-id="2a7d2-107">Hostování více verzí ve službě pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="2a7d2-107">Hosting Multiple Versions in a Workflow Service</span></span>  
 <span data-ttu-id="2a7d2-108"><xref:System.ServiceModel.Activities.WorkflowServiceHost>obsahuje dvě vlastnosti, které lze nakonfigurovat tak, aby umožňovaly <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> provádění <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>více verzí pracovního postupu vedle sebe: a .</span><span class="sxs-lookup"><span data-stu-id="2a7d2-108"><xref:System.ServiceModel.Activities.WorkflowServiceHost> contains two properties that can be configured to allow multiple versions of a workflow to execute side-by-side: <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> and <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span> <span data-ttu-id="2a7d2-109"><xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A>obsahuje podporované verze služby pracovního <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> postupu a slouží k jednoznačné identifikaci jednotlivých služeb pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-109"><xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> contains the supported versions of the workflow service, and <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is used to uniquely identify each workflow service.</span></span> <span data-ttu-id="2a7d2-110">To se provádí tak, že <xref:System.Activities.WorkflowIdentity> se přizpůsobujete službě pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-110">This is done by associating a <xref:System.Activities.WorkflowIdentity> with the workflow service.</span></span> <span data-ttu-id="2a7d2-111">A <xref:System.Activities.WorkflowIdentity> obsahuje tři identifikační informace.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-111">A <xref:System.Activities.WorkflowIdentity> contains three identifying pieces of information.</span></span> <span data-ttu-id="2a7d2-112"><xref:System.Activities.WorkflowIdentity.Name%2A>a <xref:System.Activities.WorkflowIdentity.Version%2A> obsahují název <xref:System.Version> a a a <xref:System.Activities.WorkflowIdentity.Package%2A> jsou povinné a je volitelné a lze použít k určení další řetězec obsahující informace, jako je název sestavení nebo jiné požadované informace.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-112"><xref:System.Activities.WorkflowIdentity.Name%2A> and <xref:System.Activities.WorkflowIdentity.Version%2A> contain a name and a <xref:System.Version> and are required, and <xref:System.Activities.WorkflowIdentity.Package%2A> is optional and can be used to specify an additional string containing information such as assembly name or other desired information.</span></span> <span data-ttu-id="2a7d2-113">Každá služba pracovního <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> postupu obsažená <xref:System.Activities.WorkflowIdentity>v kolekci musí mít jedinečný .</span><span class="sxs-lookup"><span data-stu-id="2a7d2-113">Each workflow service contained in the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection must have a unique <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="2a7d2-114">A <xref:System.Activities.WorkflowIdentity> je jedinečný, pokud některý z <xref:System.Activities.WorkflowIdentity>jeho tří vlastností se liší od jiného .</span><span class="sxs-lookup"><span data-stu-id="2a7d2-114">A <xref:System.Activities.WorkflowIdentity> is unique if any of its three properties are different from another <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="2a7d2-115">A `null` <xref:System.Activities.WorkflowIdentity> je přípustná <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>hodnota pro , ale pouze jedna předchozí `null` <xref:System.Activities.WorkflowIdentity>verze služby pracovního postupu může mít .</span><span class="sxs-lookup"><span data-stu-id="2a7d2-115">A `null` <xref:System.Activities.WorkflowIdentity> is an allowable value for <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, but only one previous version of a workflow service may have a `null` <xref:System.Activities.WorkflowIdentity>.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2a7d2-116">A <xref:System.Activities.WorkflowIdentity> by nemělobsahovat žádné osobně identifikovatelné informace (PII).</span><span class="sxs-lookup"><span data-stu-id="2a7d2-116">A <xref:System.Activities.WorkflowIdentity> should not contain any personally identifiable information (PII).</span></span> <span data-ttu-id="2a7d2-117"><xref:System.Activities.WorkflowIdentity>se skládá ze tří <xref:System.Activities.WorkflowIdentity.Name%2A> <xref:System.String>částí: <xref:System.Activities.WorkflowIdentity.Version%2A> <xref:System.Version>a ( <xref:System.Activities.WorkflowIdentity.Package%2A> <xref:System.String>), a ( ), a a ( ).</span><span class="sxs-lookup"><span data-stu-id="2a7d2-117"><xref:System.Activities.WorkflowIdentity> is composed of three parts: a <xref:System.Activities.WorkflowIdentity.Name%2A> (<xref:System.String>), a <xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>), and a <xref:System.Activities.WorkflowIdentity.Package%2A> (<xref:System.String>).</span></span> <span data-ttu-id="2a7d2-118">Informace o <xref:System.Activities.WorkflowIdentity> použité k vytvoření instance jsou vyzařovány všem nakonfigurovaným sledovacím službám v několika různých bodech životního cyklu aktivity v době běhu.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-118">Information about the <xref:System.Activities.WorkflowIdentity> used to create an instance is emitted to any configured tracking services at several different points of the activity life-cycle by the runtime.</span></span> <span data-ttu-id="2a7d2-119">Sledování WF nemá žádný mechanismus pro skrytí PII (citlivá uživatelská data).</span><span class="sxs-lookup"><span data-stu-id="2a7d2-119">WF Tracking does not have any mechanism to hide PII (sensitive user data).</span></span> <span data-ttu-id="2a7d2-120"><xref:System.Activities.WorkflowIdentity> Instance by proto neměla obsahovat žádná data PII, protože bude vyzařována za běhu v záznamech sledování a může být viditelná pro všechny osoby s přístupem k zobrazení záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-120">Therefore, a <xref:System.Activities.WorkflowIdentity> instance should not contain any PII data as it will be emitted by the runtime in tracking records and may be visible to anyone with access to view the tracking records.</span></span>  
  
### <a name="rules-for-hosting-multiple-versions-of-a-workflow-service"></a><span data-ttu-id="2a7d2-121">Pravidla pro hostování více verzí služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="2a7d2-121">Rules for Hosting Multiple Versions of a Workflow Service</span></span>  
 <span data-ttu-id="2a7d2-122">Když uživatel přidá další verzi <xref:System.ServiceModel.Activities.WorkflowServiceHost>, existuje několik podmínek, které musí být splněny, aby služba pracovního postupu, které mají být hostovány se stejnou sadou koncových bodů a popis.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-122">When a user adds an additional version to the <xref:System.ServiceModel.Activities.WorkflowServiceHost>, there are several conditions that must be met in order for a workflow service to be hosted with the same set of endpoints and description.</span></span> <span data-ttu-id="2a7d2-123">Pokud některá z dalších verzí nesplňují <xref:System.ServiceModel.Activities.WorkflowServiceHost> tyto podmínky, `Open` vyvolá výjimku při volání.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-123">If any of the additional versions fail to meet these conditions, the <xref:System.ServiceModel.Activities.WorkflowServiceHost> throws an exception when `Open` is called.</span></span> <span data-ttu-id="2a7d2-124">Každá definice pracovního postupu poskytnutá hostiteli jako další verze musí splňovat následující požadavky (kde primární verze je definice služby pracovního postupu, která je poskytována konstruktoru hostitele).</span><span class="sxs-lookup"><span data-stu-id="2a7d2-124">Each workflow definition provided to the host as an additional version must meet the following requirements (where the primary version is the workflow service definition that is provided to the host constructor).</span></span> <span data-ttu-id="2a7d2-125">Další verze pracovního postupu musí:</span><span class="sxs-lookup"><span data-stu-id="2a7d2-125">The additional workflow version must:</span></span>  
  
- <span data-ttu-id="2a7d2-126">Mají stejné <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> jako primární verze služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-126">Have the same the <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> as the primary version of the workflow service.</span></span>  
  
- <span data-ttu-id="2a7d2-127">Nesmí mít <xref:System.ServiceModel.Activities.Receive> žádné <xref:System.ServiceModel.Activities.SendReply> nebo <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> aktivity v jeho, které nejsou v primární verzi a musí odpovídat smlouvy operace.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-127">Must not have any <xref:System.ServiceModel.Activities.Receive> or <xref:System.ServiceModel.Activities.SendReply> activities in its <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> that are not in the primary version, and they must match the operation contract.</span></span>  
  
- <span data-ttu-id="2a7d2-128">Mít jedinečný <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-128">Have a unique <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span> <span data-ttu-id="2a7d2-129">Jedna a pouze jedna definice `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>pracovního postupu může mít .</span><span class="sxs-lookup"><span data-stu-id="2a7d2-129">One and only one workflow definition may have a `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span>  
  
 <span data-ttu-id="2a7d2-130">Některé změny jsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-130">Some changes are permitted.</span></span> <span data-ttu-id="2a7d2-131">Následující položky se mohou lišit mezi verzemi:</span><span class="sxs-lookup"><span data-stu-id="2a7d2-131">The following items may be different between the versions:</span></span>  
  
- <span data-ttu-id="2a7d2-132">Může <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> mít jiný název a balíček než primární verze.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-132">The <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> may have a different Name and Package than the primary version.</span></span>  
  
- <span data-ttu-id="2a7d2-133">Hodnota <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> se může lišit od primární verze.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-133">The <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> value may be different than the primary version.</span></span>  
  
- <span data-ttu-id="2a7d2-134">Může <xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> být jiný než primární verze.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-134">The <xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> may be different than the primary version.</span></span>  
  
- <span data-ttu-id="2a7d2-135">Může <xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> být jiný než primární verze.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-135">The <xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> may be different than the primary version.</span></span>  
  
### <a name="configuring-the-definitionidentity"></a><span data-ttu-id="2a7d2-136">Konfigurace identity DefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="2a7d2-136">Configuring the DefinitionIdentity</span></span>  
 <span data-ttu-id="2a7d2-137">Když je služba pracovního postupu vytvořena <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> pomocí návrháře pracovního postupu, je nastavena pomocí okna **Vlastnosti.**</span><span class="sxs-lookup"><span data-stu-id="2a7d2-137">When a workflow service is created using the workflow designer, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is set using the **Properties** window.</span></span> <span data-ttu-id="2a7d2-138">Kliknutím mimo kořenovou aktivitu služby v návrháři vyberte službu pracovního postupu a z nabídky **Zobrazení** zvolte **Okno vlastnosti.**</span><span class="sxs-lookup"><span data-stu-id="2a7d2-138">Click outside of the service’s root activity in the designer to select the workflow service, and choose **Properties Window** from the **View** menu.</span></span> <span data-ttu-id="2a7d2-139">V rozevíracím seznamu, který se zobrazí vedle **vlastnosti DefinitionIdentity,** vyberte příkaz <xref:System.Activities.WorkflowIdentity> **WorkflowIdentity** a potom rozbalte a zadejte požadované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-139">Select **WorkflowIdentity** from the drop-down list that appears beside the **DefinitionIdentity** property, and then expand and specify the desired <xref:System.Activities.WorkflowIdentity> properties.</span></span> <span data-ttu-id="2a7d2-140">V <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> následujícím příkladu je <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` nakonfigurován <xref:System.Activities.WorkflowIdentity.Version%2A> `1.0.0.0`s a a .</span><span class="sxs-lookup"><span data-stu-id="2a7d2-140">In the following example the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured with the <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Version%2A> of `1.0.0.0`.</span></span> <span data-ttu-id="2a7d2-141"><xref:System.Activities.WorkflowIdentity.Package%2A>je nepovinný a `null`v tomto příkladu je .</span><span class="sxs-lookup"><span data-stu-id="2a7d2-141"><xref:System.Activities.WorkflowIdentity.Package%2A> is optional and in this example is `null`.</span></span>  
  
 ![Snímek obrazovky, který zobrazuje vlastnost DefinitionIdentity.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-property.bmp)  
  
 <span data-ttu-id="2a7d2-143">Pokud je služba pracovního postupu <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> hostována samostatně, je nakonfigurována při vytváření služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-143">When a workflow service is self-hosted, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured when the workflow service is constructed.</span></span> <span data-ttu-id="2a7d2-144">V následujícím příkladu <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> je nakonfigurován se stejnými hodnotami <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` jako <xref:System.Activities.WorkflowIdentity.Name%2A> `1.0.0.0`v předchozím příkladu s a a .</span><span class="sxs-lookup"><span data-stu-id="2a7d2-144">In the following example, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured with the same values as the previous example, with the <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Name%2A> of `1.0.0.0`.</span></span>  
  
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
  
 <span data-ttu-id="2a7d2-145">A <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> není vyžadováno, i když pouze jedna verze služby pracovního postupu může mít **null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-145">A <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is not required, although only one version of the workflow service may have a **null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2a7d2-146">To je užitečné, pokud byla služba <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> nasazena zpočátku bez nakonfigurované a pak je vytvořena aktualizovaná verze.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-146">This is useful if the service was deployed initially without a <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> configured, and then an updated version is created.</span></span>  
  
### <a name="adding-a-new-version-to-a-web-hosted-workflow-service"></a><span data-ttu-id="2a7d2-147">Přidání nové verze do služby pracovního postupu hostované na webu</span><span class="sxs-lookup"><span data-stu-id="2a7d2-147">Adding a New Version to a Web-hosted Workflow Service</span></span>  
 <span data-ttu-id="2a7d2-148">Prvním krokem při konfiguraci nové verze služby pracovního postupu ve službě hostované `App_Code` ve webovém provozu je vytvoření nové složky ve složce, která má stejný název jako soubor služby.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-148">The first step in configuring a new version of a workflow service in a web-hosted service is to create a new folder in the `App_Code` folder that has the same name as the service file.</span></span> <span data-ttu-id="2a7d2-149">Pokud je soubor `xamlx` služby `MortgageWorkflow.xamlx`pojmenován , musí `MortgageWorkflow`být složka pojmenována .</span><span class="sxs-lookup"><span data-stu-id="2a7d2-149">If the service’s `xamlx` file is named `MortgageWorkflow.xamlx`, then the folder must be named `MortgageWorkflow`.</span></span> <span data-ttu-id="2a7d2-150">Umístěte kopii `xamlx` souboru původní služby do této složky a přejmenujte ji na nový název, například `MortgageWorkflowV1.xamlx`.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-150">Place a copy of the original service’s `xamlx` file into this folder and rename it to a new name, such as `MortgageWorkflowV1.xamlx`.</span></span> <span data-ttu-id="2a7d2-151">Proveďte požadované změny primární služby, aktualizujte její <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>a potom službu nasaďte.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-151">Make the desired changes to the primary service, update its <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, and then deploy the service.</span></span> <span data-ttu-id="2a7d2-152">V následujícím příkladu <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> byla aktualizována s a <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` a a . `2.0.0.0` <xref:System.Activities.WorkflowIdentity.Version%2A></span><span class="sxs-lookup"><span data-stu-id="2a7d2-152">In the following example the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> has been updated with a <xref:System.Activities.WorkflowIdentity.Name%2A> of `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Version%2A> of `2.0.0.0`.</span></span>  
  
 ![Snímek obrazovky, který zobrazuje DefinitionIdentity of WorkflowIdentity.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-workflowidentity.bmp)  
  
 <span data-ttu-id="2a7d2-154">Po restartování služby bude předchozí verze automaticky <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> přidána do kolekce, `App_Code` protože je umístěna v určené podsložce.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-154">When the service restarts, the previous version will automatically be added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection because it is located in the designated `App_Code` subfolder.</span></span> <span data-ttu-id="2a7d2-155">Všimněte si, že pokud má `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> primární verze služby pracovního postupu předchozí verze nebudou přidány.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-155">Note that if the primary version of the workflow service has a `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> the previous versions will not be added.</span></span> <span data-ttu-id="2a7d2-156">Jedna verze může `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>mít , ale pokud existuje více verzí, primární `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> verze nesmí být ta s nebo <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> jinak předchozí verze nebudou přidány do kolekce.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-156">One version may have a `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, but if there are multiple versions the primary version must not be the one with the `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> or else the previous versions will not be added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span>  
  
### <a name="adding-a-new-version-to-a-self-hosted-workflow-service"></a><span data-ttu-id="2a7d2-157">Přidání nové verze do služby pracovního postupu hostované samostatně</span><span class="sxs-lookup"><span data-stu-id="2a7d2-157">Adding a New Version to a Self-hosted Workflow Service</span></span>  
 <span data-ttu-id="2a7d2-158">Při přidávání nové verze do služby pracovního postupu hostované ho s vlastním hostitelem <xref:System.ServiceModel.Activities.WorkflowServiceHost> je nakonfigurován <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> a primární verze služby pracovního postupu a předchozí verze musí být explicitně přidány do kolekce.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-158">When adding a new version to a self-hosted workflow service, the <xref:System.ServiceModel.Activities.WorkflowServiceHost> is configured with the primary version of the workflow service, and previous versions must be explicitly added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span> <span data-ttu-id="2a7d2-159">V následujícím příkladu <xref:System.ServiceModel.Activities.WorkflowServiceHost> je a nakonfigurován s `MortgageWorkflowV2` primární službou pracovního postupu, `MortgageWorkflowV1` která používá definici pracovního postupu, a do <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekce je přidána služba pracovního postupu nakonfigurovaná s definicí pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-159">In the following example, a <xref:System.ServiceModel.Activities.WorkflowServiceHost> is configured with a primary workflow service that uses a `MortgageWorkflowV2` workflow definition, and a workflow service configured with a `MortgageWorkflowV1` workflow definition is added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span> <span data-ttu-id="2a7d2-160">Každá služba pracovního postupu <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> je konfigurována s jedinečným, který odráží verzi definice pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-160">Each workflow service is configured with a unique <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> that reflects the version of the workflow definition.</span></span>  
  
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
