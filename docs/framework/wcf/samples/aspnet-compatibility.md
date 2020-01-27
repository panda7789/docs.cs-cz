---
title: Režim kompatibility ASP.NET
ms.date: 03/30/2017
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
ms.openlocfilehash: 1f1690cdd1a880c852abc04ea8e4958bae2c5432
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728018"
---
# <a name="aspnet-compatibility"></a>Režim kompatibility ASP.NET

Tato ukázka předvádí, jak povolit režim kompatibility ASP.NET v Windows Communication Foundation (WCF). Služby běžící v režimu kompatibility ASP.NET se plně účastní kanálu aplikace ASP.NET a můžou využívat funkce ASP.NET, jako je například autorizace souborů a adres URL, stav relace a třída <xref:System.Web.HttpContext>. Třída <xref:System.Web.HttpContext> umožňuje přístup k souborům cookie, relacím a dalším funkcím ASP.NET. Tento režim vyžaduje, aby vazby používaly přenos HTTP a samotná služba musí být hostovaná ve službě IIS.

V této ukázce je klient Konzolová aplikace (spustitelný soubor) a služba je hostovaná ve službě Internetová informační služba (IIS).

> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.

Tato ukázka vyžaduje, aby byl fond aplikací .NET Framework 4 spuštěn. Chcete-li vytvořit nový fond aplikací nebo upravit výchozí fond aplikací, postupujte podle těchto kroků.

1. Otevřete **Ovládací panely**.  V části **systém a záhlaví zabezpečení** otevřete aplet **Nástroje pro správu** . Otevřete applet **správce Internetová informační služba (IIS)** .

2. Rozbalte ovládací prvek TreeView v podokně **připojení** . Vyberte uzel **fondy aplikací** .

3. Pokud chcete nastavit výchozí fond aplikací tak, aby používal .NET Framework 4 (což může způsobit problémy s nekompatibilitou s existujícími lokalitami), klikněte pravým tlačítkem myši na položku seznamu **DefaultAppPool** a vyberte **základní nastavení..** . Nastavte **verzi rozhraní .NET Framework** , která se má vyžádat, na **rozhraní .NET Framework v 4.0.30128** (nebo novější).

4. Pokud chcete vytvořit nový fond aplikací, který používá .NET Framework 4 (pro zachování kompatibility pro jiné aplikace), klikněte pravým tlačítkem myši na uzel **fondy aplikací** a vyberte **Přidat fond aplikací..** . Pojmenujte nový fond aplikací a nastavte **verzi rozhraní .NET Framework** , kterou si můžete stáhnout, do **rozhraní .NET Framework v 4.0.30128** (nebo novější). Po spuštění následujících kroků nastavení klikněte pravým tlačítkem myši na aplikaci **ServiceModelSamples** a vyberte možnost **Spravovat aplikaci**, **Upřesnit nastavení...** . Nastavte **fond aplikací** na nový fond aplikací.

> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`

Tato ukázka je založená na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), která implementuje službu kalkulačky. `ICalculator` kontrakt byl změněn jako `ICalculatorSession` smlouva, aby bylo možné provést sadu operací a přitom zachovat běžící výsledek.

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

Služba udržuje stav pomocí funkce pro každého klienta jako více operací služby k provedení výpočtu. Klient může získat aktuální výsledek voláním `Result` a může vymazat výsledek na nulu voláním `Clear`.

Služba používá relaci ASP.NET k uložení výsledku pro každou relaci klienta. Díky tomu může služba udržovat běžící výsledek pro každého klienta napříč více voláními služby.

> [!NOTE]
> Stav relace ASP.NET a relace WCF jsou velmi různé. Podrobnosti o relacích WCF najdete v tématu [relace](../../../../docs/framework/wcf/samples/session.md) .

Služba má závislost Intimate ve stavu relace ASP.NET a vyžaduje režim kompatibility ASP.NET pro správné fungování. Tyto požadavky jsou vyjádřeny deklarativně použitím atributu `AspNetCompatibilityRequirements`.

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

Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi. V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.

```console
0, + 100, - 50, * 17.65, / 2 = 441.25
Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Ujistěte se, že jste provedli [jednorázovou proceduru nastavení Windows Communication Foundation ukázek](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

3. Po sestavení řešení spusťte soubor Setup. bat a nastavte aplikaci ServiceModelSamples ve službě IIS 7,0. Adresář ServiceModelSamples by se teď měl zobrazit jako aplikace IIS 7,0.

4. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

## <a name="see-also"></a>Viz také:

- [Hostování technologie AppFabric a ukázky trvalosti](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
