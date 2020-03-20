---
title: Relace
ms.date: 03/30/2017
helpviewer_keywords:
- Sessions
ms.assetid: 36e1db50-008c-4b32-8d09-b56e790b8417
ms.openlocfilehash: 85f1034999fc4cd36075c49bd8f4631bbd283679
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183367"
---
# <a name="session"></a>Relace
Ukázka relace ukazuje, jak implementovat smlouvu, která vyžaduje relaci. Relace poskytuje kontext pro provádění více operací. To umožňuje službě přidružit stav k dané relaci, takže následné operace mohou použít stav předchozí operace. Tato ukázka je založena na [začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), který implementuje kalkulačku služby. Smlouva `ICalculator` byla upravena tak, aby umožňovala provádění sady aritmetických operací při zachování průběžného výsledku. Tato funkce je definována smlouvou. `ICalculatorSession` Služba udržuje stav pro klienta jako více operací služby jsou volány k provedení výpočtu. Klient může načíst aktuální `Result()` výsledek voláním a vymazat `Clear()`výsledek na nulu voláním .  
  
 V této ukázce je klient konzolovou aplikací (.exe) a služba je hostována internetovou informační službou (IIS).  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 <xref:System.ServiceModel.SessionMode> Nastavení smlouvy zajistit, `Required` že při smlouvy je vystavena přes konkrétní vazbu, vazba podporuje relace. Pokud vazba nepodporuje relace je vyvolána výjimka. Rozhraní `ICalculatorSession` je definováno tak, že lze volat jednu nebo více operací, které mění průběžný výsledek, jak je znázorněno v následujícím ukázkovém kódu.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples", SessionMode=SessionMode.Required)]  
public interface ICalculatorSession  
{  
    [OperationContract(IsOneWay=true)]  
    void Clear();  
    [OperationContract(IsOneWay = true)]  
    void AddTo(double n);  
    [OperationContract(IsOneWay = true)]  
    void SubtractFrom(double n);  
    [OperationContract(IsOneWay = true)]  
    void MultiplyBy(double n);  
    [OperationContract(IsOneWay = true)]  
    void DivideBy(double n);  
    [OperationContract]  
    double Result();  
}  
```  
  
 Služba používá <xref:System.ServiceModel.InstanceContextMode> of <xref:System.ServiceModel.InstanceContextMode.PerSession> svázat kontext dané instance služby na každou příchozí relaci. To umožňuje službě udržovat spuštěný výsledek pro každou relaci v místní členské proměnné.  
  
```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
public class CalculatorService : ICalculatorSession  
{  
    double result = 0.0D;  
  
    public void Clear()  
    {  result = 0.0D; }  
  
    public void AddTo(double n)  
    {  result += n;   }  
  
    public void SubtractFrom(double n)  
    {  result -= n;   }  
  
    public void MultiplyBy(double n)  
    {  result *= n;   }  
  
    public void DivideBy(double n)  
    {  result /= n;   }  
  
    public double Result()  
    {  return result; }  
}  
```  
  
 Při spuštění ukázky klient provede několik požadavků na server a požaduje výsledek, který se pak zobrazí v okně klientské konzole. Stisknutím klávesy ENTER v okně klienta vypněte klienta.  
  
```console  
(((0 + 100) - 50) * 17.65) / 2 = 441.25  
Press <ENTER> to terminate client.  
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
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Session`  
