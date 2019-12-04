---
title: XmlSerializer – zpracování chyb
ms.date: 03/30/2017
ms.assetid: c6b80f14-64f4-4162-ae76-71664cf42fd3
ms.openlocfilehash: 171fa67c3c63a99c52ac2a96e97084fb29b3dcf5
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714526"
---
# <a name="xmlserializer-faults"></a>XmlSerializer – zpracování chyb
Ukázka kontraktu selhání <xref:System.Xml.Serialization.XmlSerializer> ukazuje, jak komunikovat s informacemi o chybě ze služby klientovi pomocí <xref:System.Xml.Serialization.XmlSerializer>. Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md)s nějakým dalším kódem přidaným do služby pro převod vnitřní výjimky na chybu. Klient se pokusí provést dělení nulou, aby vynutil chybový stav služby.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Smlouva kalkulačky byla upravena tak, aby zahrnovala <xref:System.ServiceModel.FaultContractAttribute>, jak je znázorněno v následujícím ukázkovém kódu. Také <xref:System.ServiceModel.XmlSerializerFormatAttribute> slouží k povolení serializace pomocí <xref:System.Xml.Serialization.XmlSerializer>. Vlastnost <xref:System.ServiceModel.XmlSerializerFormatAttribute.SupportFaults%2A> je nastavena na hodnotu `true` u tohoto atributu, která dává serializátoru pokyn pro použití <xref:System.Xml.Serialization.XmlSerializer> pro čtení a zápis chyb.  
  
```csharp
[XmlSerializerFormat(SupportFaults=true)]  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    int Add(int n1, int n2);  
  
    [OperationContract]  
    int Subtract(int n1, int n2);  
  
    [OperationContract]  
    int Multiply(int n1, int n2);  
  
    [OperationContract]  
    [FaultContract(typeof(MathFault))]  
    int Divide(int n1, int n2);  
}  
```  
  
 Při generování kódu pro klientský proxy server je nutné použít příznak **/UseSerializerForFaults** pro nástroj pro [Svcutil metadat (. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\XmlSerializerFaults`  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.XmlSerializerFormatAttribute>
- <xref:System.ServiceModel.XmlSerializerFormatAttribute.SupportFaults%2A>
