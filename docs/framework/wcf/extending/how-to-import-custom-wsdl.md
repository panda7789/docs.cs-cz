---
title: 'Postupy: Import vlastního WSDL'
ms.date: 03/30/2017
ms.assetid: ddc3718d-ce60-44f6-92af-a5c67477dd99
ms.openlocfilehash: 10fc3282560d35e61044a367f8172571096d76bd
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975892"
---
# <a name="how-to-import-custom-wsdl"></a><span data-ttu-id="f5bbc-102">Postupy: Import vlastního WSDL</span><span class="sxs-lookup"><span data-stu-id="f5bbc-102">How to: Import Custom WSDL</span></span>
<span data-ttu-id="f5bbc-103">Toto téma popisuje, jak importovat vlastní WSDL.</span><span class="sxs-lookup"><span data-stu-id="f5bbc-103">This topic describes how to import custom WSDL.</span></span> <span data-ttu-id="f5bbc-104">Chcete-li zpracovat vlastní WSDL, je nutné implementovat rozhraní <xref:System.ServiceModel.Description.IWsdlImportExtension>.</span><span class="sxs-lookup"><span data-stu-id="f5bbc-104">To handle the custom WSDL, you must implement the <xref:System.ServiceModel.Description.IWsdlImportExtension> interface.</span></span>  
  
### <a name="to-import-custom-wsdl"></a><span data-ttu-id="f5bbc-105">Import vlastního WSDL</span><span class="sxs-lookup"><span data-stu-id="f5bbc-105">To import custom WSDL</span></span>  
  
1. <span data-ttu-id="f5bbc-106">Implementujte <xref:System.ServiceModel.Description.IWsdlImportExtension>.</span><span class="sxs-lookup"><span data-stu-id="f5bbc-106">Implement <xref:System.ServiceModel.Description.IWsdlImportExtension>.</span></span> <span data-ttu-id="f5bbc-107">Implementací metody <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%28System.Web.Services.Description.ServiceDescriptionCollection%2CSystem.Xml.Schema.XmlSchemaSet%2CSystem.Collections.Generic.ICollection%7BSystem.Xml.XmlElement%7D%29> upravte metadata předtím, než se naimportují.</span><span class="sxs-lookup"><span data-stu-id="f5bbc-107">Implement the <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%28System.Web.Services.Description.ServiceDescriptionCollection%2CSystem.Xml.Schema.XmlSchemaSet%2CSystem.Collections.Generic.ICollection%7BSystem.Xml.XmlElement%7D%29> method to modify the metadata before it is imported.</span></span> <span data-ttu-id="f5bbc-108">Implementací metod <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> a <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> upravte smlouvy a koncové body importované z metadat.</span><span class="sxs-lookup"><span data-stu-id="f5bbc-108">Implement the <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> and <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> methods to modify contracts and endpoints imported from the metadata.</span></span> <span data-ttu-id="f5bbc-109">Chcete-li získat přístup k importované smlouvě nebo koncovému bodu, použijte odpovídající objekt kontextu (<xref:System.ServiceModel.Description.WsdlContractConversionContext> nebo <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>):</span><span class="sxs-lookup"><span data-stu-id="f5bbc-109">To access the imported contract or endpoint, use the corresponding context object (<xref:System.ServiceModel.Description.WsdlContractConversionContext> or <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>):</span></span>  
  
    ```csharp
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
  
2. <span data-ttu-id="f5bbc-110">Nakonfigurujte klientskou aplikaci tak, aby používala vlastní Import WSDL.</span><span class="sxs-lookup"><span data-stu-id="f5bbc-110">Configure the client application to use the custom WSDL importer.</span></span> <span data-ttu-id="f5bbc-111">Všimněte si, že pokud používáte Svcutil. exe, měli byste tuto konfiguraci přidat do konfiguračního souboru pro Svcutil. exe (Svcutil. exe. config):</span><span class="sxs-lookup"><span data-stu-id="f5bbc-111">Note that if you are using Svcutil.exe, you should add this configuration to the configuration file for Svcutil.exe (Svcutil.exe.config):</span></span>  
  
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
  
3. <span data-ttu-id="f5bbc-112">Vytvořte novou instanci <xref:System.ServiceModel.Description.WsdlImporter> (předejte do instance <xref:System.ServiceModel.Description.MetadataSet>, která obsahuje dokumenty WSDL, které chcete importovat) a zavolejte <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>:</span><span class="sxs-lookup"><span data-stu-id="f5bbc-112">Create a new <xref:System.ServiceModel.Description.WsdlImporter> instance (passing in the <xref:System.ServiceModel.Description.MetadataSet> instance that contains the WSDL documents that you want to import), and call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>:</span></span>  
  
    ```csharp
    WsdlImporter importer = new WsdlImporter(metaDocs);
    System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f5bbc-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f5bbc-113">See also</span></span>

- [<span data-ttu-id="f5bbc-114">Metadata</span><span class="sxs-lookup"><span data-stu-id="f5bbc-114">Metadata</span></span>](../feature-details/metadata.md)
- [<span data-ttu-id="f5bbc-115">Export a import metadat</span><span class="sxs-lookup"><span data-stu-id="f5bbc-115">Exporting and Importing Metadata</span></span>](../feature-details/exporting-and-importing-metadata.md)
- [<span data-ttu-id="f5bbc-116">Vlastní publikování WSDL</span><span class="sxs-lookup"><span data-stu-id="f5bbc-116">Custom WSDL Publication</span></span>](../samples/custom-wsdl-publication.md)
