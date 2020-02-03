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
# <a name="aspnet-compatibility"></a><span data-ttu-id="3d5ca-102">Režim kompatibility ASP.NET</span><span class="sxs-lookup"><span data-stu-id="3d5ca-102">ASP.NET Compatibility</span></span>

<span data-ttu-id="3d5ca-103">Tato ukázka předvádí, jak povolit režim kompatibility ASP.NET v Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="3d5ca-103">This sample demonstrates how to enable ASP.NET Compatibility mode in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="3d5ca-104">Služby běžící v režimu kompatibility ASP.NET se plně účastní kanálu aplikace ASP.NET a můžou využívat funkce ASP.NET, jako je například autorizace souborů a adres URL, stav relace a třída <xref:System.Web.HttpContext>.</span><span class="sxs-lookup"><span data-stu-id="3d5ca-104">Services running in ASP.NET Compatibility mode participate fully in the ASP.NET application pipeline and can make use of ASP.NET features such as file/URL authorization, session state, and the <xref:System.Web.HttpContext> class.</span></span> <span data-ttu-id="3d5ca-105">Třída <xref:System.Web.HttpContext> umožňuje přístup k souborům cookie, relacím a dalším funkcím ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="3d5ca-105">The <xref:System.Web.HttpContext> class allows access to cookies, sessions, and other ASP.NET features.</span></span> <span data-ttu-id="3d5ca-106">Tento režim vyžaduje, aby vazby používaly přenos HTTP a samotná služba musí být hostovaná ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="3d5ca-106">This mode requires that the bindings use the HTTP transport and the service itself must be hosted in IIS.</span></span>

<span data-ttu-id="3d5ca-107">V této ukázce je klient Konzolová aplikace (spustitelný soubor) a služba je hostovaná ve službě Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="3d5ca-107">In this sample, the client is a console application (an executable) and the service is hosted in Internet Information Services (IIS).</span></span>

> [!NOTE]
> <span data-ttu-id="3d5ca-108">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="3d5ca-108">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="3d5ca-109">Tato ukázka vyžaduje, aby byl fond aplikací .NET Framework 4 spuštěn.</span><span class="sxs-lookup"><span data-stu-id="3d5ca-109">This sample requires a .NET Framework 4 application pool in order to run.</span></span> <span data-ttu-id="3d5ca-110">Chcete-li vytvořit nový fond aplikací nebo upravit výchozí fond aplikací, postupujte podle těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="3d5ca-110">To create a new application pool, or to modify the default application pool, follow these steps.</span></span>

1. <span data-ttu-id="3d5ca-111">Otevřete **Ovládací panely**.</span><span class="sxs-lookup"><span data-stu-id="3d5ca-111">Open **Control Panel**.</span></span>  <span data-ttu-id="3d5ca-112">V části **systém a záhlaví zabezpečení** otevřete aplet **Nástroje pro správu** .</span><span class="sxs-lookup"><span data-stu-id="3d5ca-112">Open the **Administrative Tools** applet under the **System and Security** heading.</span></span> <span data-ttu-id="3d5ca-113">Otevřete applet **správce Internetová informační služba (IIS)** .</span><span class="sxs-lookup"><span data-stu-id="3d5ca-113">Open the **Internet Information Services (IIS) Manager** applet.</span></span>

2. <span data-ttu-id="3d5ca-114">Rozbalte ovládací prvek TreeView v podokně **připojení** .</span><span class="sxs-lookup"><span data-stu-id="3d5ca-114">Expand the treeview in the **Connections** pane.</span></span> <span data-ttu-id="3d5ca-115">Vyberte uzel **fondy aplikací** .</span><span class="sxs-lookup"><span data-stu-id="3d5ca-115">Select the **Application Pools** node.</span></span>

3. <span data-ttu-id="3d5ca-116">Pokud chcete nastavit výchozí fond aplikací tak, aby používal .NET Framework 4 (což může způsobit problémy s nekompatibilitou s existujícími lokalitami), klikněte pravým tlačítkem myši na položku seznamu **DefaultAppPool** a vyberte **základní nastavení..** .</span><span class="sxs-lookup"><span data-stu-id="3d5ca-116">To set the default application pool to use .NET Framework 4 (which may cause incompatibility problems with existing sites), right-click the **DefaultAppPool** list item and select **Basic Settings…**.</span></span> <span data-ttu-id="3d5ca-117">Nastavte **verzi rozhraní .NET Framework** , která se má vyžádat, na **rozhraní .NET Framework v 4.0.30128** (nebo novější).</span><span class="sxs-lookup"><span data-stu-id="3d5ca-117">Set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span>

4. <span data-ttu-id="3d5ca-118">Pokud chcete vytvořit nový fond aplikací, který používá .NET Framework 4 (pro zachování kompatibility pro jiné aplikace), klikněte pravým tlačítkem myši na uzel **fondy aplikací** a vyberte **Přidat fond aplikací..** .</span><span class="sxs-lookup"><span data-stu-id="3d5ca-118">To create a new application pool that uses .NET Framework 4 (to preserve compatibility for other applications), right-click the **Application Pools** node and select **Add Application Pool…**.</span></span> <span data-ttu-id="3d5ca-119">Pojmenujte nový fond aplikací a nastavte **verzi rozhraní .NET Framework** , kterou si můžete stáhnout, do **rozhraní .NET Framework v 4.0.30128** (nebo novější).</span><span class="sxs-lookup"><span data-stu-id="3d5ca-119">Name the new application pool, and set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span> <span data-ttu-id="3d5ca-120">Po spuštění následujících kroků nastavení klikněte pravým tlačítkem myši na aplikaci **ServiceModelSamples** a vyberte možnost **Spravovat aplikaci**, **Upřesnit nastavení...** .</span><span class="sxs-lookup"><span data-stu-id="3d5ca-120">After running the setup steps below, right-click the **ServiceModelSamples** application and select **Manage Application**, **Advanced Settings…**.</span></span> <span data-ttu-id="3d5ca-121">Nastavte **fond aplikací** na nový fond aplikací.</span><span class="sxs-lookup"><span data-stu-id="3d5ca-121">Set the **Application Pool** to the new application pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3d5ca-122">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="3d5ca-122">The samples may already be installed on your computer.</span></span> <span data-ttu-id="3d5ca-123">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="3d5ca-123">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="3d5ca-124">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="3d5ca-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3d5ca-125">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="3d5ca-125">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`

<span data-ttu-id="3d5ca-126">Tato ukázka je založená na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), která implementuje službu kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="3d5ca-126">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="3d5ca-127">`ICalculator` kontrakt byl změněn jako `ICalculatorSession` smlouva, aby bylo možné provést sadu operací a přitom zachovat běžící výsledek.</span><span class="sxs-lookup"><span data-stu-id="3d5ca-127">The `ICalculator` contract has been modified as the `ICalculatorSession` contract to allow a set of operations to be performed, while keeping a running result.</span></span>

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

<span data-ttu-id="3d5ca-128">Služba udržuje stav pomocí funkce pro každého klienta jako více operací služby k provedení výpočtu.</span><span class="sxs-lookup"><span data-stu-id="3d5ca-128">The service maintains state, using the feature, for each client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="3d5ca-129">Klient může získat aktuální výsledek voláním `Result` a může vymazat výsledek na nulu voláním `Clear`.</span><span class="sxs-lookup"><span data-stu-id="3d5ca-129">The client can retrieve the current result by calling `Result` and can clear the result to zero by calling `Clear`.</span></span>

<span data-ttu-id="3d5ca-130">Služba používá relaci ASP.NET k uložení výsledku pro každou relaci klienta.</span><span class="sxs-lookup"><span data-stu-id="3d5ca-130">The service uses the ASP.NET session to store the result for each client session.</span></span> <span data-ttu-id="3d5ca-131">Díky tomu může služba udržovat běžící výsledek pro každého klienta napříč více voláními služby.</span><span class="sxs-lookup"><span data-stu-id="3d5ca-131">This allows the service to maintain the running result for each client across multiple calls to the service.</span></span>

> [!NOTE]
> <span data-ttu-id="3d5ca-132">Stav relace ASP.NET a relace WCF jsou velmi různé.</span><span class="sxs-lookup"><span data-stu-id="3d5ca-132">ASP.NET session state and WCF sessions are very different things.</span></span> <span data-ttu-id="3d5ca-133">Podrobnosti o relacích WCF najdete v tématu [relace](../../../../docs/framework/wcf/samples/session.md) .</span><span class="sxs-lookup"><span data-stu-id="3d5ca-133">See [Session](../../../../docs/framework/wcf/samples/session.md) for details on WCF sessions.</span></span>

<span data-ttu-id="3d5ca-134">Služba má závislost Intimate ve stavu relace ASP.NET a vyžaduje režim kompatibility ASP.NET pro správné fungování.</span><span class="sxs-lookup"><span data-stu-id="3d5ca-134">The service has an intimate dependency on ASP.NET session state and requires ASP.NET compatibility mode to function correctly.</span></span> <span data-ttu-id="3d5ca-135">Tyto požadavky jsou vyjádřeny deklarativně použitím atributu `AspNetCompatibilityRequirements`.</span><span class="sxs-lookup"><span data-stu-id="3d5ca-135">These requirements are expressed declaratively by applying the `AspNetCompatibilityRequirements` attribute.</span></span>

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

<span data-ttu-id="3d5ca-136">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="3d5ca-136">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="3d5ca-137">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="3d5ca-137">Press ENTER in the client window to shut down the client.</span></span>

```console
0, + 100, - 50, * 17.65, / 2 = 441.25
Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3d5ca-138">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="3d5ca-138">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="3d5ca-139">Ujistěte se, že jste provedli [jednorázovou proceduru nastavení Windows Communication Foundation ukázek](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3d5ca-139">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="3d5ca-140">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3d5ca-140">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="3d5ca-141">Po sestavení řešení spusťte soubor Setup. bat a nastavte aplikaci ServiceModelSamples ve službě IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="3d5ca-141">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in IIS 7.0.</span></span> <span data-ttu-id="3d5ca-142">Adresář ServiceModelSamples by se teď měl zobrazit jako aplikace IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="3d5ca-142">The ServiceModelSamples directory should now appear as an IIS 7.0 Application.</span></span>

4. <span data-ttu-id="3d5ca-143">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3d5ca-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3d5ca-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="3d5ca-144">See also</span></span>

- <span data-ttu-id="3d5ca-145">[Hostování technologie AppFabric a ukázky trvalosti](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="3d5ca-145">[AppFabric Hosting and Persistence Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
