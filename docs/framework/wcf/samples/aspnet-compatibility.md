---
title: Režim kompatibility ASP.NET
ms.date: 03/30/2017
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
ms.openlocfilehash: 01381dc579f5ae3eadd2f913a0e09d7d259794a1
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59304210"
---
# <a name="aspnet-compatibility"></a>Režim kompatibility ASP.NET
Tato ukázka předvádí, jak povolit režim kompatibility ASP.NET ve Windows Communication Foundation (WCF). Služby spuštěné v režimu plně účastnit kanálu aplikace ASP.NET a mohl provádět režim kompatibility ASP.NET používat funkce technologie ASP.NET, jako je soubor nebo adresa URL autorizační, stav relace a <xref:System.Web.HttpContext> třídy. <xref:System.Web.HttpContext> Třída umožňuje přístup k souborů cookie, relace a další funkce technologie ASP.NET. Tento režim vyžaduje, že vazby pomocí přenos pomocí protokolu HTTP a samotné služby musí být hostovaný ve službě IIS.  
  
 V této ukázce klient je konzolová aplikace (spustitelný soubor) a služba je hostována v Internetové informační služby (IIS).  
  
> [!NOTE]
>  Postupu a sestavení pokyny k instalaci pro tuto ukázku se nachází na konci tohoto tématu.  
  
Tato ukázka vyžaduje [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] fond aplikací tak, aby bylo možné spustit. Chcete-li vytvořit nový fond aplikací nebo změnit výchozí fond aplikací, postupujte podle těchto kroků.  

1. Otevřete **Ovládací panely**.  Otevřít **nástroje pro správu** aplet pod **systém a zabezpečení** záhlaví. Otevřít **Správce Internetové informační služby (IIS)** aplet.  

2. Ve stromovém zobrazení rozbalte **připojení** podokně. Vyberte **fondy aplikací** uzlu.  

3. Nastavit výchozí fond aplikací používat [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (která může způsobit problémy s kompatibilitou s existující weby), klikněte pravým tlačítkem myši **DefaultAppPool** položky seznamu a vyberte **základní nastavení...** . Nastavit **rozhraní .net Framework verze** rozevírací k **rozhraní .net Framework v4.0.30128** (nebo novější).  

4. Chcete-li vytvořit nový fond aplikací, který používá [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (pro zachování kompatibility pro jiné aplikace), klikněte pravým tlačítkem **fondy aplikací** uzel a vyberte možnost **přidat fond aplikací...** . Pojmenujte nový fond aplikací a nastavte **rozhraní .net Framework verze** rozevírací k **rozhraní .net Framework v4.0.30128** (nebo novější). Po spuštění instalace kroky níže, klikněte pravým tlačítkem myši **ServiceModelSamples** aplikaci a vyberte **spravovat aplikaci**, **Upřesnit nastavení...** . Nastavte **fond aplikací** pro nový fond aplikací.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`  
  
 Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), který implementuje Kalkulačka služby. `ICalculator` Kontraktu byla upravena jako `ICalculatorSession` smlouvy povolit sadu operací, a zajistit přitom ochranu spuštěné výsledek.  
  
```csharp  
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
  
 Služba zajišťuje stavu, pomocí funkce, pro každého klienta, jako jsou volány více operací služby k provedení výpočtu. Klient může načíst aktuální výsledek voláním `Result` a můžete vymazat výsledek, který má nulovou voláním `Clear`.  
  
 Služba relace ASP.NET používá k ukládání výsledků pro každou relaci klienta. To umožňuje službě údržby spuštěné výsledek pro každého klienta napříč více volání služby.  
  
> [!NOTE]
> Stavu relace ASP.NET a WCF relace jsou velmi různé věci. Zobrazit [relace](../../../../docs/framework/wcf/samples/session.md) podrobné informace o relacích WCF.
  
 Služba má dokonalou závislosti na stavu relace ASP.NET a vyžaduje režim kompatibility ASP.NET fungovat správně. Tyto požadavky jsou vyjádřeny deklarativně použitím `AspNetCompatibilityRequirements` atribut.  
  
```csharp  
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
  
 Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně Klient vypnutí klient.  
  
```console
0, + 100, - 50, * 17.65, / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Ujistěte se, jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Po řešení je sestavený Build, spusťte Setup.bat nastavit aplikaci ServiceModelSamples [!INCLUDE[iisver](../../../../includes/iisver-md.md)]. Adresář ServiceModelSamples by se měla objevit jako [!INCLUDE[iisver](../../../../includes/iisver-md.md)] aplikace.  
  
4. Spusťte ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Viz také:

- [Hostování AppFabric a ukázky trvalosti](https://go.microsoft.com/fwlink/?LinkId=193961)
