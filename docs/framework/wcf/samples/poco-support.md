---
title: Podpora objektů POCO
ms.date: 03/30/2017
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
ms.openlocfilehash: e94f6d9576ed96613d975a66c1965820002f94ce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183418"
---
# <a name="poco-support"></a>Podpora objektů POCO
Tato ukázka ukazuje podporu serializace pro neoznačené typy; to znamená typy, na které nebyly použity atributy serializace, někdy označované jako typy prostých starých clr objektů (POCO). Odvodí <xref:System.Runtime.Serialization.DataContractSerializer> kontrakt dat pro všechny veřejné neoznačené typy, které mají konstruktor bez parametrů. Kontrakty dat umožňují předávat strukturovaná data do a ze služeb. Další informace o neoznačených typech naleznete v [tématu Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
 Tato ukázka je založena na [začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), ale používá komplexní čísla namísto primitivních číselných typů. Je také podobný ukázky [smlouvy základní data,](../../../../docs/framework/wcf/samples/basic-data-contract.md) s tím rozdílem, <xref:System.Runtime.Serialization.DataContractAttribute> že atributy a <xref:System.Runtime.Serialization.DataMemberAttribute> nejsou použity.  
  
 Služba je hostována internetovou informační službou (IIS) a klient je konzolová aplikace (.exe).  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 Třída `ComplexNumber` se používá `ServiceContract`v . Typ `ComplexNumber` nemá atributy <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> a, jak je znázorněno v následujícím ukázkovém kódu. Ve výchozím nastavení jsou všechny veřejné vlastnosti a pole serializovány.  
  
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
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>
- [Serializovatelné typy](../../../../docs/framework/wcf/feature-details/serializable-types.md)
