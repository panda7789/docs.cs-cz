---
title: Vlastní publikování WSDL
ms.date: 03/30/2017
ms.assetid: 3b3e8103-2c95-4db3-a05b-46aa8e9d4d29
ms.openlocfilehash: 8674d852be45119b247ec10bbc639922850d5a90
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928853"
---
# <a name="custom-wsdl-publication"></a>Vlastní publikování WSDL
Tato ukázka předvádí, jak:  
  
- Implementujte vlastní <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> atribut pro export vlastností atributu jako anotace WSDL. <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType>  
  
- Implementujte <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> pro import vlastních poznámek WSDL.  
  
- <xref:System.ServiceModel.Description.IServiceContractGenerationExtension?displayProperty=nameWithType> Implementujte <xref:System.ServiceModel.Description.IOperationContractGenerationExtension?displayProperty=nameWithType> a na vlastní chování kontraktu a chování vlastní operace pro zápis importovaných poznámek jako komentářů v CodeDom pro importovanou smlouvu a operaci.  
  
- Použijte ke stažení WSDL <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> , a pro Import WSDL pomocí vlastního programu <xref:System.ServiceModel.Description.ServiceContractGenerator?displayProperty=nameWithType> pro Import WSDL, a pro generování kódu klienta Windows Communication Foundation (WCF) s poznámkami WSDL jako///a komentáři v a C# <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> Visual Basic.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
## <a name="service"></a>Služba  
 Služba v této ukázce je označena dvěma vlastními atributy. První, `WsdlDocumentationAttribute`, přijímá řetězec v konstruktoru a lze jej použít pro poskytnutí rozhraní kontraktu nebo operace s řetězcem, který popisuje jeho použití. Druhý, `WsdlParamOrReturnDocumentationAttribute`,, lze použít pro návrat hodnoty nebo parametry k popisu těchto hodnot v operaci. Následující příklad ukazuje kontrakt služby, `ICalculator`popsaný pomocí těchto atributů.  
  
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
  
 `WsdlDocumentationAttribute` Implementuje <xref:System.ServiceModel.Description.ContractDescription> <xref:System.ServiceModel.Description.OperationDescription> a, takže instance atributů jsou přidány do odpovídající nebo při otevření služby. <xref:System.ServiceModel.Description.IOperationBehavior> <xref:System.ServiceModel.Description.IContractBehavior> Atribut také implementuje <xref:System.ServiceModel.Description.IWsdlExportExtension>. Při <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> volání metody <xref:System.ServiceModel.Description.WsdlExporter> , která slouží k <xref:System.ServiceModel.Description.WsdlContractConversionContext> exportu metadat a obsahuje objekty popisu služby, jsou předány jako parametry, které umožňují úpravu exportovaných metadat.  
  
 V této ukázce, v závislosti na tom, zda má <xref:System.ServiceModel.Description.ContractDescription> objekt kontextu exportu <xref:System.ServiceModel.Description.OperationDescription>nebo, je komentář extrahován z atributu pomocí vlastnosti text a je přidán do prvku poznámky WSDL, jak je znázorněno v následujícím kódu.  
  
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
```  
  
 Je-li exportována operace, používá ukázka reflexe k získání `WsdlParamOrReturnDocumentationAttribute` všech hodnot parametrů a vrácených hodnot a přidává je do prvků poznámky WSDL pro tuto operaci následujícím způsobem.  
  
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
 Tato ukázka nepoužívá Svcutil. exe. Smlouva je k dispozici v souboru generatedClient.cs tak, aby po ukázce předvedla vlastní import a generování kódu WSDL, službu lze vyvolat. Chcete-li použít následující vlastní Import WSDL pro tento příklad, můžete spustit Svcutil. exe a zadat `/svcutilConfig` možnost a zadat cestu ke konfiguračnímu souboru klienta použitému v této ukázce, který odkazuje na `WsdlDocumentation.dll` knihovnu. Aby bylo možné `WsdlDocumentationImporter`načíst, ale Svuctil. exe musí být schopna najít a `WsdlDocumentation.dll` načíst knihovnu, což znamená, že je registrována v globální mezipaměti sestavení (GAC), v cestě nebo je ve stejném adresáři jako Svcutil. exe. Pro základní vzorek, jako je to nejjednodušší, je zkopírovat Svcutil. exe a konfigurační soubor klienta do stejného adresáře jako `WsdlDocumentation.dll` a spustit ho odtud.  
  
## <a name="the-custom-wsdl-importer"></a>Vlastní Import WSDL  
 <xref:System.ServiceModel.Description.IWsdlImportExtension> Vlastní <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> objekt `WsdlDocumentationImporter` také implementuje<xref:System.ServiceModel.Description.IContractBehavior> a<xref:System.ServiceModel.Description.IOperationBehavior> k přidání do importovaných ServiceEndpoints a a k vyvolání pro úpravu generování kódu při kontraktu nebo operaci. vytváří se kód.  
  
 Nejprve ukázka v <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> metodě určí, zda je Poznámka WSDL na úrovni smlouvy nebo operace, a přidá samu sebe jako chování v příslušném oboru a předá importovaná text poznámky do konstruktoru.  
  
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
  
 Po vygenerování kódu pak systém vyvolá <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> metody a a <xref:System.ServiceModel.Description.IOperationContractGenerationExtension.GenerateOperation%28System.ServiceModel.Description.OperationContractGenerationContext%29> předává příslušné kontextové informace. Ukázka formátuje vlastní anotace WSDL a vkládá je jako komentáře do CodeDom.  
  
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
 Klientská aplikace načte vlastní Import WSDL zadáním do konfiguračního souboru aplikace.  
  
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
  
 Po určení vlastního dovozce načte systém metadat WCF vlastní dovozce do libovolného <xref:System.ServiceModel.Description.WsdlImporter> vytvořeného pro tento účel. V této ukázce se <xref:System.ServiceModel.Description.MetadataExchangeClient> používá ke stažení metadat <xref:System.ServiceModel.Description.WsdlImporter> , ke správné konfiguraci pro import metadat pomocí vlastního dovozce, který <xref:System.ServiceModel.Description.ServiceContractGenerator> ukázka vytvoří, a k zkompilování upravených informací o kontraktu do obou Visual Basic a C# klientský kód, který lze použít v sadě Visual Studio pro podporu technologie IntelliSense nebo kompilování do dokumentace XML.  
  
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
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\WsdlDocumentation`  
