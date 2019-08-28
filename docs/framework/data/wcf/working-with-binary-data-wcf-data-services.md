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
ms.openlocfilehash: 21501ec9d0af4c785dd86946fa34c1041bb34b9d
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70043902"
---
# <a name="working-with-binary-data-wcf-data-services"></a>Práce s binárními daty (WCF Data Services)

Klientská knihovna umožňuje načíst a aktualizovat binární data [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] z informačního kanálu jedním z následujících způsobů: [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]

- Jako vlastnost primitivního typu entity. Toto je doporučená metoda pro práci s malými binárními datovými objekty, které je možné snadno načíst do paměti. V tomto případě binární vlastnost je vlastnost entity zveřejněná datovým modelem a datová služba serializace binární data jako binární kódovaný kód XML ve zprávě odpovědi Base-64.

- Jako samostatný binární datový proud prostředků. Toto je doporučená metoda pro přístup k datům binárních rozsáhlých objektů (BLOB), které mohou představovat fotografii, video nebo jakýkoli jiný typ binárních kódovaných dat, a jejich změny.

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]implementuje streamování binárních dat pomocí protokolu HTTP, jak je definováno [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]v. V tomto mechanismu se binární data považují za mediální prostředek, který je oddělený od, ale s entitou, která se nazývá záznam pro Media Link. Další informace najdete v tématu [poskytovatel streamování](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).

> [!TIP]
> Podrobný příklad vytvoření klientské aplikace Windows Presentation Foundation (WPF), která stahuje soubory binárních imagí ze [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] služby, která ukládá fotky, najdete v části post [Data Services zprostředkovatel streamování – část 2: Přístup k datovému proudu mediálních prostředků](https://go.microsoft.com/fwlink/?LinkId=201637)z klienta. Pokud si chcete stáhnout vzorový kód pro službu Stream Photo data Service podanou v blogovém příspěvku, podívejte se na [ukázku služby streamování fotek data](https://go.microsoft.com/fwlink/?LinkId=198988) v galerii kódu na webu MSDN.

## <a name="entity-metadata"></a>Metadata entit

Entita, která má související datový proud mediálních prostředků, je uvedena v metadatech datové služby `HasStream` podle atributu použitého pro typ entity, který je položkou odkazu na média. V následujícím příkladu `PhotoInfo` je entita položkou Media linku, která má související mediální prostředek, který je označen `HasStream` atributem.

[!code-xml[Astoria Photo Streaming Service#HasStream](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_photo_streaming_service/xml/photodata.edmx#hasstream)]

Zbývající příklady v tomto tématu ukazují, jak používat a měnit datový proud mediálních prostředků. Úplný příklad toho, jak používat datový proud mediálních prostředků v .NET Framework klientské aplikace pomocí [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klientské knihovny, najdete v příspěvku přístup k datovému [proudu mediálních prostředků z klienta](https://go.microsoft.com/fwlink/?LinkID=201637).

## <a name="accessing-the-binary-resource-stream"></a>Přístup k binárnímu datovému proudu prostředků

Klientská knihovna poskytuje metody pro přístup k datovým proudům [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]binárních prostředků z datové služby založené na datech. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Při stahování mediálního prostředku můžete použít buď identifikátor URI mediálního prostředku, nebo můžete získat binární datový proud, který obsahuje data mediálních prostředků. Data prostředků médií můžete také nahrát jako binární datový proud.

> [!TIP]
> Podrobný příklad vytvoření klientské aplikace Windows Presentation Foundation (WPF), která stahuje soubory binárních imagí ze [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] služby, která ukládá fotky, najdete v části post [Data Services zprostředkovatel streamování – část 2: Přístup k datovému proudu mediálních prostředků](https://go.microsoft.com/fwlink/?LinkId=201637)z klienta. Pokud si chcete stáhnout vzorový kód pro službu Stream Photo data Service podanou v blogovém příspěvku, podívejte se na [ukázku služby streamování fotek data](https://go.microsoft.com/fwlink/?LinkId=198988) v galerii kódu na webu MSDN.

### <a name="getting-the-uri-of-the-binary-stream"></a>Získávání identifikátoru URI binárního datového proudu

Při načítání určitých typů mediálních prostředků, jako jsou obrázky a jiné mediální soubory, je často snazší použít identifikátor URI mediálního prostředku ve vaší aplikaci, než je třeba zpracovat binární datový proud. Chcete-li získat identifikátor URI datového proudu prostředků přidruženého k záznamu média, je nutné zavolat <xref:System.Data.Services.Client.DataServiceContext.GetReadStreamUri%2A> metodu <xref:System.Data.Services.Client.DataServiceContext> na instanci, která sleduje entitu. Následující příklad ukazuje, jak zavolat <xref:System.Data.Services.Client.DataServiceContext.GetReadStreamUri%2A> metodu pro získání identifikátoru URI datového proudu mediálního prostředku, který se používá k vytvoření nové image v klientovi:

[!code-csharp[Astoria Photo Streaming Client#GetReadStreamUri](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_photo_streaming_client/cs/photowindow.xaml.cs#getreadstreamuri)]
[!code-vb[Astoria Photo Streaming Client#GetReadStreamUri](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_photo_streaming_client/vb/photowindow.xaml.vb#getreadstreamuri)]

### <a name="downloading-the-binary-resource-stream"></a>Stahuje se binární datový proud prostředků.

Při načítání binárního datového proudu prostředků je nutné zavolat <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> metodu <xref:System.Data.Services.Client.DataServiceContext> na instanci, která sleduje položku odkazu na média. Tato metoda pošle požadavek na datovou službu, která vrátí <xref:System.Data.Services.Client.DataServiceStreamResponse> objekt, který má odkaz na datový proud, který obsahuje prostředek. Tuto metodu použijte, pokud vaše aplikace vyžaduje binární prostředek jako <xref:System.IO.Stream>. Následující příklad ukazuje, jak zavolat <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> metodu pro načtení datového proudu, který se používá k vytvoření nové image v klientovi:

[!code-csharp[Astoria Streaming Client#GetReadStreamClient](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_streaming_client/cs/customerphotowindow.xaml.cs#getreadstreamclient)]
[!code-vb[Astoria Streaming Client#GetReadStreamClient](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_streaming_client/vb/customerphotowindow.xaml.vb#getreadstreamclient)]

> [!NOTE]
> Hlavička Content-Length ve zprávě odpovědi, která obsahuje binární datový proud, není nastavena datovou službou. Tato hodnota nemusí odrážet skutečnou délku binárního datového proudu.

### <a name="uploading-a-media-resource-as-a-stream"></a>Nahrání mediálního prostředku jako datového proudu

Chcete-li vložit nebo aktualizovat mediální prostředek, zavolejte <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> metodu <xref:System.Data.Services.Client.DataServiceContext> na instanci, která sleduje entitu. Tato metoda pošle požadavek na datovou službu, která obsahuje prostředek média načtený ze zadaného datového proudu. Následující příklad ukazuje, jak zavolat <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> metodu pro odeslání obrázku do datové služby:

[!code-csharp[Astoria Photo Streaming Client#SetSaveStream](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_photo_streaming_client/cs/photodetailswindow.xaml.cs#setsavestream)]
[!code-vb[Astoria Photo Streaming Client#SetSaveStream](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_photo_streaming_client/vb/photodetailswindow.xaml.vb#setsavestream)]

V tomto příkladu <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> je metoda volána zadáním `true` hodnoty `closeStream` parametru. To zaručuje, že <xref:System.Data.Services.Client.DataServiceContext> zavře datový proud po nahrání binárních dat do datové služby.

> [!NOTE]
> Když zavoláte <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A>, datový proud nebude odeslán do datové služby, dokud <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> není volána metoda.

## <a name="see-also"></a>Viz také:

- [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [Vazba dat k ovládacím prvkům](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)
