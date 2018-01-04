---
title: "Podpora objektů POCO"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c471a6726d8f7e621d666e014b2363c088e2b0e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="poco-support"></a>Podpora objektů POCO
Tento příklad znázorňuje podporu serializace zrušit označení typy; To znamená typy, pro které nebyly použity atributy serializace, někdy označuje jako typy prostý staré CLR objektů POCO (). <xref:System.Runtime.Serialization.DataContractSerializer> Odvodí kontraktu dat pro všechny veřejné typy zrušit označení, které mají výchozí konstruktor. Kontrakty dat umožňují předat strukturovaných dat do a ze služby. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Zrušit označení typy, viz [Serializovatelné typy](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
 Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), ale používá komplexní čísla místo číselný primitivní typy. Je podobná [základní kontrakt dat](../../../../docs/framework/wcf/samples/basic-data-contract.md) ukázkové, vyjma toho, že <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> atributy se nepoužívají.  
  
 Služba je hostovaná Internetové informační služby (IIS) a klient je konzolová aplikace (.exe).  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 `ComplexNumber` Třída se používá `ServiceContract`. `ComplexNumber` Typ nemá <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> atributy, jak je znázorněno v následujícím ukázkovém kódu. Ve výchozím nastavení se serializují všechny veřejné vlastnosti a pole.  
  
```  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>  
 [Serializovatelné typy](../../../../docs/framework/wcf/feature-details/serializable-types.md)
