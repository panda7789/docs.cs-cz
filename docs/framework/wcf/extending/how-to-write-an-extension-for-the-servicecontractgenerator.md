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
# <a name="how-to-write-an-extension-for-the-servicecontractgenerator"></a>Postupy: Vytvoření rozšíření pro třídu ServiceContractGenerator
Toto téma popisuje, jak napsat rozšíření pro <xref:System.ServiceModel.Description.ServiceContractGenerator>. To lze provést implementací rozhraní <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> v chování operace nebo implementací rozhraní <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> v chování kontraktu. Toto téma ukazuje, jak implementovat rozhraní <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> pro chování kontraktu.  
  
 <xref:System.ServiceModel.Description.ServiceContractGenerator> generuje kontrakty služby, typy klientů a konfigurace klienta z <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>a instancí <xref:System.ServiceModel.Channels.Binding>. Obvykle importujete instance <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>a <xref:System.ServiceModel.Channels.Binding> z metadat služby a pak tyto instance použít k vygenerování kódu pro volání služby. V tomto příkladu se <xref:System.ServiceModel.Description.IWsdlImportExtension> implementace používá ke zpracování poznámek WSDL a pak přidání rozšíření pro generování kódu do importovaných smluv za účelem generování komentářů k vygenerovanému kódu.  
  
### <a name="to-write-an-extension-for-the-servicecontractgenerator"></a>Zápis rozšíření pro ServiceContractGenerator  
  
1. Implementujte <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>. Chcete-li upravit vygenerovanou kontrakt služby, použijte instanci <xref:System.ServiceModel.Description.ServiceContractGenerationContext> předanou do metody <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29>.  
  
    ```csharp
    public void GenerateContract(ServiceContractGenerationContext context)  
    {  
        Console.WriteLine("In generate contract.");  
        context.ContractType.Comments.AddRange(Formatter.FormatComments(commentText));  
    }  
    ```  
  
2. Implementujte <xref:System.ServiceModel.Description.IWsdlImportExtension> stejné třídy. Metoda <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> může zpracovat konkrétní rozšíření WSDL (poznámky WSDL v tomto případě) přidáním rozšíření pro generování kódu do importované instance <xref:System.ServiceModel.Description.ContractDescription>.  
  
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
  
3. Přidejte nástroj WSDL import do konfigurace klienta.  
  
    ```xml  
    <metadata>  
      <wsdlImporters>  
        <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
      </wsdlImporters>  
    </metadata>  
    ```  
  
4. V klientském kódu vytvořte `MetadataExchangeClient` a zavolejte `GetMetadata`.  
  
    ```csharp
    var mexClient = new MetadataExchangeClient(metadataAddress);  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet metaDocs = mexClient.GetMetadata();  
    ```  
  
5. Vytvořte `WsdlImporter` a zavolejte `ImportAllContracts`.  
  
    ```csharp
    var importer = new WsdlImporter(metaDocs);
    System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
6. Vytvořte `ServiceContractGenerator` a zavolejte `GenerateServiceContractType` pro každou smlouvu.  
  
    ```csharp
    var generator = new ServiceContractGenerator();  
    foreach (ContractDescription contract in contracts)  
    {  
       generator.GenerateServiceContractType(contract);  
    }  
    if (generator.Errors.Count != 0)  
       throw new Exception("There were errors during code compilation.");  
    ```  
  
7. <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> se zavolá automaticky pro každé chování kontraktu u dané smlouvy, která implementuje <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>. Tato metoda pak může změnit předanou <xref:System.ServiceModel.Description.ServiceContractGenerationContext>. V tomto příkladu jsou přidány komentáře.  
  
## <a name="see-also"></a>Viz také:

- [Metadata](../feature-details/metadata.md)
- [Postupy: Import vlastního WSDL](how-to-import-custom-wsdl.md)
