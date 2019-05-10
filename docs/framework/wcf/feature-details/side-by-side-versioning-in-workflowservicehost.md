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
# <a name="side-by-side-versioning-in-workflowservicehost"></a>Práce s víc verzemi současně ve třídě WorkflowServiceHost
<xref:System.ServiceModel.Activities.WorkflowServiceHost> Počínaje verzí vedle sebe [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] poskytuje možnost hostování několika verzí služby pracovního postupu v jednom koncovém bodu. Vedle sebe funkce poskytované umožňuje nakonfigurovat tak, aby nové instance služby pracovního postupu jsou vytvořené pomocí novou definici pracovního postupu při spuštění úplné pomocí existující definici instance služby pracovního postupu. Toto téma obsahuje přehled používání vedle sebe provádění pracovního postupu služby <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
> [!NOTE]
>  Stáhněte si ukázku a podívejte se video s návodem, Správa verzí vedle sebe služby pracovního postupu najdete v tématu [vedle sebe Správa verzí pomocí služby pracovního postupu Xamlx Web-Hosted](https://go.microsoft.com/fwlink/?LinkId=393746).  
  
## <a name="hosting-multiple-versions-in-a-workflow-service"></a>Hostování několika verzí služby pracovního postupu  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost> obsahuje dvě vlastnosti, které můžete nakonfigurovat tak, aby více verzí pracovního postupu ke spuštění vedle sebe: <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> a <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>. <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> obsahuje podporovaných verzí služby pracovního postupu a <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> slouží k jednoznačné identifikaci každé služby pracovního postupu. Je to tím, že přidružíte <xref:System.Activities.WorkflowIdentity> službě pracovního postupu. A <xref:System.Activities.WorkflowIdentity> obsahuje tři identifikační údaje. <xref:System.Activities.WorkflowIdentity.Name%2A> a <xref:System.Activities.WorkflowIdentity.Version%2A> obsahovat název a <xref:System.Version> a jsou povinné, a <xref:System.Activities.WorkflowIdentity.Package%2A> je volitelný a slouží k určení další řetězec obsahující informace, jako je název sestavení nebo jiné požadované informace. Každá služba pracovního postupu součástí <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekce musí mít jedinečnou <xref:System.Activities.WorkflowIdentity>. A <xref:System.Activities.WorkflowIdentity> je jedinečné, pokud některý z jeho tři vlastnosti se liší od jiného <xref:System.Activities.WorkflowIdentity>. A `null` <xref:System.Activities.WorkflowIdentity> není povolená hodnota pro <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, ale mohou mít pouze jednu předchozí verzi služby pracovních postupů `null` <xref:System.Activities.WorkflowIdentity>.  
  
> [!IMPORTANT]
>  A <xref:System.Activities.WorkflowIdentity> nesmí obsahovat žádné identifikovatelné osobní údaje (PII). <xref:System.Activities.WorkflowIdentity> se skládá ze tří částí: <xref:System.Activities.WorkflowIdentity.Name%2A> (<xref:System.String>), <xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>) a <xref:System.Activities.WorkflowIdentity.Package%2A> (<xref:System.String>). Informace o <xref:System.Activities.WorkflowIdentity> použitý k vytvoření instance je vygenerován pro všechny nakonfigurované sledování životního cyklu služeb v několika různých fázích aktivity modulem runtime. Sledování WF nemá žádný mechanismus skrýt identifikovatelné osobní údaje (citlivými daty). Proto <xref:System.Activities.WorkflowIdentity> instance by neměla obsahovat žádná data identifikovatelné osobní údaje, jak bude vygenerován modulem runtime ve sledování záznamů a mohou být viditelná pro každý, kdo má přístup k zobrazení záznamů sledování.  
  
### <a name="rules-for-hosting-multiple-versions-of-a-workflow-service"></a>Pravidla pro hostování více verzí služby pracovního postupu  
 Pokud uživatel přidá další verze pro <xref:System.ServiceModel.Activities.WorkflowServiceHost>, existuje několik podmínek, které musí být splněny v pořadí pro službu pracovního postupu hostovat se stejnou sadu koncových bodů a popis. Pokud některé z dalších verzí splňovat tyto podmínky <xref:System.ServiceModel.Activities.WorkflowServiceHost> vyvolá výjimku při `Open` je volána. Každá definice pracovního postupu, který je k dispozici na hostitele jako další verze musí splňovat následující požadavky (kde primární verze je definice služby pracovního postupu, který byl poskytnut konstruktor hostitele). Verze další pracovní postup musí:  
  
- Mají stejné <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> jako primární verzí služby pracovního postupu.  
  
- Nesmí mít žádné <xref:System.ServiceModel.Activities.Receive> nebo <xref:System.ServiceModel.Activities.SendReply> aktivit v jeho <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> , které nejsou ve primárního verzi a musí se shodovat s kontrakt.  
  
- Mít jedinečnou <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>. Může mít jeden a pouze jeden definice pracovního postupu `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.  
  
 Některé změny nejsou povoleny. Následující položky se může lišit mezi verzemi:  
  
- <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> Může mít jiný název a balíček než primární verze.  
  
- <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> Hodnota může být jiné než primární verze.  
  
- <xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> Může být jiný než primární verze.  
  
- <xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> Může být jiný než primární verze.  
  
### <a name="configuring-the-definitionidentity"></a>Konfigurace identitou DefinitionIdentity  
 Při vytvoření služby pracovních postupů pomocí návrháře postupu provádění <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> se nastavuje pomocí **vlastnosti** okna. Klikněte na tlačítko mimo kořenová aktivita služby v Návrháři vyberte služby pracovního postupu a zvolte **okno vlastností** z **zobrazení** nabídky. Vyberte **identita WorkflowIdentity** z rozevíracího seznamu, který se zobrazí vedle **identitou DefinitionIdentity** vlastnosti, rozbalte položku a zadejte požadovaný <xref:System.Activities.WorkflowIdentity> vlastnosti. V následujícím příkladu <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> má nakonfigurovanou <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` a <xref:System.Activities.WorkflowIdentity.Version%2A> z `1.0.0.0`. <xref:System.Activities.WorkflowIdentity.Package%2A> je volitelný a v tomto příkladu je `null`.  
  
 ![Snímek obrazovky s identitou DefinitionIdentity vlastnost.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-property.bmp)  
  
 Když je služba pracovního postupu v místním prostředí, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> je nakonfigurovaný, když se služba pracovního postupu. V následujícím příkladu <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> konfigurován pomocí stejné hodnoty jako předchozí příklad s <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` a <xref:System.Activities.WorkflowIdentity.Name%2A> z `1.0.0.0`.  
  
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
  
 A <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> není vyžadováno, ačkoli může mít pouze jednu verzi služby pracovního postupu **null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.  
  
> [!NOTE]
>  To je užitečné, pokud služba byl zpočátku bez nasadit <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> nakonfigurované, a vytvoří aktualizovanou verzi.  
  
### <a name="adding-a-new-version-to-a-web-hosted-workflow-service"></a>Přidává se nová verze služby hostované webového pracovního postupu  
 Prvním krokem při konfiguraci nové verze služby pracovních postupů v hostované webové služby je vytvoření nové složky v `App_Code` složku, která má stejný název jako soubor služby. Pokud služby `xamlx` soubor `MortgageWorkflow.xamlx`, pak musí mít název složky `MortgageWorkflow`. Umístěte kopii původní službě `xamlx` souboru do této složky a přejmenujte jej na nový název, jako například `MortgageWorkflowV1.xamlx`. Proveďte požadované změny pro primární služby, aktualizujte její <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>a poté nasaďte službu. V následujícím příkladu <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> byla aktualizována <xref:System.Activities.WorkflowIdentity.Name%2A> z `MortageWorkflow` a <xref:System.Activities.WorkflowIdentity.Version%2A> z `2.0.0.0`.  
  
 ![Snímek obrazovky s identitou DefinitionIdentity identita WorkflowIdentity.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-workflowidentity.bmp)  
  
 Po restartování služby předchozí verzi se automaticky přidají do <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekce vzhledem k tomu, že se nachází v určené `App_Code` podsložky. Všimněte si, že pokud má primární verzí služby pracovního postupu `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> předchozích verzích se nepřidá. Může mít jednu verzi `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, ale pokud existuje více verzí primární verze nesmí být se `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> nebo jinak nepřidají do předchozí verze <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekce.  
  
### <a name="adding-a-new-version-to-a-self-hosted-workflow-service"></a>Přidává se nová verze služby pracovního postupu v místním prostředí  
 Při přidávání nové verze služby pracovních postupů v místním prostředí, <xref:System.ServiceModel.Activities.WorkflowServiceHost> je nakonfigurována s primární verzí služby pracovního postupu a předchozí verze musí být explicitně přidán <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekce. V následujícím příkladu <xref:System.ServiceModel.Activities.WorkflowServiceHost> má nakonfigurovanou primární pracovní postup služby, který používá `MortgageWorkflowV2` definice pracovního postupu a služby pracovních postupů nakonfigurovanou `MortgageWorkflowV1` definice pracovního postupu se přidá do <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekce. Každý pracovní postup služba je nakonfigurována s jedinečným <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> , která odpovídá verzi modulu definice pracovního postupu.  
  
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
