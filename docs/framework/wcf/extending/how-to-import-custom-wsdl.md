---
title: 'Postupy: Import vlastního WSDL'
ms.date: 03/30/2017
ms.assetid: ddc3718d-ce60-44f6-92af-a5c67477dd99
ms.openlocfilehash: 33762afffca6e90cb32c358bee6d9f29ca609994
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488267"
---
# <a name="how-to-import-custom-wsdl"></a>Postupy: Import vlastního WSDL
Toto téma popisuje postup importování vlastní WSDL. Pro zpracování vlastního WSDL, je nutné implementovat <xref:System.ServiceModel.Description.IWsdlImportExtension> rozhraní.  
  
### <a name="to-import-custom-wsdl"></a>Chcete-li importovat vlastní WSDL  
  
1.  Implementace <xref:System.ServiceModel.Description.IWsdlImportExtension>. Implementace <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%28System.Web.Services.Description.ServiceDescriptionCollection%2CSystem.Xml.Schema.XmlSchemaSet%2CSystem.Collections.Generic.ICollection%7BSystem.Xml.XmlElement%7D%29> metoda upravit metadata před jejich importem. Implementace <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> a <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> metody k úpravě kontraktech a importovat z metadat koncových bodů. Pro přístup k importovaných kontraktů nebo koncový bod, použijte odpovídající objekt context (<xref:System.ServiceModel.Description.WsdlContractConversionContext> nebo <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>):  
  
    ```  
    public class WsdlDocumentationImporter : IWsdlImportExtension  
       {  
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
       }  
    ```  
  
2.  Nakonfigurujte klientskou aplikaci používat vlastní – Importér WSDL. Všimněte si, že pokud používáte Svcutil.exe, měli byste přidat tato konfigurace do konfiguračního souboru pro Svcutil.exe (Svcutil.exe.config):  
  
    ```xml  
    <system.serviceModel>  
          <client>  
            <endpoint   
              address="http://localhost:8000/Fibonacci"   
              binding="wsHttpBinding"  
              contract="IFibonacci"  
            />  
            <metadata>  
              <wsdlImporters>  
                <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
              </wsdlImporters>  
            </metadata>  
          </client>  
        </system.serviceModel>  
    ```  
  
3.  Vytvořte novou <xref:System.ServiceModel.Description.WsdlImporter> instance (předávání v <xref:System.ServiceModel.Description.MetadataSet> instanci, která obsahuje WSDL dokumenty, které chcete importovat) a volání <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>:  
  
    ```  
    WsdlImporter importer = new WsdlImporter(metaDocs);          System.Collections.ObjectModel.Collection<ContractDescription> contracts  = importer.ImportAllContracts();  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Metadata](../../../../docs/framework/wcf/feature-details/metadata.md)  
 [Export a import metadat](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)  
 [Vlastní publikování WSDL](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)
