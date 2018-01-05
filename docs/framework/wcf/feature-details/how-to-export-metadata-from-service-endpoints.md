---
title: "Postupy: Export metadat z koncových bodů služby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b6c4dfd0-f270-43ec-961a-e16eb6af2f2c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 14b045ef55ac0b6d76bb06e711b4134d54b3d61f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-export-metadata-from-service-endpoints"></a>Postupy: Export metadat z koncových bodů služby
Toto téma vysvětluje, jak pro export metadat z koncových bodů služby.  
  
### <a name="to-export-metadata-from-service-endpoints"></a>Pro export metadat z koncových bodů služby  
  
1.  Vytvořte nový projekt aplikace konzoly Visual Studio. Přidejte uvedeném v následujících krocích v vygenerovaný soubor Program.cs v rámci metody main() kódu.  
  
2.  Vytvoření <xref:System.ServiceModel.Description.WsdlExporter>.  
  
     [!code-csharp[S_UEWsdlExporter#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#1)]
     [!code-vb[S_UEWsdlExporter#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#1)]  
  
3.  Nastavte <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> vlastnost na jednu z hodnot z <xref:System.ServiceModel.Description.PolicyVersion> výčtu. Tato ukázka nastaví na hodnotu <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> která odpovídá WS-Policy 1.5.  
  
     [!code-csharp[S_UEWsdlExporter#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#2)]
     [!code-vb[S_UEWsdlExporter#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#2)]  
  
4.  Vytvoření pole <xref:System.ServiceModel.Description.ServiceEndpoint> objekty.  
  
     [!code-csharp[S_UEWsdlExporter#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#3)]
     [!code-vb[S_UEWsdlExporter#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#3)]  
  
5.  Exportujte metadat pro každý koncový bod služby.  
  
     [!code-csharp[S_UEWsdlExporter#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#4)]
     [!code-vb[S_UEWsdlExporter#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#4)]  
  
6.  Zkontrolujte a ujistěte se, že během procesu exportu nedošlo k žádným chybám načtení metadat.  
  
     [!code-csharp[S_UEWsdlExporter#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#5)]
     [!code-vb[S_UEWsdlExporter#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#5)]  
  
7.  Teď můžete použít metadata, například zapisovat do souboru voláním <xref:System.ServiceModel.Description.MetadataSet.WriteTo%28System.Xml.XmlWriter%29> metoda.  
  
## <a name="example"></a>Příklad  
 Zde je úplný výpis pro tento příklad kódu.  
  
 [!code-csharp[S_UEWsdlExporter#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#0)]
 [!code-vb[S_UEWsdlExporter#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#0)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Při kompilaci souboru Program.cs odkaz System.ServiceModel.dll.  
  
## <a name="see-also"></a>Viz také  
 [Přehled architektury metadat](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)  
 [Používání metadat](../../../../docs/framework/wcf/feature-details/using-metadata.md)  
 [Koncové body: adresy, vazby a kontrakty](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
