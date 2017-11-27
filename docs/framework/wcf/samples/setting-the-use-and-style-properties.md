---
title: "Nastavení vlastností Use a Style"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c09a0600-116f-41cf-900a-1b7e4ea4e300
caps.latest.revision: "28"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 21409597b8fe27992c08bbe76f56e78013156c46
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="setting-the-use-and-style-properties"></a>Nastavení vlastností Use a Style
Tento příklad znázorňuje způsob použití vlastností použití a stylu na <xref:System.ServiceModel.XmlSerializerFormatAttribute> a <xref:System.ServiceModel.DataContractFormatAttribute>. Tyto vlastnosti vliv na způsob formátování zprávy. Ve výchozím nastavení, je formátovaného textu zprávy se stylem nastavena na <xref:System.ServiceModel.OperationFormatStyle.Document>. Tato nastavení lze na úrovni kontraktu služby nebo úroveň kontrakt operaci.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> Vlastnost stylu určuje způsob formátování WSDL metadata pro službu. Možné hodnoty jsou <xref:System.ServiceModel.OperationFormatStyle.Document>, a <xref:System.ServiceModel.OperationFormatStyle.Rpc>. RPC znamená, že WSDL reprezentace zprávy vyměňují operace obsahuje parametry, jako by šlo vzdálené volání procedury. Následuje příklad.  
  
```xml  
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">  
  <wsdl:part name="n1" type="xsd:double"/>  
  <wsdl:part name="n2" type="xsd:double"/>  
</wsdl:message>  
```  
  
 Nastavení stylu <xref:System.ServiceModel.OperationFormatStyle.Document> znamená, že reprezentace WSDL obsahuje jediný prvek, který reprezentuje dokument, který se vyměňují operace, jak je znázorněno v následujícím příkladu.  
  
```xml  
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">  
  <wsdl:part name="parameters" element="tns:Add"/>  
</wsdl:message>  
```  
  
 <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> Vlastnost určuje formát zprávy. Možné hodnoty jsou <xref:System.ServiceModel.OperationFormatUse.Literal> a <xref:System.ServiceModel.OperationFormatUse.Encoded>; výchozí hodnota je <xref:System.ServiceModel.OperationFormatUse.Literal>. Literál znamená, že zpráva není literál instanci schéma ve schématu WSDL, jak je znázorněno v následujícím dokumentu / literálu příklad.  
  
```xml  
<Add xmlns="http://Microsoft.ServiceModel.Samples">  
  <n1>100</n1>  
  <n2>15.99</n2>  
</Add>  
```  
  
 Kódovaný znamená, že schémata ve schématu WSDL jsou abstraktní specifikace, které jsou zakódovány podle pravidel najít v protokolu SOAP 1.1 část 5. Následuje příklad RPC/kódováno.  
  
```xml  
<q1:Add xmlns:q1="http://Microsoft.ServiceModel.Samples">  
  <n1 xsi:type="xsd:double" xmlns="">100</n1>  
  <n2 xsi:type="xsd:double" xmlns="">15.99</n2>  
</q1:Add>  
```  
  
 WS-I Basic 1.0 profil zakáže použití <xref:System.ServiceModel.OperationFormatUse.Encoded> a měli používat jenom ho Pokud to vyžaduje starší verze služby. `Encoded` Formát zprávy je k dispozici pouze při použití třídy XmlSerializer.  
  
 Abyste mohli zobrazit zprávy se odesílají a přijímají, je na základě této ukázce [trasování a protokolování zpráv](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md). Konfigurace služby a zdrojového kódu bylo upraveno, aby povolit a využívat trasování a protokolování zpráv. Kromě toho <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> byl nakonfigurován bez zabezpečení, takže zaznamenané zprávy lze zobrazit v nezašifrované podobě. Výsledný protokoly trasování (System.ServiceModel.e2e a Message.log) by měl zobrazit pomocí [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Trasování jsou konfigurována pro vytvořit ve složce C:\LOGS. Před spuštěním ukázky vytvořte složku. Chcete-li zobrazit obsah zprávy v nástroji Prohlížeč trasování, vyberte **zprávy** v vlevo a vpravo podokna nástroje.  
  
 Následující kód ukazuje kontrakt služby s <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> vlastnost nastavena na hodnotu <xref:System.ServiceModel.OperationFormatUse> a formát text zprávy se změnil z výchozí <xref:System.ServiceModel.OperationFormatStyle> k <xref:System.ServiceModel.OperationFormatStyle.Document>.  
  
```  
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
  
 Rozdíl mezi různými <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> a <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> nastavení, je upravit ve službě, znovu vygenerovat klienta, spuštění vzorového a zkontrolujte soubor c:\logs\message.logs pomocí nástroje prohlížeče trasování služeb. Dopad na metadata také sledujte zobrazením http://localhost/ServiceModelSamples/service.svc?wsdl. Metadata pro služby je obvykle rozdělena na více stránkách. Stránka hlavní wsdl obsahuje WSDL vazby, ale zobrazit http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0 sledovat definice zpráv.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Vytvořte C:\LOGS adresář pro protokolování zpráv. Síťová služba zápisu oprávnění pro tento adresář uživateli přidělte.  
  
3.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\UseAndStyle`  
  
## <a name="see-also"></a>Viz také
