---
title: Nastavení vlastnosti použití a stylu – Ukázky WCF
ms.date: 03/30/2017
ms.assetid: c09a0600-116f-41cf-900a-1b7e4ea4e300
ms.openlocfilehash: 654bba8535ab253bdd34f64e7b6ab2fab66fd33b
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65637700"
---
# <a name="setting-the-use-and-style-properties"></a><span data-ttu-id="09124-102">Nastavení vlastností Use a Style</span><span class="sxs-lookup"><span data-stu-id="09124-102">Setting the Use and Style Properties</span></span>

<span data-ttu-id="09124-103">Tento příklad znázorňuje způsob použití vlastností použití a stylu na <xref:System.ServiceModel.XmlSerializerFormatAttribute> a <xref:System.ServiceModel.DataContractFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="09124-103">This sample demonstrates how to use the Use and Style properties on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> and the <xref:System.ServiceModel.DataContractFormatAttribute>.</span></span> <span data-ttu-id="09124-104">Tyto vlastnosti vliv na způsob formátování zprávy.</span><span class="sxs-lookup"><span data-stu-id="09124-104">These properties affect how messages are formatted.</span></span> <span data-ttu-id="09124-105">Ve výchozím nastavení, text zprávy je formátováno s stylu nastavena na <xref:System.ServiceModel.OperationFormatStyle.Document>.</span><span class="sxs-lookup"><span data-stu-id="09124-105">By default, the message body is formatted with the style set to <xref:System.ServiceModel.OperationFormatStyle.Document>.</span></span> <span data-ttu-id="09124-106">Tato nastavení se dá nastavit na úrovni kontraktu služby nebo úroveň operace kontraktu.</span><span class="sxs-lookup"><span data-stu-id="09124-106">These settings can be specified at either the service contract level or the operation contract level.</span></span>

> [!NOTE]
>  <span data-ttu-id="09124-107">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="09124-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="09124-108"><xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> Vlastnost stylu určuje formátování WSDL metadat služby.</span><span class="sxs-lookup"><span data-stu-id="09124-108">The <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> style property determines how the WSDL metadata for the service is formatted.</span></span> <span data-ttu-id="09124-109">Možné hodnoty jsou <xref:System.ServiceModel.OperationFormatStyle.Document>, a <xref:System.ServiceModel.OperationFormatStyle.Rpc>.</span><span class="sxs-lookup"><span data-stu-id="09124-109">Possible values are <xref:System.ServiceModel.OperationFormatStyle.Document>, and <xref:System.ServiceModel.OperationFormatStyle.Rpc>.</span></span> <span data-ttu-id="09124-110">RPC znamená, že WSDL reprezentace pro operace, které si vyměňují zprávy obsahuje parametry, jako by šlo vzdálené volání procedury.</span><span class="sxs-lookup"><span data-stu-id="09124-110">RPC means that the WSDL representation of messages exchanged for an operation contains parameters as if it were a remote procedure call.</span></span> <span data-ttu-id="09124-111">Následuje příklad.</span><span class="sxs-lookup"><span data-stu-id="09124-111">The following is an example.</span></span>

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="n1" type="xsd:double"/>
  <wsdl:part name="n2" type="xsd:double"/>
</wsdl:message>
```

<span data-ttu-id="09124-112">Nastavení stylu <xref:System.ServiceModel.OperationFormatStyle.Document> znamená, že reprezentace WSDL obsahuje jeden element, který představuje dokument, který se vyměňují pro operace, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="09124-112">Setting the style to <xref:System.ServiceModel.OperationFormatStyle.Document> means that the WSDL representation contains a single element that represents the document that is exchanged for an operation as shown in the following example.</span></span>

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="parameters" element="tns:Add"/>
</wsdl:message>
```

<span data-ttu-id="09124-113"><xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> Vlastnost určuje formát zprávy.</span><span class="sxs-lookup"><span data-stu-id="09124-113">The <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> property determines the format of the message.</span></span> <span data-ttu-id="09124-114">Možné hodnoty jsou <xref:System.ServiceModel.OperationFormatUse.Literal> a <xref:System.ServiceModel.OperationFormatUse.Encoded>; výchozí hodnota je <xref:System.ServiceModel.OperationFormatUse.Literal>.</span><span class="sxs-lookup"><span data-stu-id="09124-114">Possible values are <xref:System.ServiceModel.OperationFormatUse.Literal> and <xref:System.ServiceModel.OperationFormatUse.Encoded>; the default value is <xref:System.ServiceModel.OperationFormatUse.Literal>.</span></span> <span data-ttu-id="09124-115">Literál znamená, že zprávy je literál instance schématu ve schématu WSDL, jak je znázorněno v následujícím dokumentu nebo literál příklad.</span><span class="sxs-lookup"><span data-stu-id="09124-115">Literal means that the message is a literal instance of the schema in the WSDL as shown in the following Document/ Literal example.</span></span>

```xml
<Add xmlns="http://Microsoft.ServiceModel.Samples">
  <n1>100</n1>
  <n2>15.99</n2>
</Add>
```

<span data-ttu-id="09124-116">Kódování znamená, že se schémata ve schématu WSDL jsou abstraktní specifikace, které jsou kódovány podle pravidel nalezena v protokolu SOAP 1.1 oddíl 5.</span><span class="sxs-lookup"><span data-stu-id="09124-116">Encoded means that the schemas in the WSDL are abstract specifications that are encoded according to the rules found in SOAP 1.1 section 5.</span></span> <span data-ttu-id="09124-117">Následuje příklad RPC a Encoded.</span><span class="sxs-lookup"><span data-stu-id="09124-117">The following is an RPC/Encoded example.</span></span>

```xml
<q1:Add xmlns:q1="http://Microsoft.ServiceModel.Samples">
  <n1 xsi:type="xsd:double" xmlns="">100</n1>
  <n2 xsi:type="xsd:double" xmlns="">15.99</n2>
</q1:Add>
```

<span data-ttu-id="09124-118">WS-I základní profil 1.0 zakazují použití <xref:System.ServiceModel.OperationFormatUse.Encoded> a musí ho používáte jenom v případě potřeby ve starších verzí služeb.</span><span class="sxs-lookup"><span data-stu-id="09124-118">The WS-I Basic Profile 1.0 prohibits the use of <xref:System.ServiceModel.OperationFormatUse.Encoded> and you should only use it when required by legacy services.</span></span> <span data-ttu-id="09124-119">`Encoded` Formát zprávy je k dispozici pouze při používání třídy XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="09124-119">The `Encoded` message format is only available when using the XmlSerializer.</span></span>

<span data-ttu-id="09124-120">Aby bylo možné zobrazit zprávy se odeslané a přijaté, tato ukázka je založena na [trasování a protokolování zpráv](tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="09124-120">To allow you to see the messages being sent and received, this sample is based on the [Tracing and Message Logging](tracing-and-message-logging.md).</span></span> <span data-ttu-id="09124-121">Konfigurace služby a zdrojový kód se upravila tak povolit a využívat trasování a protokolování zpráv.</span><span class="sxs-lookup"><span data-stu-id="09124-121">The service configuration and source code have been modified to enable and utilize tracing and message logging.</span></span> <span data-ttu-id="09124-122">Kromě toho <xref:System.ServiceModel.WSHttpBinding> není nakonfigurovaná bez zabezpečení, takže protokolované zprávy lze zobrazit v nezašifrované podobě.</span><span class="sxs-lookup"><span data-stu-id="09124-122">In addition, the <xref:System.ServiceModel.WSHttpBinding> has been configured without security, so the logged messages can be viewed in an unencrypted format.</span></span> <span data-ttu-id="09124-123">Výsledný protokoly trasování (System.ServiceModel.e2e a Message.log) by měl zobrazit pomocí [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="09124-123">The resulting trace logs (System.ServiceModel.e2e and Message.log) should be viewed by using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="09124-124">Bude vytvořena ve složce C:\LOGS se konfigurují trasování.</span><span class="sxs-lookup"><span data-stu-id="09124-124">The traces are configured to be created in the C:\LOGS folder.</span></span> <span data-ttu-id="09124-125">Vytvořte složku před spuštěním ukázky.</span><span class="sxs-lookup"><span data-stu-id="09124-125">Create the folder before running the sample.</span></span> <span data-ttu-id="09124-126">Chcete-li zobrazit obsah zprávy v nástroji prohlížeče trasování, vyberte **zprávy** vlevo a vpravo podokna nástroje.</span><span class="sxs-lookup"><span data-stu-id="09124-126">To view message contents in the Trace Viewer tool, select **Messages** in both the left and the right panes of the tool.</span></span>

<span data-ttu-id="09124-127">Následující kód ukazuje kontrakt služby s <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> vlastnost nastavena na hodnotu <xref:System.ServiceModel.OperationFormatUse> a změnit formát těla zprávy z výchozího <xref:System.ServiceModel.OperationFormatStyle> k <xref:System.ServiceModel.OperationFormatStyle.Document>.</span><span class="sxs-lookup"><span data-stu-id="09124-127">The following code shows the service contract with the <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> property set to <xref:System.ServiceModel.OperationFormatUse> and the format of the message body changed from the default <xref:System.ServiceModel.OperationFormatStyle> to <xref:System.ServiceModel.OperationFormatStyle.Document>.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"),
XmlSerializerFormat(Style = OperationFormatStyle.Rpc, 
                                 Use = OperationFormatUse.Encoded)]
public interface IUseAndStyleCalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
}
```

<span data-ttu-id="09124-128">Pokud chcete zobrazit rozdíl mezi různými <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> a <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> nastavení, upravovat ve službě, znovu vygenerovat klienta, spusťte ukázku a zkontrolujte soubor c:\logs\message.logs pomocí nástroje prohlížeče trasování služeb.</span><span class="sxs-lookup"><span data-stu-id="09124-128">To see the difference between the different <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> and <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> settings, modify them in the service, regenerate the client, run the sample, and examine the c:\logs\message.logs file with the Service Trace Viewer tool.</span></span> <span data-ttu-id="09124-129">Také sledovat dopad na metadata zobrazením `http://localhost/ServiceModelSamples/service.svc?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="09124-129">Also observe the impact on the metadata by viewing `http://localhost/ServiceModelSamples/service.svc?wsdl`.</span></span> <span data-ttu-id="09124-130">Metadata služby je obvykle rozdělit do více stránek.</span><span class="sxs-lookup"><span data-stu-id="09124-130">The metadata for services is typically broken up into multiple pages.</span></span> <span data-ttu-id="09124-131">Na stránce hlavní wsdl obsahuje vazby WSDL, ale zobrazit `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0` sledovat definice zpráv.</span><span class="sxs-lookup"><span data-stu-id="09124-131">The main wsdl page contains the WSDL bindings, but view `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0` to observe the message definitions.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="09124-132">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="09124-132">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="09124-133">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="09124-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="09124-134">Vytvoření C:\LOGS adresáře pro protokolování zpráv.</span><span class="sxs-lookup"><span data-stu-id="09124-134">Create a C:\LOGS directory for logging messages.</span></span> <span data-ttu-id="09124-135">Dejte uživateli oprávnění pro tento adresář k zápisu síťové služby.</span><span class="sxs-lookup"><span data-stu-id="09124-135">Give the user Network Service write permissions for this directory.</span></span>

3. <span data-ttu-id="09124-136">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="09124-136">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="09124-137">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="09124-137">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="09124-138">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="09124-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="09124-139">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="09124-139">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="09124-140">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="09124-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="09124-141">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="09124-141">This sample is located in the following directory.</span></span>
> 
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\UseAndStyle`
