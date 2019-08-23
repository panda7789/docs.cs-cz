---
title: Práce s víc verzemi současně ve třídě WorkflowServiceHost
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 60887eed-df40-4412-b812-41e1dd329d15
ms.openlocfilehash: ba0bcdf152ab0ee6632ae472db0bc81496cb6381
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969227"
---
# <a name="side-by-side-versioning-in-workflowservicehost"></a><span data-ttu-id="10450-102">Práce s víc verzemi současně ve třídě WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="10450-102">Side by Side Versioning in WorkflowServiceHost</span></span>
<span data-ttu-id="10450-103"><xref:System.ServiceModel.Activities.WorkflowServiceHost> Souběžná Správa verzí zavedená v .NET Framework 4,5 poskytuje možnost hostovat více verzí služby pracovních postupů v jednom koncovém bodě.</span><span class="sxs-lookup"><span data-stu-id="10450-103">The <xref:System.ServiceModel.Activities.WorkflowServiceHost> side-by-side versioning introduced in .NET Framework 4.5 provides the capability to host multiple versions of a workflow service on a single endpoint.</span></span> <span data-ttu-id="10450-104">Funkce souběžného sdílení umožňuje nakonfigurovat službu pracovního postupu tak, aby se nové instance služby pracovního postupu vytvořily pomocí nové definice pracovního postupu, zatímco spuštěné instance se dokončí pomocí existující definice.</span><span class="sxs-lookup"><span data-stu-id="10450-104">The side-by-side functionality provided allows a workflow service to be configured so that new instances of the workflow service are created using the new workflow definition, while running instances complete using the existing definition.</span></span> <span data-ttu-id="10450-105">Toto téma poskytuje přehled souběžného spouštění služby pracovního postupu pomocí nástroje <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="10450-105">This topic provides an overview of workflow service side-by-side execution using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="10450-106">Pokud si chcete stáhnout ukázku a podívat se na video s návodem k souběžné verzi služby pracovního postupu, přečtěte si téma [Správa verzí vedle sebe pomocí služby pracovního postupu XAMLX na webu](https://go.microsoft.com/fwlink/?LinkId=393746).</span><span class="sxs-lookup"><span data-stu-id="10450-106">To download a sample and watch a video walkthrough of workflow service side-by-side versioning, see [Side by Side Versioning with a Web-Hosted Xamlx Workflow Service](https://go.microsoft.com/fwlink/?LinkId=393746).</span></span>  
  
## <a name="hosting-multiple-versions-in-a-workflow-service"></a><span data-ttu-id="10450-107">Hostování více verzí ve službě pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="10450-107">Hosting Multiple Versions in a Workflow Service</span></span>  
 <span data-ttu-id="10450-108"><xref:System.ServiceModel.Activities.WorkflowServiceHost>obsahuje dvě vlastnosti, které je možné nakonfigurovat tak, aby umožňovaly souběžné provádění více verzí pracovního postupu: <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> a. <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A></span><span class="sxs-lookup"><span data-stu-id="10450-108"><xref:System.ServiceModel.Activities.WorkflowServiceHost> contains two properties that can be configured to allow multiple versions of a workflow to execute side-by-side: <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> and <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span> <span data-ttu-id="10450-109"><xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A>obsahuje podporované verze služby pracovního postupu a <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> slouží k jednoznačné identifikaci jednotlivých služeb pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="10450-109"><xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> contains the supported versions of the workflow service, and <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is used to uniquely identify each workflow service.</span></span> <span data-ttu-id="10450-110">To se provádí přidružením <xref:System.Activities.WorkflowIdentity> ke službě pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="10450-110">This is done by associating a <xref:System.Activities.WorkflowIdentity> with the workflow service.</span></span> <span data-ttu-id="10450-111">A <xref:System.Activities.WorkflowIdentity> obsahuje tři identifikační údaje, které jsou k diskusy.</span><span class="sxs-lookup"><span data-stu-id="10450-111">A <xref:System.Activities.WorkflowIdentity> contains three identifying pieces of information.</span></span> <span data-ttu-id="10450-112"><xref:System.Activities.WorkflowIdentity.Name%2A>a <xref:System.Activities.WorkflowIdentity.Version%2A> musí obsahovat název <xref:System.Version> a <xref:System.Activities.WorkflowIdentity.Package%2A> a a a je nepovinné a lze jej použít k určení dalšího řetězce obsahujícího informace, jako je například název sestavení nebo jiné požadované informace.</span><span class="sxs-lookup"><span data-stu-id="10450-112"><xref:System.Activities.WorkflowIdentity.Name%2A> and <xref:System.Activities.WorkflowIdentity.Version%2A> contain a name and a <xref:System.Version> and are required, and <xref:System.Activities.WorkflowIdentity.Package%2A> is optional and can be used to specify an additional string containing information such as assembly name or other desired information.</span></span> <span data-ttu-id="10450-113">Každá služba pracovního postupu obsažená <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> v kolekci musí mít jedinečný <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="10450-113">Each workflow service contained in the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection must have a unique <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="10450-114">Objekt <xref:System.Activities.WorkflowIdentity> je jedinečný, pokud se některá z jeho tří vlastností liší od <xref:System.Activities.WorkflowIdentity>jiného.</span><span class="sxs-lookup"><span data-stu-id="10450-114">A <xref:System.Activities.WorkflowIdentity> is unique if any of its three properties are different from another <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="10450-115">A `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> `null` je povolená hodnota pro, ale může mít jenom jedna předchozí <xref:System.Activities.WorkflowIdentity>verze služby pracovního postupu. <xref:System.Activities.WorkflowIdentity></span><span class="sxs-lookup"><span data-stu-id="10450-115">A `null` <xref:System.Activities.WorkflowIdentity> is an allowable value for <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, but only one previous version of a workflow service may have a `null` <xref:System.Activities.WorkflowIdentity>.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="10450-116"><xref:System.Activities.WorkflowIdentity> By neměl obsahovat žádné identifikovatelné osobní údaje (PII).</span><span class="sxs-lookup"><span data-stu-id="10450-116">A <xref:System.Activities.WorkflowIdentity> should not contain any personally identifiable information (PII).</span></span> <span data-ttu-id="10450-117"><xref:System.Activities.WorkflowIdentity>se skládá ze tří částí: a <xref:System.Activities.WorkflowIdentity.Name%2A> (<xref:System.String>), a <xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>), a <xref:System.Activities.WorkflowIdentity.Package%2A> a (<xref:System.String>).</span><span class="sxs-lookup"><span data-stu-id="10450-117"><xref:System.Activities.WorkflowIdentity> is composed of three parts: a <xref:System.Activities.WorkflowIdentity.Name%2A> (<xref:System.String>), a <xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>), and a <xref:System.Activities.WorkflowIdentity.Package%2A> (<xref:System.String>).</span></span> <span data-ttu-id="10450-118">Informace o <xref:System.Activities.WorkflowIdentity> použití pro vytvoření instance jsou generovány do všech nakonfigurovaných služeb sledování v několika různých místech životního cyklu aktivity modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="10450-118">Information about the <xref:System.Activities.WorkflowIdentity> used to create an instance is emitted to any configured tracking services at several different points of the activity life-cycle by the runtime.</span></span> <span data-ttu-id="10450-119">Sledování WF nemá žádný mechanismus pro skrytí PII (citlivých uživatelských dat).</span><span class="sxs-lookup"><span data-stu-id="10450-119">WF Tracking does not have any mechanism to hide PII (sensitive user data).</span></span> <span data-ttu-id="10450-120"><xref:System.Activities.WorkflowIdentity> Instance by proto neměla obsahovat žádná data PII, protože bude vygenerována modulem runtime ve sledování záznamů a může být viditelná pro kohokoli s přístupem k zobrazení záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="10450-120">Therefore, a <xref:System.Activities.WorkflowIdentity> instance should not contain any PII data as it will be emitted by the runtime in tracking records and may be visible to anyone with access to view the tracking records.</span></span>  
  
### <a name="rules-for-hosting-multiple-versions-of-a-workflow-service"></a><span data-ttu-id="10450-121">Pravidla pro hostování více verzí služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="10450-121">Rules for Hosting Multiple Versions of a Workflow Service</span></span>  
 <span data-ttu-id="10450-122">Když uživatel přidá k <xref:System.ServiceModel.Activities.WorkflowServiceHost>portálu další verzi, existuje několik podmínek, které je potřeba splnit, aby se služba pracovního postupu mohla hostovat se stejnou sadou koncových bodů a popisu.</span><span class="sxs-lookup"><span data-stu-id="10450-122">When a user adds an additional version to the <xref:System.ServiceModel.Activities.WorkflowServiceHost>, there are several conditions that must be met in order for a workflow service to be hosted with the same set of endpoints and description.</span></span> <span data-ttu-id="10450-123">Pokud kterákoli z dalších verzí selže při splnění těchto podmínek, <xref:System.ServiceModel.Activities.WorkflowServiceHost> vyvolá výjimku při `Open` volání metody.</span><span class="sxs-lookup"><span data-stu-id="10450-123">If any of the additional versions fail to meet these conditions, the <xref:System.ServiceModel.Activities.WorkflowServiceHost> throws an exception when `Open` is called.</span></span> <span data-ttu-id="10450-124">Každá definice pracovního postupu poskytnutá hostiteli jako další verze musí splňovat následující požadavky (kde primární verze je definice služby pracovního postupu, která je k dispozici pro konstruktor hostitele).</span><span class="sxs-lookup"><span data-stu-id="10450-124">Each workflow definition provided to the host as an additional version must meet the following requirements (where the primary version is the workflow service definition that is provided to the host constructor).</span></span> <span data-ttu-id="10450-125">Další verze pracovního postupu musí:</span><span class="sxs-lookup"><span data-stu-id="10450-125">The additional workflow version must:</span></span>  
  
- <span data-ttu-id="10450-126">Mít stejné <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> jako primární verze služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="10450-126">Have the same the <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> as the primary version of the workflow service.</span></span>  
  
- <span data-ttu-id="10450-127">Nesmí mít žádné <xref:System.ServiceModel.Activities.Receive> aktivity ani <xref:System.ServiceModel.Activities.SendReply> aktivity <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> , které nejsou v primární verzi, a musí se shodovat s kontraktem operace.</span><span class="sxs-lookup"><span data-stu-id="10450-127">Must not have any <xref:System.ServiceModel.Activities.Receive> or <xref:System.ServiceModel.Activities.SendReply> activities in its <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> that are not in the primary version, and they must match the operation contract.</span></span>  
  
- <span data-ttu-id="10450-128">Mít jedinečný <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="10450-128">Have a unique <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span> <span data-ttu-id="10450-129">Jedna definice pracovního postupu může mít jednu z `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>nich.</span><span class="sxs-lookup"><span data-stu-id="10450-129">One and only one workflow definition may have a `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span>  
  
 <span data-ttu-id="10450-130">Některé změny jsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="10450-130">Some changes are permitted.</span></span> <span data-ttu-id="10450-131">Mezi verzemi se můžou lišit tyto položky:</span><span class="sxs-lookup"><span data-stu-id="10450-131">The following items may be different between the versions:</span></span>  
  
- <span data-ttu-id="10450-132"><xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> Může mít jiný název a balíček než primární verze.</span><span class="sxs-lookup"><span data-stu-id="10450-132">The <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> may have a different Name and Package than the primary version.</span></span>  
  
- <span data-ttu-id="10450-133"><xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> Hodnota se může lišit od primární verze.</span><span class="sxs-lookup"><span data-stu-id="10450-133">The <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> value may be different than the primary version.</span></span>  
  
- <span data-ttu-id="10450-134"><xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> Může se lišit od primární verze.</span><span class="sxs-lookup"><span data-stu-id="10450-134">The <xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> may be different than the primary version.</span></span>  
  
- <span data-ttu-id="10450-135"><xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> Může se lišit od primární verze.</span><span class="sxs-lookup"><span data-stu-id="10450-135">The <xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> may be different than the primary version.</span></span>  
  
### <a name="configuring-the-definitionidentity"></a><span data-ttu-id="10450-136">Konfigurace identitou DefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="10450-136">Configuring the DefinitionIdentity</span></span>  
 <span data-ttu-id="10450-137"><xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> Je-li služba pracovního postupu vytvořena pomocí návrháře pracovních postupů, je nastavena pomocí okna **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="10450-137">When a workflow service is created using the workflow designer, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is set using the **Properties** window.</span></span> <span data-ttu-id="10450-138">Kliknutím mimo kořenovou aktivitu služby v návrháři vyberte službu pracovního postupu a v nabídce **zobrazení** zvolte **okno Vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="10450-138">Click outside of the service’s root activity in the designer to select the workflow service, and choose **Properties Window** from the **View** menu.</span></span> <span data-ttu-id="10450-139">V rozevíracím seznamu, který se zobrazí vedle vlastnosti **identitou DefinitionIdentity** , vyberte <xref:System.Activities.WorkflowIdentity> **Identita WorkflowIdentity** a potom rozbalte a zadejte požadované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="10450-139">Select **WorkflowIdentity** from the drop-down list that appears beside the **DefinitionIdentity** property, and then expand and specify the desired <xref:System.Activities.WorkflowIdentity> properties.</span></span> <span data-ttu-id="10450-140">V následujícím <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> příkladu je nakonfigurován `MortgageWorkflow` <xref:System.Activities.WorkflowIdentity.Name%2A> s a a <xref:System.Activities.WorkflowIdentity.Version%2A> `1.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="10450-140">In the following example the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured with the <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Version%2A> of `1.0.0.0`.</span></span> <span data-ttu-id="10450-141"><xref:System.Activities.WorkflowIdentity.Package%2A>je volitelný a v tomto příkladu je `null`.</span><span class="sxs-lookup"><span data-stu-id="10450-141"><xref:System.Activities.WorkflowIdentity.Package%2A> is optional and in this example is `null`.</span></span>  
  
 ![Snímek obrazovky zobrazující vlastnost identitou DefinitionIdentity](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-property.bmp)  
  
 <span data-ttu-id="10450-143">Když je služba pracovního postupu v místním prostředí hostována <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> , je konfigurována při vytvoření služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="10450-143">When a workflow service is self-hosted, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured when the workflow service is constructed.</span></span> <span data-ttu-id="10450-144"><xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> V následujícím příkladu je nakonfigurován se stejnými hodnotami jako v předchozím příkladu `MortgageWorkflow` <xref:System.Activities.WorkflowIdentity.Name%2A> s a a <xref:System.Activities.WorkflowIdentity.Name%2A>. `1.0.0.0`</span><span class="sxs-lookup"><span data-stu-id="10450-144">In the following example, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured with the same values as the previous example, with the <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Name%2A> of `1.0.0.0`.</span></span>  
  
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
  
 <span data-ttu-id="10450-145">A <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> není vyžadován, i když pouze jedna verze služby pracovního postupu může mít **hodnotu null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="10450-145">A <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is not required, although only one version of the workflow service may have a **null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="10450-146">To je užitečné, pokud byla služba nasazena zpočátku bez <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> nakonfigurovaného a pak je vytvořena aktualizovaná verze.</span><span class="sxs-lookup"><span data-stu-id="10450-146">This is useful if the service was deployed initially without a <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> configured, and then an updated version is created.</span></span>  
  
### <a name="adding-a-new-version-to-a-web-hosted-workflow-service"></a><span data-ttu-id="10450-147">Přidání nové verze do služby pracovního postupu hostovaného na webu</span><span class="sxs-lookup"><span data-stu-id="10450-147">Adding a New Version to a Web-hosted Workflow Service</span></span>  
 <span data-ttu-id="10450-148">Prvním krokem při konfiguraci nové verze služby pracovního postupu v rámci služby hostované na webu je vytvoření nové složky ve `App_Code` složce, která má stejný název jako soubor služby.</span><span class="sxs-lookup"><span data-stu-id="10450-148">The first step in configuring a new version of a workflow service in a web-hosted service is to create a new folder in the `App_Code` folder that has the same name as the service file.</span></span> <span data-ttu-id="10450-149">Pokud má `xamlx` soubor služby název `MortgageWorkflow.xamlx`, musí být tato složka pojmenována `MortgageWorkflow`.</span><span class="sxs-lookup"><span data-stu-id="10450-149">If the service’s `xamlx` file is named `MortgageWorkflow.xamlx`, then the folder must be named `MortgageWorkflow`.</span></span> <span data-ttu-id="10450-150">Do této složky umístěte kopii `xamlx` souboru původní služby a přejmenujte ji na nový název, `MortgageWorkflowV1.xamlx`třeba.</span><span class="sxs-lookup"><span data-stu-id="10450-150">Place a copy of the original service’s `xamlx` file into this folder and rename it to a new name, such as `MortgageWorkflowV1.xamlx`.</span></span> <span data-ttu-id="10450-151">Proveďte požadované změny primární služby, aktualizujte její <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>a potom nasaďte službu.</span><span class="sxs-lookup"><span data-stu-id="10450-151">Make the desired changes to the primary service, update its <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, and then deploy the service.</span></span> <span data-ttu-id="10450-152">V následujícím <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> příkladu byl aktualizován `MortgageWorkflow` <xref:System.Activities.WorkflowIdentity.Name%2A> pomocí a a <xref:System.Activities.WorkflowIdentity.Version%2A> `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="10450-152">In the following example the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> has been updated with a <xref:System.Activities.WorkflowIdentity.Name%2A> of `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Version%2A> of `2.0.0.0`.</span></span>  
  
 ![Snímek obrazovky zobrazující identitou DefinitionIdentity z identita WorkflowIdentity](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-workflowidentity.bmp)  
  
 <span data-ttu-id="10450-154">Po restartování služby bude předchozí verze automaticky přidána do <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekce, protože je umístěna v určené `App_Code` podsložce.</span><span class="sxs-lookup"><span data-stu-id="10450-154">When the service restarts, the previous version will automatically be added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection because it is located in the designated `App_Code` subfolder.</span></span> <span data-ttu-id="10450-155">Všimněte si, že pokud primární verze služby pracovního postupu má `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> , nebudou přidány předchozí verze.</span><span class="sxs-lookup"><span data-stu-id="10450-155">Note that if the primary version of the workflow service has a `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> the previous versions will not be added.</span></span> <span data-ttu-id="10450-156">Jedna verze `null`může mít <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, ale v případě, že existuje více verzí, primární verze nesmí `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> být součástí, <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> nebo jinak nebudou předchozí verze do kolekce přidány.</span><span class="sxs-lookup"><span data-stu-id="10450-156">One version may have a `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, but if there are multiple versions the primary version must not be the one with the `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> or else the previous versions will not be added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span>  
  
### <a name="adding-a-new-version-to-a-self-hosted-workflow-service"></a><span data-ttu-id="10450-157">Přidání nové verze do samoobslužné služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="10450-157">Adding a New Version to a Self-hosted Workflow Service</span></span>  
 <span data-ttu-id="10450-158">Když přidáváte novou verzi do samoobslužné služby pracovního postupu, <xref:System.ServiceModel.Activities.WorkflowServiceHost> je nakonfigurovaná s primární verzí služby pracovního postupu a předchozí verze musí být explicitně přidané <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> do kolekce.</span><span class="sxs-lookup"><span data-stu-id="10450-158">When adding a new version to a self-hosted workflow service, the <xref:System.ServiceModel.Activities.WorkflowServiceHost> is configured with the primary version of the workflow service, and previous versions must be explicitly added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span> <span data-ttu-id="10450-159">V následujícím příkladu <xref:System.ServiceModel.Activities.WorkflowServiceHost> je nakonfigurovaná pomocí primární služby pracovního postupu, která `MortgageWorkflowV2` používá definici pracovního postupu, a do <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekce se přidá služba `MortgageWorkflowV1` pracovního postupu nakonfigurovaná s definicí pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="10450-159">In the following example, a <xref:System.ServiceModel.Activities.WorkflowServiceHost> is configured with a primary workflow service that uses a `MortgageWorkflowV2` workflow definition, and a workflow service configured with a `MortgageWorkflowV1` workflow definition is added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span> <span data-ttu-id="10450-160">Každá služba pracovního postupu je nakonfigurovaná s <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> jedinečným, který odráží verzi definice pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="10450-160">Each workflow service is configured with a unique <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> that reflects the version of the workflow definition.</span></span>  
  
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
