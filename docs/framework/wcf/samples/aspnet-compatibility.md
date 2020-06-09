---
title: Režim kompatibility ASP.NET
ms.date: 03/30/2017
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
ms.openlocfilehash: 23930e0756d3fbefc28a8f650b5a056106145a50
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594709"
---
# <a name="aspnet-compatibility"></a><span data-ttu-id="95682-102">Režim kompatibility ASP.NET</span><span class="sxs-lookup"><span data-stu-id="95682-102">ASP.NET Compatibility</span></span>

<span data-ttu-id="95682-103">Tato ukázka předvádí, jak povolit režim kompatibility ASP.NET v Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="95682-103">This sample demonstrates how to enable ASP.NET Compatibility mode in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="95682-104">Služby běžící v režimu kompatibility ASP.NET se plně účastní kanálu aplikace ASP.NET a můžou využívat funkce ASP.NET, jako je například autorizace souborů a adres URL, stav relace a <xref:System.Web.HttpContext> Třída.</span><span class="sxs-lookup"><span data-stu-id="95682-104">Services running in ASP.NET Compatibility mode participate fully in the ASP.NET application pipeline and can make use of ASP.NET features such as file/URL authorization, session state, and the <xref:System.Web.HttpContext> class.</span></span> <span data-ttu-id="95682-105"><xref:System.Web.HttpContext>Třída umožňuje přístup k souborům cookie, relacím a dalším funkcím ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="95682-105">The <xref:System.Web.HttpContext> class allows access to cookies, sessions, and other ASP.NET features.</span></span> <span data-ttu-id="95682-106">Tento režim vyžaduje, aby vazby používaly přenos HTTP a samotná služba musí být hostovaná ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="95682-106">This mode requires that the bindings use the HTTP transport and the service itself must be hosted in IIS.</span></span>

<span data-ttu-id="95682-107">V této ukázce je klient Konzolová aplikace (spustitelný soubor) a služba je hostovaná ve službě Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="95682-107">In this sample, the client is a console application (an executable) and the service is hosted in Internet Information Services (IIS).</span></span>

> [!NOTE]
> <span data-ttu-id="95682-108">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="95682-108">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="95682-109">Tato ukázka vyžaduje, aby byl fond aplikací .NET Framework 4 spuštěn.</span><span class="sxs-lookup"><span data-stu-id="95682-109">This sample requires a .NET Framework 4 application pool in order to run.</span></span> <span data-ttu-id="95682-110">Chcete-li vytvořit nový fond aplikací nebo upravit výchozí fond aplikací, postupujte podle těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="95682-110">To create a new application pool, or to modify the default application pool, follow these steps.</span></span>

1. <span data-ttu-id="95682-111">Otevřete **Ovládací panely**.</span><span class="sxs-lookup"><span data-stu-id="95682-111">Open **Control Panel**.</span></span>  <span data-ttu-id="95682-112">V části **systém a záhlaví zabezpečení** otevřete aplet **Nástroje pro správu** .</span><span class="sxs-lookup"><span data-stu-id="95682-112">Open the **Administrative Tools** applet under the **System and Security** heading.</span></span> <span data-ttu-id="95682-113">Otevřete applet **správce Internetová informační služba (IIS)** .</span><span class="sxs-lookup"><span data-stu-id="95682-113">Open the **Internet Information Services (IIS) Manager** applet.</span></span>

2. <span data-ttu-id="95682-114">Rozbalte ovládací prvek TreeView v podokně **připojení** .</span><span class="sxs-lookup"><span data-stu-id="95682-114">Expand the treeview in the **Connections** pane.</span></span> <span data-ttu-id="95682-115">Vyberte uzel **fondy aplikací** .</span><span class="sxs-lookup"><span data-stu-id="95682-115">Select the **Application Pools** node.</span></span>

3. <span data-ttu-id="95682-116">Pokud chcete nastavit výchozí fond aplikací tak, aby používal .NET Framework 4 (což může způsobit problémy s nekompatibilitou s existujícími lokalitami), klikněte pravým tlačítkem myši na položku seznamu **DefaultAppPool** a vyberte **základní nastavení..**.</span><span class="sxs-lookup"><span data-stu-id="95682-116">To set the default application pool to use .NET Framework 4 (which may cause incompatibility problems with existing sites), right-click the **DefaultAppPool** list item and select **Basic Settings…**.</span></span> <span data-ttu-id="95682-117">Nastavte **verzi rozhraní .NET Framework** , která se má vyžádat, na **rozhraní .NET Framework v 4.0.30128** (nebo novější).</span><span class="sxs-lookup"><span data-stu-id="95682-117">Set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span>

4. <span data-ttu-id="95682-118">Pokud chcete vytvořit nový fond aplikací, který používá .NET Framework 4 (pro zachování kompatibility pro jiné aplikace), klikněte pravým tlačítkem myši na uzel **fondy aplikací** a vyberte **Přidat fond aplikací..**.</span><span class="sxs-lookup"><span data-stu-id="95682-118">To create a new application pool that uses .NET Framework 4 (to preserve compatibility for other applications), right-click the **Application Pools** node and select **Add Application Pool…**.</span></span> <span data-ttu-id="95682-119">Pojmenujte nový fond aplikací a nastavte **verzi rozhraní .NET Framework** , kterou si můžete stáhnout, do **rozhraní .NET Framework v 4.0.30128** (nebo novější).</span><span class="sxs-lookup"><span data-stu-id="95682-119">Name the new application pool, and set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span> <span data-ttu-id="95682-120">Po spuštění následujících kroků nastavení klikněte pravým tlačítkem myši na aplikaci **ServiceModelSamples** a vyberte možnost **Spravovat aplikaci**, **Upřesnit nastavení...**.</span><span class="sxs-lookup"><span data-stu-id="95682-120">After running the setup steps below, right-click the **ServiceModelSamples** application and select **Manage Application**, **Advanced Settings…**.</span></span> <span data-ttu-id="95682-121">Nastavte **fond aplikací** na nový fond aplikací.</span><span class="sxs-lookup"><span data-stu-id="95682-121">Set the **Application Pool** to the new application pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="95682-122">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="95682-122">The samples may already be installed on your computer.</span></span> <span data-ttu-id="95682-123">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="95682-123">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="95682-124">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="95682-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="95682-125">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="95682-125">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`

<span data-ttu-id="95682-126">Tato ukázka je založená na [Začínáme](getting-started-sample.md), která implementuje službu kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="95682-126">This sample is based on the [Getting Started](getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="95682-127">`ICalculator`Smlouva byla upravena jako `ICalculatorSession` kontrakt, aby bylo možné provést sadu operací, a přitom zachovat běžící výsledek.</span><span class="sxs-lookup"><span data-stu-id="95682-127">The `ICalculator` contract has been modified as the `ICalculatorSession` contract to allow a set of operations to be performed, while keeping a running result.</span></span>

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

<span data-ttu-id="95682-128">Služba udržuje stav pomocí funkce pro každého klienta jako více operací služby k provedení výpočtu.</span><span class="sxs-lookup"><span data-stu-id="95682-128">The service maintains state, using the feature, for each client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="95682-129">Klient může načíst aktuální výsledek voláním `Result` a může vymazat výsledek na nulu voláním `Clear` .</span><span class="sxs-lookup"><span data-stu-id="95682-129">The client can retrieve the current result by calling `Result` and can clear the result to zero by calling `Clear`.</span></span>

<span data-ttu-id="95682-130">Služba používá relaci ASP.NET k uložení výsledku pro každou relaci klienta.</span><span class="sxs-lookup"><span data-stu-id="95682-130">The service uses the ASP.NET session to store the result for each client session.</span></span> <span data-ttu-id="95682-131">Díky tomu může služba udržovat běžící výsledek pro každého klienta napříč více voláními služby.</span><span class="sxs-lookup"><span data-stu-id="95682-131">This allows the service to maintain the running result for each client across multiple calls to the service.</span></span>

> [!NOTE]
> <span data-ttu-id="95682-132">Stav relace ASP.NET a relace WCF jsou velmi různé.</span><span class="sxs-lookup"><span data-stu-id="95682-132">ASP.NET session state and WCF sessions are very different things.</span></span> <span data-ttu-id="95682-133">Podrobnosti o relacích WCF najdete v tématu [relace](session.md) .</span><span class="sxs-lookup"><span data-stu-id="95682-133">See [Session](session.md) for details on WCF sessions.</span></span>

<span data-ttu-id="95682-134">Služba má závislost Intimate ve stavu relace ASP.NET a vyžaduje režim kompatibility ASP.NET pro správné fungování.</span><span class="sxs-lookup"><span data-stu-id="95682-134">The service has an intimate dependency on ASP.NET session state and requires ASP.NET compatibility mode to function correctly.</span></span> <span data-ttu-id="95682-135">Tyto požadavky jsou vyjádřeny deklarativně použitím `AspNetCompatibilityRequirements` atributu.</span><span class="sxs-lookup"><span data-stu-id="95682-135">These requirements are expressed declaratively by applying the `AspNetCompatibilityRequirements` attribute.</span></span>

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

<span data-ttu-id="95682-136">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="95682-136">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="95682-137">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="95682-137">Press ENTER in the client window to shut down the client.</span></span>

```console
0, + 100, - 50, * 17.65, / 2 = 441.25
Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="95682-138">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="95682-138">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="95682-139">Ujistěte se, že jste provedli [jednorázovou proceduru nastavení Windows Communication Foundation ukázek](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="95682-139">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="95682-140">Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="95682-140">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="95682-141">Po sestavení řešení spusťte soubor Setup. bat a nastavte aplikaci ServiceModelSamples ve službě IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="95682-141">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in IIS 7.0.</span></span> <span data-ttu-id="95682-142">Adresář ServiceModelSamples by se teď měl zobrazit jako aplikace IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="95682-142">The ServiceModelSamples directory should now appear as an IIS 7.0 Application.</span></span>

4. <span data-ttu-id="95682-143">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="95682-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="95682-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="95682-144">See also</span></span>

- <span data-ttu-id="95682-145">[Hostování technologie AppFabric a ukázky trvalosti](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="95682-145">[AppFabric Hosting and Persistence Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
