---
title: Podpora objektů POCO
ms.date: 03/30/2017
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
ms.openlocfilehash: 8d94d6a9700c38014aa53ee9910b53239fc28b0a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640027"
---
# <a name="poco-support"></a>Podpora objektů POCO
Tato ukázka předvádí, podpora serializaci zrušeno označení typy; To znamená typy, na které nebyly použity atributy serializace, někdy označovány jako obyčejný staré CLR objektů POCO typy. <xref:System.Runtime.Serialization.DataContractSerializer> Odvodí kontraktu dat pro všechny veřejné zrušeno označení typy, které mají výchozí konstruktor. Kontrakty dat umožňuje předání strukturovaná data do a ze služby. Další informace o typech zrušeno označení, naleznete v tématu [Serializovatelné typy](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
 Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), ale používá komplexní čísla namísto primitivní číselné typy. Je také podobné jako [základní kontrakt dat](../../../../docs/framework/wcf/samples/basic-data-contract.md) ukázkový, s výjimkou, že <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> nejsou použity atributy.  
  
 Služba je hostována v Internetové informační služby (IIS) a klient je konzolová aplikace (.exe).  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 `ComplexNumber` Třída se používá `ServiceContract`. `ComplexNumber` Typ nemá <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> atributy, jak je znázorněno v následujícím ukázkovém kódu. Ve výchozím nastavení se serializují všechny veřejné vlastnosti a pole.  
  
```csharp
public class ComplexNumber  
{  
    public double Real;  
    public double Imaginary;  
    public ComplexNumber()  
    {  
        Real = double.MinValue;  
        Imaginary = double.MinValue;  
    }  
    public ComplexNumber(double real, double imaginary)  
    {  
        this.Real = real;  
        this.Imaginary = imaginary;  
    }  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>
- [Serializovatelné typy](../../../../docs/framework/wcf/feature-details/serializable-types.md)
