---
title: Hostování IIS pomocí vloženého kódu
ms.date: 03/30/2017
helpviewer_keywords:
- Web hosted service
- IIS Hosting Using Inline Code Sample [Windows Communication Foundation]
ms.assetid: 56fe3687-a34b-4661-8e30-b33770f413fa
ms.openlocfilehash: 4fa4c7ff92252733fcff65e4fc3ab3c6b3624181
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186885"
---
# <a name="iis-hosting-using-inline-code"></a>Hostování IIS pomocí vloženého kódu
Tato ukázka předvádí, jak implementovat služba hostovaná podle Internetové informační služby (IIS), kde je kód služby jsou obsaženy v řádku v souboru .svc a je zkompilován na vyžádání. Kód služby je možné implementovat také přímo do souborů se zdrojovým kódem v adresáři \App_Code aplikace nebo zkompilovány do sestavení nasazeno v \bin. Tento příklad neukazuje těchto technik.  
  
> [!NOTE]
>  Postupu a sestavení pokyny k instalaci pro tuto ukázku se nachází na konci tohoto tématu.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\InlineCode`  
  
 Vzorek ukazuje typické služba, která implementuje kontrakt, který definuje vzor komunikace požadavek odpověď. Služba je hostována ve službě IIS a kódu služby je zcela obsažený v souboru Service.svc. Služba aktivována hostitele je a kompilovaná první zpráva odeslaná do služby na vyžádání. Neexistuje žádné předkompilace nezbytné. Implementuje služby `ICalculator` smlouvy, jak je definováno v následujícím kódu:  
  
```csharp
// Define a service contract.  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
    public interface ICalculator  
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
  
 Implementace služby vypočítá a vrátí odpovídající výsledek.  
  
```svc
<%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService" %>   
```
```csharp
// Service class that implements the service contract.  
public class CalculatorService : ICalculator  
{  
    public double Add(double n1, double n2)  
    {  
        return n1 + n2;  
    }  
    public double Subtract(double n1, double n2)  
    {  
        return n1 - n2;  
    }  
    public double Multiply(double n1, double n2)  
    {  
        return n1 * n2;  
    }  
    public double Divide(double n1, double n2)  
    {  
        return n1 / n2;  
    }  
}  
```  
  
 Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně Klient vypnutí klient.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Po řešení je sestavený Build, spusťte setup.bat nastavit aplikaci ServiceModelSamples [!INCLUDE[iisver](../../../../includes/iisver-md.md)]. Adresář ServiceModelSamples by se měla objevit jako [!INCLUDE[iisver](../../../../includes/iisver-md.md)] aplikace.  
  
4.  Spusťte ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md). Příklad o tom, jak vytvořit klientskou aplikaci, která může volat tuto službu, naleznete v tématu [jak: Vytvoření klienta](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
## <a name="see-also"></a>Viz také:

- [Hostování AppFabric a ukázky trvalosti](https://go.microsoft.com/fwlink/?LinkId=193961)
