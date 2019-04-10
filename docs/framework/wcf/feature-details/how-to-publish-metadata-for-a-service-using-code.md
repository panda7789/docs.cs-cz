---
title: 'Postupy: Publikování metadat služby promocí kódu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 51407e6d-4d87-42d5-be7c-9887b8652006
ms.openlocfilehash: 870142724321629d6dbeccd4118b814283901776
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59297964"
---
# <a name="how-to-publish-metadata-for-a-service-using-code"></a>Postupy: Publikování metadat služby promocí kódu
Toto je jedna z dva postupy: témata, které popisují publikování metadat služby Windows Communication Foundation (WCF). Existují dva způsoby, jak určit, jak by měla služba publikování metadat, je používán konfigurační soubor a pomocí kódu. Toto téma ukazuje, jak publikování metadat služby promocí kódu.  
  
> [!CAUTION]
>  Toto téma ukazuje, jak měla být zveřejněna metadata nezabezpečené způsobem. Jakýkoli klient může načíst metadata ze služby. Pokud budete potřebovat vaše služba měla být zveřejněna metadata bezpečným způsobem. Zobrazit [koncový bod metadat zabezpečení vlastní](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).  
  
 Další informace o publikování metadat v konfiguračním souboru, naleznete v tématu [jak: Publikování metadat služby promocí konfiguračního souboru](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md). Publikování metadat umožňuje klientům pro načtení metadat pomocí žádost o přenos WS získat nebo pomocí požadavku HTTP/GET `?wsdl` řetězec dotazu. Ujistěte se, že kód funguje je nutné vytvořit základní služby WCF. Základní služba v místním prostředí je k dispozici v následujícím kódu.  
  
 [!code-csharp[htPublishMetadataCode#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#0)]
 [!code-vb[htPublishMetadataCode#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#0)]  
  
### <a name="to-publish-metadata-in-code"></a>Publikování metadat v kódu  
  
1. V rámci metody main konzolové aplikace vytvořit instanci <xref:System.ServiceModel.ServiceHost> objekt předáním typ služby a základní adresa.  
  
     [!code-csharp[htPublishMetadataCode#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#1)]
     [!code-vb[htPublishMetadataCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#1)]  
  
2. Vytvořit blok try bezprostředně pod kód v kroku 1, to zachytává všechny výjimky, které získat vyvolána, když je služba spuštěna.  
  
     [!code-csharp[htPublishMetadataCode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#2)]
     [!code-vb[htPublishMetadataCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#2)]  
  
     [!code-csharp[htPublishMetadataCode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#3)]
     [!code-vb[htPublishMetadataCode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#3)]  
  
3. Zkontrolujte, zda již obsahuje tohoto hostitele služby <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, pokud ne, vytvořte nový <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance.  
  
     [!code-csharp[htPublishMetadataCode#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#4)]
     [!code-vb[htPublishMetadataCode#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#4)]  
  
4. Nastavte <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> vlastnost `true.`  
  
     [!code-csharp[htPublishMetadataCode#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#5)]
     [!code-vb[htPublishMetadataCode#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#5)]  
  
5. <xref:System.ServiceModel.Description.ServiceMetadataBehavior> Obsahuje <xref:System.ServiceModel.Description.MetadataExporter> vlastnost. <xref:System.ServiceModel.Description.MetadataExporter> Obsahuje <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> vlastnost. Nastavte hodnotu <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> vlastnost <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>. <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> Vlastnost může být také nastavena na <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>. Pokud je nastavena na <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> Exportér metadat generuje informace o zásadách s metadaty, která "odpovídá 1.5 WS-Policy. Pokud je nastavena na <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> Exportér metadat generuje informace o zásadách, která odpovídá 1.2 WS-Policy.  
  
     [!code-csharp[htPublishMetadataCode#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#6)]
     [!code-vb[htPublishMetadataCode#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#6)]  
  
6. Přidat <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance hostitele služby kolekce chování.  
  
     [!code-csharp[htPublishMetadataCode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#7)]
     [!code-vb[htPublishMetadataCode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#7)]  
  
7. Přidáte koncový bod výměny metadat k hostiteli služby.  
  
     [!code-csharp[htPublishMetadataCode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#8)]
     [!code-vb[htPublishMetadataCode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#8)]  
  
8. Přidání koncového bodu aplikace k hostiteli služby.  
  
     [!code-csharp[htPublishMetadataCode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#9)]
     [!code-vb[htPublishMetadataCode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#9)]  
  
    > [!NOTE]
    >  Pokud nemůžete přidat žádné koncové body pro službu, modulu runtime přidá výchozí koncové body za vás. V tomto příkladu vzhledem k tomu, že služba má <xref:System.ServiceModel.Description.ServiceMetadataBehavior> nastavena na `true`, že služba má povoleno publikování metadat. Další informace o výchozí koncové body, naleznete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
9. Otevření hostitele služby a čekání na příchozí volání. Když uživatel stiskne klávesu ENTER, zavřete hostitele služby.  
  
     [!code-csharp[htPublishMetadataCode#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#10)]
     [!code-vb[htPublishMetadataCode#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#10)]  
  
10. Vytvořte a spusťte konzolovou aplikaci.  
  
11. Pomocí aplikace Internet Explorer a přejděte do základní adresa služby (http://localhost:8001/MetadataSample v této ukázce) a ověřte, zda je povoleno publikování metadat. Zobrazí se webové stránky zobrazí s textem "Jednoduché služby" v horní části a bezprostředně pod "Službu jste vytvořili." Pokud ne, zobrazí se zpráva v horní části výslednou stránku: "Publikování metadat pro tuto službu je aktuálně zakázaný."  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje implementaci základní služby WCF, který publikuje metadata pro služby v kódu.  
  
 [!code-csharp[htPublishMetadataCode#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#11)]
 [!code-vb[htPublishMetadataCode#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#11)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Hostování služby WCF ve spravované aplikaci](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [Vlastní hostování](../../../../docs/framework/wcf/samples/self-host.md)
- [Přehled architektury metadat](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [Používání metadat](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [Postupy: Publikování metadat služby promocí konfiguračního souboru](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
