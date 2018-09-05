---
title: Přizpůsobení informačního kanálu (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, feeds
- WCF Data Services, Atom protocol
- Atom Publishing Protocol [WCF Data Services]
- WCF Data Services, customizing feeds
ms.assetid: 0d1a39bc-6462-4683-bd7d-e74e0fd28a85
ms.openlocfilehash: 1922351ffb11d5ff6541ef22dee623c20d153d6a
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43747064"
---
# <a name="feed-customization-wcf-data-services"></a>Přizpůsobení informačního kanálu (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] používá [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] k vystavení dat jako informační kanál. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] podporuje formáty Atom i JavaScript Object Notation (JSON) pro datové kanály. Pokud používáte informační kanál, Atom [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] poskytuje standardní metodu k serializaci dat, jako je například entit a vztahů do formátu XML, které mohou být součástí těla zprávy HTTP. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Definuje výchozí vlastnost entity mapování mezi elementy Atom a data, která je obsažená v entitách. Další informace najdete v tématu [OData: formát Atom](https://go.microsoft.com/fwlink/?LinkID=185794).  
  
 Můžete mít aplikace scénář, který vyžaduje serializovat vlastnost dat vrácených datové služby přizpůsobené způsobem, nikoli ve standardním formátu informačního kanálu. S [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)], serializace v datových kanálů můžete přizpůsobit tak, aby vlastnosti entity mohou být mapovány na nepoužívané prvky a atributy položky nebo vlastní elementy položky v informačním kanálu.  
  
> [!NOTE]
>  Přizpůsobení informačního kanálu je podporována pouze pro informační kanály Atom. Vlastní informační kanály nebudou zobrazeny, pokud se požaduje formát JSON pro vrácené informační kanál.  
  
 S [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], můžete definovat mapování alternativních vlastnost entity pro datovou část Atom ručně použitím atributy pro typy entit v datovém modelu. Zprostředkovatel zdroje dat služby dat určuje, jak byste měli použít tyto atributy.  
  
> [!IMPORTANT]
>  Když definujete vlastní informační kanály, je nutné zaručit, že všechny vlastnosti entity, které mají vlastní mapování definovaná jsou zahrnuty v projekci. Vlastnost mapované entity není obsažen v projekci, může dojít ke ztrátě dat. Další informace najdete v tématu [projekce dotazů](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md).  
  
## <a name="customizing-feeds-with-the-entity-framework-provider"></a>Přizpůsobení informačních kanálů prostřednictvím zprostředkovatele Entity Framework  
 Datový model se používá [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] zprostředkovatele je vyjádřena jako kód XML v souboru .edmx. V takovém případě atributy, které definují vlastní informační kanály jsou přidány do `EntityType` a `Property` prvky, které představují typy entit a vlastnosti v datovém modelu. Tyto atributy přizpůsobení informačního kanálu nejsou definovány v [ \[MC CSDL\]: koncepční formátu definičního souboru schématu](https://go.microsoft.com/fwlink/?LinkId=159072), což je formát, který [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] poskytovatel použije k definování datového modelu. Proto je třeba deklarovat informačního kanálu přizpůsobení atributů v oboru názvů konkrétní schématu, která je definována jako `m="http://schemas.microsoft.com/ado/2007/08/dataservices/metadata"`. Následující fragment XML ukazuje informačního kanálu přizpůsobení atributy použité na `Property` prvky `Products` typ entity, které definují `ProductName`, `ReorderLevel`, a `UnitsInStock` vlastnosti.  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedAttributes](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/northwind.csdl#edmfeedattributes)]  
  
 Tyto atributy vytvořit následující vlastní datový kanál pro `Products` sady entit. V přizpůsobené datového kanálu `ProductName` hodnota vlastnosti se zobrazí v obou v `author` elementu a stejně jako `ProductName` element vlastnosti a `UnitsInStock` vlastnost se zobrazí v prvku vlastní má svůj vlastní jedinečný obor názvů a s `ReorderLevel` vlastnosti jako datový typ atributu:  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedResultProduct](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/edmfeedresult.xml#edmfeedresultproduct)]  
  
 Další informace najdete v tématu [postupy: přizpůsobení informačních kanálů pomocí zprostředkovatele Entity Framework](../../../../docs/framework/data/wcf/how-to-customize-feeds-with-ef-provider-wcf-data-services.md).  
  
> [!NOTE]
>  Vzhledem k tomu, že rozšíření do datového modelu v návrháři entit nejsou podporovány, je nutné ručně upravit soubor XML, který obsahuje datový model. Další informace o soubor EDMX, který je generován [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] nástroje, viz [edmx soubor přehled](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4).  
  
### <a name="custom-feed-attributes"></a>Vlastní informační kanál atributy  
 V následující tabulce jsou uvedeny atributy XML, které přizpůsobení informačních kanálů, které můžete přidat Konceptuální schéma definici jazyka (CSDL), který definuje datový model. Tyto atributy jsou rovnocenné vlastností <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> použít prostřednictvím zprostředkovatele reflexe.  
  
|Název atributu|Popis|  
|--------------------|-----------------|  
|`FC_ContentKind`|Určuje typ obsahu. Následující klíčová slova definovat syndikace typy obsahu.<br /><br /> `text:` Hodnota vlastnosti se zobrazí v informačním kanálu jako text.<br /><br /> `html:` Hodnota vlastnosti se zobrazí v informačním kanálu ve formátu HTML.<br /><br /> `xhtml:` Hodnota vlastnosti se zobrazí v informačním kanálu ve formátu HTML ve formátu XML.<br /><br /> Tato klíčová slova jsou ekvivalentem hodnoty <xref:System.Data.Services.Common.SyndicationTextContentKind> výčtu použít prostřednictvím zprostředkovatele reflexe.<br /><br /> Tento atribut není podporovaná, až `FC_NsPrefix` a `FC_NsUri` atributy se používají.<br /><br /> Pokud zadáte hodnotu `xhtml` pro `FC_ContentKind` atribut, ujistěte se, že hodnota vlastnosti obsahuje správně formátovaná data XML. Datové služby vrací hodnotu bez provedení jakékoli transformace. Musíte také zajistit, že mají všechny předpony – element XML v souboru XML vrácený identifikátor URI oboru názvů a předpony, které jsou definovány v informačním kanálu pro mapovanou.|  
|`FC_KeepInContent`|Označuje, že hodnota odkazovaná vlastnosti mají být použity v části obsah informačního kanálu a v umístění pro mapovanou. Platné hodnoty jsou `true` a `false`. Aby výsledný informačního kanálu zpětně kompatibilní s předchozími verzemi [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], zadejte hodnotu `true` abyste měli jistotu, že hodnota je obsažena v části obsah informačního kanálu.|  
|`FC_NsPrefix`|Předpona oboru názvů XML elementu v mapování bez syndikace. Tento atribut je potřeba použít s `FC_NsUri` atribut a nelze jej použít s `FC_ContentKind` atribut.|  
|`FC_NsUri`|Obor názvů URI elementu XML v mapování bez syndikace. Tento atribut je potřeba použít s `FC_NsPrefix` atribut a nelze jej použít s `FC_ContentKind` atribut.|  
|`FC_SourcePath`|Cesta vlastnosti entity, ke kterému je tento informační kanál mapování se pravidlo vztahuje. Tento atribut je podporována pouze v případě je použita `EntityType` elementu.<br /><br /> <xref:System.Data.Services.Common.EntityPropertyMappingAttribute.SourcePath%2A> Vlastnost nemůže odkazovat přímo komplexního typu. Pro komplexní typy, je nutné použít výraz cesta kde jsou názvy vlastností oddělit je zpětným lomítkem (`/`) znaků. Například jsou povoleny následující hodnoty pro typ entity `Person` s celočíselnou vlastnost `Age` a komplexní vlastnost<br /><br /> `Address`:<br /><br /> `Age`<br /><br /> `Address/Street`<br /><br /> <xref:System.Data.Services.Common.EntityPropertyMappingAttribute.SourcePath%2A> Vlastnost nelze nastavit na hodnotu, která obsahuje mezery nebo jakýkoli jiný znak, který není platný v názvu vlastnosti.|  
|`FC_TargetPath`|Název cílového elementu výsledný informačního kanálu pro mapování vlastnost. Tento element může být prvek definované ve specifikaci Atom nebo vlastní element.<br /><br /> Následující klíčová slova jsou předdefinované syndikace cílová cesta hodnoty, které odkazují na konkrétní umístění v [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačního kanálu.<br /><br /> `SyndicationAuthorEmail:` `atom:email` Podřízený prvek `atom:author` elementu.<br /><br /> `SyndicationAuthorName:` `atom:name` Podřízený prvek `atom:author` elementu.<br /><br /> `SyndicationAuthorUri:` `atom:uri` Podřízený prvek `atom:author` elementu.<br /><br /> `SyndicationContributorEmail:` `atom:email` Podřízený prvek `atom:contributor` elementu.<br /><br /> `SyndicationContributorName:` `atom:name` Podřízený prvek `atom:contributor` elementu.<br /><br /> `SyndicationContributorUri:` `atom:uri` Podřízený prvek `atom:contributor` elementu.<br /><br /> `SyndicationCustomProperty:` Prvek vlastní vlastnosti. Při mapování na prvek vlastní, cíl musí být výraz cesty, ve kterém jsou vnořené elementy oddělit je zpětným lomítkem (`/`) a atributy jsou určeny znak ampersand (`@`). V následujícím příkladu, řetězec `UnitsInStock/@ReorderLevel` mapuje hodnotu vlastnosti na atribut s názvem `ReorderLevel` na podřízený element s názvem `UnitsInStock` kořenového elementu vstupu.<br /><br /> `<Property Name="ReorderLevel" Type="Int16"               m:FC_TargetPath="UnitsInStock/@ReorderLevel"               m:FC_NsPrefix="Northwind"               m:FC_NsUri="http://schemas.examples.microsoft.com/dataservices"               m:FC_KeepInContent="false"               />`<br /><br /> Pokud jsou cílem názvu vlastního elementu `FC_NsPrefix` a `FC_NsUri` atributy musí být také zadána.<br /><br /> `SyndicationPublished:` `atom:published` Elementu.<br /><br /> `SyndicationRights:` `atom:rights` Elementu.<br /><br /> `SyndicationSummary:` `atom:summary` Elementu.<br /><br /> `SyndicationTitle:` `atom:title` Elementu.<br /><br /> `SyndicationUpdated:` `atom:updated` Elementu.<br /><br /> Tato klíčová slova jsou ekvivalentem hodnoty <xref:System.Data.Services.Common.SyndicationItemProperty> výčtu použít prostřednictvím zprostředkovatele reflexe.|  
  
> [!NOTE]
>  Názvy a hodnoty atributů jsou malá a velká písmena. Atributy mohou být použity buď `EntityType` element nebo na jeden nebo více `Property` prvky, ale ne obojí.  
  
## <a name="customizing-feeds-with-the-reflection-provider"></a>Přizpůsobení informačních kanálů prostřednictvím zprostředkovatele reflexe  
 Chcete-li přizpůsobení informačních kanálů pro datový model, který bylo implementováno pomocí zprostředkovatel reflexe, přidejte jeden nebo více instancí <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> atribut třídy, které představují typy entit v datovém modelu. Vlastnosti <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> třída odpovídat informačního kanálu přizpůsobení atributů, které jsou popsány v předchozí části. Následuje příklad deklarace `Order` typu, s vlastní informační kanál mapování definované pro obě vlastnosti.  
  
> [!NOTE]
>  Datový model v tomto příkladu je definována v tématu [postupy: vytvoření datové služby pomocí zprostředkovatel reflexe](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md).  
  
 [!code-csharp[Astoria Custom Feeds#CustomOrderFeed](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria custom feeds/cs/orderitems.svc.cs#customorderfeed)]
 [!code-vb[Astoria Custom Feeds#CustomOrderFeed](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria custom feeds/vb/orderitems.svc.vb#customorderfeed)]  
  
 Tyto atributy vytvořit následující vlastní datový kanál pro `Orders` sady entit. V tomto přizpůsobit informační kanál, `OrderId` hodnota vlastnosti se zobrazí pouze v `title` elementu `entry` a `Customer` hodnota vlastnosti se zobrazí v `author` elementu a stejně jako `Customer` property – element:  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResult](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/iqueryablefeedresult.xml#iqueryablefeedresult)]  
  
 Další informace najdete v tématu [postupy: přizpůsobení informačních kanálů prostřednictvím zprostředkovatele reflexe](../../../../docs/framework/data/wcf/how-to-customize-feeds-with-the-reflection-provider-wcf-data-services.md).  
  
## <a name="customizing-feeds-with-a-custom-data-service-provider"></a>Přizpůsobení informačních kanálů prostřednictvím zprostředkovatele služeb vlastních dat  
 Přizpůsobení informačního kanálu pro datový model definované pomocí poskytovatele služeb vlastních dat je definován pro typ prostředku voláním <xref:System.Data.Services.Providers.ResourceType.AddEntityPropertyMappingAttribute%2A> na <xref:System.Data.Services.Providers.ResourceType> , který představuje typ entity v datovém modelu. Další informace najdete v tématu [Vlastní zprostředkovatelé datových služeb](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md).  
  
## <a name="consuming-custom-feeds"></a>Použití vlastní informační kanály  
 Když vaše aplikace přímo využívá [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačního kanálu, musí být schopen zpracovat všechny vlastní elementy a atributy v vrácené informační kanál. Pokud jste implementovali vlastní informační kanály v datovém modelu, bez ohledu na zprostředkovateli datových služeb `$metadata` koncový bod vrací vlastní informační kanál informace jako vlastní atributy informačního kanálu v CSDL vrácené službou data. Při použití **přidat odkaz na službu** dialogové okno nebo [datasvcutil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) nástroj pro generování tříd klientské datové služby, vlastní informační kanál atributy se používají k zajištění, že žádosti a odpovědi datové služby jsou správně zpracovány.  
  
## <a name="feed-customization-considerations"></a>Důležité informace o přizpůsobení informačního kanálu  
 Při definování vlastního informačního kanálu mapování byste měli zvážit následující.  
  
-   [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klienta považuje za mapované prvky v informačním kanálu prázdný obsahující jenom prázdné znaky. Z tohoto důvodu nejsou vyhodnocena mapované prvky, které obsahují pouze prázdné znaky na klientovi stejnou prázdnými znaky. Zachovat tento mezer na straně klienta, musíte nastavit hodnotu `KeepInContext` k `true` v atributu mapování informačního kanálu.  
  
## <a name="versioning-requirements"></a>Požadavky na správu verzí  
 Přizpůsobení informačního kanálu má následující [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokol požadavků na správu verzí:  
  
-   Přizpůsobení informačního kanálu vyžaduje, aby tento klient i data služby podpory verze 2.0 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokol a novějších verzích.  
  
 Další informace najdete v tématu [Správa verzí datové služby](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).  
  
## <a name="see-also"></a>Viz také  
 [Zprostředkovatel reflexe](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)  
 [Zprostředkovatel Entity Framework](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)
