---
title: "Vlastní publikování WSDL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b3e8103-2c95-4db3-a05b-46aa8e9d4d29
caps.latest.revision: "21"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7e390bf728cde703a967fcea954583f6e5f84002
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="custom-wsdl-publication"></a>Vlastní publikování WSDL
Tento příklad znázorňuje postup:  
  
-   Implementace <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> na vlastní <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> atribut, který chcete exportovat vlastnosti atribut jako WSDL poznámky.  
  
-   Implementace <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> Import vlastního WSDL poznámky.  
  
-   Implementace <xref:System.ServiceModel.Description.IServiceContractGenerationExtension?displayProperty=nameWithType> a <xref:System.ServiceModel.Description.IOperationContractGenerationExtension?displayProperty=nameWithType> na vlastní smlouvy chování a vlastní operace chování, v uvedeném pořadí, zápis importované poznámky jako komentáře v modelu CodeDom pro importované kontrakt a operace.  
  
-   Použití <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> ke stažení WSDL, <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> import schématu WSDL pomocí vlastní – Importér WSDL a <xref:System.ServiceModel.Description.ServiceContractGenerator?displayProperty=nameWithType> ke generování [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] kód klienta s poznámkami WSDL jako / / / a ''' komentáře v jazyce C# a Visual Basic.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
## <a name="service"></a>Služba  
 Služby v této ukázce je označené dvěma vlastní atributy. První, `WsdlDocumentationAttribute`, přijme řetězec v konstruktoru a dají se použít k poskytování rozhraní kontraktu nebo operaci s řetězec, který popisuje jeho použití. Druhá s názvem `WsdlParamOrReturnDocumentationAttribute`, můžete použít k vrácení hodnoty nebo parametry, které popisují tyto hodnoty v operaci. Následující příklad ukazuje kontraktu služby `ICalculator`, které jsou popsány pomocí těchto atributů.  
  
```  
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
  
 `WsdlDocumentationAttribute` Implementuje <xref:System.ServiceModel.Description.IContractBehavior> a <xref:System.ServiceModel.Description.IOperationBehavior>, takže instance atributy jsou přidány do odpovídajících <xref:System.ServiceModel.Description.ContractDescription> nebo <xref:System.ServiceModel.Description.OperationDescription> při otevření službu. Atribut také implementuje <xref:System.ServiceModel.Description.IWsdlExportExtension>. Když <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> je volána, <xref:System.ServiceModel.Description.WsdlExporter> používané pro export metadat a <xref:System.ServiceModel.Description.WsdlContractConversionContext> obsahující popis služby předávání objektů v jako parametry umožňující úpravy exportovaný metadat.  
  
 V této ukázce, v závislosti na tom, jestli má objekt context exportu <xref:System.ServiceModel.Description.ContractDescription> nebo <xref:System.ServiceModel.Description.OperationDescription>, komentář se extrahuje z atributu pomocí vlastnosti text a je přidán do elementu WSDL poznámky, jak je znázorněno v následujícím kódu.  
  
```  
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
  
 Pokud je v průběhu operace exportu příklad používá reflexe získat žádné `WsdlParamOrReturnDocumentationAttribute` hodnoty pro parametry a návratové hodnoty a přidá je do elementů poznámky WSDL pro tuto operaci následujícím způsobem.  
  
```  
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
  
 Ukázka pak publikuje metadata standardní způsobem, pomocí následujícího konfiguračního souboru.  
  
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
  
## <a name="svcutil-client"></a>Svcutil klienta  
 Tato ukázka nepoužívá Svcutil.exe. Kontrakt je zadaný v generatedClient.cs nelze vyvolat soubor, který po ukázku ukazuje vlastní importu WSDL a generování kódu, službu. Pokud chcete použít následující vlastní – Importér WSDL pro tento příklad, můžete spustit Svcutil.exe a zadejte `/svcutilConfig` možnost poskytnutí cestu k souboru konfigurace klienta použít v této ukázce, která odkazuje `WsdlDocumentation.dll` knihovny. Načíst `WsdlDocumentationImporter`, ale musí být schopný pro vyhledání a načtení Svuctil.exe `WsdlDocumentation.dll` knihovny, tzn. buď ji je zaregistrován v globální mezipaměti sestavení, v cestě, nebo je ve stejném adresáři jako Svcutil.exe. Základní příklad, jako je tato, je nejjednodušší cesta ke kopírování Svcutil.exe a konfigurační soubor klienta do stejného adresáře jako `WsdlDocumentation.dll` a spusťte jej z ní.  
  
## <a name="the-custom-wsdl-importer"></a>Program pro import vlastního WSDL  
 Vlastní <xref:System.ServiceModel.Description.IWsdlImportExtension> objekt `WsdlDocumentationImporter` také implementuje <xref:System.ServiceModel.Description.IContractBehavior> a <xref:System.ServiceModel.Description.IOperationBehavior> přidat do třídy importované ServiceEndpoints a <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> a <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> má být volána k úpravě generování kódu při kontrakt nebo operace Probíhá vytváření kódu.  
  
 V první <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> metoda, ukázku Určuje, zda WSDL poznámky na úrovni kontrakt nebo operace a přidá sám sebe jako chování v příslušné oboru, a jeho konstruktoru předá text importované poznámky.  
  
```  
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
  
 Poté, když se vygeneruje kód, systém vyvolá <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> a <xref:System.ServiceModel.Description.IOperationContractGenerationExtension.GenerateOperation%28System.ServiceModel.Description.OperationContractGenerationContext%29> metody, předávání informací odpovídající kontext. Ukázka formáty vlastní poznámky WSDL a vloží je do modelu CodeDom jako komentáře.  
  
```  
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
  
## <a name="the-client-application"></a>Klientské aplikace  
 Klientská aplikace načte vlastní – Importér WSDL zadáním v konfiguračním souboru aplikace.  
  
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
  
 Jakmile byl zadán vlastní – Importér, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] systém metadat načte vlastní – Importér do jakéhokoli <xref:System.ServiceModel.Description.WsdlImporter> vytvořený pro tento účel. Této ukázce se používá <xref:System.ServiceModel.Description.MetadataExchangeClient> stáhnout metadata, <xref:System.ServiceModel.Description.WsdlImporter> správně nakonfigurovaná tak, aby import metadat pomocí vlastní – Importér ukázka vytvoří, a <xref:System.ServiceModel.Description.ServiceContractGenerator> zkompilovat upravené kontrakt informace do obou jazyka Visual Basic C# kódu a klienta, můžete použít v sadě Visual Studio pro podporu technologie Intellisense nebo zkompilovat do dokumentace XML.  
  
```  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\WsdlDocumentation`  
  
## <a name="see-also"></a>Viz také
