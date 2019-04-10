---
title: 'Postupy: Vytvoření rozšíření pro třídu ServiceContractGenerator'
ms.date: 03/30/2017
ms.assetid: 876ca823-bd16-4bdf-9e0f-02092df90e51
ms.openlocfilehash: c9e10efccf0d51e6b78aace1296d227a78a9f91d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59340617"
---
# <a name="how-to-write-an-extension-for-the-servicecontractgenerator"></a><span data-ttu-id="09ebf-102">Postupy: Vytvoření rozšíření pro třídu ServiceContractGenerator</span><span class="sxs-lookup"><span data-stu-id="09ebf-102">How to: Write an Extension for the ServiceContractGenerator</span></span>
<span data-ttu-id="09ebf-103">Toto téma popisuje postup vytvoření rozšíření pro <xref:System.ServiceModel.Description.ServiceContractGenerator>.</span><span class="sxs-lookup"><span data-stu-id="09ebf-103">This topic describes how to write an extension for the <xref:System.ServiceModel.Description.ServiceContractGenerator>.</span></span> <span data-ttu-id="09ebf-104">To můžete udělat pomocí implementace <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> rozhraní na na chování operace nebo implementaci <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> rozhraní kontraktu chování.</span><span class="sxs-lookup"><span data-stu-id="09ebf-104">This can be done by implementing the <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> interface on an operation behavior or implementing the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interface on a contract behavior.</span></span> <span data-ttu-id="09ebf-105">Toto téma ukazuje, jak implementovat <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> rozhraní kontraktu chování.</span><span class="sxs-lookup"><span data-stu-id="09ebf-105">This topic shows how to implement the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interface on a contract behavior.</span></span>  
  
 <span data-ttu-id="09ebf-106"><xref:System.ServiceModel.Description.ServiceContractGenerator> Generuje kontrakty služeb, typy klientů a konfigurace klientů z <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, a <xref:System.ServiceModel.Channels.Binding> instancí.</span><span class="sxs-lookup"><span data-stu-id="09ebf-106">The <xref:System.ServiceModel.Description.ServiceContractGenerator> generates service contracts, client types, and client configurations from <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, and <xref:System.ServiceModel.Channels.Binding> instances.</span></span> <span data-ttu-id="09ebf-107">Obvykle importovat <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, a <xref:System.ServiceModel.Channels.Binding> instancí z metadat služby a pak použijte tyto instance pro generování kódu pro volání služby.</span><span class="sxs-lookup"><span data-stu-id="09ebf-107">Typically, you import <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, and <xref:System.ServiceModel.Channels.Binding> instances from service metadata and then use these instances to generate code to call the service.</span></span> <span data-ttu-id="09ebf-108">V tomto příkladu <xref:System.ServiceModel.Description.IWsdlImportExtension> implementace se používá ke zpracování WSDL poznámky a pak přidejte rozšíření generování kódu do importovaných kontraktů generovat komentáře k generovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="09ebf-108">In this example, an <xref:System.ServiceModel.Description.IWsdlImportExtension> implementation is used to process WSDL annotations and then add code generation extensions to the imported contracts to generate comments on the generated code.</span></span>  
  
### <a name="to-write-an-extension-for-the-servicecontractgenerator"></a><span data-ttu-id="09ebf-109">Pro vytvoření rozšíření pro třídu ServiceContractGenerator</span><span class="sxs-lookup"><span data-stu-id="09ebf-109">To write an extension for the ServiceContractGenerator</span></span>  
  
1. <span data-ttu-id="09ebf-110">Implementace <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span><span class="sxs-lookup"><span data-stu-id="09ebf-110">Implement <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span></span> <span data-ttu-id="09ebf-111">Chcete-li upravit kontrakt generovaný služby, použijte <xref:System.ServiceModel.Description.ServiceContractGenerationContext> instance předána do <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> metody.</span><span class="sxs-lookup"><span data-stu-id="09ebf-111">To modify the generated service contract, use the <xref:System.ServiceModel.Description.ServiceContractGenerationContext> instance passed into the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> method.</span></span>  
  
    ```  
    public void GenerateContract(ServiceContractGenerationContext context)  
    {  
        Console.WriteLine("In generate contract.");  
    context.ContractType.Comments.AddRange(Formatter.FormatComments(commentText));  
    }  
    ```  
  
2. <span data-ttu-id="09ebf-112">Implementace <xref:System.ServiceModel.Description.IWsdlImportExtension> ve stejné třídě.</span><span class="sxs-lookup"><span data-stu-id="09ebf-112">Implement <xref:System.ServiceModel.Description.IWsdlImportExtension> on the same class.</span></span> <span data-ttu-id="09ebf-113"><xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> Metoda může zpracovat konkrétní rozšíření WSDL (WSDL poznámky v tomto případě) tak, že přidáte rozšíření generování kódu pro importované <xref:System.ServiceModel.Description.ContractDescription> instance.</span><span class="sxs-lookup"><span data-stu-id="09ebf-113">The <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> method can process a specific WSDL extension (WSDL annotations in this case) by adding a code generation extension to the imported <xref:System.ServiceModel.Description.ContractDescription> instance.</span></span>  
  
    ```  
    public void ImportContract(WsdlImporter importer, WsdlContractConversionContext context)  
       {  
                // Contract documentation  
             if (context.WsdlPortType.Documentation != null)  
             {  
                    context.Contract.Behaviors.Add(new WsdlDocumentationImporter(context.WsdlPortType.Documentation));  
             }  
             // Operation documentation  
             foreach (Operation operation in context.WsdlPortType.Operations)  
             {  
                if (operation.Documentation != null)  
                {  
                   OperationDescription operationDescription = context.Contract.Operations.Find(operation.Name);  
                   if (operationDescription != null)  
                   {  
                            operationDescription.Behaviors.Add(new WsdlDocumentationImporter(operation.Documentation));  
                   }  
                }  
             }  
          }  
          public void BeforeImport(ServiceDescriptionCollection wsdlDocuments, XmlSchemaSet xmlSchemas, ICollection<XmlElement> policy)   
            {  
                Console.WriteLine("BeforeImport called.");  
            }  
  
          public void ImportEndpoint(WsdlImporter importer, WsdlEndpointConversionContext context)   
            {  
                Console.WriteLine("ImportEndpoint called.");  
            }  
    ```  
  
3. <span data-ttu-id="09ebf-114">Přidáte do vaší konfigurace klienta programu pro import WSDL.</span><span class="sxs-lookup"><span data-stu-id="09ebf-114">Add the WSDL importer to your client configuration.</span></span>  
  
    ```xml  
    <metadata>  
      <wsdlImporters>  
        <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
      </wsdlImporters>  
    </metadata>  
    ```  
  
4. <span data-ttu-id="09ebf-115">Vytvořte v kódu klienta `MetadataExchangeClient` a volat `GetMetadata`.</span><span class="sxs-lookup"><span data-stu-id="09ebf-115">In the client code, create a `MetadataExchangeClient` and call `GetMetadata`.</span></span>  
  
    ```  
    MetadataExchangeClient mexClient = new MetadataExchangeClient(metadataAddress);  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet metaDocs = mexClient.GetMetadata();  
    ```  
  
5. <span data-ttu-id="09ebf-116">Vytvoření `WsdlImporter` a volat `ImportAllContracts`.</span><span class="sxs-lookup"><span data-stu-id="09ebf-116">Create a `WsdlImporter` and call `ImportAllContracts`.</span></span>  
  
    ```  
    WsdlImporter importer = new WsdlImporter(metaDocs);            System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
6. <span data-ttu-id="09ebf-117">Vytvoření `ServiceContractGenerator` a volat `GenerateServiceContractType` pro každou smlouvu.</span><span class="sxs-lookup"><span data-stu-id="09ebf-117">Create a `ServiceContractGenerator` and call `GenerateServiceContractType` for each contract.</span></span>  
  
    ```  
    ServiceContractGenerator generator = new ServiceContractGenerator();  
    foreach (ContractDescription contract in contracts)  
    {  
       generator.GenerateServiceContractType(contract);  
    }  
    if (generator.Errors.Count != 0)  
       throw new Exception("There were errors during code compilation.");  
    ```  
  
7. <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> <span data-ttu-id="09ebf-118">je volána automaticky pro každý smlouvy chování pro daný kontrakt, který implementuje <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span><span class="sxs-lookup"><span data-stu-id="09ebf-118">is called automatically for each contract behavior on a given contract that implements <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span></span> <span data-ttu-id="09ebf-119">Tato metoda poté můžete upravit <xref:System.ServiceModel.Description.ServiceContractGenerationContext> předán.</span><span class="sxs-lookup"><span data-stu-id="09ebf-119">This method can then modify the <xref:System.ServiceModel.Description.ServiceContractGenerationContext> passed in.</span></span> <span data-ttu-id="09ebf-120">V tomto příkladu jsou přidány poznámky.</span><span class="sxs-lookup"><span data-stu-id="09ebf-120">In this example comments are added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09ebf-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="09ebf-121">See also</span></span>

- [<span data-ttu-id="09ebf-122">Metadata</span><span class="sxs-lookup"><span data-stu-id="09ebf-122">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)
- [<span data-ttu-id="09ebf-123">Postupy: Import vlastního WSDL</span><span class="sxs-lookup"><span data-stu-id="09ebf-123">How to: Import Custom WSDL</span></span>](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)
