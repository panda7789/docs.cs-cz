---
title: 'Postupy: Vytvoření rozšíření pro třídu ServiceContractGenerator'
ms.date: 03/30/2017
ms.assetid: 876ca823-bd16-4bdf-9e0f-02092df90e51
ms.openlocfilehash: 68b380a40448f21ba770aa47c7188b818fa8f9e7
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975882"
---
# <a name="how-to-write-an-extension-for-the-servicecontractgenerator"></a><span data-ttu-id="20eec-102">Postupy: Vytvoření rozšíření pro třídu ServiceContractGenerator</span><span class="sxs-lookup"><span data-stu-id="20eec-102">How to: Write an Extension for the ServiceContractGenerator</span></span>
<span data-ttu-id="20eec-103">Toto téma popisuje, jak napsat rozšíření pro <xref:System.ServiceModel.Description.ServiceContractGenerator>.</span><span class="sxs-lookup"><span data-stu-id="20eec-103">This topic describes how to write an extension for the <xref:System.ServiceModel.Description.ServiceContractGenerator>.</span></span> <span data-ttu-id="20eec-104">To lze provést implementací rozhraní <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> v chování operace nebo implementací rozhraní <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> v chování kontraktu.</span><span class="sxs-lookup"><span data-stu-id="20eec-104">This can be done by implementing the <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> interface on an operation behavior or implementing the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interface on a contract behavior.</span></span> <span data-ttu-id="20eec-105">Toto téma ukazuje, jak implementovat rozhraní <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> pro chování kontraktu.</span><span class="sxs-lookup"><span data-stu-id="20eec-105">This topic shows how to implement the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interface on a contract behavior.</span></span>  
  
 <span data-ttu-id="20eec-106"><xref:System.ServiceModel.Description.ServiceContractGenerator> generuje kontrakty služby, typy klientů a konfigurace klienta z <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>a instancí <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="20eec-106">The <xref:System.ServiceModel.Description.ServiceContractGenerator> generates service contracts, client types, and client configurations from <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, and <xref:System.ServiceModel.Channels.Binding> instances.</span></span> <span data-ttu-id="20eec-107">Obvykle importujete instance <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>a <xref:System.ServiceModel.Channels.Binding> z metadat služby a pak tyto instance použít k vygenerování kódu pro volání služby.</span><span class="sxs-lookup"><span data-stu-id="20eec-107">Typically, you import <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, and <xref:System.ServiceModel.Channels.Binding> instances from service metadata and then use these instances to generate code to call the service.</span></span> <span data-ttu-id="20eec-108">V tomto příkladu se <xref:System.ServiceModel.Description.IWsdlImportExtension> implementace používá ke zpracování poznámek WSDL a pak přidání rozšíření pro generování kódu do importovaných smluv za účelem generování komentářů k vygenerovanému kódu.</span><span class="sxs-lookup"><span data-stu-id="20eec-108">In this example, an <xref:System.ServiceModel.Description.IWsdlImportExtension> implementation is used to process WSDL annotations and then add code generation extensions to the imported contracts to generate comments on the generated code.</span></span>  
  
### <a name="to-write-an-extension-for-the-servicecontractgenerator"></a><span data-ttu-id="20eec-109">Zápis rozšíření pro ServiceContractGenerator</span><span class="sxs-lookup"><span data-stu-id="20eec-109">To write an extension for the ServiceContractGenerator</span></span>  
  
1. <span data-ttu-id="20eec-110">Implementujte <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span><span class="sxs-lookup"><span data-stu-id="20eec-110">Implement <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span></span> <span data-ttu-id="20eec-111">Chcete-li upravit vygenerovanou kontrakt služby, použijte instanci <xref:System.ServiceModel.Description.ServiceContractGenerationContext> předanou do metody <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29>.</span><span class="sxs-lookup"><span data-stu-id="20eec-111">To modify the generated service contract, use the <xref:System.ServiceModel.Description.ServiceContractGenerationContext> instance passed into the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> method.</span></span>  
  
    ```csharp
    public void GenerateContract(ServiceContractGenerationContext context)  
    {  
        Console.WriteLine("In generate contract.");  
        context.ContractType.Comments.AddRange(Formatter.FormatComments(commentText));  
    }  
    ```  
  
2. <span data-ttu-id="20eec-112">Implementujte <xref:System.ServiceModel.Description.IWsdlImportExtension> stejné třídy.</span><span class="sxs-lookup"><span data-stu-id="20eec-112">Implement <xref:System.ServiceModel.Description.IWsdlImportExtension> on the same class.</span></span> <span data-ttu-id="20eec-113">Metoda <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> může zpracovat konkrétní rozšíření WSDL (poznámky WSDL v tomto případě) přidáním rozšíření pro generování kódu do importované instance <xref:System.ServiceModel.Description.ContractDescription>.</span><span class="sxs-lookup"><span data-stu-id="20eec-113">The <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> method can process a specific WSDL extension (WSDL annotations in this case) by adding a code generation extension to the imported <xref:System.ServiceModel.Description.ContractDescription> instance.</span></span>  
  
    ```csharp
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
  
3. <span data-ttu-id="20eec-114">Přidejte nástroj WSDL import do konfigurace klienta.</span><span class="sxs-lookup"><span data-stu-id="20eec-114">Add the WSDL importer to your client configuration.</span></span>  
  
    ```xml  
    <metadata>  
      <wsdlImporters>  
        <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
      </wsdlImporters>  
    </metadata>  
    ```  
  
4. <span data-ttu-id="20eec-115">V klientském kódu vytvořte `MetadataExchangeClient` a zavolejte `GetMetadata`.</span><span class="sxs-lookup"><span data-stu-id="20eec-115">In the client code, create a `MetadataExchangeClient` and call `GetMetadata`.</span></span>  
  
    ```csharp
    var mexClient = new MetadataExchangeClient(metadataAddress);  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet metaDocs = mexClient.GetMetadata();  
    ```  
  
5. <span data-ttu-id="20eec-116">Vytvořte `WsdlImporter` a zavolejte `ImportAllContracts`.</span><span class="sxs-lookup"><span data-stu-id="20eec-116">Create a `WsdlImporter` and call `ImportAllContracts`.</span></span>  
  
    ```csharp
    var importer = new WsdlImporter(metaDocs);
    System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
6. <span data-ttu-id="20eec-117">Vytvořte `ServiceContractGenerator` a zavolejte `GenerateServiceContractType` pro každou smlouvu.</span><span class="sxs-lookup"><span data-stu-id="20eec-117">Create a `ServiceContractGenerator` and call `GenerateServiceContractType` for each contract.</span></span>  
  
    ```csharp
    var generator = new ServiceContractGenerator();  
    foreach (ContractDescription contract in contracts)  
    {  
       generator.GenerateServiceContractType(contract);  
    }  
    if (generator.Errors.Count != 0)  
       throw new Exception("There were errors during code compilation.");  
    ```  
  
7. <span data-ttu-id="20eec-118"><xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> se zavolá automaticky pro každé chování kontraktu u dané smlouvy, která implementuje <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span><span class="sxs-lookup"><span data-stu-id="20eec-118"><xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> is called automatically for each contract behavior on a given contract that implements <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span></span> <span data-ttu-id="20eec-119">Tato metoda pak může změnit předanou <xref:System.ServiceModel.Description.ServiceContractGenerationContext>.</span><span class="sxs-lookup"><span data-stu-id="20eec-119">This method can then modify the <xref:System.ServiceModel.Description.ServiceContractGenerationContext> passed in.</span></span> <span data-ttu-id="20eec-120">V tomto příkladu jsou přidány komentáře.</span><span class="sxs-lookup"><span data-stu-id="20eec-120">In this example comments are added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20eec-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="20eec-121">See also</span></span>

- [<span data-ttu-id="20eec-122">Metadata</span><span class="sxs-lookup"><span data-stu-id="20eec-122">Metadata</span></span>](../feature-details/metadata.md)
- [<span data-ttu-id="20eec-123">Postupy: Import vlastního WSDL</span><span class="sxs-lookup"><span data-stu-id="20eec-123">How to: Import Custom WSDL</span></span>](how-to-import-custom-wsdl.md)
