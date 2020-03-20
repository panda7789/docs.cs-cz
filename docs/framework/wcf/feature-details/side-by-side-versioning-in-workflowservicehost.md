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
# <a name="side-by-side-versioning-in-workflowservicehost"></a>Práce s víc verzemi současně ve třídě WorkflowServiceHost
Souběžná <xref:System.ServiceModel.Activities.WorkflowServiceHost> správa verzí zavedená v rozhraní .NET Framework 4.5 poskytuje možnost hostovat více verzí služby pracovního postupu v jednom koncovém bodě. Poskytovaná funkce vedle sebe umožňuje konfiguraci služby pracovního postupu tak, aby byly vytvořeny nové instance služby pracovního postupu pomocí nové definice pracovního postupu, zatímco spuštěné instance byly dokončeny pomocí existující definice. Toto téma obsahuje přehled služby pracovního <xref:System.ServiceModel.Activities.WorkflowServiceHost>postupu souběžné spuštění pomocí .  
  
> [!NOTE]
> Chcete-li stáhnout ukázku a podívat se na video návod ke službě pracovního postupu vedle sebe, přečtěte si informace [o správě verzí vedle sebe pomocí služby Xamlx Workflow Service hostované na webu](https://go.microsoft.com/fwlink/?LinkId=393746).  
  
## <a name="hosting-multiple-versions-in-a-workflow-service"></a>Hostování více verzí ve službě pracovního postupu  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>obsahuje dvě vlastnosti, které lze nakonfigurovat tak, aby umožňovaly <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> provádění <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>více verzí pracovního postupu vedle sebe: a . <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A>obsahuje podporované verze služby pracovního <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> postupu a slouží k jednoznačné identifikaci jednotlivých služeb pracovního postupu. To se provádí tak, že <xref:System.Activities.WorkflowIdentity> se přizpůsobujete službě pracovního postupu. A <xref:System.Activities.WorkflowIdentity> obsahuje tři identifikační informace. <xref:System.Activities.WorkflowIdentity.Name%2A>a <xref:System.Activities.WorkflowIdentity.Version%2A> obsahují název <xref:System.Version> a a a <xref:System.Activities.WorkflowIdentity.Package%2A> jsou povinné a je volitelné a lze použít k určení další řetězec obsahující informace, jako je název sestavení nebo jiné požadované informace. Každá služba pracovního <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> postupu obsažená <xref:System.Activities.WorkflowIdentity>v kolekci musí mít jedinečný . A <xref:System.Activities.WorkflowIdentity> je jedinečný, pokud některý z <xref:System.Activities.WorkflowIdentity>jeho tří vlastností se liší od jiného . A `null` <xref:System.Activities.WorkflowIdentity> je přípustná <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>hodnota pro , ale pouze jedna předchozí `null` <xref:System.Activities.WorkflowIdentity>verze služby pracovního postupu může mít .  
  
> [!IMPORTANT]
> A <xref:System.Activities.WorkflowIdentity> by nemělobsahovat žádné osobně identifikovatelné informace (PII). <xref:System.Activities.WorkflowIdentity>se skládá ze tří <xref:System.Activities.WorkflowIdentity.Name%2A> <xref:System.String>částí: <xref:System.Activities.WorkflowIdentity.Version%2A> <xref:System.Version>a ( <xref:System.Activities.WorkflowIdentity.Package%2A> <xref:System.String>), a ( ), a a ( ). Informace o <xref:System.Activities.WorkflowIdentity> použité k vytvoření instance jsou vyzařovány všem nakonfigurovaným sledovacím službám v několika různých bodech životního cyklu aktivity v době běhu. Sledování WF nemá žádný mechanismus pro skrytí PII (citlivá uživatelská data). <xref:System.Activities.WorkflowIdentity> Instance by proto neměla obsahovat žádná data PII, protože bude vyzařována za běhu v záznamech sledování a může být viditelná pro všechny osoby s přístupem k zobrazení záznamů sledování.  
  
### <a name="rules-for-hosting-multiple-versions-of-a-workflow-service"></a>Pravidla pro hostování více verzí služby pracovního postupu  
 Když uživatel přidá další verzi <xref:System.ServiceModel.Activities.WorkflowServiceHost>, existuje několik podmínek, které musí být splněny, aby služba pracovního postupu, které mají být hostovány se stejnou sadou koncových bodů a popis. Pokud některá z dalších verzí nesplňují <xref:System.ServiceModel.Activities.WorkflowServiceHost> tyto podmínky, `Open` vyvolá výjimku při volání. Každá definice pracovního postupu poskytnutá hostiteli jako další verze musí splňovat následující požadavky (kde primární verze je definice služby pracovního postupu, která je poskytována konstruktoru hostitele). Další verze pracovního postupu musí:  
  
- Mají stejné <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> jako primární verze služby pracovního postupu.  
  
- Nesmí mít <xref:System.ServiceModel.Activities.Receive> žádné <xref:System.ServiceModel.Activities.SendReply> nebo <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> aktivity v jeho, které nejsou v primární verzi a musí odpovídat smlouvy operace.  
  
- Mít jedinečný <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>. Jedna a pouze jedna definice `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>pracovního postupu může mít .  
  
 Některé změny jsou povoleny. Následující položky se mohou lišit mezi verzemi:  
  
- Může <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> mít jiný název a balíček než primární verze.  
  
- Hodnota <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> se může lišit od primární verze.  
  
- Může <xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> být jiný než primární verze.  
  
- Může <xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> být jiný než primární verze.  
  
### <a name="configuring-the-definitionidentity"></a>Konfigurace identity DefinitionIdentity  
 Když je služba pracovního postupu vytvořena <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> pomocí návrháře pracovního postupu, je nastavena pomocí okna **Vlastnosti.** Kliknutím mimo kořenovou aktivitu služby v návrháři vyberte službu pracovního postupu a z nabídky **Zobrazení** zvolte **Okno vlastnosti.** V rozevíracím seznamu, který se zobrazí vedle **vlastnosti DefinitionIdentity,** vyberte příkaz <xref:System.Activities.WorkflowIdentity> **WorkflowIdentity** a potom rozbalte a zadejte požadované vlastnosti. V <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> následujícím příkladu je <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` nakonfigurován <xref:System.Activities.WorkflowIdentity.Version%2A> `1.0.0.0`s a a . <xref:System.Activities.WorkflowIdentity.Package%2A>je nepovinný a `null`v tomto příkladu je .  
  
 ![Snímek obrazovky, který zobrazuje vlastnost DefinitionIdentity.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-property.bmp)  
  
 Pokud je služba pracovního postupu <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> hostována samostatně, je nakonfigurována při vytváření služby pracovního postupu. V následujícím příkladu <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> je nakonfigurován se stejnými hodnotami <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` jako <xref:System.Activities.WorkflowIdentity.Name%2A> `1.0.0.0`v předchozím příkladu s a a .  
  
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
  
 A <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> není vyžadováno, i když pouze jedna verze služby pracovního postupu může mít **null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.  
  
> [!NOTE]
> To je užitečné, pokud byla služba <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> nasazena zpočátku bez nakonfigurované a pak je vytvořena aktualizovaná verze.  
  
### <a name="adding-a-new-version-to-a-web-hosted-workflow-service"></a>Přidání nové verze do služby pracovního postupu hostované na webu  
 Prvním krokem při konfiguraci nové verze služby pracovního postupu ve službě hostované `App_Code` ve webovém provozu je vytvoření nové složky ve složce, která má stejný název jako soubor služby. Pokud je soubor `xamlx` služby `MortgageWorkflow.xamlx`pojmenován , musí `MortgageWorkflow`být složka pojmenována . Umístěte kopii `xamlx` souboru původní služby do této složky a přejmenujte ji na nový název, například `MortgageWorkflowV1.xamlx`. Proveďte požadované změny primární služby, aktualizujte její <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>a potom službu nasaďte. V následujícím příkladu <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> byla aktualizována s a <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` a a . `2.0.0.0` <xref:System.Activities.WorkflowIdentity.Version%2A>  
  
 ![Snímek obrazovky, který zobrazuje DefinitionIdentity of WorkflowIdentity.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-workflowidentity.bmp)  
  
 Po restartování služby bude předchozí verze automaticky <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> přidána do kolekce, `App_Code` protože je umístěna v určené podsložce. Všimněte si, že pokud má `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> primární verze služby pracovního postupu předchozí verze nebudou přidány. Jedna verze může `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>mít , ale pokud existuje více verzí, primární `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> verze nesmí být ta s nebo <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> jinak předchozí verze nebudou přidány do kolekce.  
  
### <a name="adding-a-new-version-to-a-self-hosted-workflow-service"></a>Přidání nové verze do služby pracovního postupu hostované samostatně  
 Při přidávání nové verze do služby pracovního postupu hostované ho s vlastním hostitelem <xref:System.ServiceModel.Activities.WorkflowServiceHost> je nakonfigurován <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> a primární verze služby pracovního postupu a předchozí verze musí být explicitně přidány do kolekce. V následujícím příkladu <xref:System.ServiceModel.Activities.WorkflowServiceHost> je a nakonfigurován s `MortgageWorkflowV2` primární službou pracovního postupu, `MortgageWorkflowV1` která používá definici pracovního postupu, a do <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekce je přidána služba pracovního postupu nakonfigurovaná s definicí pracovního postupu. Každá služba pracovního postupu <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> je konfigurována s jedinečným, který odráží verzi definice pracovního postupu.  
  
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
