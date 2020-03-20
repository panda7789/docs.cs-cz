---
title: Vlastní publikování WSDL
ms.date: 03/30/2017
ms.assetid: 3b3e8103-2c95-4db3-a05b-46aa8e9d4d29
ms.openlocfilehash: ae6d5fdf243d5000090e993bd3353c6180d0ccaa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145056"
---
# <a name="custom-wsdl-publication"></a>Vlastní publikování WSDL
Tato ukázka ukazuje, jak:  
  
- Implementujte <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> na <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> vlastní atribut exportovat atribut vlastnosti jako poznámky WSDL.  
  
- Implementovat <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> importovat vlastní WSDL poznámky.  
  
- <xref:System.ServiceModel.Description.IServiceContractGenerationExtension?displayProperty=nameWithType> Implementovat <xref:System.ServiceModel.Description.IOperationContractGenerationExtension?displayProperty=nameWithType> a na vlastní chování smlouvy a vlastní operace chování, respektive psát importované poznámky jako komentáře v CodeDom pro importované smlouvy a operace.  
  
- Pomocí <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> ke stažení WSDL, <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> a importovat WSDL pomocí vlastního wsdl import a <xref:System.ServiceModel.Description.ServiceContractGenerator?displayProperty=nameWithType> generovat Windows Communication Foundation (WCF) klientský kód s WSDL poznámky jako /// a ''' komentáře v Jazyce C# a Visual Basic.  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
## <a name="service"></a>Služba  
 Služba v této ukázce je označena dvěma vlastními atributy. První , `WsdlDocumentationAttribute`přijímá řetězec v konstruktoru a lze použít k poskytnutí rozhraní smlouvy nebo operace s řetězcem, který popisuje jeho použití. Druhý , `WsdlParamOrReturnDocumentationAttribute`lze použít k vrácení hodnot nebo parametrů k popisu těchto hodnot v operaci. Následující příklad ukazuje servisní `ICalculator`smlouvu , popsanou pomocí těchto atributů.  
  
```csharp  
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
// Document it.  
[WsdlDocumentation("The ICalculator contract performs basic calculation services.")]  
public interface ICalculator  
{  
    [OperationContract]  
    [WsdlDocumentation("The Add operation adds two numbers and returns the result.")]  
    [return:WsdlParamOrReturnDocumentation("The result of adding the two arguments together.")]  
    double Add(  
      [WsdlParamOrReturnDocumentation("The first value to add.")]double n1,
      [WsdlParamOrReturnDocumentation("The second value to add.")]double n2  
    );  
  
    [OperationContract]  
    [WsdlDocumentation("The Subtract operation subtracts the second argument from the first.")]  
    [return:WsdlParamOrReturnDocumentation("The result of the second argument subtracted from the first.")]  
    double Subtract(  
      [WsdlParamOrReturnDocumentation("The value from which the second is subtracted.")]double n1,
      [WsdlParamOrReturnDocumentation("The value that is subtracted from the first.")]double n2  
    );  
  
    [OperationContract]  
    [WsdlDocumentation("The Multiply operation multiplies two values.")]  
    [return:WsdlParamOrReturnDocumentation("The result of multiplying the first and second arguments.")]  
    double Multiply(  
      [WsdlParamOrReturnDocumentation("The first value to multiply.")]double n1,
      [WsdlParamOrReturnDocumentation("The second value to multiply.")]double n2  
    );  
  
    [OperationContract]  
    [WsdlDocumentation("The Divide operation returns the value of the first argument divided by the second argument.")]  
    [return:WsdlParamOrReturnDocumentation("The result of dividing the first argument by the second.")]  
    double Divide(  
      [WsdlParamOrReturnDocumentation("The numerator.")]double n1,
      [WsdlParamOrReturnDocumentation("The denominator.")]double n2  
    );  
}  
```  
  
 Implements `WsdlDocumentationAttribute` <xref:System.ServiceModel.Description.IContractBehavior> a <xref:System.ServiceModel.Description.IOperationBehavior>, tak atribut instance jsou <xref:System.ServiceModel.Description.ContractDescription> přidány <xref:System.ServiceModel.Description.OperationDescription> do odpovídající nebo při otevření služby. Atribut také implementuje <xref:System.ServiceModel.Description.IWsdlExportExtension>. Při <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> volání, <xref:System.ServiceModel.Description.WsdlExporter> který se používá k exportu <xref:System.ServiceModel.Description.WsdlContractConversionContext> metadat a který obsahuje objekty popisu služby jsou předány jako parametry umožňující změnu exportovaných metadat.  
  
 V této ukázce, v závislosti <xref:System.ServiceModel.Description.ContractDescription> na <xref:System.ServiceModel.Description.OperationDescription>tom, zda export kontextu objekt má nebo , komentář je extrahován z atributu pomocí vlastnosti text a je přidán do wsdl anotace prvek, jak je znázorněno v následujícím kódu.  
  
```csharp
public void ExportContract(WsdlExporter exporter, WsdlContractConversionContext context)
{
    if (contractDescription != null)
    {
        // Inside this block it is the contract-level comment attribute.
        // This.Text returns the string for the contract attribute.
        // Set the doc element; if this isn't done first, there is no XmlElement in the
        // DocumentElement property.
        context.WsdlPortType.Documentation = string.Empty;
        // Contract comments.
        XmlDocument owner = context.WsdlPortType.DocumentationElement.OwnerDocument;
        XmlElement summaryElement = owner.CreateElement("summary");
        summaryElement.InnerText = this.Text;
        context.WsdlPortType.DocumentationElement.AppendChild(summaryElement);
    }
    else
    {
        Operation operation = context.GetOperation(operationDescription);
        if (operation != null)
        {
            // We are dealing strictly with the operation here.
            // This.Text returns the string for the operation-level attributes.
            // Set the doc element; if this isn't done first, there is no XmlElement in the
            // DocumentElement property.
            operation.Documentation = String.Empty;

            // Operation C# triple comments.
            XmlDocument owner = operation.DocumentationElement.OwnerDocument;
            XmlElement newSummaryElement = owner.CreateElement("summary");
            newSummaryElement.InnerText = this.Text;
            operation.DocumentationElement.AppendChild(newSummaryElement);
        }
    }
}
```  
  
 Pokud je operace exportována, ukázka používá `WsdlParamOrReturnDocumentationAttribute` reflexe k získání všech hodnot pro parametry a vrácené hodnoty a přidá je do prvků poznámky WSDL pro tuto operaci následujícím způsobem.  
  
```csharp
// Get returns information  
ParameterInfo returnValue = operationDescription.SyncMethod.ReturnParameter;  
object[] returnAttrs = returnValue.GetCustomAttributes(typeof(WsdlParamOrReturnDocumentationAttribute), false);  
if (returnAttrs.Length != 0)  
{  
    // <returns>text.</returns>  
    XmlElement returnsElement = owner.CreateElement("returns");  
    returnsElement.InnerText = ((WsdlParamOrReturnDocumentationAttribute)returnAttrs[0]).ParamComment;  
    operation.DocumentationElement.AppendChild(returnsElement);  
}  
  
// Get parameter information.  
ParameterInfo[] args = operationDescription.SyncMethod.GetParameters();  
for (int i = 0; i < args.Length; i++)  
{  
    object[] docAttrs = args[i].GetCustomAttributes(typeof(WsdlParamOrReturnDocumentationAttribute), false);  
    if (docAttrs.Length == 1)  
    {  
        // <param name="Int1">Text.</param>  
        XmlElement newParamElement = owner.CreateElement("param");  
        XmlAttribute paramName = owner.CreateAttribute("name");  
        paramName.Value = args[i].Name;  
        newParamElement.InnerText = ((WsdlParamOrReturnDocumentationAttribute)docAttrs[0]).ParamComment;  
        newParamElement.Attributes.Append(paramName);  
        operation.DocumentationElement.AppendChild(newParamElement);  
    }  
}  
```  
  
 Ukázka pak publikuje metadata standardním způsobem pomocí následujícího konfiguračního souboru.  
  
```xml  
<services>  
  <service
      name="Microsoft.ServiceModel.Samples.CalculatorService"  
      behaviorConfiguration="CalculatorServiceBehavior">  
    <!-- ICalculator is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc  -->  
    <endpoint address=""  
              binding="wsHttpBinding"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    <!-- the mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex -->  
    <endpoint address="mex"  
              binding="mexHttpBinding"  
              contract="IMetadataExchange" />  
  </service>  
</services>  
  
<!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="svcutil-client"></a>Klient Svcutil  
 Tato ukázka nepoužívá Svcutil.exe. Smlouva je k dispozici v souboru generatedClient.cs tak, aby po ukázka ukazuje vlastní WSDL import a generování kódu, služby lze vyvolat. Chcete-li použít následující vlastní WSDL import pro tento příklad, můžete spustit `/svcutilConfig` Svcutil.exe a zadat možnost, která poskytuje `WsdlDocumentation.dll` cestu ke konfiguračnímu souboru klienta použitému v této ukázce, který odkazuje na knihovnu. Chcete-li `WsdlDocumentationImporter`však načíst program , musí být program Svuctil.exe schopen vyhledat a načíst knihovnu, `WsdlDocumentation.dll` což znamená, že je registrován v globální mezipaměti sestavení v cestě nebo je ve stejném adresáři jako svcutil.exe. Pro základní vzorek, jako je tento, nejjednodušší věc udělat, je zkopírovat Svcutil.exe `WsdlDocumentation.dll` a konfigurační soubor klienta do stejného adresáře jako a spustit jej odtud.  
  
## <a name="the-custom-wsdl-importer"></a>Vlastní wsdl import  
 Vlastní <xref:System.ServiceModel.Description.IWsdlImportExtension> objekt `WsdlDocumentationImporter` také <xref:System.ServiceModel.Description.IContractBehavior> implementuje <xref:System.ServiceModel.Description.IOperationBehavior> a má být přidán <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> do <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> importovaných ServiceEndpoints a má být vyvolán k úpravě generování kódu při vytváření smlouvy nebo operace.  
  
 Nejprve v <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> metodě ukázka určuje, zda je anotace WSDL na úrovni smlouvy nebo operace a přidá se jako chování v příslušném oboru a předá importovaný text poznámky svému konstruktoru.  
  
```csharp
public void ImportContract(WsdlImporter importer, WsdlContractConversionContext context)  
{  
    // Contract Documentation  
    if (context.WsdlPortType.Documentation != null)  
    {  
        // System examines the contract behaviors to see whether any implement IWsdlImportExtension.  
        context.Contract.Behaviors.Add(new WsdlDocumentationImporter(context.WsdlPortType.Documentation));  
    }  
    // Operation Documentation  
    foreach (Operation operation in context.WsdlPortType.Operations)  
    {  
        if (operation.Documentation != null)  
        {  
            OperationDescription operationDescription = context.Contract.Operations.Find(operation.Name);  
            if (operationDescription != null)  
            {  
                // System examines the operation behaviors to see whether any implement IWsdlImportExtension.  
                operationDescription.Behaviors.Add(new WsdlDocumentationImporter(operation.Documentation));  
            }  
        }  
    }  
}  
```  
  
 Potom při generování kódu, systém vyvolá <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> a <xref:System.ServiceModel.Description.IOperationContractGenerationExtension.GenerateOperation%28System.ServiceModel.Description.OperationContractGenerationContext%29> metody, předávání příslušné informace o kontextu. Ukázka zformátuje vlastní poznámky WSDL a vloží je jako komentáře do CodeDom.  
  
```csharp
public void GenerateContract(ServiceContractGenerationContext context)  
{  
    Debug.WriteLine("In generate contract.");  
    context.ContractType.Comments.AddRange(FormatComments(text));  
}  
  
public void GenerateOperation(OperationContractGenerationContext context)  
{  
    context.SyncMethod.Comments.AddRange(FormatComments(text));  
    Debug.WriteLine("In generate operation.");  
}  
```  
  
## <a name="the-client-application"></a>Klientská aplikace  
 Klientská aplikace načte vlastní import WSDL zadáním v konfiguračním souboru aplikace.  
  
```xml  
<client>  
  <endpoint address="http://localhost/servicemodelsamples/service.svc"
  binding="wsHttpBinding"
  contract="ICalculator" />  
  <metadata>  
    <wsdlImporters>  
      <extension type="Microsoft.ServiceModel.Samples.WsdlDocumentationImporter, WsdlDocumentation"/>  
    </wsdlImporters>  
  </metadata>  
</client>  
```  
  
 Po zadání vlastního dovozce načte systém metadat WCF vlastní <xref:System.ServiceModel.Description.WsdlImporter> importér do všech vytvořených pro tento účel. Tato ukázka <xref:System.ServiceModel.Description.MetadataExchangeClient> používá ke stažení <xref:System.ServiceModel.Description.WsdlImporter> metadata, správně nakonfigurován pro import metadat pomocí <xref:System.ServiceModel.Description.ServiceContractGenerator> vlastního importu vzorku vytvoří a zkompilovat upravené informace o smlouvě do jazyka Visual Basic a C# klientský kód, který lze použít v sadě Visual Studio pro podporu Intellisense nebo kompilovány do dokumentace XML.  
  
```csharp
/// From WSDL Documentation:  
///
/// <summary>The ICalculator contract performs basic calculation
/// services.</summary>
///
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.ServiceContractAttribute(Namespace="http://Microsoft.ServiceModel.Samples", ConfigurationName="ICalculator")]  
public interface ICalculator  
{  
  
    /// From WSDL Documentation:  
    ///
    /// <summary>The Add operation adds two numbers and returns the
    /// result.</summary><returns>The result of adding the two arguments
    /// together.</returns><param name="n1">The first value to add.</param><param
    /// name="n2">The second value to add.</param>
    ///
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Add", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/AddResponse")]  
    double Add(double n1, double n2);  
  
    /// From WSDL Documentation:  
    ///
    /// <summary>The Subtract operation subtracts the second argument from the
    /// first.</summary><returns>The result of the second argument subtracted from the
    /// first.</returns><param name="n1">The value from which the second is
    /// subtracted.</param><param name="n2">The value that is subtracted from the
    /// first.</param>
    ///
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Subtract", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/SubtractResponse")]  
    double Subtract(double n1, double n2);  
  
    /// From WSDL Documentation:  
    ///
    /// <summary>The Multiply operation multiplies two values.</summary><returns>The
    /// result of multiplying the first and second arguments.</returns><param
    /// name="n1">The first value to multiply.</param><param name="n2">The second value
    /// to multiply.</param>
    ///
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Multiply", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/MultiplyResponse")]  
    double Multiply(double n1, double n2);  
  
    /// From WSDL Documentation:  
    ///
    /// <summary>The Divide operation returns the value of the first argument divided
    /// by the second argument.</summary><returns>The result of dividing the first
    /// argument by the second.</returns><param name="n1">The numerator.</param><param
    /// name="n2">The denominator.</param>
    ///
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Divide", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/DivideResponse")]  
    double Divide(double n1, double n2);  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\WsdlDocumentation`  
