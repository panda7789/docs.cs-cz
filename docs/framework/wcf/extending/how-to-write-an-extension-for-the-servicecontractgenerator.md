---
title: 'Postupy: Vytvoření rozšíření pro třídu ServiceContractGenerator'
ms.date: 03/30/2017
ms.assetid: 876ca823-bd16-4bdf-9e0f-02092df90e51
ms.openlocfilehash: af23babd9255c45b9fa89b5c167de6960f0f690e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855720"
---
# <a name="how-to-write-an-extension-for-the-servicecontractgenerator"></a><span data-ttu-id="8cd69-102">Postupy: Vytvoření rozšíření pro třídu ServiceContractGenerator</span><span class="sxs-lookup"><span data-stu-id="8cd69-102">How to: Write an Extension for the ServiceContractGenerator</span></span>
<span data-ttu-id="8cd69-103">Toto téma popisuje, jak napsat rozšíření pro <xref:System.ServiceModel.Description.ServiceContractGenerator>.</span><span class="sxs-lookup"><span data-stu-id="8cd69-103">This topic describes how to write an extension for the <xref:System.ServiceModel.Description.ServiceContractGenerator>.</span></span> <span data-ttu-id="8cd69-104">To lze provést implementací <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> rozhraní v chování operace nebo <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> implementací rozhraní v chování kontraktu.</span><span class="sxs-lookup"><span data-stu-id="8cd69-104">This can be done by implementing the <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> interface on an operation behavior or implementing the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interface on a contract behavior.</span></span> <span data-ttu-id="8cd69-105">Toto téma ukazuje, jak implementovat <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> rozhraní v chování kontraktu.</span><span class="sxs-lookup"><span data-stu-id="8cd69-105">This topic shows how to implement the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interface on a contract behavior.</span></span>  
  
 <span data-ttu-id="8cd69-106">Vygeneruje kontrakty služby, typy klientů a konfigurace klienta z <xref:System.ServiceModel.Description.ServiceEndpoint>instancí <xref:System.ServiceModel.Description.ContractDescription>, a <xref:System.ServiceModel.Channels.Binding>. <xref:System.ServiceModel.Description.ServiceContractGenerator></span><span class="sxs-lookup"><span data-stu-id="8cd69-106">The <xref:System.ServiceModel.Description.ServiceContractGenerator> generates service contracts, client types, and client configurations from <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, and <xref:System.ServiceModel.Channels.Binding> instances.</span></span> <span data-ttu-id="8cd69-107">Obvykle importujete <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>a <xref:System.ServiceModel.Channels.Binding> instance z metadat služby a pak tyto instance použít k vygenerování kódu pro volání služby.</span><span class="sxs-lookup"><span data-stu-id="8cd69-107">Typically, you import <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, and <xref:System.ServiceModel.Channels.Binding> instances from service metadata and then use these instances to generate code to call the service.</span></span> <span data-ttu-id="8cd69-108">V tomto příkladu <xref:System.ServiceModel.Description.IWsdlImportExtension> se implementace používá ke zpracování poznámek WSDL a následné přidání rozšíření pro generování kódu do importovaných smluv za účelem generování komentářů k vygenerovanému kódu.</span><span class="sxs-lookup"><span data-stu-id="8cd69-108">In this example, an <xref:System.ServiceModel.Description.IWsdlImportExtension> implementation is used to process WSDL annotations and then add code generation extensions to the imported contracts to generate comments on the generated code.</span></span>  
  
### <a name="to-write-an-extension-for-the-servicecontractgenerator"></a><span data-ttu-id="8cd69-109">Zápis rozšíření pro ServiceContractGenerator</span><span class="sxs-lookup"><span data-stu-id="8cd69-109">To write an extension for the ServiceContractGenerator</span></span>  
  
1. <span data-ttu-id="8cd69-110">Implementujte <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span><span class="sxs-lookup"><span data-stu-id="8cd69-110">Implement <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span></span> <span data-ttu-id="8cd69-111">Chcete-li upravit vygenerovanou kontrakt služby, <xref:System.ServiceModel.Description.ServiceContractGenerationContext> použijte instanci předanou <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> metodě.</span><span class="sxs-lookup"><span data-stu-id="8cd69-111">To modify the generated service contract, use the <xref:System.ServiceModel.Description.ServiceContractGenerationContext> instance passed into the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> method.</span></span>  
  
    ```csharp
    public void GenerateContract(ServiceContractGenerationContext context)  
    {  
        Console.WriteLine("In generate contract.");  
    context.ContractType.Comments.AddRange(Formatter.FormatComments(commentText));  
    }  
    ```  
  
2. <span data-ttu-id="8cd69-112">Implementovat <xref:System.ServiceModel.Description.IWsdlImportExtension> na stejnou třídu.</span><span class="sxs-lookup"><span data-stu-id="8cd69-112">Implement <xref:System.ServiceModel.Description.IWsdlImportExtension> on the same class.</span></span> <span data-ttu-id="8cd69-113">Metoda může zpracovat konkrétní rozšíření WSDL (anotace WSDL v tomto případě) přidáním rozšíření pro generování kódu do importované <xref:System.ServiceModel.Description.ContractDescription> instance. <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29></span><span class="sxs-lookup"><span data-stu-id="8cd69-113">The <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> method can process a specific WSDL extension (WSDL annotations in this case) by adding a code generation extension to the imported <xref:System.ServiceModel.Description.ContractDescription> instance.</span></span>  
  
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
  
3. <span data-ttu-id="8cd69-114">Přidejte nástroj WSDL import do konfigurace klienta.</span><span class="sxs-lookup"><span data-stu-id="8cd69-114">Add the WSDL importer to your client configuration.</span></span>  
  
    ```xml  
    <metadata>  
      <wsdlImporters>  
        <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
      </wsdlImporters>  
    </metadata>  
    ```  
  
4. <span data-ttu-id="8cd69-115">V klientském kódu vytvořte `MetadataExchangeClient` volání `GetMetadata`a.</span><span class="sxs-lookup"><span data-stu-id="8cd69-115">In the client code, create a `MetadataExchangeClient` and call `GetMetadata`.</span></span>  
  
    ```csharp  
    MetadataExchangeClient mexClient = new MetadataExchangeClient(metadataAddress);  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet metaDocs = mexClient.GetMetadata();  
    ```  
  
5. <span data-ttu-id="8cd69-116">Vytvořte volání `WsdlImporter` `ImportAllContracts`a.</span><span class="sxs-lookup"><span data-stu-id="8cd69-116">Create a `WsdlImporter` and call `ImportAllContracts`.</span></span>  
  
    ```csharp  
    WsdlImporter importer = new WsdlImporter(metaDocs);            System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
6. <span data-ttu-id="8cd69-117">Vytvořte a zavolejte `GenerateServiceContractType` pro každou kontrakt. `ServiceContractGenerator`</span><span class="sxs-lookup"><span data-stu-id="8cd69-117">Create a `ServiceContractGenerator` and call `GenerateServiceContractType` for each contract.</span></span>  
  
    ```csharp  
    ServiceContractGenerator generator = new ServiceContractGenerator();  
    foreach (ContractDescription contract in contracts)  
    {  
       generator.GenerateServiceContractType(contract);  
    }  
    if (generator.Errors.Count != 0)  
       throw new Exception("There were errors during code compilation.");  
    ```  
  
7. <span data-ttu-id="8cd69-118"><xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29>se nazývá automaticky pro každé chování kontraktu v dané kontraktu, <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>který implementuje.</span><span class="sxs-lookup"><span data-stu-id="8cd69-118"><xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> is called automatically for each contract behavior on a given contract that implements <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span></span> <span data-ttu-id="8cd69-119">Tato metoda pak může změnit <xref:System.ServiceModel.Description.ServiceContractGenerationContext> předanou funkci.</span><span class="sxs-lookup"><span data-stu-id="8cd69-119">This method can then modify the <xref:System.ServiceModel.Description.ServiceContractGenerationContext> passed in.</span></span> <span data-ttu-id="8cd69-120">V tomto příkladu jsou přidány komentáře.</span><span class="sxs-lookup"><span data-stu-id="8cd69-120">In this example comments are added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cd69-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8cd69-121">See also</span></span>

- [<span data-ttu-id="8cd69-122">Metadata</span><span class="sxs-lookup"><span data-stu-id="8cd69-122">Metadata</span></span>](../feature-details/metadata.md)
- [<span data-ttu-id="8cd69-123">Postupy: Importovat vlastní WSDL</span><span class="sxs-lookup"><span data-stu-id="8cd69-123">How to: Import Custom WSDL</span></span>](how-to-import-custom-wsdl.md)
