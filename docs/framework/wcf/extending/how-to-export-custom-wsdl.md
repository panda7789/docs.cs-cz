---
title: 'Postupy: Export vlastního WSDL'
ms.date: 03/30/2017
ms.assetid: 5c1e4b58-b76b-472b-9635-2f80d42a0734
ms.openlocfilehash: 86c6be86febb21f3c676d28357b29db5dcca07db
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645142"
---
# <a name="how-to-export-custom-wsdl"></a>Postupy: Export vlastního WSDL
Toto téma vysvětluje, jak exportovat informace o vlastním WSDL. Provedete to nadefinujeme nový atribut kód volá `WsdlDocumentationAttribute` , který bude přidání vlastních informací do WSDL vygenerované službou.  
  
### <a name="to-export-custom-wsdl-information"></a>Export vlastního WSDL informace  
  
1.  Implementujte rozhraní <xref:System.ServiceModel.Description.IWsdlExportExtension>. Toto rozhraní je možné implementovat na třídu, která implementuje některý z následujících rozhraní: <xref:System.ServiceModel.Description.IOperationBehavior>, <xref:System.ServiceModel.Description.IContractBehavior>, nebo <xref:System.ServiceModel.Description.IEndpointBehavior>. To může být implementováno na třídu odvozenou z <xref:System.ServiceModel.Channels.BindingElement>. Tato ukázka implementuje <xref:System.ServiceModel.Description.IWsdlExportExtension> na třídu atributu, který implementuje <xref:System.ServiceModel.Description.IContractBehavior>.  
  
2.  <xref:System.ServiceModel.Description.IWsdlExportExtension> definuje dvě metody <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> a <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29>. Tyto metody umožňují změnit nebo přidat (nebo upravit a přidat) Další informace do <xref:System.ServiceModel.Description.WsdlContractConversionContext>. Tento ukázkový v <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> metoda, načte kolekci <xref:System.ServiceModel.Description.OperationDescription> objekty a pak Iteruje přes kolekci kontrolují `WsdlDocumentationAttribute`. Pokud není nalezen takový, přidružený k atributu text je extrahován, je generována summary element a summary element se přidá do `DocumentationElement` operace.  
  
    ```  
            public void ExportContract(WsdlExporter exporter, WsdlContractConversionContext context)  
    {  
                Console.WriteLine("Inside ExportContract");  
    if (context.Contract != null)  
    {  
                    // Set the document element; if this is not done first, there is no XmlElement in the   
                    // DocumentElement property.  
                    context.WsdlPortType.Documentation = string.Empty;   
                    // Contract comments.  
                    XmlDocument owner = context.WsdlPortType.DocumentationElement.OwnerDocument;  
                    XmlElement summaryElement = Formatter.CreateSummaryElement(owner, this.Text);   
                    context.WsdlPortType.DocumentationElement.AppendChild(summaryElement);  
  
                    foreach (OperationDescription op in context.Contract.Operations)  
                    {  
                        Operation operation = context.GetOperation(op);  
                        object[] opAttrs = op.SyncMethod.GetCustomAttributes(typeof(WsdlDocumentationAttribute), false);  
                        if (opAttrs.Length == 1)  
                        {  
                            string opComment = ((WsdlDocumentationAttribute)opAttrs[0]).Text;  
  
                            // This.Text returns the string for the operation-level attributes.  
                            // Set the doc element; if this is not done first, there is no XmlElement in the   
                            // DocumentElement property.  
                            operation.Documentation = String.Empty;  
  
                            XmlDocument opOwner = operation.DocumentationElement.OwnerDocument;  
                            XmlElement newSummaryElement = Formatter.CreateSummaryElement(opOwner, opComment);  
                            operation.DocumentationElement.AppendChild(newSummaryElement);  
                        }  
                    }  
                }  
    ```  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje úplnou implementaci daného `WsdlDocumentationAttribute` třídy.  
  
```  
public class WsdlDocumentationAttribute : Attribute, IContractBehavior, IWsdlExportExtension  
{  
string text;  
       XmlElement customWsdlDocElement = null;  
public WsdlDocumentationAttribute(string text)  
{ this.text = text;}  
  
       public WsdlDocumentationAttribute(XmlElement wsdlDocElement)  
        { this.customWsdlDocElement = wsdlDocElement; }  
  
        public XmlElement WsdlDocElement  
        {  
            get { return this.customWsdlDocElement; }  
            set { this.customWsdlDocElement = value; }  
        }  
       public string Text  
{  
get { return this.text; }  
set { this.text = value; }  
}  
  
     public void ExportContract(WsdlExporter exporter, WsdlContractConversionContext context)  
{  
          Console.WriteLine("Inside ExportContract");  
if (context.Contract != null)  
{  
                // Set the document element; if this is not done first, there is no XmlElement in the   
                // DocumentElement property.  
                context.WsdlPortType.Documentation = string.Empty;   
                // Contract comments.  
                XmlDocument owner = context.WsdlPortType.DocumentationElement.OwnerDocument;  
                XmlElement summaryElement = Formatter.CreateSummaryElement(owner, this.Text);   
                context.WsdlPortType.DocumentationElement.AppendChild(summaryElement);  
  
                foreach (OperationDescription op in context.Contract.Operations)  
                {  
                    Operation operation = context.GetOperation(op);  
                    object[] opAttrs = op.SyncMethod.GetCustomAttributes(typeof(WsdlDocumentationAttribute), false);  
                    if (opAttrs.Length == 1)  
                    {  
                        string opComment = ((WsdlDocumentationAttribute)opAttrs[0]).Text;  
  
                        // This.Text returns the string for the operation-level attributes.  
                        // Set the document element; if this is not done first, there is no XmlElement in the   
                        // DocumentElement property.  
                        operation.Documentation = String.Empty;  
  
                        XmlDocument opOwner = operation.DocumentationElement.OwnerDocument;  
                        XmlElement newSummaryElement = Formatter.CreateSummaryElement(opOwner, opComment);  
                        operation.DocumentationElement.AppendChild(newSummaryElement);  
                    }  
                }  
            }  
        }  
  
public void ExportEndpoint(WsdlExporter exporter, WsdlEndpointConversionContext context)   
        {  
            Console.WriteLine("ExportEndpoint called.");  
        }  
  
        public void AddBindingParameters(ContractDescription description, ServiceEndpoint endpoint, BindingParameterCollection parameters)  
        { return; }  
  
        public void ApplyClientBehavior(ContractDescription description, ServiceEndpoint endpoint, ClientRuntime client)  
        { return; }  
  
        public void ApplyDispatchBehavior(ContractDescription description, ServiceEndpoint endpoint, DispatchRuntime dispatch)  
        { return; }  
  
        public void Validate(ContractDescription description, ServiceEndpoint endpoint) { return; }  
    }  
  
  public class Formatter  
  {  
  
#region Utility Functions  
  
    public static XmlElement CreateSummaryElement(XmlDocument owningDoc, string text)  
    {  
      XmlElement summaryElement = owningDoc.CreateElement("summary");  
      summaryElement.InnerText = text;  
      return summaryElement;  
    }  
  
public static CodeCommentStatementCollection FormatComments(string text)  
{  
      /*  
       * Note that in Visual C# the XML comment format absorbs a   
       * documentation element with a line break in the middle. This sample  
       * could take an XmlElement and create code comments in which   
       * the element never had a line break in it.  
      */  
  
      CodeCommentStatementCollection collection = new CodeCommentStatementCollection();  
collection.Add(new CodeCommentStatement("From WsdlDocumentation:", true));  
collection.Add(new CodeCommentStatement(String.Empty, true));  
  
foreach (string line in WordWrap(text, 80))  
{  
collection.Add(new CodeCommentStatement(line, true));  
}  
  
collection.Add(new CodeCommentStatement(String.Empty, true));  
return collection;  
}  
  
public static Collection<string> WordWrap(string text, int columnWidth)  
{  
Collection<string> lines = new Collection<string>();  
System.Text.StringBuilder builder = new System.Text.StringBuilder();  
  
string[] words = text.Split(' ');  
foreach (string word in words)  
{  
if ((builder.Length > 0) && ((builder.Length + word.Length + 1) > columnWidth))  
{  
lines.Add(builder.ToString());  
builder = new System.Text.StringBuilder();  
}  
builder.Append(word);  
builder.Append(' ');  
}  
lines.Add(builder.ToString());  
  
return lines;  
}  
  
#endregion    
  
    public static XmlElement CreateReturnsElement(XmlDocument owner, string p)  
    {  
      XmlElement returnsElement = owner.CreateElement("returns");  
      returnsElement.InnerText = p;  
      return returnsElement;  
    }  
  }  
```  
  
## <a name="see-also"></a>Viz také:
- [Metadata](../../../../docs/framework/wcf/feature-details/metadata.md)
