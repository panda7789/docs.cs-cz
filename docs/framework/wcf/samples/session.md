---
title: Relace
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Sessions
ms.assetid: 36e1db50-008c-4b32-8d09-b56e790b8417
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 01c1bc2d202080349db32452adfe549d7a6dd3cc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="session"></a>Relace
Relace příklad znázorňuje způsob implementace kontraktu, která vyžaduje relaci. Relaci poskytuje kontext pro provádění více operací. To umožňuje službě k přidružení stavu dané relace tak, aby následných operací můžete použít stav předchozí operace. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), který implementuje službu kalkulačky. `ICalculator` Kontrakt změnila umožňující sadu aritmetické operace, které mají být provedeny, a zajistit přitom ochranu výsledku spuštěné. Tato funkce je definována `ICalculatorSession` kontrakt. Služba udržuje stavu pro klienta jako výpočet se říká víc operací služeb. Klient může získat aktuální výsledek pomocí volání `Result()` a zrušte zaškrtnutí výsledek, který má nula voláním `Clear()`.  
  
 V této ukázce klienta je konzolová aplikace (.exe) a služba je hostovaná Internetové informační služby (IIS).  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Nastavení <xref:System.ServiceModel.SessionMode> smlouvy na `Required` zajišťuje Pokud přes konkrétní vazbu je vystavený kontrakt, vazbu podporuje relací. Pokud vazba nepodporuje relace je vyvolána výjimka. `ICalculatorSession` Rozhraní je definováno tak, že je možné volat jednu nebo více operací, které upraví spuštěné výsledek, jak je znázorněno v následujícím ukázkovém kódu.  
  
```  
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
  
 Používání služby <xref:System.ServiceModel.InstanceContextMode> z <xref:System.ServiceModel.InstanceContextMode.PerSession> vytvořit vazbu instance kontextu uvedená služba každý příchozí relace. To umožňuje službě udržovat spuštěné výsledek pro každou relaci v místní členské proměnné.  
  
```  
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
  
 Když spustíte ukázku, klient provede několik požadavků na server a požadavky výsledek, který potom zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně klienta vypnout klienta.  
  
```  
(((0 + 100) - 50) * 17.65) / 2 = 441.25  
Press <ENTER> to terminate client.  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Session`  
  
## <a name="see-also"></a>Viz také
