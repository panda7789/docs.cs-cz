---
title: "Přizpůsobení informačního kanálu (služby WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, feeds
- WCF Data Services, Atom protocol
- Atom Publishing Protocol [WCF Data Services]
- WCF Data Services, customizing feeds
ms.assetid: 0d1a39bc-6462-4683-bd7d-e74e0fd28a85
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e31f14d59bb2ac7caa233ff60c60eb944ee5bbbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="feed-customization-wcf-data-services"></a>Přizpůsobení informačního kanálu (služby WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]používá [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] vystavit data jako informačního kanálu. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]podporuje formáty Atom i JavaScript Object Notation (JSON) pro datové kanály. Při použití informačního kanálu, Atom [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] poskytuje standardní metodu k serializaci dat, jako je například entity a vztahy do formátu XML, který může být zahrnutý v textu zprávy HTTP. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]Definuje výchozí vlastnost entity mapování mezi data, která je součástí entity a elementy Atom. Další informace najdete v tématu [OData: formát Atom](http://go.microsoft.com/fwlink/?LinkID=185794).  
  
 Můžete mít aplikační scénář, který vyžaduje serializovat data vlastnost vrácený službou data způsobem, vlastní, nikoli ve standardním formátu informačního kanálu. S [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)], serializace v informačním kanálu dat můžete přizpůsobit tak, aby vlastnosti entity, může být namapovaný na nepoužívané elementů a atributů položku nebo na vlastní elementy položky v informačním kanálu.  
  
> [!NOTE]
>  Přizpůsobení informačního kanálu je podporována pouze pro informační kanály Atom. Vlastní kanály nebudou zobrazeny, pokud se požaduje formátu JSON pro vrácené informačního kanálu.  
  
 S [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], můžete definovat mapování alternativní vlastnost entity pro datovou část Atom aplikací ručně atributů typy entit v datovém modelu. Zprostředkovatel zdroje dat služby dat určuje, jak byste měli použít tyto atributy.  
  
> [!IMPORTANT]
>  Když definujete vlastní informační kanály, musí zaručit, že všechny vlastnosti entity, které mají vlastní mapování definovaná jsou zahrnuty v projekci. Vlastnost namapované entity není obsažen v projekci, může dojít ke ztrátě dat. Další informace najdete v tématu [projekce dotazu](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md).  
  
## <a name="customizing-feeds-with-the-entity-framework-provider"></a>Přizpůsobení informačních kanálů v aplikaci zprostředkovatele Entity Framework  
 Datový model použít s [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] zprostředkovatele je reprezentován jako kód XML v souboru EDMX. V takovém případě atributy, které definují vlastní informačních kanálů jsou přidány do `EntityType` a `Property` prvky, které představují typy entit a vlastnosti v datovém modelu. Nejsou tyto informačního kanálu vlastní atributy definované v [ \[MC CSDL\]: koncepční formátu definičního souboru schématu](http://go.microsoft.com/fwlink/?LinkId=159072), který je formátem, který [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] poskytovatele používá k definování datového modelu. Proto je potřeba deklarovat informačního kanálu vlastní atributy v oboru názvů konkrétní schématu, která je definována jako `m="http://schemas.microsoft.com/ado/2007/08/dataservices/metadata"`. Následující fragment kódu XML ukazuje informačního kanálu vlastní atributy použité na `Property` prvky `Products` typ entity, které definují `ProductName`, `ReorderLevel`, a `UnitsInStock` vlastnosti.  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedAttributes](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/northwind.csdl#edmfeedattributes)]  
  
 Tyto atributy vytvořit následující vlastní datový kanál pro `Products` sady entit. V informačním kanálu, přizpůsobené dat `ProductName` hodnotu vlastnosti se zobrazí v obou v `author` element a jako `ProductName` element vlastnosti a `UnitsInStock` vlastnost zobrazena v vlastní element, který má svůj vlastní jedinečný obor názvů a `ReorderLevel` vlastnost jako atribut:  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedResultProduct](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/edmfeedresult.xml#edmfeedresultproduct)]  
  
 Další informace najdete v tématu [postupy: přizpůsobení kanály pomocí zprostředkovatele Entity Framework](../../../../docs/framework/data/wcf/how-to-customize-feeds-with-ef-provider-wcf-data-services.md).  
  
> [!NOTE]
>  Vzhledem k tomu, že rozšíření do datového modelu Entity Designer nepodporuje, je nutné ručně upravit soubor XML, který obsahuje datový model. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]soubor EDMX, který je generovaný [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] nástroje, viz [.edmx souboru přehled](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4).  
  
### <a name="custom-feed-attributes"></a>Vlastní kanál atributy  
 V následující tabulce jsou uvedeny atributy XML, které přizpůsobit informační kanály, které můžete přidat do konceptuálního schématu definice language (CSDL), která definuje datový model. Tyto atributy odpovídají vlastnosti <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> použití se zprostředkovatelem reflexe.  
  
|Název atributu|Popis|  
|--------------------|-----------------|  
|`FC_ContentKind`|Určuje typ obsahu. Následující klíčová slova definovat syndikace typy obsahu.<br /><br /> `text:`Hodnota vlastnosti se zobrazí v informačním kanálu jako text.<br /><br /> `html:`Hodnota vlastnosti se zobrazí v informačním kanálu jako kód HTML.<br /><br /> `xhtml:`Hodnota vlastnosti se zobrazí v informačním kanálu jako kód HTML formátu XML.<br /><br /> Tato klíčová slova jsou ekvivalentem hodnoty <xref:System.Data.Services.Common.SyndicationTextContentKind> výčtu použití se zprostředkovatelem reflexe.<br /><br /> Tento atribut není podporovaná, až `FC_NsPrefix` a `FC_NsUri` atributy se používají.<br /><br /> Pokud zadáte hodnotu `xhtml` pro `FC_ContentKind` atribut, ujistěte se, že hodnota vlastnosti obsahuje správně formátovaný XML. Služba data vrací hodnotu bez provedení všechny transformace. Je nutné zajistit, aby měly všechny předpony – element XML v vráceného souboru XML. identifikátor URI oboru názvů a předpony, které jsou definované v informačním kanálu namapované.|  
|`FC_KeepInContent`|Označuje, že hodnota vlastnosti odkazované mají být použity v části obsah informačního kanálu i v namapované umístění. Platné hodnoty jsou `true` a `false`. Chcete-li výsledné informačního kanálu zpětně kompatibilní s dřívějšími verzemi nástroje [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], zadejte hodnotu `true` a ujistěte se, že hodnota je obsažena v části obsah informačního kanálu.|  
|`FC_NsPrefix`|Předpona oboru názvů XML elementu bez syndikace mapování. Tento atribut se musí používat s `FC_NsUri` atribut a nelze jej použít s `FC_ContentKind` atribut.|  
|`FC_NsUri`|Identifikátor URI oboru element XML bez syndikace mapování. Tento atribut se musí používat s `FC_NsPrefix` atribut a nelze jej použít s `FC_ContentKind` atribut.|  
|`FC_SourcePath`|Cesta k vlastnosti entity, na němž je tato kanálu mapování pravidlo vztahuje. Tento atribut je podporována pouze v případě je používán `EntityType` elementu.<br /><br /> <xref:System.Data.Services.Common.EntityPropertyMappingAttribute.SourcePath%2A> Vlastnost nelze odkazovat přímo komplexního typu. Pro komplexní typy, je nutné použít výraz cesty kde názvů vlastností oddělených zpětné lomítko (`/`) znaků. Například následující hodnoty jsou povolené pro typ entity `Person` s ve vlastnosti integer `Age` a komplexní vlastnost<br /><br /> `Address`:<br /><br /> `Age`<br /><br /> `Address/Street`<br /><br /> <xref:System.Data.Services.Common.EntityPropertyMappingAttribute.SourcePath%2A> Vlastnost nelze nastavit na hodnotu, která obsahuje mezeru nebo libovolný znak, který není platný název vlastnosti.|  
|`FC_TargetPath`|Název elementu target výsledné informačního kanálu pro mapování vlastnost. Tento element může být element definované specifikací Atom nebo vlastního elementu.<br /><br /> Následující klíčová slova jsou předdefinované syndikace cílová cesta hodnoty, které odkazují na konkrétní umístění v [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačního kanálu.<br /><br /> `SyndicationAuthorEmail:``atom:email` Podřízený element `atom:author` elementu.<br /><br /> `SyndicationAuthorName:``atom:name` Podřízený element `atom:author` elementu.<br /><br /> `SyndicationAuthorUri:``atom:uri` Podřízený element `atom:author` elementu.<br /><br /> `SyndicationContributorEmail:``atom:email` Podřízený element `atom:contributor` elementu.<br /><br /> `SyndicationContributorName:``atom:name` Podřízený element `atom:contributor` elementu.<br /><br /> `SyndicationContributorUri:``atom:uri` Podřízený element `atom:contributor` elementu.<br /><br /> `SyndicationCustomProperty:`Element vlastní vlastnosti. Při mapování na prvek vlastní, cíl musí být výraz cesty, ve kterém jsou vnořených elementů oddělených zpětné lomítko (`/`) a atributy jsou určené ampersand (`@`). V následujícím příkladu, řetězec `UnitsInStock/@ReorderLevel` hodnotu vlastnosti se mapuje na atribut s názvem `ReorderLevel` na podřízený element s názvem `UnitsInStock` kořenového prvku položku.<br /><br /> `<Property Name="ReorderLevel" Type="Int16"               m:FC_TargetPath="UnitsInStock/@ReorderLevel"               m:FC_NsPrefix="Northwind"               m:FC_NsUri="http://schemas.examples.microsoft.com/dataservices"               m:FC_KeepInContent="false"               />`<br /><br /> Pokud jsou cílem název vlastního elementu, `FC_NsPrefix` a `FC_NsUri` atributy musí být také zadána.<br /><br /> `SyndicationPublished:``atom:published` Elementu.<br /><br /> `SyndicationRights:``atom:rights` Elementu.<br /><br /> `SyndicationSummary:``atom:summary` Elementu.<br /><br /> `SyndicationTitle:``atom:title` Elementu.<br /><br /> `SyndicationUpdated:``atom:updated` Elementu.<br /><br /> Tato klíčová slova jsou ekvivalentem hodnoty <xref:System.Data.Services.Common.SyndicationItemProperty> výčtu použití se zprostředkovatelem reflexe.|  
  
> [!NOTE]
>  Názvy a hodnoty atributů jsou malá a velká písmena. Atributy mohou být použity buď `EntityType` element nebo na jeden nebo více `Property` elementů, ale ne na obou.  
  
## <a name="customizing-feeds-with-the-reflection-provider"></a>Přizpůsobení informačních kanálů s poskytovatelem reflexe  
 Chcete-li přizpůsobit informační kanály pro datový model, který byl implementován pomocí reflexe zprostředkovatele, přidejte jednu nebo více instancí <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> atribut třídy, které představují typy entit v datovém modelu. Vlastnosti <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> třída odpovídat informačního kanálu vlastní atributy, které jsou popsané v předchozí části. Následuje příklad deklarace `Order` typu, s vlastní kanál mapování definovaná pro obě vlastnosti.  
  
> [!NOTE]
>  Datový model v tomto příkladu je definován v sekci [postup: vytvoření služby Data pomocí poskytovatele reflexe](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md).  
  
 [!code-csharp[Astoria Custom Feeds#CustomOrderFeed](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria custom feeds/cs/orderitems.svc.cs#customorderfeed)]
 [!code-vb[Astoria Custom Feeds#CustomOrderFeed](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria custom feeds/vb/orderitems.svc.vb#customorderfeed)]  
  
 Tyto atributy vytvořit následující vlastní datový kanál pro `Orders` sady entit. V tomto přizpůsobit informační kanál, `OrderId` hodnotu vlastnosti zobrazí pouze v `title` element `entry` a `Customer` hodnotu vlastnosti zobrazí v `author` element a jako `Customer` element vlastnosti:  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResult](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/iqueryablefeedresult.xml#iqueryablefeedresult)]  
  
 Další informace najdete v tématu [postupy: přizpůsobení kanály pomocí reflexe zprostředkovatele](../../../../docs/framework/data/wcf/how-to-customize-feeds-with-the-reflection-provider-wcf-data-services.md).  
  
## <a name="customizing-feeds-with-a-custom-data-service-provider"></a>Přizpůsobení informačních kanálů s poskytovatelem služeb vlastních dat  
 Kanál přizpůsobení datového modelu definované pomocí poskytovatele služeb vlastních dat je definován pro typ prostředku voláním <xref:System.Data.Services.Providers.ResourceType.AddEntityPropertyMappingAttribute%2A> na <xref:System.Data.Services.Providers.ResourceType> , která představuje typ entity v datovém modelu. Další informace najdete v tématu [vlastní Data poskytovatelé](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md).  
  
## <a name="consuming-custom-feeds"></a>Použití vlastní kanály  
 Pokud vaše aplikace přímo využívá [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanálu, musí být schopna zpracovat všechny vlastní elementy a atributy ve vrácené informačního kanálu. Pokud jste implementovali vlastní kanály v datovém modelu, bez ohledu na poskytovatele dat služeb, `$metadata` koncový bod vrátí vlastní kanál informace jako vlastní atributy informačního kanálu v CSDL vrácený službou data. Při použití **přidat odkaz na službu** dialogové okno nebo [datasvcutil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) nástroj pro generování klienta datových služba tříd, přizpůsobené informačního kanálu atributy se používají k zajištění, které požadavky a odpovědi Služba data jsou zpracovány správně.  
  
## <a name="feed-customization-considerations"></a>Důležité informace o přizpůsobení informačního kanálu  
 Měli byste zvážit následující při definování vlastní mapování informačního kanálu.  
  
-   [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klienta zpracovává mapované prvky v informačním kanálu jako prázdný při obsahují jenom prázdné znaky. Z toho důvodu nejsou materializovat mapované prvky, které obsahovat jenom prázdné znaky na klienta se stejným prázdný znak. Pokud chcete zachovat tento prázdné znaky na straně klienta, musíte nastavit hodnotu `KeepInContext` k `true` v atributu informačního kanálu mapování.  
  
## <a name="versioning-requirements"></a>Požadavky na Správa verzí  
 Přizpůsobení informačního kanálu má následující [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokolu požadavků na správu verzí:  
  
-   Informačního kanálu vlastní nastavení vyžaduje, že klient i data služby podpory verze 2.0 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokol a novější verze.  
  
 Další informace najdete v tématu [verze datové služby](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).  
  
## <a name="see-also"></a>Viz také  
 [Reflexe zprostředkovatele](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)  
 [Zprostředkovatel Entity Framework](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)
