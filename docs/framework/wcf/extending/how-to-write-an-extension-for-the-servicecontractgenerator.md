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
# <a name="how-to-write-an-extension-for-the-servicecontractgenerator"></a>Postupy: Vytvoření rozšíření pro třídu ServiceContractGenerator
Toto téma popisuje postup vytvoření rozšíření pro <xref:System.ServiceModel.Description.ServiceContractGenerator>. To můžete udělat pomocí implementace <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> rozhraní na na chování operace nebo implementaci <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> rozhraní kontraktu chování. Toto téma ukazuje, jak implementovat <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> rozhraní kontraktu chování.  
  
 <xref:System.ServiceModel.Description.ServiceContractGenerator> Generuje kontrakty služeb, typy klientů a konfigurace klientů z <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, a <xref:System.ServiceModel.Channels.Binding> instancí. Obvykle importovat <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, a <xref:System.ServiceModel.Channels.Binding> instancí z metadat služby a pak použijte tyto instance pro generování kódu pro volání služby. V tomto příkladu <xref:System.ServiceModel.Description.IWsdlImportExtension> implementace se používá ke zpracování WSDL poznámky a pak přidejte rozšíření generování kódu do importovaných kontraktů generovat komentáře k generovaného kódu.  
  
### <a name="to-write-an-extension-for-the-servicecontractgenerator"></a>Pro vytvoření rozšíření pro třídu ServiceContractGenerator  
  
1. Implementace <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>. Chcete-li upravit kontrakt generovaný služby, použijte <xref:System.ServiceModel.Description.ServiceContractGenerationContext> instance předána do <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> metody.  
  
    ```  
    public void GenerateContract(ServiceContractGenerationContext context)  
    {  
        Console.WriteLine("In generate contract.");  
    context.ContractType.Comments.AddRange(Formatter.FormatComments(commentText));  
    }  
    ```  
  
2. Implementace <xref:System.ServiceModel.Description.IWsdlImportExtension> ve stejné třídě. <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> Metoda může zpracovat konkrétní rozšíření WSDL (WSDL poznámky v tomto případě) tak, že přidáte rozšíření generování kódu pro importované <xref:System.ServiceModel.Description.ContractDescription> instance.  
  
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
  
3. Přidáte do vaší konfigurace klienta programu pro import WSDL.  
  
    ```xml  
    <metadata>  
      <wsdlImporters>  
        <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
      </wsdlImporters>  
    </metadata>  
    ```  
  
4. Vytvořte v kódu klienta `MetadataExchangeClient` a volat `GetMetadata`.  
  
    ```  
    MetadataExchangeClient mexClient = new MetadataExchangeClient(metadataAddress);  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet metaDocs = mexClient.GetMetadata();  
    ```  
  
5. Vytvoření `WsdlImporter` a volat `ImportAllContracts`.  
  
    ```  
    WsdlImporter importer = new WsdlImporter(metaDocs);            System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
6. Vytvoření `ServiceContractGenerator` a volat `GenerateServiceContractType` pro každou smlouvu.  
  
    ```  
    ServiceContractGenerator generator = new ServiceContractGenerator();  
    foreach (ContractDescription contract in contracts)  
    {  
       generator.GenerateServiceContractType(contract);  
    }  
    if (generator.Errors.Count != 0)  
       throw new Exception("There were errors during code compilation.");  
    ```  
  
7. <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> je volána automaticky pro každý smlouvy chování pro daný kontrakt, který implementuje <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>. Tato metoda poté můžete upravit <xref:System.ServiceModel.Description.ServiceContractGenerationContext> předán. V tomto příkladu jsou přidány poznámky.  
  
## <a name="see-also"></a>Viz také:

- [Metadata](../../../../docs/framework/wcf/feature-details/metadata.md)
- [Postupy: Import vlastního WSDL](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)
