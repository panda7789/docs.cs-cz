---
title: Nastavování ukázek vlastností použití a stylu
ms.date: 03/30/2017
ms.assetid: c09a0600-116f-41cf-900a-1b7e4ea4e300
ms.openlocfilehash: 36111aa05680fb8b369cde6b42d22c9c3b8474ad
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345134"
---
# <a name="setting-the-use-and-style-properties"></a><span data-ttu-id="2bd5c-102">Nastavení vlastností Use a Style</span><span class="sxs-lookup"><span data-stu-id="2bd5c-102">Setting the Use and Style Properties</span></span>

<span data-ttu-id="2bd5c-103">Tato ukázka předvádí, jak používat vlastnosti use a Style na <xref:System.ServiceModel.XmlSerializerFormatAttribute> a <xref:System.ServiceModel.DataContractFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="2bd5c-103">This sample demonstrates how to use the Use and Style properties on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> and the <xref:System.ServiceModel.DataContractFormatAttribute>.</span></span> <span data-ttu-id="2bd5c-104">Tyto vlastnosti mají vliv na formátování zpráv.</span><span class="sxs-lookup"><span data-stu-id="2bd5c-104">These properties affect how messages are formatted.</span></span> <span data-ttu-id="2bd5c-105">Ve výchozím nastavení je tělo zprávy formátováno pomocí stylu nastaveného na <xref:System.ServiceModel.OperationFormatStyle.Document>.</span><span class="sxs-lookup"><span data-stu-id="2bd5c-105">By default, the message body is formatted with the style set to <xref:System.ServiceModel.OperationFormatStyle.Document>.</span></span> <span data-ttu-id="2bd5c-106">Tato nastavení je možné zadat buď na úrovni smlouvy služby, nebo na úrovni smlouvy o operaci.</span><span class="sxs-lookup"><span data-stu-id="2bd5c-106">These settings can be specified at either the service contract level or the operation contract level.</span></span>

> [!NOTE]
> <span data-ttu-id="2bd5c-107">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="2bd5c-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="2bd5c-108">Vlastnost Style <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> určuje, jak je formátována metadata WSDL pro službu.</span><span class="sxs-lookup"><span data-stu-id="2bd5c-108">The <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> style property determines how the WSDL metadata for the service is formatted.</span></span> <span data-ttu-id="2bd5c-109">Možné hodnoty jsou <xref:System.ServiceModel.OperationFormatStyle.Document>a <xref:System.ServiceModel.OperationFormatStyle.Rpc>.</span><span class="sxs-lookup"><span data-stu-id="2bd5c-109">Possible values are <xref:System.ServiceModel.OperationFormatStyle.Document>, and <xref:System.ServiceModel.OperationFormatStyle.Rpc>.</span></span> <span data-ttu-id="2bd5c-110">RPC znamená, že reprezentace zprávy WSDL vyměňované pro operaci obsahuje parametry, jako by šlo o vzdálené volání procedur.</span><span class="sxs-lookup"><span data-stu-id="2bd5c-110">RPC means that the WSDL representation of messages exchanged for an operation contains parameters as if it were a remote procedure call.</span></span> <span data-ttu-id="2bd5c-111">Například:</span><span class="sxs-lookup"><span data-stu-id="2bd5c-111">The following is an example.</span></span>

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="n1" type="xsd:double"/>
  <wsdl:part name="n2" type="xsd:double"/>
</wsdl:message>
```

<span data-ttu-id="2bd5c-112">Nastavení stylu na <xref:System.ServiceModel.OperationFormatStyle.Document> znamená, že reprezentace WSDL obsahuje jediný element, který představuje dokument, který je vyměněn pro operaci, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2bd5c-112">Setting the style to <xref:System.ServiceModel.OperationFormatStyle.Document> means that the WSDL representation contains a single element that represents the document that is exchanged for an operation as shown in the following example.</span></span>

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="parameters" element="tns:Add"/>
</wsdl:message>
```

<span data-ttu-id="2bd5c-113">Vlastnost <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> určuje formát zprávy.</span><span class="sxs-lookup"><span data-stu-id="2bd5c-113">The <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> property determines the format of the message.</span></span> <span data-ttu-id="2bd5c-114">Možné hodnoty jsou <xref:System.ServiceModel.OperationFormatUse.Literal> a <xref:System.ServiceModel.OperationFormatUse.Encoded>; Výchozí hodnota je <xref:System.ServiceModel.OperationFormatUse.Literal>.</span><span class="sxs-lookup"><span data-stu-id="2bd5c-114">Possible values are <xref:System.ServiceModel.OperationFormatUse.Literal> and <xref:System.ServiceModel.OperationFormatUse.Encoded>; the default value is <xref:System.ServiceModel.OperationFormatUse.Literal>.</span></span> <span data-ttu-id="2bd5c-115">Literál znamená, že zpráva je literální instance schématu v jazyce WSDL, jak je znázorněno v následujícím příkladu dokumentu/literálu.</span><span class="sxs-lookup"><span data-stu-id="2bd5c-115">Literal means that the message is a literal instance of the schema in the WSDL as shown in the following Document/ Literal example.</span></span>

```xml
<Add xmlns="http://Microsoft.ServiceModel.Samples">
  <n1>100</n1>
  <n2>15.99</n2>
</Add>
```

<span data-ttu-id="2bd5c-116">Kódovaný znamená, že schémata v jazyce WSDL jsou abstraktní specifikace, které jsou zakódovány podle pravidel nalezených v protokolu SOAP 1,1 oddíl 5.</span><span class="sxs-lookup"><span data-stu-id="2bd5c-116">Encoded means that the schemas in the WSDL are abstract specifications that are encoded according to the rules found in SOAP 1.1 section 5.</span></span> <span data-ttu-id="2bd5c-117">Následuje příklad RPC/Encoded.</span><span class="sxs-lookup"><span data-stu-id="2bd5c-117">The following is an RPC/Encoded example.</span></span>

```xml
<q1:Add xmlns:q1="http://Microsoft.ServiceModel.Samples">
  <n1 xsi:type="xsd:double" xmlns="">100</n1>
  <n2 xsi:type="xsd:double" xmlns="">15.99</n2>
</q1:Add>
```

<span data-ttu-id="2bd5c-118">Základní profil WS-I 1,0 zakáže použití <xref:System.ServiceModel.OperationFormatUse.Encoded> a v případě potřeby jej byste měli používat jenom v případě, že to vyžadují starší služby.</span><span class="sxs-lookup"><span data-stu-id="2bd5c-118">The WS-I Basic Profile 1.0 prohibits the use of <xref:System.ServiceModel.OperationFormatUse.Encoded> and you should only use it when required by legacy services.</span></span> <span data-ttu-id="2bd5c-119">Formát zprávy `Encoded` je k dispozici pouze při použití objektu XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="2bd5c-119">The `Encoded` message format is only available when using the XmlSerializer.</span></span>

<span data-ttu-id="2bd5c-120">Tato ukázka je založena na [trasování a protokolování zpráv](tracing-and-message-logging.md), aby bylo možné zobrazit zprávy odesílané a přijímané.</span><span class="sxs-lookup"><span data-stu-id="2bd5c-120">To allow you to see the messages being sent and received, this sample is based on the [Tracing and Message Logging](tracing-and-message-logging.md).</span></span> <span data-ttu-id="2bd5c-121">Konfigurace a zdrojový kód služby byly upraveny tak, aby umožňovaly a využily trasování a protokolování zpráv.</span><span class="sxs-lookup"><span data-stu-id="2bd5c-121">The service configuration and source code have been modified to enable and utilize tracing and message logging.</span></span> <span data-ttu-id="2bd5c-122">Kromě toho je <xref:System.ServiceModel.WSHttpBinding> nakonfigurovaný bez zabezpečení, takže protokolované zprávy můžete zobrazit v nešifrovaném formátu.</span><span class="sxs-lookup"><span data-stu-id="2bd5c-122">In addition, the <xref:System.ServiceModel.WSHttpBinding> has been configured without security, so the logged messages can be viewed in an unencrypted format.</span></span> <span data-ttu-id="2bd5c-123">Výsledné protokoly trasování (System. ServiceModel. e2e a Message. log) by se měly zobrazit pomocí [nástroje Service Trace Viewer (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="2bd5c-123">The resulting trace logs (System.ServiceModel.e2e and Message.log) should be viewed by using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="2bd5c-124">Trasování jsou nakonfigurovaná tak, aby se vytvořila ve složce C:\Logs.</span><span class="sxs-lookup"><span data-stu-id="2bd5c-124">The traces are configured to be created in the C:\LOGS folder.</span></span> <span data-ttu-id="2bd5c-125">Před spuštěním ukázky vytvořte složku.</span><span class="sxs-lookup"><span data-stu-id="2bd5c-125">Create the folder before running the sample.</span></span> <span data-ttu-id="2bd5c-126">Chcete-li zobrazit obsah zprávy v nástroji Prohlížeč trasování, vyberte **zprávy** v levém a pravém podokně nástroje.</span><span class="sxs-lookup"><span data-stu-id="2bd5c-126">To view message contents in the Trace Viewer tool, select **Messages** in both the left and the right panes of the tool.</span></span>

<span data-ttu-id="2bd5c-127">Následující kód ukazuje kontrakt služby s vlastností <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> nastavenou na <xref:System.ServiceModel.OperationFormatUse> a formát textu zprávy se změnil z výchozí <xref:System.ServiceModel.OperationFormatStyle> na <xref:System.ServiceModel.OperationFormatStyle.Document>.</span><span class="sxs-lookup"><span data-stu-id="2bd5c-127">The following code shows the service contract with the <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> property set to <xref:System.ServiceModel.OperationFormatUse> and the format of the message body changed from the default <xref:System.ServiceModel.OperationFormatStyle> to <xref:System.ServiceModel.OperationFormatStyle.Document>.</span></span>

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

<span data-ttu-id="2bd5c-128">Chcete-li zobrazit rozdíl mezi různými nastaveními <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> a <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A>, upravte je ve službě, znovu vygenerujte klienta, spusťte ukázku a Prohlédněte si soubor c:\logs\message.logs pomocí nástroje Service Trace Viewer.</span><span class="sxs-lookup"><span data-stu-id="2bd5c-128">To see the difference between the different <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> and <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> settings, modify them in the service, regenerate the client, run the sample, and examine the c:\logs\message.logs file with the Service Trace Viewer tool.</span></span> <span data-ttu-id="2bd5c-129">Také Sledujte dopad na metadata zobrazením `http://localhost/ServiceModelSamples/service.svc?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="2bd5c-129">Also observe the impact on the metadata by viewing `http://localhost/ServiceModelSamples/service.svc?wsdl`.</span></span> <span data-ttu-id="2bd5c-130">Metadata pro služby jsou obvykle rozdělena na více stránek.</span><span class="sxs-lookup"><span data-stu-id="2bd5c-130">The metadata for services is typically broken up into multiple pages.</span></span> <span data-ttu-id="2bd5c-131">Hlavní stránka WSDL obsahuje vazby WSDL, ale zobrazení `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0`, aby bylo možné sledovat definice zpráv.</span><span class="sxs-lookup"><span data-stu-id="2bd5c-131">The main wsdl page contains the WSDL bindings, but view `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0` to observe the message definitions.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2bd5c-132">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="2bd5c-132">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="2bd5c-133">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2bd5c-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="2bd5c-134">Vytvořte adresář C:\Logs. pro protokolování zpráv.</span><span class="sxs-lookup"><span data-stu-id="2bd5c-134">Create a C:\LOGS directory for logging messages.</span></span> <span data-ttu-id="2bd5c-135">Udělte síťové službě uživateli oprávnění zapisovat pro tento adresář.</span><span class="sxs-lookup"><span data-stu-id="2bd5c-135">Give the user Network Service write permissions for this directory.</span></span>

3. <span data-ttu-id="2bd5c-136">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2bd5c-136">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="2bd5c-137">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2bd5c-137">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2bd5c-138">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="2bd5c-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2bd5c-139">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="2bd5c-139">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="2bd5c-140">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="2bd5c-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2bd5c-141">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="2bd5c-141">This sample is located in the following directory.</span></span>
> 
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\UseAndStyle`
