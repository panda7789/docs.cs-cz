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
ms.openlocfilehash: b4ea05b0112af4c1dcb6308a08ab3b31c586fbe8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790865"
---
# <a name="feed-customization-wcf-data-services"></a>Přizpůsobení informačního kanálu (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)][!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] používá k vystavení dat jako informačního kanálu. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]podporuje formáty Atom i JavaScript Object Notation (JSON) pro datové kanály. Pokud používáte informační kanál Atom, [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] poskytuje standardní metodu pro serializaci dat, jako jsou například entity a relace, do formátu XML, který lze zahrnout do textu zprávy HTTP. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]definuje výchozí mapování vlastností entit mezi daty, která jsou obsažená v entitách a elementech Atom. Další informace najdete v tématu [OData: Formát](https://go.microsoft.com/fwlink/?LinkID=185794)Atom.  
  
 Můžete mít scénář aplikace, který vyžaduje, aby data vlastnosti vrácená datovou službou byla serializována vlastním způsobem, nikoli ve formátu standardního informačního kanálu. Pomocí [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]nástroje lze v datovém kanálu upravit serializaci tak, aby vlastnosti entity mohly být mapovány na nepoužívané prvky a atributy položky nebo na vlastní prvky položky v informačním kanálu.  
  
> [!NOTE]
> Přizpůsobení informačního kanálu se podporuje jenom pro kanály Atom. Vlastní kanály nejsou vraceny, pokud je pro vrácený kanál požadován formát JSON.  
  
 Pomocí [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]můžete definovat alternativní mapování vlastností entit pro datovou část Atom ručním použitím atributů na typy entit v datovém modelu. Poskytovatel zdroje dat datové služby určuje, jak byste měli tyto atributy použít.  
  
> [!IMPORTANT]
> Když definujete vlastní kanály, musíte zaručit, že všechny vlastnosti entity, které mají definované vlastní mapování, jsou zahrnuté do projekce. Pokud v projekci není obsažena vlastnost mapované entity, může dojít ke ztrátě dat. Další informace najdete v tématu [projekce dotazů](query-projections-wcf-data-services.md).  
  
## <a name="customizing-feeds-with-the-entity-framework-provider"></a>Přizpůsobení informačních kanálů pomocí poskytovatele Entity Framework  
 Datový model, který se používá [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] u poskytovatele, je v souboru. edmx reprezentován jako XML. V tomto případě jsou atributy, které definují vlastní kanály, přidány do `EntityType` prvků a `Property` , které představují typy entit a vlastnosti v datovém modelu. Tyto atributy přizpůsobení informačního kanálu nejsou definované [v \[MC-\]CSDL: Definiční formát](https://go.microsoft.com/fwlink/?LinkId=159072)definičního souboru schématu, což je formát [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] , který poskytovatel používá k definování datového modelu. Proto je nutné deklarovat atributy přizpůsobení kanálu v konkrétním oboru názvů schématu, který je definován jako `m="http://schemas.microsoft.com/ado/2007/08/dataservices/metadata"`. Následující fragment kódu XML ukazuje atributy přizpůsobení informačního kanálu `Property` aplikované na `Products` prvky typu `ProductName`entity, které definují `ReorderLevel`vlastnosti, `UnitsInStock` a.  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedAttributes](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/northwind.csdl#edmfeedattributes)]  
  
 Tyto atributy vytváří pro `Products` sadu entit následující přizpůsobený datový kanál. V přizpůsobeném datovém kanálu `ProductName` je hodnota vlastnosti zobrazena v `author` prvku v elementu i jako `ProductName` element vlastnosti a `UnitsInStock` vlastnost je zobrazena ve vlastním prvku, který má svůj vlastní jedinečný obor názvů a s `ReorderLevel` vlastnost jako atribut:  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedResultProduct](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/edmfeedresult.xml#edmfeedresultproduct)]  
  
 Další informace najdete v tématu [jak: Přizpůsobte kanály pomocí poskytovatele](how-to-customize-feeds-with-ef-provider-wcf-data-services.md)Entity Framework.  
  
> [!NOTE]
> Vzhledem k tomu, že Entity Designer nepodporuje rozšíření datového modelu, je nutné ručně upravit soubor XML, který obsahuje datový model. Další informace o souboru. edmx, který generuje nástroje model EDM (Entity Data Model), najdete v tématu [Přehled souborů. edmx (Entity Framework)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)).  
  
### <a name="custom-feed-attributes"></a>Vlastní atributy kanálu  
 V následující tabulce jsou uvedeny atributy jazyka XML, které přizpůsobují kanály, které lze přidat do jazyka CSDL (konceptuální schéma Definition Language), který definuje datový model. Tyto atributy jsou ekvivalentní vlastnostem <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> použitým u poskytovatele reflexe.  
  
|Název atributu|Popis|  
|--------------------|-----------------|  
|`FC_ContentKind`|Určuje typ obsahu. Následující klíčová slova definují typy obsahu syndikace.<br /><br /> `text:`Hodnota vlastnosti se zobrazí v informačním kanálu jako text.<br /><br /> `html:`Hodnota vlastnosti se zobrazí v informačním kanálu jako HTML.<br /><br /> `xhtml:`Hodnota vlastnosti se zobrazí v informačním kanálu jako HTML ve formátu XML.<br /><br /> Tato klíčová slova jsou ekvivalentní hodnotám <xref:System.Data.Services.Common.SyndicationTextContentKind> výčtu použitým u poskytovatele reflexe.<br /><br /> Tento atribut není podporován, pokud `FC_NsPrefix` jsou použity atributy a. `FC_NsUri`<br /><br /> Zadáte-li hodnotu `xhtml` `FC_ContentKind` atributu, je nutné zajistit, aby hodnota vlastnosti obsahovala správně formátovaný kód XML. Datová služba vrátí hodnotu bez provedení jakékoli transformace. Musíte také zajistit, aby všechny předpony XML elementů v vráceném kódu XML měly obor názvů URI a předponu definovanou v mapovaném informačním kanálu.|  
|`FC_KeepInContent`|Označuje, že hodnota odkazované vlastnosti by měla být zahrnutá v části obsah informačního kanálu i v mapovaném umístění. Platné hodnoty jsou `true` a `false`. Chcete-li [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], aby výsledný kanál byl zpětně kompatibilní s dřívějšími verzemi nástroje, `true` zadejte hodnotu, abyste se ujistili, že hodnota je zahrnuta v části obsah informačního kanálu.|  
|`FC_NsPrefix`|Předpona oboru názvů elementu XML v mapování bez syndikace. Tento atribut musí být použit s `FC_NsUri` atributem a nelze jej použít `FC_ContentKind` s atributem.|  
|`FC_NsUri`|Identifikátor URI oboru názvů elementu XML v mapování bez syndikace. Tento atribut musí být použit s `FC_NsPrefix` atributem a nelze jej použít `FC_ContentKind` s atributem.|  
|`FC_SourcePath`|Cesta k vlastnosti entity, na kterou se vztahuje pravidlo mapování kanálu Tento atribut je podporován pouze v případě, že je použit `EntityType` v elementu.<br /><br /> <xref:System.Data.Services.Common.EntityPropertyMappingAttribute.SourcePath%2A> Vlastnost nemůže odkazovat přímo na složitý typ. U komplexních typů je nutné použít výraz cesty, ve kterém jsou názvy vlastností odděleny znakem zpětného lomítka (`/`). Například následující hodnoty jsou povoleny pro typ `Person` entity s vlastností `Age` Integer a komplexní vlastností.<br /><br /> `Address`:<br /><br /> `Age`<br /><br /> `Address/Street`<br /><br /> <xref:System.Data.Services.Common.EntityPropertyMappingAttribute.SourcePath%2A> Vlastnost nemůže být nastavena na hodnotu, která obsahuje mezeru nebo jakýkoli jiný znak, který není platný v názvu vlastnosti.|  
|`FC_TargetPath`|Název cílového prvku výsledného informačního kanálu, který bude mapovat vlastnost. Tento element může být prvek definovaný specifikacemi Atom nebo vlastním prvkem.<br /><br /> Následující klíčová slova jsou předdefinovaná cílová hodnota pro cestu syndikace, která odkazuje na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] konkrétní umístění v informačním kanálu.<br /><br /> `SyndicationAuthorEmail:``atom:email` Podřízený element`atom:author` elementu.<br /><br /> `SyndicationAuthorName:``atom:name` Podřízený element`atom:author` elementu.<br /><br /> `SyndicationAuthorUri:``atom:uri` Podřízený element`atom:author` elementu.<br /><br /> `SyndicationContributorEmail:``atom:email` Podřízený element`atom:contributor` elementu.<br /><br /> `SyndicationContributorName:``atom:name` Podřízený element`atom:contributor` elementu.<br /><br /> `SyndicationContributorUri:``atom:uri` Podřízený element`atom:contributor` elementu.<br /><br /> `SyndicationCustomProperty:`Prvek vlastní vlastnosti. Při mapování na vlastní prvek musí být cílem výraz cesty, ve kterém jsou vnořené prvky odděleny zpětným lomítkem (`/`) a atributy určeny ampersand (`@`). V následujícím příkladu řetězec `UnitsInStock/@ReorderLevel` mapuje hodnotu vlastnosti na atribut pojmenovaný `ReorderLevel` na podřízeném elementu s názvem `UnitsInStock` kořenového elementu položky.<br /><br /> `<Property Name="ReorderLevel" Type="Int16"               m:FC_TargetPath="UnitsInStock/@ReorderLevel"               m:FC_NsPrefix="Northwind"               m:FC_NsUri="http://schemas.examples.microsoft.com/dataservices"               m:FC_KeepInContent="false"               />`<br /><br /> Pokud je cílem název vlastního elementu, `FC_NsPrefix` musí být také zadány atributy a. `FC_NsUri`<br /><br /> `SyndicationPublished:``atom:published` Element.<br /><br /> `SyndicationRights:``atom:rights` Element.<br /><br /> `SyndicationSummary:``atom:summary` Element.<br /><br /> `SyndicationTitle:``atom:title` Element.<br /><br /> `SyndicationUpdated:``atom:updated` Element.<br /><br /> Tato klíčová slova jsou ekvivalentní hodnotám <xref:System.Data.Services.Common.SyndicationItemProperty> výčtu použitým u poskytovatele reflexe.|  
  
> [!NOTE]
> V názvech atributů a hodnotách se rozlišují malá a velká písmena. Atributy lze použít buď na `EntityType` element, nebo na jeden nebo více `Property` prvků, ale nikoli na obě.  
  
## <a name="customizing-feeds-with-the-reflection-provider"></a>Přizpůsobení informačních kanálů pomocí poskytovatele reflexe  
 Chcete-li přizpůsobit kanály pro datový model, který byl implementován pomocí poskytovatele reflexe, přidejte jednu nebo více instancí <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> atributu do tříd, které reprezentují typy entit v datovém modelu. Vlastnosti <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> třídy odpovídají atributům přizpůsobení informačního kanálu, které jsou popsány v předchozí části. Následuje příklad deklarace `Order` typu s mapováním vlastního informačního kanálu definovaného pro obě vlastnosti.  
  
> [!NOTE]
> Datový model pro tento příklad je definován v tématu [postupy: Vytvořte datovou službu pomocí poskytovatele](create-a-data-service-using-rp-wcf-data-services.md)reflexe.  
  
 [!code-csharp[Astoria Custom Feeds#CustomOrderFeed](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_custom_feeds/cs/orderitems.svc.cs#customorderfeed)]
 [!code-vb[Astoria Custom Feeds#CustomOrderFeed](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_custom_feeds/vb/orderitems.svc.vb#customorderfeed)]  
  
 Tyto atributy vytváří pro `Orders` sadu entit následující přizpůsobený datový kanál. V tomto přizpůsobeném informačním kanálu se `OrderId` hodnota vlastnosti zobrazuje pouze `title` v `Customer` prvku `entry` `author` a hodnota vlastnosti zobrazuje jak v elementu, tak jako `Customer` element vlastnosti:  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResult](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/iqueryablefeedresult.xml#iqueryablefeedresult)]  
  
 Další informace najdete v tématu [jak: Přizpůsobte kanály pomocí poskytovatele](how-to-customize-feeds-with-the-reflection-provider-wcf-data-services.md)reflexe.  
  
## <a name="customizing-feeds-with-a-custom-data-service-provider"></a>Přizpůsobení informačních kanálů pomocí vlastního poskytovatele datových služeb  
 Přizpůsobení informačního kanálu pro datový model definovaný pomocí vlastního poskytovatele datové služby je definováno pro typ prostředku voláním metody <xref:System.Data.Services.Providers.ResourceType.AddEntityPropertyMappingAttribute%2A> <xref:System.Data.Services.Providers.ResourceType> , která představuje typ entity v datovém modelu. Další informace najdete v tématu [Vlastní poskytovatelé datových služeb](custom-data-service-providers-wcf-data-services.md).  
  
## <a name="consuming-custom-feeds"></a>Spotřebovávání vlastních kanálů  
 Když vaše aplikace přímo spotřebovává [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informační kanál, musí být schopna zpracovat všechny přizpůsobené prvky a atributy ve vráceném kanálu. Pokud jste v datovém modelu implementovali vlastní kanály bez ohledu na zprostředkovatele datové služby, `$metadata` vrátí koncový bod vlastní informace o kanálu jako atributy vlastního kanálu ve službě CSDL vrácené datovou službou. Když použijete dialogové okno **Přidat odkaz na službu** nebo nástroj [DataSvcUtil. exe](wcf-data-service-client-utility-datasvcutil-exe.md) ke generování tříd klientských dat, přizpůsobené atributy kanálu slouží k zajištění správného zpracování požadavků a odpovědí na datovou službu.  
  
## <a name="feed-customization-considerations"></a>Požadavky na přizpůsobení informačního kanálu  
 Při definování mapování vlastních kanálů byste měli vzít v úvahu následující skutečnosti:  
  
- [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klient považuje mapované prvky v informačním kanálu za prázdné, pokud obsahují pouze prázdné znaky. Z tohoto důvodu nejsou namapované prvky, které obsahují pouze prázdné znaky, nematerializované na klientovi se stejným prázdným znakem. Chcete-li zachovat toto prázdné místo na klientovi, je nutné nastavit hodnotu `KeepInContext` na na `true` v atributu mapování informačního kanálu.  
  
## <a name="versioning-requirements"></a>Požadavky na správu verzí  
 Přizpůsobení informačního kanálu má [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] následující požadavky na verzi protokolu:  
  
- Přizpůsobení informačního kanálu vyžaduje, aby klient i datová služba podporovaly verzi 2,0 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokolu a pozdějších verzí.  
  
 Další informace najdete v tématu [Správa verzí datových služeb](data-service-versioning-wcf-data-services.md).  
  
## <a name="see-also"></a>Viz také:

- [Zprostředkovatel reflexe](reflection-provider-wcf-data-services.md)
- [Zprostředkovatel Entity Framework](entity-framework-provider-wcf-data-services.md)
