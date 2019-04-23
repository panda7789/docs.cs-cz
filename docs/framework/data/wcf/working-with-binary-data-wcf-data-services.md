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
ms.openlocfilehash: de85a3aca629582e79712b71ae2e3413b919ab28
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59517236"
---
# <a name="working-with-binary-data-wcf-data-services"></a>Práce s binárními daty (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klientská knihovna umožňuje načíst a aktualizovat binární data ze [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] kanálu v jednom z následujících způsobů:  
  
-   Jako vlastnost primitivního typu entity. Toto je doporučená metoda pro práci s daty malé binární objekty, které je možné snadno načíst do paměti. V tomto případě binární vlastnost je vlastnost entity vystavené datový model a datové služby serializuje binárních dat jako XML binární kódováním base-64 ve zprávě s odpovědí.  
  
-   Jako samostatný prostředek binární datový proud. Toto je doporučená metoda pro přístup k a změna data binárního rozsáhlého objektu (BLOB), který může představovat fotografie, video nebo jakéhokoli jiného typu zakódovaná binární data.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] implementuje streamování binární data pomocí protokolu HTTP, jak jsou definovány v [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. Binární data v tento mechanismus je považován za mediální zdroj, který je oddělený od ale souvisejících s entitou, která se nazývá položku media link entry. Další informace najdete v tématu [streamování poskytovatele](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).  
  
> [!TIP]
>  Podrobný příklad toho, jak vytvořit klientskou aplikaci Windows Presentation Foundation (WPF), která stahuje soubory binární obrázků ze [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] služba, která ukládá fotografie, najdete v příspěvku [dat služby streamování poskytovatele –. část 2: Přístup k Stream zdroj média z klienta](https://go.microsoft.com/fwlink/?LinkId=201637). Stáhněte si ukázkový kód pro službu datového proudu fotografií dat vybrané v blogovém příspěvku, najdete v článku [streamování fotek ukázková Data pro služby](https://go.microsoft.com/fwlink/?LinkId=198988) v Galerie kódu na webu MSDN.  
  
## <a name="entity-metadata"></a>Metadata entit  
 Entita, která má související datový proud prostředků je podle metadat datové služby pomocí `HasStream` atribut použitý pro typ entity, která je položka s odkazem na médium. V následujícím příkladu `PhotoInfo` entita je položku media link entry, která má související zdroje média, indikován `HasStream` atribut.  
  
 [!code-xml[Astoria Photo Streaming Service#HasStream](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_photo_streaming_service/xml/photodata.edmx#hasstream)]  
  
 Zbývající příklady v tomto tématu ukazují, jak získávat přístup a měnit datový proud prostředků média. Úplný příklad toho, jak využívat datový proud prostředku média v klientské aplikaci rozhraní .NET Framework pomocí [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klientské knihovny, najdete v příspěvku [přístup k Stream zdroj média z klienta](https://go.microsoft.com/fwlink/?LinkID=201637).  
  
## <a name="accessing-the-binary-resource-stream"></a>Přístup k Stream binární prostředek  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klientská knihovna poskytuje metody pro přístup k datové proudy binární prostředek ze [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]– na základě dat služby. Při stahování prostředku média, můžete použít buď identifikátor URI prostředku média nebo můžete získat binární datový proud, který obsahuje vlastní data zdroj média. Můžete také nahrát data prostředku média jako binárního datového proudu.  
  
> [!TIP]
>  Podrobný příklad toho, jak vytvořit klientskou aplikaci Windows Presentation Foundation (WPF), která stahuje soubory binární obrázků ze [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] služba, která ukládá fotografie, najdete v příspěvku [dat služby streamování poskytovatele –. část 2: Přístup k Stream zdroj média z klienta](https://go.microsoft.com/fwlink/?LinkId=201637). Stáhněte si ukázkový kód pro službu datového proudu fotografií dat vybrané v blogovém příspěvku, najdete v článku [streamování fotek ukázková Data pro služby](https://go.microsoft.com/fwlink/?LinkId=198988) v Galerie kódu na webu MSDN.  
  
### <a name="getting-the-uri-of-the-binary-stream"></a>Získání identifikátoru URI binární Stream  
 Při načítání určitých typů prostředků média, jako jsou obrázky a další soubory médií, často je jednodušší použít identifikátor URI prostředku médií ve vaší aplikaci než zpracování samotný datový proud binárních dat. Chcete-li získat identifikátor URI přidružený k položku dávající media link entry datový proud prostředku, musí volat <xref:System.Data.Services.Client.DataServiceContext.GetReadStreamUri%2A> metodu na <xref:System.Data.Services.Client.DataServiceContext> instanci, která se sleduje subjekt. Následující příklad ukazuje, jak volat <xref:System.Data.Services.Client.DataServiceContext.GetReadStreamUri%2A> metodu k získání identifikátoru URI datový proud prostředku média, který se používá k vytvoření nové bitové kopie na straně klienta:  
  
 [!code-csharp[Astoria Photo Streaming Client#GetReadStreamUri](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_photo_streaming_client/cs/photowindow.xaml.cs#getreadstreamuri)]
 [!code-vb[Astoria Photo Streaming Client#GetReadStreamUri](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_photo_streaming_client/vb/photowindow.xaml.vb#getreadstreamuri)]  
  
### <a name="downloading-the-binary-resource-stream"></a>Stažení binárního prostředku Stream  
 Při načítání datového proudu binární prostředek, je nutné volat <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> metodu <xref:System.Data.Services.Client.DataServiceContext> instanci, která se ke sledování položka media link entry. Tato metoda odešle požadavek do služby data, která vrací <xref:System.Data.Services.Client.DataServiceStreamResponse> objektu, který obsahuje odkaz na datový proud, který obsahuje prostředek. Tuto metodu použijte, pokud vaše aplikace vyžaduje binární prostředek jako <xref:System.IO.Stream>. Následující příklad ukazuje, jak volat <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> metodu pro načtení datový proud, který se používá k vytvoření nové bitové kopie na straně klienta:  
  
 [!code-csharp[Astoria Streaming Client#GetReadStreamClient](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_streaming_client/cs/customerphotowindow.xaml.cs#getreadstreamclient)]
 [!code-vb[Astoria Streaming Client#GetReadStreamClient](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_streaming_client/vb/customerphotowindow.xaml.vb#getreadstreamclient)]  
  
> [!NOTE]
>  Datová služba není nastavena hlavička Content-Length ve zprávě s odpovědí, který obsahuje binární datový proud. Tato hodnota nemusí odrážet skutečné délce binární datový proud.  
  
### <a name="uploading-a-media-resource-as-a-stream"></a>Nahrávání mediálního prostředku jako Stream  
 Chcete-li vložit nebo aktualizovat prostředek médií, zavolejte <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> metodu <xref:System.Data.Services.Client.DataServiceContext> instanci, která se sleduje subjekt. Tato metoda odešle požadavek do služby data, která obsahuje mediální zdroj číst ze zadaného datového proudu. Následující příklad ukazuje, jak volat <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> metodu pro odeslání image do datové služby:  
  
 [!code-csharp[Astoria Photo Streaming Client#SetSaveStream](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_photo_streaming_client/cs/photodetailswindow.xaml.cs#setsavestream)]
 [!code-vb[Astoria Photo Streaming Client#SetSaveStream](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_photo_streaming_client/vb/photodetailswindow.xaml.vb#setsavestream)]  
  
 V tomto příkladu <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> metoda je volána zadáním hodnotu `true` pro `closeStream` parametru. To zaručuje, že <xref:System.Data.Services.Client.DataServiceContext> zavře datový proud po binární data se odešlou do služby data.  
  
> [!NOTE]
>  Při volání <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A>, datový proud není odeslána do služby data do <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> je volána.  
  
## <a name="see-also"></a>Viz také:

- [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [Vazba dat k ovládacím prvkům](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)
