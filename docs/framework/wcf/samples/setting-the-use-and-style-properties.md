---
title: Nastavení ukázek vlastností Use a Style
ms.date: 03/30/2017
ms.assetid: c09a0600-116f-41cf-900a-1b7e4ea4e300
ms.openlocfilehash: f400c0bc08588afa951ae33f221663b47b37602c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144029"
---
# <a name="setting-the-use-and-style-properties"></a><span data-ttu-id="871e0-102">Nastavení vlastností Use a Style</span><span class="sxs-lookup"><span data-stu-id="871e0-102">Setting the Use and Style Properties</span></span>

<span data-ttu-id="871e0-103">Tato ukázka ukazuje, jak používat Use <xref:System.ServiceModel.XmlSerializerFormatAttribute> a <xref:System.ServiceModel.DataContractFormatAttribute>Style vlastnosti na a .</span><span class="sxs-lookup"><span data-stu-id="871e0-103">This sample demonstrates how to use the Use and Style properties on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> and the <xref:System.ServiceModel.DataContractFormatAttribute>.</span></span> <span data-ttu-id="871e0-104">Tyto vlastnosti ovlivňují způsob formátování zpráv.</span><span class="sxs-lookup"><span data-stu-id="871e0-104">These properties affect how messages are formatted.</span></span> <span data-ttu-id="871e0-105">Ve výchozím nastavení je text zprávy formátován se stylem nastaveným na <xref:System.ServiceModel.OperationFormatStyle.Document>.</span><span class="sxs-lookup"><span data-stu-id="871e0-105">By default, the message body is formatted with the style set to <xref:System.ServiceModel.OperationFormatStyle.Document>.</span></span> <span data-ttu-id="871e0-106">Tato nastavení lze zadat na úrovni servisní smlouvy nebo na úrovni smlouvy o provozu.</span><span class="sxs-lookup"><span data-stu-id="871e0-106">These settings can be specified at either the service contract level or the operation contract level.</span></span>

> [!NOTE]
> <span data-ttu-id="871e0-107">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="871e0-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="871e0-108">Vlastnost <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> style určuje, jak jsou formátována metadata WSDL pro službu.</span><span class="sxs-lookup"><span data-stu-id="871e0-108">The <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> style property determines how the WSDL metadata for the service is formatted.</span></span> <span data-ttu-id="871e0-109">Možné hodnoty <xref:System.ServiceModel.OperationFormatStyle.Document>jsou <xref:System.ServiceModel.OperationFormatStyle.Rpc>a .</span><span class="sxs-lookup"><span data-stu-id="871e0-109">Possible values are <xref:System.ServiceModel.OperationFormatStyle.Document>, and <xref:System.ServiceModel.OperationFormatStyle.Rpc>.</span></span> <span data-ttu-id="871e0-110">Vzdálené volání znamená, že wsdl reprezentace zpráv vyměňovaných pro operaci obsahuje parametry, jako by se jednalo o vzdálené volání procedury.</span><span class="sxs-lookup"><span data-stu-id="871e0-110">RPC means that the WSDL representation of messages exchanged for an operation contains parameters as if it were a remote procedure call.</span></span> <span data-ttu-id="871e0-111">Následuje příklad.</span><span class="sxs-lookup"><span data-stu-id="871e0-111">The following is an example.</span></span>

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="n1" type="xsd:double"/>
  <wsdl:part name="n2" type="xsd:double"/>
</wsdl:message>
```

<span data-ttu-id="871e0-112">Nastavení stylu <xref:System.ServiceModel.OperationFormatStyle.Document> znamená, že reprezentace WSDL obsahuje jeden prvek, který představuje dokument, který je vyměněn za operaci, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="871e0-112">Setting the style to <xref:System.ServiceModel.OperationFormatStyle.Document> means that the WSDL representation contains a single element that represents the document that is exchanged for an operation as shown in the following example.</span></span>

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="parameters" element="tns:Add"/>
</wsdl:message>
```

<span data-ttu-id="871e0-113">Vlastnost <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> určuje formát zprávy.</span><span class="sxs-lookup"><span data-stu-id="871e0-113">The <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> property determines the format of the message.</span></span> <span data-ttu-id="871e0-114">Možné hodnoty <xref:System.ServiceModel.OperationFormatUse.Literal> <xref:System.ServiceModel.OperationFormatUse.Encoded>jsou a ; výchozí hodnota <xref:System.ServiceModel.OperationFormatUse.Literal>je .</span><span class="sxs-lookup"><span data-stu-id="871e0-114">Possible values are <xref:System.ServiceModel.OperationFormatUse.Literal> and <xref:System.ServiceModel.OperationFormatUse.Encoded>; the default value is <xref:System.ServiceModel.OperationFormatUse.Literal>.</span></span> <span data-ttu-id="871e0-115">Literál znamená, že zpráva je literál instance schématu v WSDL, jak je znázorněno v následujícím příkladu Document/ Literal.</span><span class="sxs-lookup"><span data-stu-id="871e0-115">Literal means that the message is a literal instance of the schema in the WSDL as shown in the following Document/ Literal example.</span></span>

```xml
<Add xmlns="http://Microsoft.ServiceModel.Samples">
  <n1>100</n1>
  <n2>15.99</n2>
</Add>
```

<span data-ttu-id="871e0-116">Kódované znamená, že schémata v WSDL jsou abstraktní specifikace, které jsou kódovány podle pravidel nalezených v soap 1.1 oddíl 5.</span><span class="sxs-lookup"><span data-stu-id="871e0-116">Encoded means that the schemas in the WSDL are abstract specifications that are encoded according to the rules found in SOAP 1.1 section 5.</span></span> <span data-ttu-id="871e0-117">Následuje příklad RPC/Encoded.</span><span class="sxs-lookup"><span data-stu-id="871e0-117">The following is an RPC/Encoded example.</span></span>

```xml
<q1:Add xmlns:q1="http://Microsoft.ServiceModel.Samples">
  <n1 xsi:type="xsd:double" xmlns="">100</n1>
  <n2 xsi:type="xsd:double" xmlns="">15.99</n2>
</q1:Add>
```

<span data-ttu-id="871e0-118">WS-I Základní profil 1.0 zakazuje <xref:System.ServiceModel.OperationFormatUse.Encoded> používání a měli byste jej používat pouze v případě, že to vyžaduje starší služby.</span><span class="sxs-lookup"><span data-stu-id="871e0-118">The WS-I Basic Profile 1.0 prohibits the use of <xref:System.ServiceModel.OperationFormatUse.Encoded> and you should only use it when required by legacy services.</span></span> <span data-ttu-id="871e0-119">Formát `Encoded` zprávy je k dispozici pouze při použití xmlserializeru.</span><span class="sxs-lookup"><span data-stu-id="871e0-119">The `Encoded` message format is only available when using the XmlSerializer.</span></span>

<span data-ttu-id="871e0-120">Chcete-li zobrazit zprávy odesílané a přijaté, tato ukázka je založena na [trasování a protokolování zpráv](tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="871e0-120">To allow you to see the messages being sent and received, this sample is based on the [Tracing and Message Logging](tracing-and-message-logging.md).</span></span> <span data-ttu-id="871e0-121">Konfigurace služby a zdrojový kód byly upraveny tak, aby umožňovala a využívala trasování a protokolování zpráv.</span><span class="sxs-lookup"><span data-stu-id="871e0-121">The service configuration and source code have been modified to enable and utilize tracing and message logging.</span></span> <span data-ttu-id="871e0-122">Kromě toho <xref:System.ServiceModel.WSHttpBinding> byla nakonfigurována bez zabezpečení, takže protokolované zprávy lze zobrazit v nešifrovaném formátu.</span><span class="sxs-lookup"><span data-stu-id="871e0-122">In addition, the <xref:System.ServiceModel.WSHttpBinding> has been configured without security, so the logged messages can be viewed in an unencrypted format.</span></span> <span data-ttu-id="871e0-123">Výsledné protokoly trasování (System.ServiceModel.e2e a Message.log) by měly být zobrazeny pomocí [nástroje Service Trace Viewer Tool (SvcTraceViewer.exe).](../service-trace-viewer-tool-svctraceviewer-exe.md)</span><span class="sxs-lookup"><span data-stu-id="871e0-123">The resulting trace logs (System.ServiceModel.e2e and Message.log) should be viewed by using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="871e0-124">Trasování jsou konfigurována tak, aby byla vytvořena ve složce C:\LOGS.</span><span class="sxs-lookup"><span data-stu-id="871e0-124">The traces are configured to be created in the C:\LOGS folder.</span></span> <span data-ttu-id="871e0-125">Před spuštěním ukázky vytvořte složku.</span><span class="sxs-lookup"><span data-stu-id="871e0-125">Create the folder before running the sample.</span></span> <span data-ttu-id="871e0-126">Chcete-li zobrazit obsah zprávy v nástroji Prohlížeč trasování, vyberte **Zprávy** v levém i pravém podokně nástroje.</span><span class="sxs-lookup"><span data-stu-id="871e0-126">To view message contents in the Trace Viewer tool, select **Messages** in both the left and the right panes of the tool.</span></span>

<span data-ttu-id="871e0-127">Následující kód zobrazuje servisní smlouvu <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> s <xref:System.ServiceModel.OperationFormatUse> vlastností nastavenou na a <xref:System.ServiceModel.OperationFormatStyle> formát <xref:System.ServiceModel.OperationFormatStyle.Document>textu zprávy změněn z výchozí na .</span><span class="sxs-lookup"><span data-stu-id="871e0-127">The following code shows the service contract with the <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> property set to <xref:System.ServiceModel.OperationFormatUse> and the format of the message body changed from the default <xref:System.ServiceModel.OperationFormatStyle> to <xref:System.ServiceModel.OperationFormatStyle.Document>.</span></span>

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

<span data-ttu-id="871e0-128">Chcete-li zobrazit rozdíl <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> mezi různými a nastaveními, upravte je ve službě, obnovte klienta, spusťte ukázku a zkontrolujte soubor c:\logs\message.logs pomocí nástroje Prohlížeč trasování služby.</span><span class="sxs-lookup"><span data-stu-id="871e0-128">To see the difference between the different <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> and <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> settings, modify them in the service, regenerate the client, run the sample, and examine the c:\logs\message.logs file with the Service Trace Viewer tool.</span></span> <span data-ttu-id="871e0-129">Také sledovat dopad na metadata `http://localhost/ServiceModelSamples/service.svc?wsdl`zobrazením .</span><span class="sxs-lookup"><span data-stu-id="871e0-129">Also observe the impact on the metadata by viewing `http://localhost/ServiceModelSamples/service.svc?wsdl`.</span></span> <span data-ttu-id="871e0-130">Metadata pro služby je obvykle rozdělena na více stránek.</span><span class="sxs-lookup"><span data-stu-id="871e0-130">The metadata for services is typically broken up into multiple pages.</span></span> <span data-ttu-id="871e0-131">Hlavní stránka wsdl obsahuje vazby WSDL, ale zobrazení `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0` sledovat definice zpráv.</span><span class="sxs-lookup"><span data-stu-id="871e0-131">The main wsdl page contains the WSDL bindings, but view `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0` to observe the message definitions.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="871e0-132">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="871e0-132">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="871e0-133">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="871e0-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="871e0-134">Vytvořte adresář C:\LOGS pro protokolování zpráv.</span><span class="sxs-lookup"><span data-stu-id="871e0-134">Create a C:\LOGS directory for logging messages.</span></span> <span data-ttu-id="871e0-135">Udělte uživateli síťovou službu oprávnění k zápisu pro tento adresář.</span><span class="sxs-lookup"><span data-stu-id="871e0-135">Give the user Network Service write permissions for this directory.</span></span>

3. <span data-ttu-id="871e0-136">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="871e0-136">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="871e0-137">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="871e0-137">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="871e0-138">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="871e0-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="871e0-139">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="871e0-139">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="871e0-140">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="871e0-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="871e0-141">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="871e0-141">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\UseAndStyle`
