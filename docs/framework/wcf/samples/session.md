---
title: Relace
ms.date: 03/30/2017
helpviewer_keywords:
- Sessions
ms.assetid: 36e1db50-008c-4b32-8d09-b56e790b8417
ms.openlocfilehash: e364b539e355f669037983813f9e6d1e0371da1f
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715077"
---
# <a name="session"></a>Relace
Ukázka relace ukazuje, jak implementovat kontrakt, který vyžaduje relaci. Relace poskytuje kontext pro provádění více operací. Díky tomu může služba přidružit stav k dané relaci, aby následné operace mohly používat stav předchozí operace. Tato ukázka je založená na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), která implementuje službu kalkulačky. `ICalculator` kontrakt byl upraven, aby bylo možné provést sadu aritmetických operací a přitom zachovat běžící výsledek. Tato funkce je definována kontraktem `ICalculatorSession`. Služba udržuje stav pro klienta jako volání více operací služby za účelem provedení výpočtu. Klient může načíst aktuální výsledek voláním `Result()` a vymazat výsledek na nulu voláním `Clear()`.  
  
 V této ukázce je klient Konzolová aplikace (. exe) a služba je hostována službou Internetová informační služba (IIS).  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Nastavení <xref:System.ServiceModel.SessionMode> kontraktu pro `Required` zajistí, že pokud se kontrakt zveřejní přes konkrétní vazbu, vazba podporuje relace. Pokud vazba nepodporuje relace, je vyvolána výjimka. Rozhraní `ICalculatorSession` je definováno tak, aby bylo možné volat jednu nebo více operací, což upravuje běžící výsledek, jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 Služba používá <xref:System.ServiceModel.InstanceContextMode> <xref:System.ServiceModel.InstanceContextMode.PerSession> ke svázání daného kontextu instance služby s každou příchozí relací. Díky tomu může služba udržovat běžící výsledek pro každou relaci v místní členské proměnné.  
  
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
  
 Když spustíte ukázku, klient provede několik požadavků na server a požádá o výsledek, který se pak zobrazí v okně konzoly klienta. V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.  
  
```console  
(((0 + 100) - 50) * 17.65) / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
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
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Session`  
