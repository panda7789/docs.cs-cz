---
title: Práce s víc verzemi současně ve třídě WorkflowServiceHost
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 60887eed-df40-4412-b812-41e1dd329d15
ms.openlocfilehash: 0323c0f10538eda2ed3b365a54470bdecac061a8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64586204"
---
# <a name="side-by-side-versioning-in-workflowservicehost"></a><span data-ttu-id="9b0b7-102">Práce s víc verzemi současně ve třídě WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="9b0b7-102">Side by Side Versioning in WorkflowServiceHost</span></span>
<span data-ttu-id="9b0b7-103"><xref:System.ServiceModel.Activities.WorkflowServiceHost> Počínaje verzí vedle sebe [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] poskytuje možnost hostování několika verzí služby pracovního postupu v jednom koncovém bodu.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-103">The <xref:System.ServiceModel.Activities.WorkflowServiceHost> side-by-side versioning introduced in [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] provides the capability to host multiple versions of a workflow service on a single endpoint.</span></span> <span data-ttu-id="9b0b7-104">Vedle sebe funkce poskytované umožňuje nakonfigurovat tak, aby nové instance služby pracovního postupu jsou vytvořené pomocí novou definici pracovního postupu při spuštění úplné pomocí existující definici instance služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-104">The side-by-side functionality provided allows a workflow service to be configured so that new instances of the workflow service are created using the new workflow definition, while running instances complete using the existing definition.</span></span> <span data-ttu-id="9b0b7-105">Toto téma obsahuje přehled používání vedle sebe provádění pracovního postupu služby <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-105">This topic provides an overview of workflow service side-by-side execution using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b0b7-106">Stáhněte si ukázku a podívejte se video s návodem, Správa verzí vedle sebe služby pracovního postupu najdete v tématu [vedle sebe Správa verzí pomocí služby pracovního postupu Xamlx Web-Hosted](https://go.microsoft.com/fwlink/?LinkId=393746).</span><span class="sxs-lookup"><span data-stu-id="9b0b7-106">To download a sample and watch a video walkthrough of workflow service side-by-side versioning, see [Side by Side Versioning with a Web-Hosted Xamlx Workflow Service](https://go.microsoft.com/fwlink/?LinkId=393746).</span></span>  
  
## <a name="hosting-multiple-versions-in-a-workflow-service"></a><span data-ttu-id="9b0b7-107">Hostování několika verzí služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="9b0b7-107">Hosting Multiple Versions in a Workflow Service</span></span>  
 <span data-ttu-id="9b0b7-108"><xref:System.ServiceModel.Activities.WorkflowServiceHost> obsahuje dvě vlastnosti, které můžete nakonfigurovat tak, aby více verzí pracovního postupu ke spuštění vedle sebe: <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> a <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-108"><xref:System.ServiceModel.Activities.WorkflowServiceHost> contains two properties that can be configured to allow multiple versions of a workflow to execute side-by-side: <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> and <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span> <span data-ttu-id="9b0b7-109"><xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> obsahuje podporovaných verzí služby pracovního postupu a <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> slouží k jednoznačné identifikaci každé služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-109"><xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> contains the supported versions of the workflow service, and <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is used to uniquely identify each workflow service.</span></span> <span data-ttu-id="9b0b7-110">Je to tím, že přidružíte <xref:System.Activities.WorkflowIdentity> službě pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-110">This is done by associating a <xref:System.Activities.WorkflowIdentity> with the workflow service.</span></span> <span data-ttu-id="9b0b7-111">A <xref:System.Activities.WorkflowIdentity> obsahuje tři identifikační údaje.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-111">A <xref:System.Activities.WorkflowIdentity> contains three identifying pieces of information.</span></span> <span data-ttu-id="9b0b7-112"><xref:System.Activities.WorkflowIdentity.Name%2A> a <xref:System.Activities.WorkflowIdentity.Version%2A> obsahovat název a <xref:System.Version> a jsou povinné, a <xref:System.Activities.WorkflowIdentity.Package%2A> je volitelný a slouží k určení další řetězec obsahující informace, jako je název sestavení nebo jiné požadované informace.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-112"><xref:System.Activities.WorkflowIdentity.Name%2A> and <xref:System.Activities.WorkflowIdentity.Version%2A> contain a name and a <xref:System.Version> and are required, and <xref:System.Activities.WorkflowIdentity.Package%2A> is optional and can be used to specify an additional string containing information such as assembly name or other desired information.</span></span> <span data-ttu-id="9b0b7-113">Každá služba pracovního postupu součástí <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekce musí mít jedinečnou <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-113">Each workflow service contained in the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection must have a unique <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="9b0b7-114">A <xref:System.Activities.WorkflowIdentity> je jedinečné, pokud některý z jeho tři vlastnosti se liší od jiného <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-114">A <xref:System.Activities.WorkflowIdentity> is unique if any of its three properties are different from another <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="9b0b7-115">A `null` <xref:System.Activities.WorkflowIdentity> není povolená hodnota pro <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, ale mohou mít pouze jednu předchozí verzi služby pracovních postupů `null` <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-115">A `null` <xref:System.Activities.WorkflowIdentity> is an allowable value for <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, but only one previous version of a workflow service may have a `null` <xref:System.Activities.WorkflowIdentity>.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9b0b7-116">A <xref:System.Activities.WorkflowIdentity> nesmí obsahovat žádné identifikovatelné osobní údaje (PII).</span><span class="sxs-lookup"><span data-stu-id="9b0b7-116">A <xref:System.Activities.WorkflowIdentity> should not contain any personally identifiable information (PII).</span></span> <span data-ttu-id="9b0b7-117"><xref:System.Activities.WorkflowIdentity> se skládá ze tří částí: <xref:System.Activities.WorkflowIdentity.Name%2A> (<xref:System.String>), <xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>) a <xref:System.Activities.WorkflowIdentity.Package%2A> (<xref:System.String>).</span><span class="sxs-lookup"><span data-stu-id="9b0b7-117"><xref:System.Activities.WorkflowIdentity> is composed of three parts: a <xref:System.Activities.WorkflowIdentity.Name%2A> (<xref:System.String>), a <xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>), and a <xref:System.Activities.WorkflowIdentity.Package%2A> (<xref:System.String>).</span></span> <span data-ttu-id="9b0b7-118">Informace o <xref:System.Activities.WorkflowIdentity> použitý k vytvoření instance je vygenerován pro všechny nakonfigurované sledování životního cyklu služeb v několika různých fázích aktivity modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-118">Information about the <xref:System.Activities.WorkflowIdentity> used to create an instance is emitted to any configured tracking services at several different points of the activity life-cycle by the runtime.</span></span> <span data-ttu-id="9b0b7-119">Sledování WF nemá žádný mechanismus skrýt identifikovatelné osobní údaje (citlivými daty).</span><span class="sxs-lookup"><span data-stu-id="9b0b7-119">WF Tracking does not have any mechanism to hide PII (sensitive user data).</span></span> <span data-ttu-id="9b0b7-120">Proto <xref:System.Activities.WorkflowIdentity> instance by neměla obsahovat žádná data identifikovatelné osobní údaje, jak bude vygenerován modulem runtime ve sledování záznamů a mohou být viditelná pro každý, kdo má přístup k zobrazení záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-120">Therefore, a <xref:System.Activities.WorkflowIdentity> instance should not contain any PII data as it will be emitted by the runtime in tracking records and may be visible to anyone with access to view the tracking records.</span></span>  
  
### <a name="rules-for-hosting-multiple-versions-of-a-workflow-service"></a><span data-ttu-id="9b0b7-121">Pravidla pro hostování více verzí služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="9b0b7-121">Rules for Hosting Multiple Versions of a Workflow Service</span></span>  
 <span data-ttu-id="9b0b7-122">Pokud uživatel přidá další verze pro <xref:System.ServiceModel.Activities.WorkflowServiceHost>, existuje několik podmínek, které musí být splněny v pořadí pro službu pracovního postupu hostovat se stejnou sadu koncových bodů a popis.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-122">When a user adds an additional version to the <xref:System.ServiceModel.Activities.WorkflowServiceHost>, there are several conditions that must be met in order for a workflow service to be hosted with the same set of endpoints and description.</span></span> <span data-ttu-id="9b0b7-123">Pokud některé z dalších verzí splňovat tyto podmínky <xref:System.ServiceModel.Activities.WorkflowServiceHost> vyvolá výjimku při `Open` je volána.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-123">If any of the additional versions fail to meet these conditions, the <xref:System.ServiceModel.Activities.WorkflowServiceHost> throws an exception when `Open` is called.</span></span> <span data-ttu-id="9b0b7-124">Každá definice pracovního postupu, který je k dispozici na hostitele jako další verze musí splňovat následující požadavky (kde primární verze je definice služby pracovního postupu, který byl poskytnut konstruktor hostitele).</span><span class="sxs-lookup"><span data-stu-id="9b0b7-124">Each workflow definition provided to the host as an additional version must meet the following requirements (where the primary version is the workflow service definition that is provided to the host constructor).</span></span> <span data-ttu-id="9b0b7-125">Verze další pracovní postup musí:</span><span class="sxs-lookup"><span data-stu-id="9b0b7-125">The additional workflow version must:</span></span>  
  
- <span data-ttu-id="9b0b7-126">Mají stejné <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> jako primární verzí služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-126">Have the same the <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> as the primary version of the workflow service.</span></span>  
  
- <span data-ttu-id="9b0b7-127">Nesmí mít žádné <xref:System.ServiceModel.Activities.Receive> nebo <xref:System.ServiceModel.Activities.SendReply> aktivit v jeho <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> , které nejsou ve primárního verzi a musí se shodovat s kontrakt.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-127">Must not have any <xref:System.ServiceModel.Activities.Receive> or <xref:System.ServiceModel.Activities.SendReply> activities in its <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> that are not in the primary version, and they must match the operation contract.</span></span>  
  
- <span data-ttu-id="9b0b7-128">Mít jedinečnou <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-128">Have a unique <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span> <span data-ttu-id="9b0b7-129">Může mít jeden a pouze jeden definice pracovního postupu `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-129">One and only one workflow definition may have a `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span>  
  
 <span data-ttu-id="9b0b7-130">Některé změny nejsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-130">Some changes are permitted.</span></span> <span data-ttu-id="9b0b7-131">Následující položky se může lišit mezi verzemi:</span><span class="sxs-lookup"><span data-stu-id="9b0b7-131">The following items may be different between the versions:</span></span>  
  
- <span data-ttu-id="9b0b7-132"><xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> Může mít jiný název a balíček než primární verze.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-132">The <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> may have a different Name and Package than the primary version.</span></span>  
  
- <span data-ttu-id="9b0b7-133"><xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> Hodnota může být jiné než primární verze.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-133">The <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> value may be different than the primary version.</span></span>  
  
- <span data-ttu-id="9b0b7-134"><xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> Může být jiný než primární verze.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-134">The <xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> may be different than the primary version.</span></span>  
  
- <span data-ttu-id="9b0b7-135"><xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> Může být jiný než primární verze.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-135">The <xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> may be different than the primary version.</span></span>  
  
### <a name="configuring-the-definitionidentity"></a><span data-ttu-id="9b0b7-136">Konfigurace identitou DefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="9b0b7-136">Configuring the DefinitionIdentity</span></span>  
 <span data-ttu-id="9b0b7-137">Při vytvoření služby pracovních postupů pomocí návrháře postupu provádění <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> se nastavuje pomocí **vlastnosti** okna.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-137">When a workflow service is created using the workflow designer, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is set using the **Properties** window.</span></span> <span data-ttu-id="9b0b7-138">Klikněte na tlačítko mimo kořenová aktivita služby v Návrháři vyberte služby pracovního postupu a zvolte **okno vlastností** z **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-138">Click outside of the service’s root activity in the designer to select the workflow service, and choose **Properties Window** from the **View** menu.</span></span> <span data-ttu-id="9b0b7-139">Vyberte **identita WorkflowIdentity** z rozevíracího seznamu, který se zobrazí vedle **identitou DefinitionIdentity** vlastnosti, rozbalte položku a zadejte požadovaný <xref:System.Activities.WorkflowIdentity> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-139">Select **WorkflowIdentity** from the drop-down list that appears beside the **DefinitionIdentity** property, and then expand and specify the desired <xref:System.Activities.WorkflowIdentity> properties.</span></span> <span data-ttu-id="9b0b7-140">V následujícím příkladu <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> má nakonfigurovanou <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` a <xref:System.Activities.WorkflowIdentity.Version%2A> z `1.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-140">In the following example the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured with the <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Version%2A> of `1.0.0.0`.</span></span> <span data-ttu-id="9b0b7-141"><xref:System.Activities.WorkflowIdentity.Package%2A> je volitelný a v tomto příkladu je `null`.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-141"><xref:System.Activities.WorkflowIdentity.Package%2A> is optional and in this example is `null`.</span></span>  
  
 ![Snímek obrazovky s identitou DefinitionIdentity vlastnost.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-property.bmp)  
  
 <span data-ttu-id="9b0b7-143">Když je služba pracovního postupu v místním prostředí, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> je nakonfigurovaný, když se služba pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-143">When a workflow service is self-hosted, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured when the workflow service is constructed.</span></span> <span data-ttu-id="9b0b7-144">V následujícím příkladu <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> konfigurován pomocí stejné hodnoty jako předchozí příklad s <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` a <xref:System.Activities.WorkflowIdentity.Name%2A> z `1.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-144">In the following example, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured with the same values as the previous example, with the <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Name%2A> of `1.0.0.0`.</span></span>  
  
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
  
 <span data-ttu-id="9b0b7-145">A <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> není vyžadováno, ačkoli může mít pouze jednu verzi služby pracovního postupu **null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-145">A <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is not required, although only one version of the workflow service may have a **null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b0b7-146">To je užitečné, pokud služba byl zpočátku bez nasadit <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> nakonfigurované, a vytvoří aktualizovanou verzi.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-146">This is useful if the service was deployed initially without a <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> configured, and then an updated version is created.</span></span>  
  
### <a name="adding-a-new-version-to-a-web-hosted-workflow-service"></a><span data-ttu-id="9b0b7-147">Přidává se nová verze služby hostované webového pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="9b0b7-147">Adding a New Version to a Web-hosted Workflow Service</span></span>  
 <span data-ttu-id="9b0b7-148">Prvním krokem při konfiguraci nové verze služby pracovních postupů v hostované webové služby je vytvoření nové složky v `App_Code` složku, která má stejný název jako soubor služby.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-148">The first step in configuring a new version of a workflow service in a web-hosted service is to create a new folder in the `App_Code` folder that has the same name as the service file.</span></span> <span data-ttu-id="9b0b7-149">Pokud služby `xamlx` soubor `MortgageWorkflow.xamlx`, pak musí mít název složky `MortgageWorkflow`.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-149">If the service’s `xamlx` file is named `MortgageWorkflow.xamlx`, then the folder must be named `MortgageWorkflow`.</span></span> <span data-ttu-id="9b0b7-150">Umístěte kopii původní službě `xamlx` souboru do této složky a přejmenujte jej na nový název, jako například `MortgageWorkflowV1.xamlx`.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-150">Place a copy of the original service’s `xamlx` file into this folder and rename it to a new name, such as `MortgageWorkflowV1.xamlx`.</span></span> <span data-ttu-id="9b0b7-151">Proveďte požadované změny pro primární služby, aktualizujte její <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>a poté nasaďte službu.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-151">Make the desired changes to the primary service, update its <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, and then deploy the service.</span></span> <span data-ttu-id="9b0b7-152">V následujícím příkladu <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> byla aktualizována <xref:System.Activities.WorkflowIdentity.Name%2A> z `MortageWorkflow` a <xref:System.Activities.WorkflowIdentity.Version%2A> z `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-152">In the following example the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> has been updated with a <xref:System.Activities.WorkflowIdentity.Name%2A> of `MortageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Version%2A> of `2.0.0.0`.</span></span>  
  
 ![Snímek obrazovky s identitou DefinitionIdentity identita WorkflowIdentity.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-workflowidentity.bmp)  
  
 <span data-ttu-id="9b0b7-154">Po restartování služby předchozí verzi se automaticky přidají do <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekce vzhledem k tomu, že se nachází v určené `App_Code` podsložky.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-154">When the service restarts, the previous version will automatically be added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection because it is located in the designated `App_Code` subfolder.</span></span> <span data-ttu-id="9b0b7-155">Všimněte si, že pokud má primární verzí služby pracovního postupu `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> předchozích verzích se nepřidá.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-155">Note that if the primary version of the workflow service has a `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> the previous versions will not be added.</span></span> <span data-ttu-id="9b0b7-156">Může mít jednu verzi `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, ale pokud existuje více verzí primární verze nesmí být se `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> nebo jinak nepřidají do předchozí verze <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-156">One version may have a `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, but if there are multiple versions the primary version must not be the one with the `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> or else the previous versions will not be added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span>  
  
### <a name="adding-a-new-version-to-a-self-hosted-workflow-service"></a><span data-ttu-id="9b0b7-157">Přidává se nová verze služby pracovního postupu v místním prostředí</span><span class="sxs-lookup"><span data-stu-id="9b0b7-157">Adding a New Version to a Self-hosted Workflow Service</span></span>  
 <span data-ttu-id="9b0b7-158">Při přidávání nové verze služby pracovních postupů v místním prostředí, <xref:System.ServiceModel.Activities.WorkflowServiceHost> je nakonfigurována s primární verzí služby pracovního postupu a předchozí verze musí být explicitně přidán <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-158">When adding a new version to a self-hosted workflow service, the <xref:System.ServiceModel.Activities.WorkflowServiceHost> is configured with the primary version of the workflow service, and previous versions must be explicitly added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span> <span data-ttu-id="9b0b7-159">V následujícím příkladu <xref:System.ServiceModel.Activities.WorkflowServiceHost> má nakonfigurovanou primární pracovní postup služby, který používá `MortgageWorkflowV2` definice pracovního postupu a služby pracovních postupů nakonfigurovanou `MortgageWorkflowV1` definice pracovního postupu se přidá do <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-159">In the following example, a <xref:System.ServiceModel.Activities.WorkflowServiceHost> is configured with a primary workflow service that uses a `MortgageWorkflowV2` workflow definition, and a workflow service configured with a `MortgageWorkflowV1` workflow definition is added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span> <span data-ttu-id="9b0b7-160">Každý pracovní postup služba je nakonfigurována s jedinečným <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> , která odpovídá verzi modulu definice pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9b0b7-160">Each workflow service is configured with a unique <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> that reflects the version of the workflow definition.</span></span>  
  
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
