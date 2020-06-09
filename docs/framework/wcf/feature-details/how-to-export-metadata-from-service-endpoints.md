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
# <a name="how-to-export-metadata-from-service-endpoints"></a><span data-ttu-id="edbb6-102">Postupy: Export metadat z koncových bodů služby</span><span class="sxs-lookup"><span data-stu-id="edbb6-102">How to: Export Metadata from Service Endpoints</span></span>
<span data-ttu-id="edbb6-103">Toto téma vysvětluje, jak exportovat metadata z koncových bodů služby.</span><span class="sxs-lookup"><span data-stu-id="edbb6-103">This topic explains how to export metadata from service endpoints.</span></span>  
  
### <a name="to-export-metadata-from-service-endpoints"></a><span data-ttu-id="edbb6-104">Export metadat z koncových bodů služby</span><span class="sxs-lookup"><span data-stu-id="edbb6-104">To export metadata from service endpoints</span></span>  
  
1. <span data-ttu-id="edbb6-105">Vytvořte nový projekt konzolové aplikace sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="edbb6-105">Create a new Visual Studio Console App Project.</span></span> <span data-ttu-id="edbb6-106">Přidejte kód zobrazený v následujících krocích v generovaném souboru Program.cs v rámci metody Main ().</span><span class="sxs-lookup"><span data-stu-id="edbb6-106">Add the code shown in the following steps in the generated Program.cs file within the main() method.</span></span>  
  
2. <span data-ttu-id="edbb6-107">Vytvořte <xref:System.ServiceModel.Description.WsdlExporter> .</span><span class="sxs-lookup"><span data-stu-id="edbb6-107">Create a <xref:System.ServiceModel.Description.WsdlExporter>.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#1)]
     [!code-vb[S_UEWsdlExporter#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#1)]  
  
3. <span data-ttu-id="edbb6-108">Nastavte <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> vlastnost na jednu z hodnot <xref:System.ServiceModel.Description.PolicyVersion> výčtu.</span><span class="sxs-lookup"><span data-stu-id="edbb6-108">Set the <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property to one of the values from the <xref:System.ServiceModel.Description.PolicyVersion> enumeration.</span></span> <span data-ttu-id="edbb6-109">Tato ukázka nastaví hodnotu, <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> která odpovídá WS-policy 1,5.</span><span class="sxs-lookup"><span data-stu-id="edbb6-109">This sample sets the value to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> which corresponds to WS-Policy 1.5.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#2)]
     [!code-vb[S_UEWsdlExporter#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#2)]  
  
4. <span data-ttu-id="edbb6-110">Vytvoří pole <xref:System.ServiceModel.Description.ServiceEndpoint> objektů.</span><span class="sxs-lookup"><span data-stu-id="edbb6-110">Create an array of <xref:System.ServiceModel.Description.ServiceEndpoint> objects.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#3)]
     [!code-vb[S_UEWsdlExporter#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#3)]  
  
5. <span data-ttu-id="edbb6-111">Exportujte metadata pro každý koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="edbb6-111">Export metadata for each service endpoint.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#4)]
     [!code-vb[S_UEWsdlExporter#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#4)]  
  
6. <span data-ttu-id="edbb6-112">Ujistěte se, že během procesu exportu nedošlo k žádným chybám a načítají se metadata.</span><span class="sxs-lookup"><span data-stu-id="edbb6-112">Check to make sure no errors occurred during the export process and retrieve the metadata.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#5)]
     [!code-vb[S_UEWsdlExporter#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#5)]  
  
7. <span data-ttu-id="edbb6-113">Nyní můžete použít metadata, jako je například zápis do souboru, voláním <xref:System.ServiceModel.Description.MetadataSet.WriteTo%28System.Xml.XmlWriter%29> metody.</span><span class="sxs-lookup"><span data-stu-id="edbb6-113">You can now use the metadata, such as write it to a file by calling the <xref:System.ServiceModel.Description.MetadataSet.WriteTo%28System.Xml.XmlWriter%29> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="edbb6-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="edbb6-114">Example</span></span>  
 <span data-ttu-id="edbb6-115">Následuje úplný výpis kódu pro tento příklad.</span><span class="sxs-lookup"><span data-stu-id="edbb6-115">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[S_UEWsdlExporter#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#0)]
 [!code-vb[S_UEWsdlExporter#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="edbb6-116">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="edbb6-116">Compiling the Code</span></span>  
 <span data-ttu-id="edbb6-117">Při kompilování Program.cs reference System. ServiceModel. dll.</span><span class="sxs-lookup"><span data-stu-id="edbb6-117">When compiling Program.cs reference System.ServiceModel.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edbb6-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="edbb6-118">See also</span></span>

- [<span data-ttu-id="edbb6-119">Přehled architektury metadat</span><span class="sxs-lookup"><span data-stu-id="edbb6-119">Metadata Architecture Overview</span></span>](metadata-architecture-overview.md)
- [<span data-ttu-id="edbb6-120">Používání metadat</span><span class="sxs-lookup"><span data-stu-id="edbb6-120">Using Metadata</span></span>](using-metadata.md)
- [<span data-ttu-id="edbb6-121">Koncové body: adresy, vazby a kontrakty</span><span class="sxs-lookup"><span data-stu-id="edbb6-121">Endpoints: Addresses, Bindings, and Contracts</span></span>](endpoints-addresses-bindings-and-contracts.md)
