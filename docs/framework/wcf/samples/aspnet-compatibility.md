---
title: "Režim kompatibility ASP.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 751fe96caa2be63e925b3107fa2c198b523bef72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="aspnet-compatibility"></a>Režim kompatibility ASP.NET
Tento příklad ukazuje, jak povolit [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] režimu kompatibility v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Služby spuštěné [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] režim kompatibility účast ve plně [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace kanálu a mohl provádět použití [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] funkce jako je například autorizace soubor nebo adresa URL, stav relace a <xref:System.Web.HttpContext> – třída. <xref:System.Web.HttpContext> Třída umožňuje přístup k souborů cookie, relací a další [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] funkce. Tento režim vyžaduje, aby vazby používají přenos HTTP a samotné služby musí být hostované ve službě IIS.  
  
 V této ukázce klienta je konzolová aplikace (spustitelného souboru) a služba je hostovaná v Internetové informační služby (IIS).  
  
> [!NOTE]
>  Nastavení postupu a sestavení pokyny k této ukázce jsou umístěné na konci tohoto tématu.  
  
> [!NOTE]
>  Tato ukázka vyžaduje [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] fond aplikací, aby bylo možné spustit. Chcete-li vytvořit nový fond aplikací, nebo upravit výchozí fond aplikací, postupujte podle těchto kroků.  
>   
>  1.  Otevřete **ovládací panely**.  Otevřete **nástroje pro správu** aplet pod **systém a zabezpečení** záhlaví. Otevřete **Správce Internetové informační služby (IIS)** aplet.  
> 2.  Rozbalte položku ve stromovém zobrazení **připojení** podokně. Vyberte **fondy aplikací** uzlu.  
> 3.  Nastavit výchozí fond aplikací používat [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (která může způsobit problémy s kompatibilitou s existujícími lokalitami), klikněte pravým tlačítkem myši **DefaultAppPool** položky seznamu a vyberte **základní nastavení...** . Nastavte **rozhraní .net Framework verze** rozevírací k **rozhraní .net Framework v4.0.30128** (nebo novější).  
> 4.  Chcete-li vytvořit nový fond aplikací, který používá [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (pro zachování kompatibility pro jiné aplikace), klikněte pravým tlačítkem myši **fondy aplikací** uzel a vyberte možnost **přidat fond aplikací...** . Název nového fondu aplikací a nastavte **rozhraní .net Framework verze** rozevírací k **rozhraní .net Framework v4.0.30128** (nebo novější). Po spuštění instalačního programu kroky níže, klikněte pravým tlačítkem myši **ServiceModelSamples** aplikace a vyberte možnost **spravovat aplikace**, **Upřesnit nastavení...** . Nastavte **fond aplikací** na nový fond aplikací.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`  
  
 Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), který implementuje službu kalkulačky. `ICalculator` Kontrakt změnila jako `ICalculatorSession` Smlouvy umožňující sadu operací, které mají být provedeny, a zajistit přitom ochranu výsledku spuštěné.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculatorSession  
{  
    [OperationContract]  
    void Clear();  
    [OperationContract]  
    void AddTo(double n);  
    [OperationContract]  
    void SubtractFrom(double n);  
    [OperationContract]  
    void MultiplyBy(double n);  
    [OperationContract]  
    void DivideBy(double n);  
    [OperationContract]  
    double Result();  
}  
```  
  
 Služba Udržovat stav, používá funkci, pro každého klienta jako výpočet se říká víc operací služeb. Klient může získat aktuální výsledek pomocí volání `Result` a můžete vymazat výsledek, který má nula voláním `Clear`.  
  
 Služba používá [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] relace uložit výsledek pro každou relaci klienta. To umožňuje službě udržet spuštěné výsledek u jednotlivých klientů přes několik volání do služby.  
  
> [!NOTE]
>  [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Stav relace a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] relací jsou velmi různých věcí.  Najdete v článku [relace](../../../../docs/framework/wcf/samples/session.md) podrobnosti o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] relací.  
  
 Služba má dokonalou závislost [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] stavu relace a vyžaduje [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] režimu kompatibility, aby správně fungoval. Tyto požadavky jsou vyjádřeny deklarativně použitím `AspNetCompatibilityRequirements` atribut.  
  
```  
[AspNetCompatibilityRequirements(RequirementsMode =  
                       AspNetCompatibilityRequirementsMode.Required)]  
public class CalculatorService : ICalculatorSession  
{  
    double Result  
    {  // store result in AspNet Session  
       get {  
          if (HttpContext.Current.Session["Result"] != null)  
             return (double)HttpContext.Current.Session["Result"];  
          return 0.0D;  
       }  
       set  
       {  
          HttpContext.Current.Session["Result"] = value;  
       }  
    }  
    public void Clear()  
    {  
        Result = 0.0D;  
    }  
    public void AddTo(double n)  
    {  
        Result += n;  
    }  
    public void SubtractFrom(double n)  
    {  
        Result -= n;  
    }  
    public void MultiplyBy(double n)  
    {  
        Result *= n;  
    }  
    public void DivideBy(double n)  
    {  
        Result /= n;  
    }  
    public double Result()  
    {  
        return Result;  
    }  
}  
```  
  
 Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně klienta vypnout klienta.  
  
```  
0, + 100, - 50, * 17.65, / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, kterou jste udělali [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Po vytvoření řešení, spusťte Setup.bat nastavit aplikaci ServiceModelSamples v [!INCLUDE[iisver](../../../../includes/iisver-md.md)]. Adresář ServiceModelSamples by se měla zobrazit jako [!INCLUDE[iisver](../../../../includes/iisver-md.md)] aplikace.  
  
4.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Viz také  
 [Ukázky trvalosti a hostování AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
