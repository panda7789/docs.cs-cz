---
title: 'Postupy: Export metadat z koncových bodů služeb'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b6c4dfd0-f270-43ec-961a-e16eb6af2f2c
ms.openlocfilehash: 6bf2eb3d295f9cbf6a7e13a612d5846ceaa75ab4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778297"
---
# <a name="how-to-export-metadata-from-service-endpoints"></a><span data-ttu-id="62673-102">Postupy: Export metadat z koncových bodů služeb</span><span class="sxs-lookup"><span data-stu-id="62673-102">How to: Export Metadata from Service Endpoints</span></span>
<span data-ttu-id="62673-103">Toto téma vysvětluje, jak pro export metadat z koncových bodů služby.</span><span class="sxs-lookup"><span data-stu-id="62673-103">This topic explains how to export metadata from service endpoints.</span></span>  
  
### <a name="to-export-metadata-from-service-endpoints"></a><span data-ttu-id="62673-104">Pro export metadat z koncových bodů služby</span><span class="sxs-lookup"><span data-stu-id="62673-104">To export metadata from service endpoints</span></span>  
  
1. <span data-ttu-id="62673-105">Vytvoření nového projektu aplikace konzoly Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="62673-105">Create a new Visual Studio Console App Project.</span></span> <span data-ttu-id="62673-106">Přidejte kód je znázorněno v následujícím postupu v generovaném souboru Program.cs v rámci metody main().</span><span class="sxs-lookup"><span data-stu-id="62673-106">Add the code shown in the following steps in the generated Program.cs file within the main() method.</span></span>  
  
2. <span data-ttu-id="62673-107">Vytvoření <xref:System.ServiceModel.Description.WsdlExporter>.</span><span class="sxs-lookup"><span data-stu-id="62673-107">Create a <xref:System.ServiceModel.Description.WsdlExporter>.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#1)]
     [!code-vb[S_UEWsdlExporter#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#1)]  
  
3. <span data-ttu-id="62673-108">Nastavte <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> vlastnost na jednu z hodnot <xref:System.ServiceModel.Description.PolicyVersion> výčtu.</span><span class="sxs-lookup"><span data-stu-id="62673-108">Set the <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property to one of the values from the <xref:System.ServiceModel.Description.PolicyVersion> enumeration.</span></span> <span data-ttu-id="62673-109">Tento příklad nastaví hodnotu <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> který odpovídá 1.5 WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="62673-109">This sample sets the value to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> which corresponds to WS-Policy 1.5.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#2)]
     [!code-vb[S_UEWsdlExporter#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#2)]  
  
4. <span data-ttu-id="62673-110">Vytvoření pole <xref:System.ServiceModel.Description.ServiceEndpoint> objekty.</span><span class="sxs-lookup"><span data-stu-id="62673-110">Create an array of <xref:System.ServiceModel.Description.ServiceEndpoint> objects.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#3)]
     [!code-vb[S_UEWsdlExporter#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#3)]  
  
5. <span data-ttu-id="62673-111">Exportujte metadat pro každého koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="62673-111">Export metadata for each service endpoint.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#4)]
     [!code-vb[S_UEWsdlExporter#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#4)]  
  
6. <span data-ttu-id="62673-112">Zkontrolujte, ujistěte se, že nedošlo k žádným chybám během procesu exportu a načtení metadat.</span><span class="sxs-lookup"><span data-stu-id="62673-112">Check to make sure no errors occurred during the export process and retrieve the metadata.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#5)]
     [!code-vb[S_UEWsdlExporter#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#5)]  
  
7. <span data-ttu-id="62673-113">Teď můžete pomocí metadat, jako je zápis do souboru pomocí volání <xref:System.ServiceModel.Description.MetadataSet.WriteTo%28System.Xml.XmlWriter%29> metody.</span><span class="sxs-lookup"><span data-stu-id="62673-113">You can now use the metadata, such as write it to a file by calling the <xref:System.ServiceModel.Description.MetadataSet.WriteTo%28System.Xml.XmlWriter%29> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62673-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="62673-114">Example</span></span>  
 <span data-ttu-id="62673-115">Následuje úplný výpis v tomto příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="62673-115">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[S_UEWsdlExporter#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#0)]
 [!code-vb[S_UEWsdlExporter#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="62673-116">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="62673-116">Compiling the Code</span></span>  
 <span data-ttu-id="62673-117">Při kompilaci souboru Program.cs odkaz System.ServiceModel.dll.</span><span class="sxs-lookup"><span data-stu-id="62673-117">When compiling Program.cs reference System.ServiceModel.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62673-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="62673-118">See also</span></span>

- [<span data-ttu-id="62673-119">Přehled architektury metadat</span><span class="sxs-lookup"><span data-stu-id="62673-119">Metadata Architecture Overview</span></span>](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [<span data-ttu-id="62673-120">Používání metadat</span><span class="sxs-lookup"><span data-stu-id="62673-120">Using Metadata</span></span>](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [<span data-ttu-id="62673-121">Koncové body: Adresy, vazby a kontrakty</span><span class="sxs-lookup"><span data-stu-id="62673-121">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
