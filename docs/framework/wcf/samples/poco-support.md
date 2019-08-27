---
title: Podpora objektů POCO
ms.date: 03/30/2017
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
ms.openlocfilehash: 6796d7948bd3ebe0a8b96a861c628b30b7540912
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044782"
---
# <a name="poco-support"></a>Podpora objektů POCO
Tato ukázka demonstruje podporu serializace pro neoznačené typy; To znamená, že typy, které atributy serializace nebyly aplikovány, se někdy označují jako prosté staré typy objektů CLR (POCO). <xref:System.Runtime.Serialization.DataContractSerializer> Odvodí kontrakt dat pro všechny veřejné neoznačené typy, které mají konstruktor bez parametrů. Kontrakty dat umožňují předat strukturovaná data službám a ze služeb. Další informace o neoznačených typech naleznete v tématu [Serializovatelné typy](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
 Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), ale používá složitá čísla namísto primitivních číselných typů. Je také podobný ukázce [základního data kontraktu](../../../../docs/framework/wcf/samples/basic-data-contract.md) s tím rozdílem, že <xref:System.Runtime.Serialization.DataContractAttribute> nejsou <xref:System.Runtime.Serialization.DataMemberAttribute> použity atributy a.  
  
 Služba je hostována službou Internetová informační služba (IIS) a klientem je Konzolová aplikace (. exe).  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Třída se používá `ServiceContract`v. `ComplexNumber` Typ nemá atributy<xref:System.Runtime.Serialization.DataMemberAttribute> a, jak je znázorněno v následujícím ukázkovém kódu. <xref:System.Runtime.Serialization.DataContractAttribute> `ComplexNumber` Ve výchozím nastavení jsou serializovány všechny veřejné vlastnosti a pole.  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>
- [Serializovatelné typy](../../../../docs/framework/wcf/feature-details/serializable-types.md)
