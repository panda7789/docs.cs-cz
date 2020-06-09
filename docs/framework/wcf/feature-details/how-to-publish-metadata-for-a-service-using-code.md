---
title: 'Postupy: Publikování metadat služby promocí kódu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 51407e6d-4d87-42d5-be7c-9887b8652006
ms.openlocfilehash: 9239e8bd9b85986d41006c4b2a21b6f2304e8275
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601228"
---
# <a name="how-to-publish-metadata-for-a-service-using-code"></a>Postupy: Publikování metadat služby promocí kódu
Jedná se o jedno ze dvou témat s postupy, které popisují publikování metadat pro službu Windows Communication Foundation (WCF). Existují dva způsoby, jak zadat, jak má služba publikovat metadata, pomocí konfiguračního souboru a pomocí kódu. V tomto tématu se dozvíte, jak publikovat metadata pro službu pomocí kódu.  
  
> [!CAUTION]
> V tomto tématu se dozvíte, jak publikovat metadata nezabezpečeným způsobem. Každý klient může získat metadata ze služby. Pokud vyžadujete, aby služba publikovala metadata zabezpečeným způsobem. viz [Vlastní zabezpečený koncový bod metadat](../samples/custom-secure-metadata-endpoint.md).  
  
 Další informace o publikování metadat v konfiguračním souboru naleznete v tématu [How to: Publish metadata for a Service using a Configuration File](how-to-publish-metadata-for-a-service-using-a-configuration-file.md). Publikování metadat umožňuje klientům načíst metadata pomocí žádosti o WS-Transfer GET nebo požadavku HTTP/GET pomocí `?wsdl` řetězce dotazu. Abyste měli jistotu, že kód pracuje, musíte vytvořit základní službu WCF. Základní Samoobslužná služba je k dispozici v následujícím kódu.  
  
 [!code-csharp[htPublishMetadataCode#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#0)]
 [!code-vb[htPublishMetadataCode#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#0)]  
  
### <a name="to-publish-metadata-in-code"></a>Publikování metadat v kódu  
  
1. V rámci metody Main aplikace konzoly vytvořte instanci <xref:System.ServiceModel.ServiceHost> objektu předáním typu služby a základní adresy.  
  
     [!code-csharp[htPublishMetadataCode#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#1)]
     [!code-vb[htPublishMetadataCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#1)]  
  
2. Vytvořte blok try hned pod kódem pro krok 1, zachytí všechny výjimky, které se vyvolaly, když je služba spuštěná.  
  
     [!code-csharp[htPublishMetadataCode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#2)]
     [!code-vb[htPublishMetadataCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#2)]  
  
     [!code-csharp[htPublishMetadataCode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#3)]
     [!code-vb[htPublishMetadataCode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#3)]  
  
3. Zkontrolujte, zda hostitel služby již obsahuje, a v <xref:System.ServiceModel.Description.ServiceMetadataBehavior> případě potřeby vytvořte novou <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instanci.  
  
     [!code-csharp[htPublishMetadataCode#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#4)]
     [!code-vb[htPublishMetadataCode#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#4)]  
  
4. Nastavte <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> vlastnost na`true.`  
  
     [!code-csharp[htPublishMetadataCode#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#5)]
     [!code-vb[htPublishMetadataCode#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#5)]  
  
5. <xref:System.ServiceModel.Description.ServiceMetadataBehavior>Obsahuje <xref:System.ServiceModel.Description.MetadataExporter> vlastnost. <xref:System.ServiceModel.Description.MetadataExporter>Obsahuje <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> vlastnost. Nastavte hodnotu <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> vlastnosti na <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> . <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A>Vlastnost lze také nastavit na hodnotu <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> . Když je nastaveno na <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> Exportér metadat, vygeneruje informace o zásadách s metadaty, která odpovídá protokolu WS-policy 1,5. Když se nastaví na <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> Exportér metadat, vygeneruje informace o zásadách, které odpovídají WS-policy 1,2.  
  
     [!code-csharp[htPublishMetadataCode#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#6)]
     [!code-vb[htPublishMetadataCode#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#6)]  
  
6. Přidejte <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instanci do kolekce chování hostitele služby.  
  
     [!code-csharp[htPublishMetadataCode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#7)]
     [!code-vb[htPublishMetadataCode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#7)]  
  
7. Přidejte koncový bod výměny metadat do hostitele služby.  
  
     [!code-csharp[htPublishMetadataCode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#8)]
     [!code-vb[htPublishMetadataCode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#8)]  
  
8. Přidejte koncový bod aplikace do hostitele služby.  
  
     [!code-csharp[htPublishMetadataCode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#9)]
     [!code-vb[htPublishMetadataCode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#9)]  
  
    > [!NOTE]
    > Pokud do služby nepřidáte žádné koncové body, modul runtime přidá pro vás výchozí koncové body. V tomto příkladu, protože je služba <xref:System.ServiceModel.Description.ServiceMetadataBehavior> nastavená na `true` , služba má povolená metadata publikování. Další informace o výchozích koncových bodech najdete v tématu [zjednodušená konfigurace](../simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../samples/simplified-configuration-for-wcf-services.md).  
  
9. Otevřete hostitele služby a počkejte na příchozí volání. Když uživatel stiskne klávesu ENTER, uzavřete hostitele služby.  
  
     [!code-csharp[htPublishMetadataCode#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#10)]
     [!code-vb[htPublishMetadataCode#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#10)]  
  
10. Vytvořte a spusťte konzolovou aplikaci.  
  
11. Pomocí Internet Exploreru přejděte na základní adresu služby ( `http://localhost:8001/MetadataSample` v této ukázce) a ověřte, jestli je zapnuté publikování metadat. Měla by se zobrazit webová stránka, která uvádí "jednoduchá služba" na začátku a hned pod "jste vytvořili službu." V takovém případě se zobrazí zpráva v horní části výsledné stránky: "publikování metadat pro tuto službu je momentálně zakázané."  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje implementaci základní služby WCF, která publikuje metadata pro službu v kódu.  
  
 [!code-csharp[htPublishMetadataCode#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#11)]
 [!code-vb[htPublishMetadataCode#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#11)]  
  
## <a name="see-also"></a>Viz také

- [Postupy: Hostování služby WCF ve spravované aplikaci](../how-to-host-a-wcf-service-in-a-managed-application.md)
- [Vlastní hostování](../samples/self-host.md)
- [Přehled architektury metadat](metadata-architecture-overview.md)
- [Používání metadat](using-metadata.md)
- [Postupy: Publikování metadat služby promocí konfiguračního souboru](how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
