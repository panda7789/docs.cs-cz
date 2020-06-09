---
title: Podpora objektů POCO
ms.date: 03/30/2017
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
ms.openlocfilehash: a9f8d185c58b22e68f7a8c11954e0e534c4bd48f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600461"
---
# <a name="poco-support"></a>Podpora objektů POCO
Tato ukázka demonstruje podporu serializace pro neoznačené typy; To znamená, že typy, které atributy serializace nebyly aplikovány, se někdy označují jako prosté staré typy objektů CLR (POCO). <xref:System.Runtime.Serialization.DataContractSerializer>Odvodí kontrakt dat pro všechny veřejné neoznačené typy, které mají konstruktor bez parametrů. Kontrakty dat umožňují předat strukturovaná data službám a ze služeb. Další informace o neoznačených typech naleznete v tématu [Serializovatelné typy](../feature-details/serializable-types.md).  
  
 Tato ukázka je založena na [Začínáme](getting-started-sample.md), ale používá složitá čísla namísto primitivních číselných typů. Je také podobný ukázce [základního data kontraktu](basic-data-contract.md) s tím rozdílem, že <xref:System.Runtime.Serialization.DataContractAttribute> nejsou <xref:System.Runtime.Serialization.DataMemberAttribute> použity atributy a.  
  
 Služba je hostována službou Internetová informační služba (IIS) a klientem je Konzolová aplikace (. exe).  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 `ComplexNumber`Třída se používá v `ServiceContract` . `ComplexNumber`Typ nemá <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> atributy a, jak je znázorněno v následujícím ukázkovém kódu. Ve výchozím nastavení jsou serializovány všechny veřejné vlastnosti a pole.  
  
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
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>
- [Serializovatelné typy](../feature-details/serializable-types.md)
