---
title: Nastavení vlastností použití a stylu – ukázky WCF
ms.date: 03/30/2017
ms.assetid: c09a0600-116f-41cf-900a-1b7e4ea4e300
ms.openlocfilehash: f92b25144759692c54aa7a1730a9bb85cab4f15f
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714427"
---
# <a name="setting-the-use-and-style-properties"></a>Nastavení vlastností Use a Style

Tato ukázka předvádí, jak používat vlastnosti use a Style na <xref:System.ServiceModel.XmlSerializerFormatAttribute> a <xref:System.ServiceModel.DataContractFormatAttribute>. Tyto vlastnosti mají vliv na formátování zpráv. Ve výchozím nastavení je tělo zprávy formátováno pomocí stylu nastaveného na <xref:System.ServiceModel.OperationFormatStyle.Document>. Tato nastavení je možné zadat buď na úrovni smlouvy služby, nebo na úrovni smlouvy o operaci.

> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.

Vlastnost Style <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> určuje, jak je formátována metadata WSDL pro službu. Možné hodnoty jsou <xref:System.ServiceModel.OperationFormatStyle.Document>a <xref:System.ServiceModel.OperationFormatStyle.Rpc>. RPC znamená, že reprezentace zprávy WSDL vyměňované pro operaci obsahuje parametry, jako by šlo o vzdálené volání procedur. Například:

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="n1" type="xsd:double"/>
  <wsdl:part name="n2" type="xsd:double"/>
</wsdl:message>
```

Nastavení stylu na <xref:System.ServiceModel.OperationFormatStyle.Document> znamená, že reprezentace WSDL obsahuje jediný element, který představuje dokument, který je vyměněn pro operaci, jak je znázorněno v následujícím příkladu.

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="parameters" element="tns:Add"/>
</wsdl:message>
```

Vlastnost <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> určuje formát zprávy. Možné hodnoty jsou <xref:System.ServiceModel.OperationFormatUse.Literal> a <xref:System.ServiceModel.OperationFormatUse.Encoded>; Výchozí hodnota je <xref:System.ServiceModel.OperationFormatUse.Literal>. Literál znamená, že zpráva je literální instance schématu v jazyce WSDL, jak je znázorněno v následujícím příkladu dokumentu/literálu.

```xml
<Add xmlns="http://Microsoft.ServiceModel.Samples">
  <n1>100</n1>
  <n2>15.99</n2>
</Add>
```

Kódovaný znamená, že schémata v jazyce WSDL jsou abstraktní specifikace, které jsou zakódovány podle pravidel nalezených v protokolu SOAP 1,1 oddíl 5. Následuje příklad RPC/Encoded.

```xml
<q1:Add xmlns:q1="http://Microsoft.ServiceModel.Samples">
  <n1 xsi:type="xsd:double" xmlns="">100</n1>
  <n2 xsi:type="xsd:double" xmlns="">15.99</n2>
</q1:Add>
```

Základní profil WS-I 1,0 zakáže použití <xref:System.ServiceModel.OperationFormatUse.Encoded> a v případě potřeby jej byste měli používat jenom v případě, že to vyžadují starší služby. Formát zprávy `Encoded` je k dispozici pouze při použití objektu XmlSerializer.

Tato ukázka je založena na [trasování a protokolování zpráv](tracing-and-message-logging.md), aby bylo možné zobrazit zprávy odesílané a přijímané. Konfigurace a zdrojový kód služby byly upraveny tak, aby umožňovaly a využily trasování a protokolování zpráv. Kromě toho je <xref:System.ServiceModel.WSHttpBinding> nakonfigurovaný bez zabezpečení, takže protokolované zprávy můžete zobrazit v nešifrovaném formátu. Výsledné protokoly trasování (System. ServiceModel. e2e a Message. log) by se měly zobrazit pomocí [nástroje Service Trace Viewer (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md). Trasování jsou nakonfigurovaná tak, aby se vytvořila ve složce C:\Logs. Před spuštěním ukázky vytvořte složku. Chcete-li zobrazit obsah zprávy v nástroji Prohlížeč trasování, vyberte **zprávy** v levém a pravém podokně nástroje.

Následující kód ukazuje kontrakt služby s vlastností <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> nastavenou na <xref:System.ServiceModel.OperationFormatUse> a formát textu zprávy se změnil z výchozí <xref:System.ServiceModel.OperationFormatStyle> na <xref:System.ServiceModel.OperationFormatStyle.Document>.

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

Chcete-li zobrazit rozdíl mezi různými nastaveními <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> a <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A>, upravte je ve službě, znovu vygenerujte klienta, spusťte ukázku a Prohlédněte si soubor c:\logs\message.logs pomocí nástroje Service Trace Viewer. Také Sledujte dopad na metadata zobrazením `http://localhost/ServiceModelSamples/service.svc?wsdl`. Metadata pro služby jsou obvykle rozdělena na více stránek. Hlavní stránka WSDL obsahuje vazby WSDL, ale zobrazení `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0`, aby bylo možné sledovat definice zpráv.

## <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).

2. Vytvořte adresář C:\Logs. pro protokolování zpráv. Udělte síťové službě uživateli oprávnění zapisovat pro tento adresář.

3. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).

4. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.
> 
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\UseAndStyle`
