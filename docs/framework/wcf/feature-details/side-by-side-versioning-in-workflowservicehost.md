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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f3629778ded2b690f8169223101d89cb551e1449
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="side-by-side-versioning-in-workflowservicehost"></a>Práce s víc verzemi současně ve třídě WorkflowServiceHost
<xref:System.ServiceModel.Activities.WorkflowServiceHost> Vedle sebe verze byla zavedená v [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] poskytuje možnosti pro hostování více verzí služby pracovních postupů na jeden koncový bod. Souběžně sdílená funkce poskytované umožňuje nakonfigurovat tak, aby nové instance služby pracovního postupu se vytvářejí pomocí nové definice pracovního postupu, při spuštění instance dokončení pomocí stávající definici pracovního postupu služby. Toto téma obsahuje přehled používání vedle sebe spuštění pracovního postupu služby <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
> [!NOTE]
>  Stáhněte si ukázku a podívejte se video s návodem verze vedle sebe služby pracovního postupu najdete v tématu [vedle sebe Správa verzí pomocí služby pracovních postupů Xamlx Web-Hosted](http://go.microsoft.com/fwlink/?LinkId=393746).  
  
## <a name="hosting-multiple-versions-in-a-workflow-service"></a>Hostování více verzí v služby pracovních postupů  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>obsahuje dvě vlastnosti, které můžete nakonfigurovat tak, aby více verzí pracovní postup provést vedle sebe: <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> a <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>. <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A>obsahuje podporovaných verzích služby pracovního postupu a <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> slouží k jednoznačné identifikaci jednotlivých služby pracovního postupu. K tomu je potřeba přidružení <xref:System.Activities.WorkflowIdentity> službou pracovního postupu. A <xref:System.Activities.WorkflowIdentity> obsahuje tři identifikační údaje. <xref:System.Activities.WorkflowIdentity.Name%2A>a <xref:System.Activities.WorkflowIdentity.Version%2A> obsahovat název a <xref:System.Version> a jsou povinné, a <xref:System.Activities.WorkflowIdentity.Package%2A> je volitelný a může sloužit k určení požadovaných další řetězec obsahující informace, jako je název sestavení nebo jiné informace. Každý služby pracovního postupu, který je součástí <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekce musí mít jedinečnou <xref:System.Activities.WorkflowIdentity>. A <xref:System.Activities.WorkflowIdentity> je jedinečný, pokud jsou některé jeho vlastnosti tři liší od jiného <xref:System.Activities.WorkflowIdentity>. A `null` <xref:System.Activities.WorkflowIdentity> je povolená hodnota pro <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, ale mohou mít pouze jeden předchozí verzi služby pracovního postupu `null` <xref:System.Activities.WorkflowIdentity>.  
  
> [!IMPORTANT]
>  A <xref:System.Activities.WorkflowIdentity> nesmí obsahovat žádné identifikovatelné osobní údaje (PII). <xref:System.Activities.WorkflowIdentity>se skládá ze tří částí: <xref:System.Activities.WorkflowIdentity.Name%2A> (<xref:System.String>), <xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>) a <xref:System.Activities.WorkflowIdentity.Package%2A> (<xref:System.String>). Informace o <xref:System.Activities.WorkflowIdentity> použít k vytvoření instance je pro všechny nakonfigurované sledování životního cyklu služeb v několika různých místech aktivity vygenerované modulem runtime. WF sledování nemá žádný mechanismus skrýt PII (citlivé uživatelských dat). Proto <xref:System.Activities.WorkflowIdentity> instance nesmí obsahovat žádná data PII tak, jak bude vygenerované modulem runtime v sledování záznamů a mohou být viditelná pro každý, kdo má přístup k zobrazení záznamů sledování.  
  
### <a name="rules-for-hosting-multiple-versions-of-a-workflow-service"></a>Pravidla pro hostování více verzí služby pracovních postupů  
 Pokud uživatel přidá další verzi <xref:System.ServiceModel.Activities.WorkflowServiceHost>, existuje několik podmínek, které je nutné splnit, aby služby pracovního postupu pro hostování se stejnou sadu koncových bodů a popis. Pokud některý z dalších verzí selže ke splnění těchto podmínek <xref:System.ServiceModel.Activities.WorkflowServiceHost> vyvolá výjimku při `Open` je volána. Každý zadaná hostitele jako další verze definice pracovního postupu musí splňovat následující požadavky (kde primární verze je definice služby pracovního postupu, který je zadán pro konstruktor hostitele). Musí být verze další pracovního postupu:  
  
-   Mít stejnou <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> jako primární verzi služby pracovního postupu.  
  
-   Nesmí mít žádné <xref:System.ServiceModel.Activities.Receive> nebo <xref:System.ServiceModel.Activities.SendReply> aktivity v jeho <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> které nejsou v primární verzi, a musí odpovídat kontrakt operaci.  
  
-   Mít jedinečnou <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>. Může mít pouze jednu definici pracovního postupu `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.  
  
 Některé změny nejsou povoleny. Následující položky se můžou lišit mezi verzemi:  
  
-   <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> Může mít jiný název a balíček než primární verze.  
  
-   <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> Hodnota může být jiný než primární verze.  
  
-   <xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> Může být jiný než primární verze.  
  
-   <xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> Může být jiný než primární verze.  
  
### <a name="configuring-the-definitionidentity"></a>Konfigurace DefinitionIdentity  
 Při vytvoření služby pracovních postupů pomocí návrháře pracovních postupů <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> se nastavuje pomocí **vlastnosti** okno. Klikněte na tlačítko mimo služby kořenové aktivity v Návrháři vyberte služby pracovního postupu, a vyberte **vlastnosti – okno** z **zobrazení** nabídky. Vyberte **WorkflowIdentity** ze seznamu rozevíracího seznamu, který se zobrazí vedle **DefinitionIdentity** vlastnost a potom rozbalte položku a zadejte požadovanou <xref:System.Activities.WorkflowIdentity> vlastnosti. V následujícím příkladu <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> nastavena <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` a <xref:System.Activities.WorkflowIdentity.Version%2A> z `1.0.0.0`. <xref:System.Activities.WorkflowIdentity.Package%2A>je volitelný a v tomto příkladu je `null`.  
  
 ![DefinitionIdentity](../../../../docs/framework/wcf/feature-details/media/workflowservicedefinitionidentityv1.bmp "WorkflowServiceDefinitionIdentityv1")  
  
 Po samoobslužné hostované služby pracovních postupů <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> je nakonfigurován, když se služby pracovního postupu. V následujícím příkladu <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> stejné hodnoty jako předchozí příklad, nakonfigurované s <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` a <xref:System.Activities.WorkflowIdentity.Name%2A> z `1.0.0.0`.  
  
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
  
 A <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> není vyžadována, i když může mít jenom jednu verzi služby pracovního postupu **null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.  
  
> [!NOTE]
>  To je užitečné, pokud je služba nasazená původně bez <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> nakonfigurovaná, a pak se vytvoří aktualizovaná verze.  
  
### <a name="adding-a-new-version-to-a-web-hosted-workflow-service"></a>Přidání nové verze do pracovního postupu hostované webové služby  
 Prvním krokem při konfiguraci nové verze služby pracovního procesu ve webové hostované služby je vytvořte novou složku v `App_Code` složky, která má stejný název jako soubor služby. Pokud služby `xamlx` název souboru je `MortgageWorkflow.xamlx`, pak musí mít název složky `MortgageWorkflow`. Umístěte kopii původní službu `xamlx` souborů do této složky a přejmenujte jej na nový název, například `MortgageWorkflowV1.xamlx`. Proveďte požadované změny do primární služby, aktualizujte jeho <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>a poté nasaďte službu. V následujícím příkladu <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> bylo aktualizováno <xref:System.Activities.WorkflowIdentity.Name%2A> z `MortageWorkflow` a <xref:System.Activities.WorkflowIdentity.Version%2A> z `2.0.0.0`.  
  
 ![DefinitionIdentity](../../../../docs/framework/wcf/feature-details/media/workflowservicedefinitionidentityv2.bmp "WorkflowServiceDefinitionIdentityv2")  
  
 Po restartování služby předchozí verze automaticky přidá do <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekce vzhledem k tomu, že se nachází v určené `App_Code` podsložky. Všimněte si, že pokud má primární verzi služby pracovního postupu `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> nepřidají předchozí verze. Může mít jednu verzi `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, ale pokud existuje více verzí primární verze nesmí být ten se `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> nebo jinak předchozí verze nepřidají k <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekce.  
  
### <a name="adding-a-new-version-to-a-self-hosted-workflow-service"></a>Přidání nové verze službě samoobslužné hostovaných pracovních postupů  
 Při přidávání nové verze službě vlastním hostováním pracovního postupu, <xref:System.ServiceModel.Activities.WorkflowServiceHost> je nakonfigurován s primární verzí služby pracovního postupu a předchozí verze musí být explicitně přidán <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekce. V následujícím příkladu <xref:System.ServiceModel.Activities.WorkflowServiceHost> je nakonfigurován pomocí služby primární pracovního postupu, který používá `MortgageWorkflowV2` definice pracovního postupu a nakonfigurované služby pracovních postupů `MortgageWorkflowV1` definice pracovního postupu se přidá do <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekce. Každý pracovní postup služba je nakonfigurována s jedinečným <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> s odpovídajícími verze definice pracovního postupu.  
  
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
