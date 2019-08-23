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
# <a name="side-by-side-versioning-in-workflowservicehost"></a>Práce s víc verzemi současně ve třídě WorkflowServiceHost
<xref:System.ServiceModel.Activities.WorkflowServiceHost> Souběžná Správa verzí zavedená v .NET Framework 4,5 poskytuje možnost hostovat více verzí služby pracovních postupů v jednom koncovém bodě. Funkce souběžného sdílení umožňuje nakonfigurovat službu pracovního postupu tak, aby se nové instance služby pracovního postupu vytvořily pomocí nové definice pracovního postupu, zatímco spuštěné instance se dokončí pomocí existující definice. Toto téma poskytuje přehled souběžného spouštění služby pracovního postupu pomocí nástroje <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
> [!NOTE]
> Pokud si chcete stáhnout ukázku a podívat se na video s návodem k souběžné verzi služby pracovního postupu, přečtěte si téma [Správa verzí vedle sebe pomocí služby pracovního postupu XAMLX na webu](https://go.microsoft.com/fwlink/?LinkId=393746).  
  
## <a name="hosting-multiple-versions-in-a-workflow-service"></a>Hostování více verzí ve službě pracovních postupů  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>obsahuje dvě vlastnosti, které je možné nakonfigurovat tak, aby umožňovaly souběžné provádění více verzí pracovního postupu: <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> a. <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A>obsahuje podporované verze služby pracovního postupu a <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> slouží k jednoznačné identifikaci jednotlivých služeb pracovního postupu. To se provádí přidružením <xref:System.Activities.WorkflowIdentity> ke službě pracovního postupu. A <xref:System.Activities.WorkflowIdentity> obsahuje tři identifikační údaje, které jsou k diskusy. <xref:System.Activities.WorkflowIdentity.Name%2A>a <xref:System.Activities.WorkflowIdentity.Version%2A> musí obsahovat název <xref:System.Version> a <xref:System.Activities.WorkflowIdentity.Package%2A> a a a je nepovinné a lze jej použít k určení dalšího řetězce obsahujícího informace, jako je například název sestavení nebo jiné požadované informace. Každá služba pracovního postupu obsažená <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> v kolekci musí mít jedinečný <xref:System.Activities.WorkflowIdentity>. Objekt <xref:System.Activities.WorkflowIdentity> je jedinečný, pokud se některá z jeho tří vlastností liší od <xref:System.Activities.WorkflowIdentity>jiného. A `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> `null` je povolená hodnota pro, ale může mít jenom jedna předchozí <xref:System.Activities.WorkflowIdentity>verze služby pracovního postupu. <xref:System.Activities.WorkflowIdentity>  
  
> [!IMPORTANT]
> <xref:System.Activities.WorkflowIdentity> By neměl obsahovat žádné identifikovatelné osobní údaje (PII). <xref:System.Activities.WorkflowIdentity>se skládá ze tří částí: a <xref:System.Activities.WorkflowIdentity.Name%2A> (<xref:System.String>), a <xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>), a <xref:System.Activities.WorkflowIdentity.Package%2A> a (<xref:System.String>). Informace o <xref:System.Activities.WorkflowIdentity> použití pro vytvoření instance jsou generovány do všech nakonfigurovaných služeb sledování v několika různých místech životního cyklu aktivity modulem runtime. Sledování WF nemá žádný mechanismus pro skrytí PII (citlivých uživatelských dat). <xref:System.Activities.WorkflowIdentity> Instance by proto neměla obsahovat žádná data PII, protože bude vygenerována modulem runtime ve sledování záznamů a může být viditelná pro kohokoli s přístupem k zobrazení záznamů sledování.  
  
### <a name="rules-for-hosting-multiple-versions-of-a-workflow-service"></a>Pravidla pro hostování více verzí služby pracovního postupu  
 Když uživatel přidá k <xref:System.ServiceModel.Activities.WorkflowServiceHost>portálu další verzi, existuje několik podmínek, které je potřeba splnit, aby se služba pracovního postupu mohla hostovat se stejnou sadou koncových bodů a popisu. Pokud kterákoli z dalších verzí selže při splnění těchto podmínek, <xref:System.ServiceModel.Activities.WorkflowServiceHost> vyvolá výjimku při `Open` volání metody. Každá definice pracovního postupu poskytnutá hostiteli jako další verze musí splňovat následující požadavky (kde primární verze je definice služby pracovního postupu, která je k dispozici pro konstruktor hostitele). Další verze pracovního postupu musí:  
  
- Mít stejné <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> jako primární verze služby pracovního postupu.  
  
- Nesmí mít žádné <xref:System.ServiceModel.Activities.Receive> aktivity ani <xref:System.ServiceModel.Activities.SendReply> aktivity <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> , které nejsou v primární verzi, a musí se shodovat s kontraktem operace.  
  
- Mít jedinečný <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>. Jedna definice pracovního postupu může mít jednu z `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>nich.  
  
 Některé změny jsou povoleny. Mezi verzemi se můžou lišit tyto položky:  
  
- <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> Může mít jiný název a balíček než primární verze.  
  
- <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> Hodnota se může lišit od primární verze.  
  
- <xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> Může se lišit od primární verze.  
  
- <xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> Může se lišit od primární verze.  
  
### <a name="configuring-the-definitionidentity"></a>Konfigurace identitou DefinitionIdentity  
 <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> Je-li služba pracovního postupu vytvořena pomocí návrháře pracovních postupů, je nastavena pomocí okna **vlastnosti** . Kliknutím mimo kořenovou aktivitu služby v návrháři vyberte službu pracovního postupu a v nabídce **zobrazení** zvolte **okno Vlastnosti** . V rozevíracím seznamu, který se zobrazí vedle vlastnosti **identitou DefinitionIdentity** , vyberte <xref:System.Activities.WorkflowIdentity> **Identita WorkflowIdentity** a potom rozbalte a zadejte požadované vlastnosti. V následujícím <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> příkladu je nakonfigurován `MortgageWorkflow` <xref:System.Activities.WorkflowIdentity.Name%2A> s a a <xref:System.Activities.WorkflowIdentity.Version%2A> `1.0.0.0`. <xref:System.Activities.WorkflowIdentity.Package%2A>je volitelný a v tomto příkladu je `null`.  
  
 ![Snímek obrazovky zobrazující vlastnost identitou DefinitionIdentity](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-property.bmp)  
  
 Když je služba pracovního postupu v místním prostředí hostována <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> , je konfigurována při vytvoření služby pracovního postupu. <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> V následujícím příkladu je nakonfigurován se stejnými hodnotami jako v předchozím příkladu `MortgageWorkflow` <xref:System.Activities.WorkflowIdentity.Name%2A> s a a <xref:System.Activities.WorkflowIdentity.Name%2A>. `1.0.0.0`  
  
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
  
 A <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> není vyžadován, i když pouze jedna verze služby pracovního postupu může mít **hodnotu null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.  
  
> [!NOTE]
> To je užitečné, pokud byla služba nasazena zpočátku bez <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> nakonfigurovaného a pak je vytvořena aktualizovaná verze.  
  
### <a name="adding-a-new-version-to-a-web-hosted-workflow-service"></a>Přidání nové verze do služby pracovního postupu hostovaného na webu  
 Prvním krokem při konfiguraci nové verze služby pracovního postupu v rámci služby hostované na webu je vytvoření nové složky ve `App_Code` složce, která má stejný název jako soubor služby. Pokud má `xamlx` soubor služby název `MortgageWorkflow.xamlx`, musí být tato složka pojmenována `MortgageWorkflow`. Do této složky umístěte kopii `xamlx` souboru původní služby a přejmenujte ji na nový název, `MortgageWorkflowV1.xamlx`třeba. Proveďte požadované změny primární služby, aktualizujte její <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>a potom nasaďte službu. V následujícím <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> příkladu byl aktualizován `MortgageWorkflow` <xref:System.Activities.WorkflowIdentity.Name%2A> pomocí a a <xref:System.Activities.WorkflowIdentity.Version%2A> `2.0.0.0`.  
  
 ![Snímek obrazovky zobrazující identitou DefinitionIdentity z identita WorkflowIdentity](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-workflowidentity.bmp)  
  
 Po restartování služby bude předchozí verze automaticky přidána do <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekce, protože je umístěna v určené `App_Code` podsložce. Všimněte si, že pokud primární verze služby pracovního postupu má `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> , nebudou přidány předchozí verze. Jedna verze `null`může mít <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, ale v případě, že existuje více verzí, primární verze nesmí `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> být součástí, <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> nebo jinak nebudou předchozí verze do kolekce přidány.  
  
### <a name="adding-a-new-version-to-a-self-hosted-workflow-service"></a>Přidání nové verze do samoobslužné služby pracovních postupů  
 Když přidáváte novou verzi do samoobslužné služby pracovního postupu, <xref:System.ServiceModel.Activities.WorkflowServiceHost> je nakonfigurovaná s primární verzí služby pracovního postupu a předchozí verze musí být explicitně přidané <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> do kolekce. V následujícím příkladu <xref:System.ServiceModel.Activities.WorkflowServiceHost> je nakonfigurovaná pomocí primární služby pracovního postupu, která `MortgageWorkflowV2` používá definici pracovního postupu, a do <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekce se přidá služba `MortgageWorkflowV1` pracovního postupu nakonfigurovaná s definicí pracovního postupu. Každá služba pracovního postupu je nakonfigurovaná s <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> jedinečným, který odráží verzi definice pracovního postupu.  
  
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
