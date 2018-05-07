---
title: Práce s binární Data (služby WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, binary data
- WCF Data Services, streams
ms.assetid: aeccc45c-d5c5-4671-ad63-a492ac8043ac
ms.openlocfilehash: 9df9dadc3d4e4e62b216134bbc2fd69c4e1122e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="working-with-binary-data-wcf-data-services"></a>Práce s binární Data (služby WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klientské knihovny umožňuje načíst a aktualizovat binární data ze [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] kanálu v jednom z následujících způsobů:  
  
-   Jako vlastnost primitivního typu entity. Toto je doporučená metoda pro práci s malá binární data objekty, které je možné snadno načíst do paměti. V takovém případě binární vlastnost je vlastnost entity zveřejněné datový model a službu data serializuje binární data jako binární kódovaného XML kódování base-64 ve zprávě s odpovědí.  
  
-   Jako datový proud samostatné binárního prostředku. Toto je doporučená metoda k přístupu a změna dat binární rozsáhlý objekt (BLOB), která může představovat fotografie, videa nebo jiný typ kódovaného binární data.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] implementuje streamování binární data pomocí protokolu HTTP, jak jsou definovány v [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. Binární data v tento mechanismus, je považován za příslušný mediální zdroj, která je oddělená od ale související s entity, která se nazývá záznam odkazu média. Další informace najdete v tématu [streamování zprostředkovatele](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).  
  
> [!TIP]
>  Podrobný příklad toho, jak vytvořit klientskou aplikaci Windows Presentation Foundation (WPF), který stahuje binární obrázkových souborů z [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] služba, která ukládá fotografie, najdete v příspěvku [služby streamování zprostředkovatele řady-část dat 2: přístup k datový proud prostředku média z klienta](http://go.microsoft.com/fwlink/?LinkId=201637). Si můžete stáhnout ukázkový kód pro službu datového proudu fotografií data umístěná v příspěvku na blogu [vysílání datového proudu fotografií služby vzorek dat](http://go.microsoft.com/fwlink/?LinkId=198988) v galerie kódů MSDN.  
  
## <a name="entity-metadata"></a>Entity Metadata  
 Entita, která má datový proud prostředku související média je uvedené v metadata služby dat pomocí `HasStream` atribut použitý typ entity, který je položka odkaz na médium. V následujícím příkladu `PhotoInfo` entita je položka odkaz médií, která má související mediálního zdroje, uvedené `HasStream` atribut.  
  
 [!code-xml[Astoria Photo Streaming Service#HasStream](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria photo streaming service/xml/photodata.edmx#hasstream)]  
  
 Zbývající příklady v tomto tématu ukazují, jak získávat přístup a měnit datový proud prostředku média. Kompletní příklad, jak využívat v aplikaci klienta rozhraní .NET Framework datový proud prostředku média pomocí [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klientské knihovny, najdete v příspěvku [přístup k datový proud prostředku média z klienta](http://go.microsoft.com/fwlink/?LinkID=201637).  
  
## <a name="accessing-the-binary-resource-stream"></a>Přístup k prostředku binární datový proud  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klientské knihovny poskytuje metody pro přístup k datové proudy binárního prostředku z [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]– na základě dat služby. Při stahování mediálního zdroje, můžete buď použít identifikátor URI prostředku média nebo můžete získat binární datový proud, který obsahuje samotná data prostředků média. Můžete také nahrát data prostředků média jako binárního datového proudu.  
  
> [!TIP]
>  Podrobný příklad toho, jak vytvořit klientskou aplikaci Windows Presentation Foundation (WPF), který stahuje binární obrázkových souborů z [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] služba, která ukládá fotografie, najdete v příspěvku [služby streamování zprostředkovatele řady-část dat 2: přístup k datový proud prostředku média z klienta](http://go.microsoft.com/fwlink/?LinkId=201637). Si můžete stáhnout ukázkový kód pro službu datového proudu fotografií data umístěná v příspěvku na blogu [vysílání datového proudu fotografií služby vzorek dat](http://go.microsoft.com/fwlink/?LinkId=198988) v galerie kódů MSDN.  
  
### <a name="getting-the-uri-of-the-binary-stream"></a>Získávání Identifikátor URI binární datový proud  
 Při načítání určitých typů médií prostředky, například bitové kopie a další soubory médií, je často jednodušší použít identifikátor URI prostředku média v aplikaci než zpracování binární datový proud sám sebe. Chcete-li získat identifikátor URI přidružený záznam udělení média odkaz datový proud prostředku, musí volat <xref:System.Data.Services.Client.DataServiceContext.GetReadStreamUri%2A> metodu <xref:System.Data.Services.Client.DataServiceContext> instanci, která je sledování entity. Následující příklad ukazuje způsob volání <xref:System.Data.Services.Client.DataServiceContext.GetReadStreamUri%2A> metoda získat identifikátor URI média datový proud prostředku, který se používá k vytvoření nové bitové kopie na straně klienta:  
  
 [!code-csharp[Astoria Photo Streaming Client#GetReadStreamUri](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria photo streaming client/cs/photowindow.xaml.cs#getreadstreamuri)]
 [!code-vb[Astoria Photo Streaming Client#GetReadStreamUri](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria photo streaming client/vb/photowindow.xaml.vb#getreadstreamuri)]  
  
### <a name="downloading-the-binary-resource-stream"></a>Stahování datový proud binárního prostředku  
 Při načítání datového proudu binárního prostředku, musí volat <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> metodu <xref:System.Data.Services.Client.DataServiceContext> instanci, která je sledování odkaz položka médií. Tato metoda odešle požadavek na službu data, která vrací <xref:System.Data.Services.Client.DataServiceStreamResponse> objekt, který obsahuje odkaz na datový proud, který obsahuje prostředek. Tuto metodu použijte, pokud vaše aplikace vyžaduje jako binárního prostředku <xref:System.IO.Stream>. Následující příklad ukazuje způsob volání <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> metoda pro načtení datový proud, který se používá k vytvoření nové bitové kopie na straně klienta:  
  
 [!code-csharp[Astoria Streaming Client#GetReadStreamClient](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria streaming client/cs/customerphotowindow.xaml.cs#getreadstreamclient)]
 [!code-vb[Astoria Streaming Client#GetReadStreamClient](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria streaming client/vb/customerphotowindow.xaml.vb#getreadstreamclient)]  
  
> [!NOTE]
>  Služba data není nastavena hlavička Content-Length ve zprávě odpovědi, která obsahuje binární datový proud. Tato hodnota nemusí odrážet skutečné délce binární datový proud.  
  
### <a name="uploading-a-media-resource-as-a-stream"></a>Nahrávání mediálního prostředku jako datový proud  
 Vložit nebo aktualizovat prostředek média, volání <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> metodu <xref:System.Data.Services.Client.DataServiceContext> instanci, která je sledování entity. Tato metoda odešle požadavek do služby data, která obsahuje zdroj média pro čtení z datového proudu zadaný. Následující příklad ukazuje způsob volání <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> metodu pro odeslání bitovou kopii k službě data:  
  
 [!code-csharp[Astoria Photo Streaming Client#SetSaveStream](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria photo streaming client/cs/photodetailswindow.xaml.cs#setsavestream)]
 [!code-vb[Astoria Photo Streaming Client#SetSaveStream](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria photo streaming client/vb/photodetailswindow.xaml.vb#setsavestream)]  
  
 V tomto příkladu <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> metoda je volána zadáním hodnotu `true` pro `closeStream` parametr. To zaručuje, že <xref:System.Data.Services.Client.DataServiceContext> datový proud se zavře po binární data se odešlou do služby data.  
  
> [!NOTE]
>  Při volání <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A>, neposílají se do službu data do datového proudu <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> je volána.  
  
## <a name="see-also"></a>Viz také  
 [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [Vazba dat k ovládacím prvkům](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)
