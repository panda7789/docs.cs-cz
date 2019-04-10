---
title: 'Postupy: Import vlastního WSDL'
ms.date: 03/30/2017
ms.assetid: ddc3718d-ce60-44f6-92af-a5c67477dd99
ms.openlocfilehash: d9a4609f08a95bbecca81aa6667102a0e4a73c67
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59303788"
---
# <a name="how-to-import-custom-wsdl"></a>Postupy: Import vlastního WSDL
Toto téma popisuje import vlastního WSDL. Pro zpracování vlastního WSDL, je nutné implementovat <xref:System.ServiceModel.Description.IWsdlImportExtension> rozhraní.  
  
### <a name="to-import-custom-wsdl"></a>Import vlastního WSDL  
  
1. Implementace <xref:System.ServiceModel.Description.IWsdlImportExtension>. Implementace <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%28System.Web.Services.Description.ServiceDescriptionCollection%2CSystem.Xml.Schema.XmlSchemaSet%2CSystem.Collections.Generic.ICollection%7BSystem.Xml.XmlElement%7D%29> metody k úpravě metadat před jejich importem. Implementace <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> a <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> metody ke změně smlouvy a naimportované z metadat koncových bodů. Pro přístup k importované smlouvy nebo koncový bod, použijte odpovídající objekt kontextu (<xref:System.ServiceModel.Description.WsdlContractConversionContext> nebo <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>):  
  
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
  
2. Konfigurovat klientskou aplikaci používat Import vlastního WSDL. Všimněte si, že pokud používáte Svcutil.exe, měli byste přidat tuto konfiguraci do konfiguračního souboru pro Svcutil.exe (Svcutil.exe.config):  
  
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
  
3. Vytvořte nový <xref:System.ServiceModel.Description.WsdlImporter> instance (předávajícího <xref:System.ServiceModel.Description.MetadataSet> instance, která obsahuje dokumenty WSDL, které chcete importovat) a volat <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>:  
  
    ```  
    WsdlImporter importer = new WsdlImporter(metaDocs);          System.Collections.ObjectModel.Collection<ContractDescription> contracts  = importer.ImportAllContracts();  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Metadata](../../../../docs/framework/wcf/feature-details/metadata.md)
- [Export a import metadat](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)
- [Vlastní publikování WSDL](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)
