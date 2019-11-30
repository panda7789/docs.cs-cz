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
ms.openlocfilehash: 08df16be9df6d55ab9f1426e205e56d9609ce72e
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569226"
---
# <a name="feed-customization-wcf-data-services"></a>Přizpůsobení informačního kanálu (WCF Data Services)
WCF Data Services používá protokol OData (Open Data Protocol) k vystavování dat jako informačního kanálu. OData podporuje formáty Atom i JavaScript Object Notation (JSON) pro datové kanály. Při použití informačního kanálu Atom poskytuje OData standardní metodu pro serializaci dat, jako jsou například entity a vztahy, do formátu XML, který může být součástí textu zprávy HTTP. OData definuje výchozí mapování vlastností entit mezi daty, která jsou obsažená v entitách a elementech Atom. Další informace najdete v tématu [Formát OData: Atom](https://go.microsoft.com/fwlink/?LinkID=185794).  
  
 Můžete mít scénář aplikace, který vyžaduje, aby data vlastnosti vrácená datovou službou byla serializována vlastním způsobem, nikoli ve formátu standardního informačního kanálu. Pomocí protokolu OData můžete v datovém kanálu upravit serializaci tak, aby vlastnosti entity mohly být namapovány na nepoužívané prvky a atributy položky nebo na vlastní prvky položky v informačním kanálu.  
  
> [!NOTE]
> Přizpůsobení informačního kanálu se podporuje jenom pro kanály Atom. Vlastní kanály nejsou vraceny, pokud je pro vrácený kanál požadován formát JSON.  
  
 Pomocí WCF Data Services můžete definovat alternativní mapování vlastností entit pro datovou část Atom ručním použitím atributů na typy entit v datovém modelu. Poskytovatel zdroje dat datové služby určuje, jak byste měli tyto atributy použít.  
  
> [!IMPORTANT]
> Když definujete vlastní kanály, musíte zaručit, že všechny vlastnosti entity, které mají definované vlastní mapování, jsou zahrnuté do projekce. Pokud v projekci není obsažena vlastnost mapované entity, může dojít ke ztrátě dat. Další informace najdete v tématu [projekce dotazů](query-projections-wcf-data-services.md).  
  
## <a name="customizing-feeds-with-the-entity-framework-provider"></a>Přizpůsobení informačních kanálů pomocí poskytovatele Entity Framework  
 Datový model používaný u poskytovatele Entity Framework je v souboru. edmx reprezentován jako XML. V tomto případě jsou atributy, které definují vlastní kanály, přidány do `EntityType` a `Property` prvky, které představují typy entit a vlastnosti v datovém modelu. Tyto atributy přizpůsobení informačního kanálu nejsou definovány ve [formátu\[MC-CSDL\]: koncepčního definičního souboru schématu](https://go.microsoft.com/fwlink/?LinkId=159072), což je formát, který poskytovatel Entity Framework používá k definování datového modelu. Proto je nutné deklarovat atributy přizpůsobení kanálu v konkrétním oboru názvů schématu, který je definován jako `m="http://schemas.microsoft.com/ado/2007/08/dataservices/metadata"`. Následující fragment kódu XML ukazuje atributy přizpůsobení informačního kanálu, které byly aplikovány na `Property` elementy `Products` typu entity, které definují vlastnosti `ProductName`, `ReorderLevel`a `UnitsInStock`.  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedAttributes](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/northwind.csdl#edmfeedattributes)]  
  
 Tyto atributy vytváří následující přizpůsobený datový kanál pro sadu entit `Products`. V přizpůsobeném datovém kanálu se hodnota vlastnosti `ProductName` zobrazuje v prvku `author` a jako `ProductName` prvek vlastnosti a vlastnost `UnitsInStock` je zobrazena ve vlastním prvku, který má svůj vlastní jedinečný obor názvů a s vlastností `ReorderLevel` jako atribut:  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedResultProduct](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/edmfeedresult.xml#edmfeedresultproduct)]  
  
 Další informace najdete v tématu [Postup: přizpůsobení informačních kanálů pomocí poskytovatele Entity Framework](how-to-customize-feeds-with-ef-provider-wcf-data-services.md).  
  
> [!NOTE]
> Vzhledem k tomu, že Entity Designer nepodporuje rozšíření datového modelu, je nutné ručně upravit soubor XML, který obsahuje datový model. Další informace o souboru. edmx, který generuje nástroje model EDM (Entity Data Model), najdete v tématu [Přehled souborů. edmx (Entity Framework)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)).  
  
### <a name="custom-feed-attributes"></a>Vlastní atributy kanálu  
 V následující tabulce jsou uvedeny atributy jazyka XML, které přizpůsobují kanály, které lze přidat do jazyka CSDL (konceptuální schéma Definition Language), který definuje datový model. Tyto atributy jsou ekvivalentní vlastností <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> používaného u poskytovatele reflexe.  
  
|Název atributu|Popis|  
|--------------------|-----------------|  
|`FC_ContentKind`|Určuje typ obsahu. Následující klíčová slova definují typy obsahu syndikace.<br /><br /> `text:` hodnota vlastnosti se v informačním kanálu zobrazí jako text.<br /><br /> `html:` hodnota vlastnosti se v informačním kanálu zobrazí jako HTML.<br /><br /> `xhtml:` hodnota vlastnosti se zobrazí v informačním kanálu jako HTML ve formátu XML.<br /><br /> Tato klíčová slova jsou ekvivalentní hodnotám výčtu <xref:System.Data.Services.Common.SyndicationTextContentKind> použitým u poskytovatele reflexe.<br /><br /> Tento atribut není podporován, je-li použit atribut `FC_NsPrefix` a `FC_NsUri`.<br /><br /> Když zadáte hodnotu `xhtml` atributu `FC_ContentKind`, je nutné zajistit, aby hodnota vlastnosti obsahovala správně formátovaný kód XML. Datová služba vrátí hodnotu bez provedení jakékoli transformace. Musíte také zajistit, aby všechny předpony XML elementů v vráceném kódu XML měly obor názvů URI a předponu definovanou v mapovaném informačním kanálu.|  
|`FC_KeepInContent`|Označuje, že hodnota odkazované vlastnosti by měla být zahrnutá v části obsah informačního kanálu i v mapovaném umístění. Platné hodnoty jsou `true` a `false`. Chcete-li, aby výsledný kanál byl zpětně kompatibilní s dřívějšími verzemi WCF Data Services, zadejte hodnotu `true`, abyste se ujistili, že hodnota je zahrnuta v části obsah informačního kanálu.|  
|`FC_NsPrefix`|Předpona oboru názvů elementu XML v mapování bez syndikace. Tento atribut musí být použit s atributem `FC_NsUri` a nelze jej použít s atributem `FC_ContentKind`.|  
|`FC_NsUri`|Identifikátor URI oboru názvů elementu XML v mapování bez syndikace. Tento atribut musí být použit s atributem `FC_NsPrefix` a nelze jej použít s atributem `FC_ContentKind`.|  
|`FC_SourcePath`|Cesta k vlastnosti entity, na kterou se vztahuje pravidlo mapování kanálu Tento atribut je podporován pouze v případě, že je použit v prvku `EntityType`.<br /><br /> Vlastnost <xref:System.Data.Services.Common.EntityPropertyMappingAttribute.SourcePath%2A> nemůže odkazovat přímo na složitý typ. U komplexních typů je nutné použít výraz cesty, kde jsou názvy vlastností odděleny znakem zpětného lomítka (`/`). Například následující hodnoty jsou povoleny pro typ entity `Person` s vlastností Integer `Age` a komplexní vlastností.<br /><br /> `Address`:<br /><br /> `Age`<br /><br /> `Address/Street`<br /><br /> Vlastnost <xref:System.Data.Services.Common.EntityPropertyMappingAttribute.SourcePath%2A> nelze nastavit na hodnotu, která obsahuje mezeru nebo jakýkoli jiný znak, který není platný v názvu vlastnosti.|  
|`FC_TargetPath`|Název cílového prvku výsledného informačního kanálu, který bude mapovat vlastnost. Tento element může být prvek definovaný specifikacemi Atom nebo vlastním prvkem.<br /><br /> Následující klíčová slova jsou předdefinovaná hodnota cíl syndikace na cestu, která odkazuje na konkrétní umístění v datovém kanálu OData.<br /><br /> `SyndicationAuthorEmail:` podřízený prvek `atom:email` elementu `atom:author`.<br /><br /> `SyndicationAuthorName:` podřízený prvek `atom:name` elementu `atom:author`.<br /><br /> `SyndicationAuthorUri:` podřízený prvek `atom:uri` elementu `atom:author`.<br /><br /> `SyndicationContributorEmail:` podřízený prvek `atom:email` elementu `atom:contributor`.<br /><br /> `SyndicationContributorName:` podřízený prvek `atom:name` elementu `atom:contributor`.<br /><br /> `SyndicationContributorUri:` podřízený prvek `atom:uri` elementu `atom:contributor`.<br /><br /> `SyndicationCustomProperty:` prvek vlastní vlastnosti. Při mapování na vlastní prvek musí být cílem výraz cesty, ve kterém jsou vnořené prvky odděleny zpětným lomítkem (`/`) a atributy jsou určeny znakem ampersand (`@`). V následujícím příkladu řetězec `UnitsInStock/@ReorderLevel` mapuje hodnotu vlastnosti na atribut s názvem `ReorderLevel` na podřízeném elementu s názvem `UnitsInStock` elementu kořenového vstupu.<br /><br /> `<Property Name="ReorderLevel" Type="Int16"               m:FC_TargetPath="UnitsInStock/@ReorderLevel"               m:FC_NsPrefix="Northwind"               m:FC_NsUri="http://schemas.examples.microsoft.com/dataservices"               m:FC_KeepInContent="false"               />`<br /><br /> Pokud je cílem název vlastního elementu, je nutné zadat také atributy `FC_NsPrefix` a `FC_NsUri`.<br /><br /> `SyndicationPublished:` prvek `atom:published`.<br /><br /> `SyndicationRights:` prvek `atom:rights`.<br /><br /> `SyndicationSummary:` prvek `atom:summary`.<br /><br /> `SyndicationTitle:` prvek `atom:title`.<br /><br /> `SyndicationUpdated:` prvek `atom:updated`.<br /><br /> Tato klíčová slova jsou ekvivalentní hodnotám výčtu <xref:System.Data.Services.Common.SyndicationItemProperty> použitým u poskytovatele reflexe.|  
  
> [!NOTE]
> V názvech atributů a hodnotách se rozlišují malá a velká písmena. Atributy lze použít buď na element `EntityType`, nebo na jeden nebo více `Property` prvků, ale nikoli na obě.  
  
## <a name="customizing-feeds-with-the-reflection-provider"></a>Přizpůsobení informačních kanálů pomocí poskytovatele reflexe  
 Chcete-li přizpůsobit kanály pro datový model, který byl implementován pomocí poskytovatele reflexe, přidejte jednu nebo více instancí atributu <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> do tříd, které reprezentují typy entit v datovém modelu. Vlastnosti třídy <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> odpovídají atributům přizpůsobení informačního kanálu, které jsou popsány v předchozí části. Následuje příklad deklarace `Order`ho typu s mapováním vlastního informačního kanálu definovaného pro obě vlastnosti.  
  
> [!NOTE]
> Datový model pro tento příklad je definován v tématu [Postupy: vytvoření datové služby pomocí poskytovatele reflexe](create-a-data-service-using-rp-wcf-data-services.md).  
  
 [!code-csharp[Astoria Custom Feeds#CustomOrderFeed](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_custom_feeds/cs/orderitems.svc.cs#customorderfeed)]
 [!code-vb[Astoria Custom Feeds#CustomOrderFeed](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_custom_feeds/vb/orderitems.svc.vb#customorderfeed)]  
  
 Tyto atributy vytváří následující přizpůsobený datový kanál pro sadu entit `Orders`. V tomto přizpůsobeném informačním kanálu se hodnota vlastnosti `OrderId` zobrazí pouze v prvku `title` `entry` a hodnota vlastnosti `Customer` zobrazí v prvku `author` a jako prvek `Customer` vlastnosti:  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResult](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/iqueryablefeedresult.xml#iqueryablefeedresult)]  
  
 Další informace najdete v tématu [Postup: Přizpůsobení kanálů pomocí poskytovatele reflexe](how-to-customize-feeds-with-the-reflection-provider-wcf-data-services.md).  
  
## <a name="customizing-feeds-with-a-custom-data-service-provider"></a>Přizpůsobení informačních kanálů pomocí vlastního poskytovatele datových služeb  
 Přizpůsobení informačního kanálu pro datový model definovaný pomocí vlastního poskytovatele datových služeb je definováno pro typ prostředku voláním <xref:System.Data.Services.Providers.ResourceType.AddEntityPropertyMappingAttribute%2A> na <xref:System.Data.Services.Providers.ResourceType>, která představuje typ entity v datovém modelu. Další informace najdete v tématu [Vlastní poskytovatelé datových služeb](custom-data-service-providers-wcf-data-services.md).  
  
## <a name="consuming-custom-feeds"></a>Spotřebovávání vlastních kanálů  
 Když vaše aplikace přímo spotřebovává kanál OData, musí být schopna zpracovat všechny přizpůsobené prvky a atributy ve vráceném kanálu. Pokud jste v datovém modelu implementovali vlastní informační kanály bez ohledu na zprostředkovatele datové služby, vrátí `$metadata` koncový bod vlastní informace o kanálu jako atributy vlastního kanálu v CSDL vrácené datovou službou. Když použijete dialogové okno **Přidat odkaz na službu** nebo nástroj [DataSvcUtil. exe](wcf-data-service-client-utility-datasvcutil-exe.md) ke generování tříd klientských dat, přizpůsobené atributy kanálu slouží k zajištění správného zpracování požadavků a odpovědí na datovou službu.  
  
## <a name="feed-customization-considerations"></a>Požadavky na přizpůsobení informačního kanálu  
 Při definování mapování vlastních kanálů byste měli vzít v úvahu následující skutečnosti:  
  
- Klient WCF Data Services považuje mapované prvky v informačním kanálu za prázdné, pokud obsahují pouze prázdné znaky. Z tohoto důvodu nejsou namapované prvky, které obsahují pouze prázdné znaky, nematerializované na klientovi se stejným prázdným znakem. Chcete-li zachovat toto prázdné místo na klientovi, je nutné nastavit hodnotu `KeepInContext` na `true` v atributu mapování informačního kanálu.  
  
## <a name="versioning-requirements"></a>Požadavky na správu verzí  
 Přizpůsobení informačního kanálu má následující požadavky na správu verzí protokolu OData:  
  
- Přizpůsobení informačního kanálu vyžaduje, aby klient i datová služba podporovaly verzi 2,0 protokolu OData a novějších verzí.  
  
 Další informace najdete v tématu [Správa verzí datových služeb](data-service-versioning-wcf-data-services.md).  
  
## <a name="see-also"></a>Viz také:

- [Zprostředkovatel reflexe](reflection-provider-wcf-data-services.md)
- [Zprostředkovatel Entity Framework](entity-framework-provider-wcf-data-services.md)
