---
title: 'Postupy: Export metadat z koncových bodů služby'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b6c4dfd0-f270-43ec-961a-e16eb6af2f2c
ms.openlocfilehash: 58e86e5566775048e081bfb4ac217a7747b98a35
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579407"
---
# <a name="how-to-export-metadata-from-service-endpoints"></a>Postupy: Export metadat z koncových bodů služby
Toto téma vysvětluje, jak exportovat metadata z koncových bodů služby.  
  
### <a name="to-export-metadata-from-service-endpoints"></a>Export metadat z koncových bodů služby  
  
1. Vytvořte nový projekt konzolové aplikace sady Visual Studio. Přidejte kód zobrazený v následujících krocích v generovaném souboru Program.cs v rámci metody Main ().  
  
2. Vytvořte <xref:System.ServiceModel.Description.WsdlExporter> .  
  
     [!code-csharp[S_UEWsdlExporter#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#1)]
     [!code-vb[S_UEWsdlExporter#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#1)]  
  
3. Nastavte <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> vlastnost na jednu z hodnot <xref:System.ServiceModel.Description.PolicyVersion> výčtu. Tato ukázka nastaví hodnotu, <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> která odpovídá WS-policy 1,5.  
  
     [!code-csharp[S_UEWsdlExporter#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#2)]
     [!code-vb[S_UEWsdlExporter#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#2)]  
  
4. Vytvoří pole <xref:System.ServiceModel.Description.ServiceEndpoint> objektů.  
  
     [!code-csharp[S_UEWsdlExporter#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#3)]
     [!code-vb[S_UEWsdlExporter#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#3)]  
  
5. Exportujte metadata pro každý koncový bod služby.  
  
     [!code-csharp[S_UEWsdlExporter#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#4)]
     [!code-vb[S_UEWsdlExporter#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#4)]  
  
6. Ujistěte se, že během procesu exportu nedošlo k žádným chybám a načítají se metadata.  
  
     [!code-csharp[S_UEWsdlExporter#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#5)]
     [!code-vb[S_UEWsdlExporter#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#5)]  
  
7. Nyní můžete použít metadata, jako je například zápis do souboru, voláním <xref:System.ServiceModel.Description.MetadataSet.WriteTo%28System.Xml.XmlWriter%29> metody.  
  
## <a name="example"></a>Příklad  
 Následuje úplný výpis kódu pro tento příklad.  
  
 [!code-csharp[S_UEWsdlExporter#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#0)]
 [!code-vb[S_UEWsdlExporter#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#0)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Při kompilování Program.cs reference System. ServiceModel. dll.  
  
## <a name="see-also"></a>Viz také

- [Přehled architektury metadat](metadata-architecture-overview.md)
- [Používání metadat](using-metadata.md)
- [Koncové body: adresy, vazby a kontrakty](endpoints-addresses-bindings-and-contracts.md)
