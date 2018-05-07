---
title: 'Postupy: Vytvoření rozšíření pro třídu ServiceContractGenerator'
ms.date: 03/30/2017
ms.assetid: 876ca823-bd16-4bdf-9e0f-02092df90e51
ms.openlocfilehash: 43105553739e104ab862b3be3cf2082fbf6d499f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-write-an-extension-for-the-servicecontractgenerator"></a>Postupy: Vytvoření rozšíření pro třídu ServiceContractGenerator
Toto téma popisuje postup vytvoření rozšíření pro <xref:System.ServiceModel.Description.ServiceContractGenerator>. To lze provést implementací <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> rozhraní na chování operaci nebo implementaci <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> rozhraní na chování kontrakt. Toto téma ukazuje, jak implementovat <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> rozhraní na chování kontrakt.  
  
 <xref:System.ServiceModel.Description.ServiceContractGenerator> Generuje kontraktů služby, typů klientů a konfigurace klienta z <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, a <xref:System.ServiceModel.Channels.Binding> instance. Obvykle importujete <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, a <xref:System.ServiceModel.Channels.Binding> instancí z metadat služby a pak použít tyto instance pro generování kódu pro volání služby. V tomto příkladu <xref:System.ServiceModel.Description.IWsdlImportExtension> implementace slouží ke zpracování WSDL poznámky a pak přidejte rozšíření pro generování kódu do importovaných kontraktů ke generování komentáře k generovaného kódu.  
  
### <a name="to-write-an-extension-for-the-servicecontractgenerator"></a>K vytvoření rozšíření pro třídu ServiceContractGenerator  
  
1.  Implementace <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>. Chcete-li upravit kontrakt generovaný služby, použijte <xref:System.ServiceModel.Description.ServiceContractGenerationContext> instance předána do <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> metoda.  
  
    ```  
    public void GenerateContract(ServiceContractGenerationContext context)  
    {  
        Console.WriteLine("In generate contract.");  
    context.ContractType.Comments.AddRange(Formatter.FormatComments(commentText));  
    }  
    ```  
  
2.  Implementace <xref:System.ServiceModel.Description.IWsdlImportExtension> u stejné třídy. <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> Metoda může zpracovat konkrétní rozšíření WSDL (WSDL poznámky v tomto případě) tak, že přidáte rozšíření pro generování kódu pro importované <xref:System.ServiceModel.Description.ContractDescription> instance.  
  
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
  
3.  Přidejte – Importér WSDL konfigurace klienta.  
  
    ```xml  
    <metadata>  
      <wsdlImporters>  
        <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
      </wsdlImporters>  
    </metadata>  
    ```  
  
4.  V kódu klienta, vytvořte `MetadataExchangeClient` a volání `GetMetadata`.  
  
    ```  
    MetadataExchangeClient mexClient = new MetadataExchangeClient(metadataAddress);  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet metaDocs = mexClient.GetMetadata();  
    ```  
  
5.  Vytvoření `WsdlImporter` a volání `ImportAllContracts`.  
  
    ```  
    WsdlImporter importer = new WsdlImporter(metaDocs);            System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
6.  Vytvoření `ServiceContractGenerator` a volání `GenerateServiceContractType` pro každý kontrakt.  
  
    ```  
    ServiceContractGenerator generator = new ServiceContractGenerator();  
    foreach (ContractDescription contract in contracts)  
    {  
       generator.GenerateServiceContractType(contract);  
    }  
    if (generator.Errors.Count != 0)  
       throw new Exception("There were errors during code compilation.");  
    ```  
  
7.  <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> je volána automaticky pro každé kontrakt chování na daný kontrakt, který implementuje <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>. Tato metoda pak můžete upravovat <xref:System.ServiceModel.Description.ServiceContractGenerationContext> předaná. V tomto příkladu jsou přidány komentáře.  
  
## <a name="see-also"></a>Viz také  
 [Metadata](../../../../docs/framework/wcf/feature-details/metadata.md)  
 [Postupy: Import vlastního WSDL](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)
