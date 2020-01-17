---
title: Zprostředkovatel streamování (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, binary data
- streaming data provider [WCF Data Services]
- WCF Data Services, streams
ms.assetid: f0978fe4-5f9f-42aa-a5c2-df395d7c9495
ms.openlocfilehash: 83f28c50c53281692e1c3c6d55cc55e8d9304ad9
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116596"
---
# <a name="streaming-provider-wcf-data-services"></a>Zprostředkovatel streamování (WCF Data Services)

Datová služba může vystavovat rozsáhlá binární data objektů. Tato binární data mohou představovat video a audio streamy, obrázky, soubory dokumentů nebo jiné typy binárních médií. Když entita v datovém modelu obsahuje jednu nebo více binárních vlastností, vrátí datová služba tato binární data zakódovaná jako základní-64 uvnitř záznamu v kanálu odpovědí. Vzhledem k tomu, že načítání a serializace velkých binárních dat tímto způsobem může ovlivnit výkon, rozhraní Open Data Protocol (OData) definuje mechanismus pro načítání binárních dat nezávisle na entitě, ke které patří. Toho je možné dosáhnout oddělením binárních dat z entity do jednoho nebo více datových proudů.

- Media Resource – binární data, která patří do určité entity, jako je video, zvuk, obrázek nebo jiný typ datového proudu mediálních prostředků.

- Položka odkazu na média – entita, která má odkaz na související datový proud mediálních prostředků.

Pomocí WCF Data Services definujete binární datový proud prostředku implementací poskytovatele dat streamování. Implementace poskytovatele streamování poskytuje datovou službu pomocí datového proudu mediálních prostředků přidruženého ke konkrétní entitě jako objekt <xref:System.IO.Stream>. Tato implementace umožňuje datové službě přijímat a vracet mediální prostředky přes HTTP jako binární datové proudy zadaného typu MIME.

Konfigurace datové služby pro podporu streamování binárních dat vyžaduje následující kroky:

1. Jeden nebo více entit v datovém modelu jako položka odkaz na médium Tyto entity by neměly zahrnovat binární data, která se mají streamovat. Všechny binární vlastnosti entity se vždycky vrátí v položce jako binární soubor s kódováním Base-64.

2. Implementujte rozhraní T:System.Data.Services.Providers.IDataServiceStreamProvider.

3. Definujte datovou službu, která implementuje rozhraní <xref:System.IServiceProvider>. Datová služba používá implementaci <xref:System.IServiceProvider.GetService%2A> pro přístup k implementaci poskytovatele datových proudů. Tato metoda vrátí příslušnou implementaci poskytovatele streamování.

4. V konfiguraci webové aplikace povolte velké proudy zpráv.

5. Povolte přístup k binárním prostředkům na serveru nebo ve zdroji dat.

Příklady v tomto tématu jsou založené na ukázkové službě streamování fotek, která je popsaná v hloubkě v rámci [série zprostředkovatelů streamování Data Services: implementace poskytovatele streamování (část 1)](https://docs.microsoft.com/archive/blogs/astoriateam/data-services-streaming-provider-series-implementing-a-streaming-provider-part-1). Zdrojový kód pro ukázku datové služby streamování fotek je k dispozici na [GitHubu](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/Streaming%20Photo%20OData%20Service%20Sample).

## <a name="defining-a-media-link-entry-in-the-data-model"></a>Definování položky s odkazem na média v datovém modelu

Zprostředkovatel zdroje dat určuje způsob, jakým je entita definovaná jako položka odkazu na média v datovém modelu.

**Zprostředkovatel Entity Framework**

Chcete-li označit, že entita je položkou Media Link Entry, přidejte atribut `HasStream` do definice typu entity v koncepčním modelu, jak je uvedeno v následujícím příkladu:

[!code-xml[Astoria Photo Streaming Service#HasStream](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_photo_streaming_service/xml/photodata.edmx#hasstream)]

Také je nutné přidat obor názvů `xmlns:m=http://schemas.microsoft.com/ado/2007/08/dataservices/metadata` buď k entitě, nebo ke kořenu souboru. edmx nebo. csdl, který definuje datový model.

Příklad datové služby, která používá poskytovatele Entity Framework a zpřístupňuje mediální prostředek, najdete v části post [Data Services poskytovatelé streamování: implementace poskytovatele streamování (část 1)](https://docs.microsoft.com/archive/blogs/astoriateam/data-services-streaming-provider-series-implementing-a-streaming-provider-part-1).

**Zprostředkovatel reflexe**

Chcete-li označit, že entita je položkou Media Link Entry, přidejte <xref:System.Data.Services.Common.HasStreamAttribute> ke třídě, která definuje typ entity v poskytovateli reflexe.

**Vlastní poskytovatel datových služeb**

Při použití vlastních poskytovatelů služeb implementujete rozhraní <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> k definování metadat pro datovou službu. Další informace najdete v tématu [Vlastní poskytovatelé datových služeb](custom-data-service-providers-wcf-data-services.md). Určíte, že binární datový proud prostředku patří do <xref:System.Data.Services.Providers.ResourceType> nastavením vlastnosti <xref:System.Data.Services.Providers.ResourceType.IsMediaLinkEntry%2A> na `true` na <xref:System.Data.Services.Providers.ResourceType>, který představuje typ entity, což je položka odkazu na média.

## <a name="implementing-the-idataservicestreamprovider-interface"></a>Implementace rozhraní IDataServiceStreamProvider

Chcete-li vytvořit datovou službu, která podporuje binární datové proudy, je nutné implementovat rozhraní <xref:System.Data.Services.Providers.IDataServiceStreamProvider>. Tato implementace umožňuje datové službě vracet binární data jako datový proud klientovi a využívat binární data jako datový proud odeslaný z klienta. Datová služba vytvoří instanci tohoto rozhraní, kdykoli potřebuje přístup k binárním datům jako datový proud. Rozhraní <xref:System.Data.Services.Providers.IDataServiceStreamProvider> určuje následující členy:

|Název členu|Popis|
|-----------------|-----------------|
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.DeleteStream%2A>|Tato metoda je vyvolána datovou službou k odstranění odpovídajícího mediálního prostředku, pokud je odstraněna její položka odkazu na média. Při implementaci <xref:System.Data.Services.Providers.IDataServiceStreamProvider>obsahuje tato metoda kód, který odstraní mediální zdroj přidružený k zadané položce Media Link.|
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStream%2A>|Tato metoda je vyvolána datovou službou, aby vracela mediální prostředek jako datový proud. Pokud implementujete <xref:System.Data.Services.Providers.IDataServiceStreamProvider>, tato metoda obsahuje kód, který poskytuje datový proud, který je používán datovou službou, na prostředek vráceného média, který je přidružen k zadané položce Media Link.|
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStreamUri%2A>|Tato metoda je vyvolána datovou službou, která vrací identifikátor URI, který se používá k vyžádání mediálního prostředku pro položku odkazu na média. Tato hodnota se používá k vytvoření atributu `src` v prvku Content položky odkazu na média a který se používá k vyžádání datového proudu. Když tato metoda vrátí `null`, datová služba automaticky určí identifikátor URI. Tuto metodu použijte, pokud potřebujete poskytnout klientům přímý přístup k binárním datům bez použití poskytovatele datových proudů.|
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetStreamContentType%2A>|Tato metoda je vyvolána datovou službou, aby vracela hodnotu typu obsahu mediálního prostředku, který je přidružen k zadané položce s odkazem na médium.|
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetStreamETag%2A>|Tato metoda je vyvolána datovou službou pro vrácení eTag datového proudu, který je přidružen k zadané entitě. Tato metoda se používá, když spravujete souběžnost pro binární data. Pokud tato metoda vrátí hodnotu null, datová služba nesleduje souběžnost.|
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A>|Tato metoda je vyvolána datovou službou, aby získala datový proud, který se používá při přijímání datového proudu odeslaného z klienta. Při implementaci <xref:System.Data.Services.Providers.IDataServiceStreamProvider>musíte vrátit zapisovatelný datový proud, do kterého datová služba zapisuje přijatá data datového proudu.|
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.ResolveType%2A>|Vrátí název typu kvalifikovaný obor názvů, který představuje typ, který musí modul runtime datové služby vytvořit pro položku odkazu na média přidruženou k datovému proudu pro mediální prostředek, který se právě vkládá.|

## <a name="creating-the-streaming-data-service"></a>Vytvoření služby streamování dat

Aby modul runtime WCF Data Services poskytoval přístup k implementaci <xref:System.Data.Services.Providers.IDataServiceStreamProvider>, je nutné, aby datová služba, kterou vytvoříte, také implementovala rozhraní <xref:System.IServiceProvider>. Následující příklad ukazuje, jak implementovat metodu <xref:System.IServiceProvider.GetService%2A> pro vrácení instance `PhotoServiceStreamProvider` třídy, která implementuje <xref:System.Data.Services.Providers.IDataServiceStreamProvider>.

[!code-csharp[Astoria Photo Streaming Service#PhotoServiceStreamingProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_photo_streaming_service/cs/photodata.svc.cs#photoservicestreamingprovider)]
[!code-vb[Astoria Photo Streaming Service#PhotoServiceStreamingProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_photo_streaming_service/vb/photodata.svc.vb#photoservicestreamingprovider)]

Obecné informace o tom, jak vytvořit datovou službu, najdete v tématu [konfigurace datové služby](configuring-the-data-service-wcf-data-services.md).

## <a name="enabling-large-binary-streams-in-the-hosting-environment"></a>Povolení rozsáhlých binárních proudů v hostitelském prostředí

Při vytváření datové služby ve webové aplikaci v ASP.NET se k poskytování implementace protokolu HTTP používá Windows Communication Foundation (WCF). Ve výchozím nastavení služba WCF omezuje velikost zpráv HTTP pouze na 65 KB. Aby bylo možné streamovat rozsáhlá binární data do a z datové služby, musíte také nakonfigurovat webovou aplikaci tak, aby povolovala velké binární soubory a používala datové proudy k přenosu. Chcete-li to provést, přidejte následující do `<configuration />` element souboru Web. config aplikace:

> [!NOTE]
> Je nutné použít režim přenosu <xref:System.ServiceModel.TransferMode.Streamed?displayProperty=nameWithType>, abyste zajistili, že se binární data v žádostech a zprávách o odezvě streamují do vyrovnávací paměti pomocí služby WCF.

Další informace najdete v tématu [streamování přenosů zpráv](../../wcf/feature-details/streaming-message-transfer.md) a přenosových [kvót](../../wcf/feature-details/transport-quotas.md).

Ve výchozím nastavení služba Internetová informační služba (IIS) také omezuje velikost požadavků na 4 MB. Chcete-li službě Data Service povolit příjem datových proudů větších než 4 MB při spuštění služby IIS, je nutné také nastavit atribut `maxRequestLength` [elementu httpRuntime (schéma nastavení ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e1f13641(v=vs.100)) v oddílu `<system.web />` konfigurace, jak je znázorněno v následujícím příkladu:

## <a name="using-data-streams-in-a-client-application"></a>Použití datových proudů v klientské aplikaci

Klientská knihovna WCF Data Services umožňuje načíst a aktualizovat tyto vystavené prostředky jako binární datové proudy na klientovi. Další informace najdete v tématu [práce s binárními daty](working-with-binary-data-wcf-data-services.md).

## <a name="considerations-for-working-with-a-streaming-provider"></a>Pokyny pro práci s poskytovatelem streamování

Níže jsou uvedené věci, které je potřeba zvážit při implementaci poskytovatele streamování a při přístupu k prostředkům médií z datové služby.

- Žádosti o sloučení nejsou u mediálních prostředků podporovány. Použijte požadavek PUT ke změně mediálního prostředku existující entity.

- Požadavek POST nelze použít k vytvoření nové položky odkaz na médium. Místo toho musíte vydat požadavek POST pro vytvoření nového mediálního prostředku a datová služba vytvoří novou položku odkazu na média s výchozími hodnotami. Tuto novou entitu je možné aktualizovat následnou SLOUČENÍm nebo požadavkem PUT. Můžete také zvážit, že entitu budete ukládat do mezipaměti a dělat v ní aktualizace, jako je například nastavení hodnoty vlastnosti na hodnotu záhlaví v žádosti POST.

- Po přijetí žádosti POST datová služba zavolá <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> k vytvoření mediálního prostředku před tím, než zavolá <xref:System.Data.Services.IUpdatable.SaveChanges%2A> a vytvoří položku odkazu na média.

- Implementace <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> by neměla vracet objekt <xref:System.IO.MemoryStream>. Pokud použijete tento druh streamu, dojde k problémům se zdrojem paměti, když služba obdrží velmi velké datové proudy.

- Při ukládání mediálních prostředků do databáze zvažte následující věci:

  - Binární vlastnost, která je zdrojem médií, by neměla být součástí datového modelu. Všechny vlastnosti vystavené v datovém modelu jsou vraceny v záznamu v kanálu odpovědí.

  - Chcete-li zvýšit výkon pomocí velkého binárního datového proudu, doporučujeme vytvořit vlastní třídu datového proudu pro ukládání binárních dat v databázi. Tuto třídu vrátí vaše implementace <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> a pošle binární data do databáze v blocích. V případě SQL Server databáze doporučujeme použít k streamování dat do databáze FILESTREAM, pokud jsou binární data větší než 1 MB.

  - Ujistěte se, že je vaše databáze navržená tak, aby ukládala binární velké proudy, které má vaše datová služba přijmout.

  - Když klient odešle požadavek POST, aby vložil záznam z média s mediálním prostředkem v jediném požadavku, <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> se volá, aby získal datový proud předtím, než datová služba vloží novou entitu do databáze. Implementace poskytovatele streamování musí být schopná zpracovat chování této datové služby. Zvažte použití samostatné tabulky dat k uložení binárních dat nebo uložení datového proudu do souboru, dokud se entita do databáze nevloží.

- Při implementaci metod <xref:System.Data.Services.Providers.IDataServiceStreamProvider.DeleteStream%2A>, <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStream%2A>nebo <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> je nutné použít hodnoty eTag a Content-Type, které jsou zadány jako parametry metody. V implementaci poskytovatele <xref:System.Data.Services.Providers.IDataServiceStreamProvider> nenastavujte záhlaví eTag nebo Content-Type.

- Ve výchozím nastavení klient odesílá velké binární proudy pomocí bloku HTTP Transfer-Encoding. Vzhledem k tomu, že vývojový server ASP.NET nepodporuje tento druh kódování, nelze tento webový server použít k hostování datové služby streamování, která musí přijímat velké binární proudy. Další informace o ASP.NET vývojovém serveru naleznete v tématu [webové servery v aplikaci Visual Studio pro webové projekty ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/58wxa9w5(v=vs.120)).

<a name="versioning"></a>

## <a name="versioning-requirements"></a>Požadavky na správu verzí

Zprostředkovatel streamování má následující požadavky na správu verzí protokolu OData:

- Zprostředkovatel streamování vyžaduje, aby datová služba podporovala verzi 2,0 protokolu OData a novějších verzí.

Další informace najdete v tématu [Správa verzí datových služeb](data-service-versioning-wcf-data-services.md).

## <a name="see-also"></a>Viz také:

- [Zprostředkovatelé datových služeb](data-services-providers-wcf-data-services.md)
- [Vlastní zprostředkovatelé datových služeb](custom-data-service-providers-wcf-data-services.md)
- [Práce s binárními daty](working-with-binary-data-wcf-data-services.md)
