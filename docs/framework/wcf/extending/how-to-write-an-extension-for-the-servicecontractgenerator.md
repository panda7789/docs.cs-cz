---
title: 'Postupy: Vytvoření rozšíření pro třídu ServiceContractGenerator'
ms.date: 03/30/2017
ms.assetid: 876ca823-bd16-4bdf-9e0f-02092df90e51
ms.openlocfilehash: b13b881a221ae0aa757b04c206125716a55f5b8c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795520"
---
# <a name="how-to-write-an-extension-for-the-servicecontractgenerator"></a>Postupy: Vytvoření rozšíření pro třídu ServiceContractGenerator
Toto téma popisuje, jak napsat rozšíření pro <xref:System.ServiceModel.Description.ServiceContractGenerator>. To lze provést implementací <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> rozhraní v chování operace nebo <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> implementací rozhraní v chování kontraktu. Toto téma ukazuje, jak implementovat <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> rozhraní v chování kontraktu.  
  
 Vygeneruje kontrakty služby, typy klientů a konfigurace klienta z <xref:System.ServiceModel.Description.ServiceEndpoint>instancí <xref:System.ServiceModel.Description.ContractDescription>, a <xref:System.ServiceModel.Channels.Binding>. <xref:System.ServiceModel.Description.ServiceContractGenerator> Obvykle importujete <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>a <xref:System.ServiceModel.Channels.Binding> instance z metadat služby a pak tyto instance použít k vygenerování kódu pro volání služby. V tomto příkladu <xref:System.ServiceModel.Description.IWsdlImportExtension> se implementace používá ke zpracování poznámek WSDL a následné přidání rozšíření pro generování kódu do importovaných smluv za účelem generování komentářů k vygenerovanému kódu.  
  
### <a name="to-write-an-extension-for-the-servicecontractgenerator"></a>Zápis rozšíření pro ServiceContractGenerator  
  
1. Implementujte <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>. Chcete-li upravit vygenerovanou kontrakt služby, <xref:System.ServiceModel.Description.ServiceContractGenerationContext> použijte instanci předanou <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> metodě.  
  
    ```  
    public void GenerateContract(ServiceContractGenerationContext context)  
    {  
        Console.WriteLine("In generate contract.");  
    context.ContractType.Comments.AddRange(Formatter.FormatComments(commentText));  
    }  
    ```  
  
2. Implementovat <xref:System.ServiceModel.Description.IWsdlImportExtension> na stejnou třídu. Metoda může zpracovat konkrétní rozšíření WSDL (anotace WSDL v tomto případě) přidáním rozšíření pro generování kódu do importované <xref:System.ServiceModel.Description.ContractDescription> instance. <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29>  
  
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
  
3. Přidejte nástroj WSDL import do konfigurace klienta.  
  
    ```xml  
    <metadata>  
      <wsdlImporters>  
        <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
      </wsdlImporters>  
    </metadata>  
    ```  
  
4. V klientském kódu vytvořte `MetadataExchangeClient` volání `GetMetadata`a.  
  
    ```  
    MetadataExchangeClient mexClient = new MetadataExchangeClient(metadataAddress);  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet metaDocs = mexClient.GetMetadata();  
    ```  
  
5. Vytvořte volání `WsdlImporter` `ImportAllContracts`a.  
  
    ```  
    WsdlImporter importer = new WsdlImporter(metaDocs);            System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
6. Vytvořte a zavolejte `GenerateServiceContractType` pro každou kontrakt. `ServiceContractGenerator`  
  
    ```  
    ServiceContractGenerator generator = new ServiceContractGenerator();  
    foreach (ContractDescription contract in contracts)  
    {  
       generator.GenerateServiceContractType(contract);  
    }  
    if (generator.Errors.Count != 0)  
       throw new Exception("There were errors during code compilation.");  
    ```  
  
7. <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29>se nazývá automaticky pro každé chování kontraktu v dané kontraktu, <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>který implementuje. Tato metoda pak může změnit <xref:System.ServiceModel.Description.ServiceContractGenerationContext> předanou funkci. V tomto příkladu jsou přidány komentáře.  
  
## <a name="see-also"></a>Viz také:

- [Metadata](../feature-details/metadata.md)
- [Postupy: Importovat vlastní WSDL](how-to-import-custom-wsdl.md)
