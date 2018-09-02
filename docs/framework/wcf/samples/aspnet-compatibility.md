---
title: Režim kompatibility ASP.NET
ms.date: 03/30/2017
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
ms.openlocfilehash: eeb09914fc90848c987127c789379549917063f6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43398232"
---
# <a name="aspnet-compatibility"></a><span data-ttu-id="ff29f-102">Režim kompatibility ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ff29f-102">ASP.NET Compatibility</span></span>
<span data-ttu-id="ff29f-103">Tato ukázka předvádí, jak povolit režim kompatibility ASP.NET ve Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ff29f-103">This sample demonstrates how to enable ASP.NET Compatibility mode in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="ff29f-104">Služby spuštěné v režimu plně účastnit kanálu aplikace ASP.NET a mohl provádět režim kompatibility ASP.NET používat funkce technologie ASP.NET, jako je soubor nebo adresa URL autorizační, stav relace a <xref:System.Web.HttpContext> třídy.</span><span class="sxs-lookup"><span data-stu-id="ff29f-104">Services running in ASP.NET Compatibility mode participate fully in the ASP.NET application pipeline and can make use of ASP.NET features such as file/URL authorization, session state, and the <xref:System.Web.HttpContext> class.</span></span> <span data-ttu-id="ff29f-105"><xref:System.Web.HttpContext> Třída umožňuje přístup k souborů cookie, relace a další funkce technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ff29f-105">The <xref:System.Web.HttpContext> class allows access to cookies, sessions, and other ASP.NET features.</span></span> <span data-ttu-id="ff29f-106">Tento režim vyžaduje, že vazby pomocí přenos pomocí protokolu HTTP a samotné služby musí být hostovaný ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="ff29f-106">This mode requires that the bindings use the HTTP transport and the service itself must be hosted in IIS.</span></span>  
  
 <span data-ttu-id="ff29f-107">V této ukázce klient je konzolová aplikace (spustitelný soubor) a služba je hostována v Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="ff29f-107">In this sample, the client is a console application (an executable) and the service is hosted in Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ff29f-108">Postupu a sestavení pokyny k instalaci pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="ff29f-108">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
<span data-ttu-id="ff29f-109">Tato ukázka vyžaduje [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] fond aplikací tak, aby bylo možné spustit.</span><span class="sxs-lookup"><span data-stu-id="ff29f-109">This sample requires a [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] application pool in order to run.</span></span> <span data-ttu-id="ff29f-110">Chcete-li vytvořit nový fond aplikací nebo změnit výchozí fond aplikací, postupujte podle těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="ff29f-110">To create a new application pool, or to modify the default application pool, follow these steps.</span></span>  

1.  <span data-ttu-id="ff29f-111">Otevřít **ovládací panely**.</span><span class="sxs-lookup"><span data-stu-id="ff29f-111">Open **Control Panel**.</span></span>  <span data-ttu-id="ff29f-112">Otevřít **nástroje pro správu** aplet pod **systém a zabezpečení** záhlaví.</span><span class="sxs-lookup"><span data-stu-id="ff29f-112">Open the **Administrative Tools** applet under the **System and Security** heading.</span></span> <span data-ttu-id="ff29f-113">Otevřít **Správce Internetové informační služby (IIS)** aplet.</span><span class="sxs-lookup"><span data-stu-id="ff29f-113">Open the **Internet Information Services (IIS) Manager** applet.</span></span>  

2.  <span data-ttu-id="ff29f-114">Ve stromovém zobrazení rozbalte **připojení** podokně.</span><span class="sxs-lookup"><span data-stu-id="ff29f-114">Expand the treeview in the **Connections** pane.</span></span> <span data-ttu-id="ff29f-115">Vyberte **fondy aplikací** uzlu.</span><span class="sxs-lookup"><span data-stu-id="ff29f-115">Select the **Application Pools** node.</span></span>  

3.  <span data-ttu-id="ff29f-116">Nastavit výchozí fond aplikací používat [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (která může způsobit problémy s kompatibilitou s existující weby), klikněte pravým tlačítkem myši **DefaultAppPool** položky seznamu a vyberte **základní nastavení...** .</span><span class="sxs-lookup"><span data-stu-id="ff29f-116">To set the default application pool to use [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (which may cause incompatibility problems with existing sites), right-click the **DefaultAppPool** list item and select **Basic Settings…**.</span></span> <span data-ttu-id="ff29f-117">Nastavit **rozhraní .net Framework verze** rozevírací k **rozhraní .net Framework v4.0.30128** (nebo novější).</span><span class="sxs-lookup"><span data-stu-id="ff29f-117">Set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span>  

4.  <span data-ttu-id="ff29f-118">Chcete-li vytvořit nový fond aplikací, který používá [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (pro zachování kompatibility pro jiné aplikace), klikněte pravým tlačítkem **fondy aplikací** uzel a vyberte možnost **přidat fond aplikací...** .</span><span class="sxs-lookup"><span data-stu-id="ff29f-118">To create a new application pool that uses [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (to preserve compatibility for other applications), right-click the **Application Pools** node and select **Add Application Pool…**.</span></span> <span data-ttu-id="ff29f-119">Pojmenujte nový fond aplikací a nastavte **rozhraní .net Framework verze** rozevírací k **rozhraní .net Framework v4.0.30128** (nebo novější).</span><span class="sxs-lookup"><span data-stu-id="ff29f-119">Name the new application pool, and set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span> <span data-ttu-id="ff29f-120">Po spuštění instalace kroky níže, klikněte pravým tlačítkem myši **ServiceModelSamples** aplikaci a vyberte **spravovat aplikaci**, **Upřesnit nastavení...** .</span><span class="sxs-lookup"><span data-stu-id="ff29f-120">After running the setup steps below, right-click the **ServiceModelSamples** application and select **Manage Application**, **Advanced Settings…**.</span></span> <span data-ttu-id="ff29f-121">Nastavte **fond aplikací** pro nový fond aplikací.</span><span class="sxs-lookup"><span data-stu-id="ff29f-121">Set the **Application Pool** to the new application pool.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ff29f-122">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="ff29f-122">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ff29f-123">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="ff29f-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ff29f-124">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="ff29f-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ff29f-125">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="ff29f-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`  
  
 <span data-ttu-id="ff29f-126">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), který implementuje Kalkulačka služby.</span><span class="sxs-lookup"><span data-stu-id="ff29f-126">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="ff29f-127">`ICalculator` Kontraktu byla upravena jako `ICalculatorSession` smlouvy povolit sadu operací, a zajistit přitom ochranu spuštěné výsledek.</span><span class="sxs-lookup"><span data-stu-id="ff29f-127">The `ICalculator` contract has been modified as the `ICalculatorSession` contract to allow a set of operations to be performed, while keeping a running result.</span></span>  
  
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
  
 <span data-ttu-id="ff29f-128">Služba zajišťuje stavu, pomocí funkce, pro každého klienta, jako jsou volány více operací služby k provedení výpočtu.</span><span class="sxs-lookup"><span data-stu-id="ff29f-128">The service maintains state, using the feature, for each client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="ff29f-129">Klient může načíst aktuální výsledek voláním `Result` a můžete vymazat výsledek, který má nulovou voláním `Clear`.</span><span class="sxs-lookup"><span data-stu-id="ff29f-129">The client can retrieve the current result by calling `Result` and can clear the result to zero by calling `Clear`.</span></span>  
  
 <span data-ttu-id="ff29f-130">Služba relace ASP.NET používá k ukládání výsledků pro každou relaci klienta.</span><span class="sxs-lookup"><span data-stu-id="ff29f-130">The service uses the ASP.NET session to store the result for each client session.</span></span> <span data-ttu-id="ff29f-131">To umožňuje službě údržby spuštěné výsledek pro každého klienta napříč více volání služby.</span><span class="sxs-lookup"><span data-stu-id="ff29f-131">This allows the service to maintain the running result for each client across multiple calls to the service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ff29f-132">Stavu relace ASP.NET a WCF relace jsou velmi různé věci.</span><span class="sxs-lookup"><span data-stu-id="ff29f-132">ASP.NET session state and WCF sessions are very different things.</span></span> <span data-ttu-id="ff29f-133">Zobrazit [relace](../../../../docs/framework/wcf/samples/session.md) podrobné informace o relacích WCF.</span><span class="sxs-lookup"><span data-stu-id="ff29f-133">See [Session](../../../../docs/framework/wcf/samples/session.md) for details on WCF sessions.</span></span>
  
 <span data-ttu-id="ff29f-134">Služba má dokonalou závislosti na stavu relace ASP.NET a vyžaduje režim kompatibility ASP.NET fungovat správně.</span><span class="sxs-lookup"><span data-stu-id="ff29f-134">The service has an intimate dependency on ASP.NET session state and requires ASP.NET compatibility mode to function correctly.</span></span> <span data-ttu-id="ff29f-135">Tyto požadavky jsou vyjádřeny deklarativně použitím `AspNetCompatibilityRequirements` atribut.</span><span class="sxs-lookup"><span data-stu-id="ff29f-135">These requirements are expressed declaratively by applying the `AspNetCompatibilityRequirements` attribute.</span></span>  
  
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
  
 <span data-ttu-id="ff29f-136">Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="ff29f-136">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="ff29f-137">Stisknutím klávesy ENTER v okně Klient vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="ff29f-137">Press ENTER in the client window to shut down the client.</span></span>  
  
```console
0, + 100, - 50, * 17.65, / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ff29f-138">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="ff29f-138">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ff29f-139">Ujistěte se, jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ff29f-139">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="ff29f-140">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ff29f-140">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="ff29f-141">Po řešení je sestavený Build, spusťte Setup.bat nastavit aplikaci ServiceModelSamples [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ff29f-141">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span></span> <span data-ttu-id="ff29f-142">Adresář ServiceModelSamples by se měla objevit jako [!INCLUDE[iisver](../../../../includes/iisver-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="ff29f-142">The ServiceModelSamples directory should now appear as an [!INCLUDE[iisver](../../../../includes/iisver-md.md)] Application.</span></span>  
  
4.  <span data-ttu-id="ff29f-143">Spusťte ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ff29f-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff29f-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff29f-144">See Also</span></span>  
 [<span data-ttu-id="ff29f-145">Hostování AppFabric a ukázky trvalosti</span><span class="sxs-lookup"><span data-stu-id="ff29f-145">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
