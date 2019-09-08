---
title: 'Postupy: Import vlastního WSDL'
ms.date: 03/30/2017
ms.assetid: ddc3718d-ce60-44f6-92af-a5c67477dd99
ms.openlocfilehash: 930cb92d8193ba3ffc1f62191f2012e104091190
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797001"
---
# <a name="how-to-import-custom-wsdl"></a>Postupy: Import vlastního WSDL
Toto téma popisuje, jak importovat vlastní WSDL. Chcete-li zpracovat vlastní WSDL, je nutné implementovat <xref:System.ServiceModel.Description.IWsdlImportExtension> rozhraní.  
  
### <a name="to-import-custom-wsdl"></a>Import vlastního WSDL  
  
1. Implementujte <xref:System.ServiceModel.Description.IWsdlImportExtension>. Implementujte <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%28System.Web.Services.Description.ServiceDescriptionCollection%2CSystem.Xml.Schema.XmlSchemaSet%2CSystem.Collections.Generic.ICollection%7BSystem.Xml.XmlElement%7D%29> metodu pro úpravu metadat před jejich importem. Implementujte metody <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29>apro úpravy smluv a koncových bodů importovaných z metadat. <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> Pro přístup k importované smlouvě nebo koncovému bodu použijte odpovídající objekt kontextu (<xref:System.ServiceModel.Description.WsdlContractConversionContext> nebo <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>):  
  
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
  
2. Nakonfigurujte klientskou aplikaci tak, aby používala vlastní Import WSDL. Všimněte si, že pokud používáte Svcutil. exe, měli byste tuto konfiguraci přidat do konfiguračního souboru pro Svcutil. exe (Svcutil. exe. config):  
  
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
  
3. Vytvořte novou <xref:System.ServiceModel.Description.WsdlImporter> instanci (předáním <xref:System.ServiceModel.Description.MetadataSet> do instance obsahující dokumenty WSDL, které chcete importovat) a zavolejte <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>:  
  
    ```  
    WsdlImporter importer = new WsdlImporter(metaDocs);          System.Collections.ObjectModel.Collection<ContractDescription> contracts  = importer.ImportAllContracts();  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Metadata](../feature-details/metadata.md)
- [Export a import metadat](../feature-details/exporting-and-importing-metadata.md)
- [Vlastní publikování WSDL](../samples/custom-wsdl-publication.md)
