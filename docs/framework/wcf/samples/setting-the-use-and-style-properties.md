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
# <a name="setting-the-use-and-style-properties"></a>Nastavení vlastností Use a Style

Tato ukázka ukazuje, jak používat Use <xref:System.ServiceModel.XmlSerializerFormatAttribute> a <xref:System.ServiceModel.DataContractFormatAttribute>Style vlastnosti na a . Tyto vlastnosti ovlivňují způsob formátování zpráv. Ve výchozím nastavení je text zprávy formátován se stylem nastaveným na <xref:System.ServiceModel.OperationFormatStyle.Document>. Tato nastavení lze zadat na úrovni servisní smlouvy nebo na úrovni smlouvy o provozu.

> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.

Vlastnost <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> style určuje, jak jsou formátována metadata WSDL pro službu. Možné hodnoty <xref:System.ServiceModel.OperationFormatStyle.Document>jsou <xref:System.ServiceModel.OperationFormatStyle.Rpc>a . Vzdálené volání znamená, že wsdl reprezentace zpráv vyměňovaných pro operaci obsahuje parametry, jako by se jednalo o vzdálené volání procedury. Následuje příklad.

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="n1" type="xsd:double"/>
  <wsdl:part name="n2" type="xsd:double"/>
</wsdl:message>
```

Nastavení stylu <xref:System.ServiceModel.OperationFormatStyle.Document> znamená, že reprezentace WSDL obsahuje jeden prvek, který představuje dokument, který je vyměněn za operaci, jak je znázorněno v následujícím příkladu.

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="parameters" element="tns:Add"/>
</wsdl:message>
```

Vlastnost <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> určuje formát zprávy. Možné hodnoty <xref:System.ServiceModel.OperationFormatUse.Literal> <xref:System.ServiceModel.OperationFormatUse.Encoded>jsou a ; výchozí hodnota <xref:System.ServiceModel.OperationFormatUse.Literal>je . Literál znamená, že zpráva je literál instance schématu v WSDL, jak je znázorněno v následujícím příkladu Document/ Literal.

```xml
<Add xmlns="http://Microsoft.ServiceModel.Samples">
  <n1>100</n1>
  <n2>15.99</n2>
</Add>
```

Kódované znamená, že schémata v WSDL jsou abstraktní specifikace, které jsou kódovány podle pravidel nalezených v soap 1.1 oddíl 5. Následuje příklad RPC/Encoded.

```xml
<q1:Add xmlns:q1="http://Microsoft.ServiceModel.Samples">
  <n1 xsi:type="xsd:double" xmlns="">100</n1>
  <n2 xsi:type="xsd:double" xmlns="">15.99</n2>
</q1:Add>
```

WS-I Základní profil 1.0 zakazuje <xref:System.ServiceModel.OperationFormatUse.Encoded> používání a měli byste jej používat pouze v případě, že to vyžaduje starší služby. Formát `Encoded` zprávy je k dispozici pouze při použití xmlserializeru.

Chcete-li zobrazit zprávy odesílané a přijaté, tato ukázka je založena na [trasování a protokolování zpráv](tracing-and-message-logging.md). Konfigurace služby a zdrojový kód byly upraveny tak, aby umožňovala a využívala trasování a protokolování zpráv. Kromě toho <xref:System.ServiceModel.WSHttpBinding> byla nakonfigurována bez zabezpečení, takže protokolované zprávy lze zobrazit v nešifrovaném formátu. Výsledné protokoly trasování (System.ServiceModel.e2e a Message.log) by měly být zobrazeny pomocí [nástroje Service Trace Viewer Tool (SvcTraceViewer.exe).](../service-trace-viewer-tool-svctraceviewer-exe.md) Trasování jsou konfigurována tak, aby byla vytvořena ve složce C:\LOGS. Před spuštěním ukázky vytvořte složku. Chcete-li zobrazit obsah zprávy v nástroji Prohlížeč trasování, vyberte **Zprávy** v levém i pravém podokně nástroje.

Následující kód zobrazuje servisní smlouvu <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> s <xref:System.ServiceModel.OperationFormatUse> vlastností nastavenou na a <xref:System.ServiceModel.OperationFormatStyle> formát <xref:System.ServiceModel.OperationFormatStyle.Document>textu zprávy změněn z výchozí na .

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

Chcete-li zobrazit rozdíl <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> mezi různými a nastaveními, upravte je ve službě, obnovte klienta, spusťte ukázku a zkontrolujte soubor c:\logs\message.logs pomocí nástroje Prohlížeč trasování služby. Také sledovat dopad na metadata `http://localhost/ServiceModelSamples/service.svc?wsdl`zobrazením . Metadata pro služby je obvykle rozdělena na více stránek. Hlavní stránka wsdl obsahuje vazby WSDL, ale zobrazení `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0` sledovat definice zpráv.

## <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Vytvořte adresář C:\LOGS pro protokolování zpráv. Udělte uživateli síťovou službu oprávnění k zápisu pro tento adresář.

3. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](building-the-samples.md).

4. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](running-the-samples.md).

> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\UseAndStyle`
