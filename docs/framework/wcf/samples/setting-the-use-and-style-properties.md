---
title: Nastavení vlastností Use a Style
ms.date: 03/30/2017
ms.assetid: c09a0600-116f-41cf-900a-1b7e4ea4e300
ms.openlocfilehash: cd6f9af034f2f36c4daf808492713fcd616e3a9c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662150"
---
# <a name="setting-the-use-and-style-properties"></a>Nastavení vlastností Use a Style
Tento příklad znázorňuje způsob použití vlastností použití a stylu na <xref:System.ServiceModel.XmlSerializerFormatAttribute> a <xref:System.ServiceModel.DataContractFormatAttribute>. Tyto vlastnosti vliv na způsob formátování zprávy. Ve výchozím nastavení, text zprávy je formátováno s stylu nastavena na <xref:System.ServiceModel.OperationFormatStyle.Document>. Tato nastavení se dá nastavit na úrovni kontraktu služby nebo úroveň operace kontraktu.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> Vlastnost stylu určuje formátování WSDL metadat služby. Možné hodnoty jsou <xref:System.ServiceModel.OperationFormatStyle.Document>, a <xref:System.ServiceModel.OperationFormatStyle.Rpc>. RPC znamená, že WSDL reprezentace pro operace, které si vyměňují zprávy obsahuje parametry, jako by šlo vzdálené volání procedury. Následuje příklad.  
  
```xml  
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">  
  <wsdl:part name="n1" type="xsd:double"/>  
  <wsdl:part name="n2" type="xsd:double"/>  
</wsdl:message>  
```  
  
 Nastavení stylu <xref:System.ServiceModel.OperationFormatStyle.Document> znamená, že reprezentace WSDL obsahuje jeden element, který představuje dokument, který se vyměňují pro operace, jak je znázorněno v následujícím příkladu.  
  
```xml  
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">  
  <wsdl:part name="parameters" element="tns:Add"/>  
</wsdl:message>  
```  
  
 <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> Vlastnost určuje formát zprávy. Možné hodnoty jsou <xref:System.ServiceModel.OperationFormatUse.Literal> a <xref:System.ServiceModel.OperationFormatUse.Encoded>; výchozí hodnota je <xref:System.ServiceModel.OperationFormatUse.Literal>. Literál znamená, že zprávy je literál instance schématu ve schématu WSDL, jak je znázorněno v následujícím dokumentu nebo literál příklad.  
  
```xml  
<Add xmlns="http://Microsoft.ServiceModel.Samples">  
  <n1>100</n1>  
  <n2>15.99</n2>  
</Add>  
```  
  
 Kódování znamená, že se schémata ve schématu WSDL jsou abstraktní specifikace, které jsou kódovány podle pravidel nalezena v protokolu SOAP 1.1 oddíl 5. Následuje příklad RPC a Encoded.  
  
```xml  
<q1:Add xmlns:q1="http://Microsoft.ServiceModel.Samples">  
  <n1 xsi:type="xsd:double" xmlns="">100</n1>  
  <n2 xsi:type="xsd:double" xmlns="">15.99</n2>  
</q1:Add>  
```  
  
 WS-I základní profil 1.0 zakazují použití <xref:System.ServiceModel.OperationFormatUse.Encoded> a musí ho používáte jenom v případě potřeby ve starších verzí služeb. `Encoded` Formát zprávy je k dispozici pouze při používání třídy XmlSerializer.  
  
 Aby bylo možné zobrazit zprávy se odeslané a přijaté, tato ukázka je založena na [trasování a protokolování zpráv](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md). Konfigurace služby a zdrojový kód se upravila tak povolit a využívat trasování a protokolování zpráv. Kromě toho <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> není nakonfigurovaná bez zabezpečení, takže protokolované zprávy lze zobrazit v nezašifrované podobě. Výsledný protokoly trasování (System.ServiceModel.e2e a Message.log) by měl zobrazit pomocí [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Bude vytvořena ve složce C:\LOGS se konfigurují trasování. Vytvořte složku před spuštěním ukázky. Chcete-li zobrazit obsah zprávy v nástroji prohlížeče trasování, vyberte **zprávy** vlevo a vpravo podokna nástroje.  
  
 Následující kód ukazuje kontrakt služby s <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> vlastnost nastavena na hodnotu <xref:System.ServiceModel.OperationFormatUse> a změnit formát těla zprávy z výchozího <xref:System.ServiceModel.OperationFormatStyle> k <xref:System.ServiceModel.OperationFormatStyle.Document>.  
  
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
  
 Pokud chcete zobrazit rozdíl mezi různými <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> a <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> nastavení, upravovat ve službě, znovu vygenerovat klienta, spusťte ukázku a zkontrolujte soubor c:\logs\message.logs pomocí nástroje prohlížeče trasování služeb. Také sledovat dopad na metadata zobrazením `http://localhost/ServiceModelSamples/service.svc?wsdl`. Metadata služby je obvykle rozdělit do více stránek. Na stránce hlavní wsdl obsahuje vazby WSDL, ale zobrazit `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0` sledovat definice zpráv.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Vytvoření C:\LOGS adresáře pro protokolování zpráv. Dejte uživateli oprávnění pro tento adresář k zápisu síťové služby.  
  
3.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\UseAndStyle`  
  
## <a name="see-also"></a>Viz také:
