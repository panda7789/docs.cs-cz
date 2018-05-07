---
title: 'Postupy: Publikování metadat služby promocí kódu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 51407e6d-4d87-42d5-be7c-9887b8652006
ms.openlocfilehash: bef5421d377bcae6e8c56b0117ebbe22a861de86
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-publish-metadata-for-a-service-using-code"></a>Postupy: Publikování metadat služby promocí kódu
Toto je jedna z dva postupy, které popisují publikování metadat služby Windows Communication Foundation (WCF). Existují dva způsoby, jak určit, jak by měla služba publikování metadat, použití konfiguračního souboru a pomocí kódu. Toto téma ukazuje, jak publikování metadat služby promocí kódu.  
  
> [!CAUTION]
>  Toto téma ukazuje, jak publikování metadat nezabezpečená způsobem. Jakýkoli klient může načíst metadata ze služby. Pokud budete potřebovat k službě pro publikování metadat zabezpečeným způsobem. v tématu [koncový bod metadat zabezpečení vlastní](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).  
  
 Další informace o publikování metadat v konfiguračním souboru najdete v tématu [postupy: publikování metadat služby promocí konfigurační soubor](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md). Publikování metadat umožňuje klientům pro načtení metadat pomocí žádost o přenos WS získat nebo žádosti o protokolu HTTP nebo získat pomocí `?wsdl` řetězec dotazu. Ujistěte se, zda kód pracuje budete musíte vytvořit základní služby WCF. Základní služba s vlastním hostováním jsou uvedené v následující kód.  
  
 [!code-csharp[htPublishMetadataCode#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#0)]
 [!code-vb[htPublishMetadataCode#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#0)]  
  
### <a name="to-publish-metadata-in-code"></a>K publikování metadat v kódu  
  
1.  V rámci hlavní metoda aplikace konzoly, vytváření instancí <xref:System.ServiceModel.ServiceHost> objekt předáním typ služby a základní adresu.  
  
     [!code-csharp[htPublishMetadataCode#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#1)]
     [!code-vb[htPublishMetadataCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#1)]  
  
2.  Vytvoření bloku try bezprostředně pod kód pro krok 1, to zachytí všechny výjimky, které získat vyvolány, když je služba spuštěná.  
  
     [!code-csharp[htPublishMetadataCode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#2)]
     [!code-vb[htPublishMetadataCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#2)]  
  
     [!code-csharp[htPublishMetadataCode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#3)]
     [!code-vb[htPublishMetadataCode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#3)]  
  
3.  Zkontrolujte, zda hostitel služby již obsahuje <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, pokud ne, vytvořte novou <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance.  
  
     [!code-csharp[htPublishMetadataCode#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#4)]
     [!code-vb[htPublishMetadataCode#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#4)]  
  
4.  Nastavte <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> vlastnosti `true.`  
  
     [!code-csharp[htPublishMetadataCode#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#5)]
     [!code-vb[htPublishMetadataCode#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#5)]  
  
5.  <xref:System.ServiceModel.Description.ServiceMetadataBehavior> Obsahuje <xref:System.ServiceModel.Description.MetadataExporter> vlastnost. <xref:System.ServiceModel.Description.MetadataExporter> Obsahuje <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> vlastnost. Nastavte hodnotu <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> vlastnost <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>. <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> Vlastnost může být také nastavena na <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>. Pokud nastavíte hodnotu <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> exportu metadat generuje informace o zásadách s metadaty, "odpovídá WS-Policy 1.5. Pokud nastavíte hodnotu <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> exportu metadat generuje informace o zásadách, který vyhovuje WS-Policy 1.2.  
  
     [!code-csharp[htPublishMetadataCode#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#6)]
     [!code-vb[htPublishMetadataCode#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#6)]  
  
6.  Přidat <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance hostitele služby chování kolekce.  
  
     [!code-csharp[htPublishMetadataCode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#7)]
     [!code-vb[htPublishMetadataCode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#7)]  
  
7.  Přidejte do hostitele služby exchange koncovým bodem metadat.  
  
     [!code-csharp[htPublishMetadataCode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#8)]
     [!code-vb[htPublishMetadataCode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#8)]  
  
8.  Přidání koncového bodu aplikace do hostitele služby.  
  
     [!code-csharp[htPublishMetadataCode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#9)]
     [!code-vb[htPublishMetadataCode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#9)]  
  
    > [!NOTE]
    >  Pokud jste ke službě nepřidávejte žádné koncové body, modul runtime přidá výchozí koncové body pro vás. V tomto příkladu protože služba má <xref:System.ServiceModel.Description.ServiceMetadataBehavior> nastavena na `true`, služba má povoleno publikování metadat. Další informace o výchozí koncové body najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
9. Otevření hostitele služby a počkejte příchozí volání. Když uživatel stiskne klávesu ENTER, zavřete hostitele služby.  
  
     [!code-csharp[htPublishMetadataCode#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#10)]
     [!code-vb[htPublishMetadataCode#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#10)]  
  
10. Sestavte a spusťte konzolovou aplikaci.  
  
11. Použijte Internet Explorer a přejděte do základní adresa služby (http://localhost:8001/MetadataSample v této ukázce) a ověřte, jestli je zapnutá publikování metadat. Zobrazí webová stránka zobrazí, která říká "Jednoduché služba" v horní části a bezprostředně pod "Službu jste vytvořili." Pokud není, zobrazí se zpráva v horní části výsledné stránky: "publikování metadat pro tato služba je aktuálně zakázaná."  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje implementaci základní služby WCF, který publikuje metadata pro služby v kódu.  
  
 [!code-csharp[htPublishMetadataCode#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#11)]
 [!code-vb[htPublishMetadataCode#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#11)]  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Hostování služby WCF ve spravované aplikaci](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)  
 [Vlastní hostování](../../../../docs/framework/wcf/samples/self-host.md)  
 [Přehled architektury metadat](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)  
 [Používání metadat](../../../../docs/framework/wcf/feature-details/using-metadata.md)  
 [Postupy: Publikování metadat služby promocí konfiguračního souboru](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
