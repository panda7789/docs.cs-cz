---
title: Práce s binárními daty (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, binary data
- WCF Data Services, streams
ms.assetid: aeccc45c-d5c5-4671-ad63-a492ac8043ac
ms.openlocfilehash: aa3e58d559121aaca401e7b851a4b4fd8e7753cd
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900834"
---
# <a name="working-with-binary-data-wcf-data-services"></a>Práce s binárními daty (WCF Data Services)

Klientská knihovna WCF Data Services umožňuje načíst a aktualizovat binární data z informačního kanálu OData (Open Data Protocol) jedním z následujících způsobů:

- Jako vlastnost primitivního typu entity. Toto je doporučená metoda pro práci s malými binárními datovými objekty, které je možné snadno načíst do paměti. V tomto případě binární vlastnost je vlastnost entity zveřejněná datovým modelem a datová služba serializace binární data jako binární kódovaný kód XML ve zprávě odpovědi Base-64.

- Jako samostatný binární datový proud prostředků. Toto je doporučená metoda pro přístup k datům binárních rozsáhlých objektů (BLOB), které mohou představovat fotografii, video nebo jakýkoli jiný typ binárních kódovaných dat, a jejich změny.

WCF Data Services implementuje streamování binárních dat pomocí protokolu HTTP, jak je definováno v OData. V tomto mechanismu se binární data považují za mediální prostředek, který je oddělený od, ale s entitou, která se nazývá záznam pro Media Link. Další informace najdete v tématu [poskytovatel streamování](streaming-provider-wcf-data-services.md).

> [!TIP]
> Podrobný příklad vytvoření klientské aplikace Windows Presentation Foundation (WPF), která stahuje soubory binárních imagí ze služby OData, která ukládá fotky, najdete v [části post Data Services zprostředkovatele streamování – část 2: přístup k datovému proudu mediálních prostředků z klienta](https://docs.microsoft.com/archive/blogs/astoriateam/data-services-streaming-provider-series-part-2-accessing-a-media-resource-stream-from-the-client). Pokud si chcete stáhnout vzorový kód pro službu Stream Photo data Service, která je vybraná v blogovém příspěvku, podívejte se na [ukázku datové služby streamování Photo data](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/Streaming%20Photo%20OData%20Service%20Sample) na GitHubu.

## <a name="entity-metadata"></a>Metadata entit

Entita, která má související datový proud mediálních prostředků, je v metadatech datové služby označená atributem `HasStream` použitým pro typ entity, která je položkou odkazu na média. V následujícím příkladu je `PhotoInfo` entitou záznam médií s odpovídajícím mediálním prostředkem, který je označen atributem `HasStream`.

[!code-xml[Astoria Photo Streaming Service#HasStream](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_photo_streaming_service/xml/photodata.edmx#hasstream)]

Zbývající příklady v tomto tématu ukazují, jak používat a měnit datový proud mediálních prostředků. Úplný příklad toho, jak používat datový proud mediálních prostředků v .NET Framework klientské aplikace pomocí WCF Data Services klientské knihovny, najdete v příspěvku [přístup k datovému proudu mediálních prostředků z klienta](https://docs.microsoft.com/archive/blogs/astoriateam/data-services-streaming-provider-series-part-2-accessing-a-media-resource-stream-from-the-client).

## <a name="accessing-the-binary-resource-stream"></a>Přístup k binárnímu datovému proudu prostředků

Klientská knihovna WCF Data Services poskytuje metody pro přístup k datovým proudům binárních prostředků z datové služby založené na OData. Při stahování mediálního prostředku můžete použít buď identifikátor URI mediálního prostředku, nebo můžete získat binární datový proud, který obsahuje data mediálních prostředků. Data prostředků médií můžete také nahrát jako binární datový proud.

> [!TIP]
> Podrobný příklad vytvoření klientské aplikace Windows Presentation Foundation (WPF), která stahuje soubory binárních imagí ze služby OData, která ukládá fotky, najdete v [části post Data Services zprostředkovatele streamování – část 2: přístup k datovému proudu mediálních prostředků z klienta](https://docs.microsoft.com/archive/blogs/astoriateam/data-services-streaming-provider-series-part-2-accessing-a-media-resource-stream-from-the-client). Pokud si chcete stáhnout vzorový kód pro službu Stream Photo data Service, která je vybraná v blogovém příspěvku, podívejte se na [ukázku datové služby streamování Photo data](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/Streaming%20Photo%20OData%20Service%20Sample) na GitHubu.

### <a name="getting-the-uri-of-the-binary-stream"></a>Získávání identifikátoru URI binárního datového proudu

Při načítání určitých typů mediálních prostředků, jako jsou obrázky a jiné mediální soubory, je často snazší použít identifikátor URI mediálního prostředku ve vaší aplikaci, než je třeba zpracovat binární datový proud. Chcete-li získat identifikátor URI datového proudu prostředků přidruženého k záznamu média, je nutné volat metodu <xref:System.Data.Services.Client.DataServiceContext.GetReadStreamUri%2A> v instanci <xref:System.Data.Services.Client.DataServiceContext>, která sleduje entitu. Následující příklad ukazuje, jak zavolat metodu <xref:System.Data.Services.Client.DataServiceContext.GetReadStreamUri%2A> pro získání identifikátoru URI datového proudu mediálního prostředku, který se používá k vytvoření nové image v klientovi:

[!code-csharp[Astoria Photo Streaming Client#GetReadStreamUri](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_photo_streaming_client/cs/photowindow.xaml.cs#getreadstreamuri)]
[!code-vb[Astoria Photo Streaming Client#GetReadStreamUri](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_photo_streaming_client/vb/photowindow.xaml.vb#getreadstreamuri)]

### <a name="downloading-the-binary-resource-stream"></a>Stahuje se binární datový proud prostředků.

Při načítání binárního datového proudu prostředků je nutné volat metodu <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> v instanci <xref:System.Data.Services.Client.DataServiceContext>, která sleduje položku odkazu na média. Tato metoda pošle požadavek na datovou službu, která vrátí objekt <xref:System.Data.Services.Client.DataServiceStreamResponse>, který má odkaz na datový proud, který obsahuje prostředek. Tuto metodu použijte, pokud vaše aplikace vyžaduje binární prostředek jako <xref:System.IO.Stream>. Následující příklad ukazuje, jak zavolat metodu <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> pro načtení datového proudu, který se používá k vytvoření nové image v klientovi:

[!code-csharp[Astoria Streaming Client#GetReadStreamClient](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_streaming_client/cs/customerphotowindow.xaml.cs#getreadstreamclient)]
[!code-vb[Astoria Streaming Client#GetReadStreamClient](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_streaming_client/vb/customerphotowindow.xaml.vb#getreadstreamclient)]

> [!NOTE]
> Hlavička Content-Length ve zprávě odpovědi, která obsahuje binární datový proud, není nastavena datovou službou. Tato hodnota nemusí odrážet skutečnou délku binárního datového proudu.

### <a name="uploading-a-media-resource-as-a-stream"></a>Nahrání mediálního prostředku jako datového proudu

Chcete-li vložit nebo aktualizovat mediální prostředek, zavolejte metodu <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> v instanci <xref:System.Data.Services.Client.DataServiceContext>, která sleduje entitu. Tato metoda pošle požadavek na datovou službu, která obsahuje prostředek média načtený ze zadaného datového proudu. Následující příklad ukazuje, jak zavolat metodu <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> pro odeslání obrázku do datové služby:

[!code-csharp[Astoria Photo Streaming Client#SetSaveStream](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_photo_streaming_client/cs/photodetailswindow.xaml.cs#setsavestream)]
[!code-vb[Astoria Photo Streaming Client#SetSaveStream](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_photo_streaming_client/vb/photodetailswindow.xaml.vb#setsavestream)]

V tomto příkladu je volána metoda <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> poskytnutím hodnoty `true` pro parametr `closeStream`. To zaručuje, že <xref:System.Data.Services.Client.DataServiceContext> zavírá datový proud po nahrání binárních dat do datové služby.

> [!NOTE]
> Když zavoláte <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A>, datový proud nebude odeslán do datové služby, dokud není volána <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A>.

## <a name="see-also"></a>Viz také:

- [Klientská knihovna pro WCF Data Services](wcf-data-services-client-library.md)
- [Vazba dat k ovládacím prvkům](binding-data-to-controls-wcf-data-services.md)
