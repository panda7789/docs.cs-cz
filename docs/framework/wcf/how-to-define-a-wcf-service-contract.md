---
title: 'Kurz: Definování smlouvy o poskytování služeb Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: 7c1c42c4f22a1a9627c147440e8e198551470b7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184095"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="d85f8-102">Kurz: Definování smlouvy o poskytování služeb Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="d85f8-102">Tutorial: Define a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="d85f8-103">Tento kurz popisuje první z pěti úloh potřebných k vytvoření základní aplikace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d85f8-103">This tutorial describes the first of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="d85f8-104">Přehled výukových programů najdete v [tématu Výuka: Začínáme s aplikacemi Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="d85f8-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="d85f8-105">Při vytváření služby WCF je vaším prvním úkolem definovat servisní smlouvu.</span><span class="sxs-lookup"><span data-stu-id="d85f8-105">When you create a WCF service, your first task is to define a service contract.</span></span> <span data-ttu-id="d85f8-106">Servisní smlouva určuje, jaké operace služba podporuje.</span><span class="sxs-lookup"><span data-stu-id="d85f8-106">The service contract specifies what operations the service supports.</span></span> <span data-ttu-id="d85f8-107">Operaci lze považovat za metodu webové služby.</span><span class="sxs-lookup"><span data-stu-id="d85f8-107">An operation can be thought of as a Web service method.</span></span> <span data-ttu-id="d85f8-108">Servisní smlouvy vytvoříte definováním rozhraní jazyka C# nebo jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d85f8-108">You create service contracts by defining a C# or Visual Basic interface.</span></span> <span data-ttu-id="d85f8-109">Rozhraní má následující charakteristiky:</span><span class="sxs-lookup"><span data-stu-id="d85f8-109">An interface has the following characteristics:</span></span>

- <span data-ttu-id="d85f8-110">Každá metoda v rozhraní odpovídá konkrétní operaci služby.</span><span class="sxs-lookup"><span data-stu-id="d85f8-110">Each method in the interface corresponds to a specific service operation.</span></span>
- <span data-ttu-id="d85f8-111">Pro každé rozhraní je <xref:System.ServiceModel.ServiceContractAttribute> nutné použít atribut.</span><span class="sxs-lookup"><span data-stu-id="d85f8-111">For each interface, you must apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span>
- <span data-ttu-id="d85f8-112">Pro každou operaci/metodu je <xref:System.ServiceModel.OperationContractAttribute> nutné použít atribut.</span><span class="sxs-lookup"><span data-stu-id="d85f8-112">For each operation/method, you must apply the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span>

<span data-ttu-id="d85f8-113">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="d85f8-113">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="d85f8-114">Vytvořte projekt **knihovny služeb WCF.**</span><span class="sxs-lookup"><span data-stu-id="d85f8-114">Create a **WCF Service Library** project.</span></span>
> - <span data-ttu-id="d85f8-115">Definujte rozhraní servisní smlouvy.</span><span class="sxs-lookup"><span data-stu-id="d85f8-115">Define a service contract interface.</span></span>

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a><span data-ttu-id="d85f8-116">Vytvoření projektu knihovny služeb WCF a definování rozhraní servisní smlouvy</span><span class="sxs-lookup"><span data-stu-id="d85f8-116">Create a WCF Service Library project and define a service contract interface</span></span>

1. <span data-ttu-id="d85f8-117">Otevřete Visual Studio jako správce.</span><span class="sxs-lookup"><span data-stu-id="d85f8-117">Open Visual Studio as an administrator.</span></span> <span data-ttu-id="d85f8-118">Chcete-li tak učinit, vyberte program sady Visual Studio v nabídce **Start** a v místní nabídce vyberte možnost **Další** > **spuštění jako správce.**</span><span class="sxs-lookup"><span data-stu-id="d85f8-118">To do so, select the Visual Studio program in the **Start** menu, and then select **More** > **Run as administrator** from the shortcut menu.</span></span>

2. <span data-ttu-id="d85f8-119">Vytvořte projekt **knihovny služeb WCF.**</span><span class="sxs-lookup"><span data-stu-id="d85f8-119">Create a **WCF Service Library** project.</span></span>

   1. <span data-ttu-id="d85f8-120">V nabídce **Soubor** vyberte **Nový** > **projekt**.</span><span class="sxs-lookup"><span data-stu-id="d85f8-120">From the **File** menu, select **New** > **Project**.</span></span>

   2. <span data-ttu-id="d85f8-121">V dialogovém okně **Nový projekt** rozbalte na levé straně **položku Visual C#** nebo **Visual Basic**a vyberte kategorii **WCF.**</span><span class="sxs-lookup"><span data-stu-id="d85f8-121">In the **New Project** dialog, on the left-hand side, expand **Visual C#** or **Visual Basic**, and then select the **WCF** category.</span></span> <span data-ttu-id="d85f8-122">Visual Studio zobrazí seznam šablon projektů ve středové části okna.</span><span class="sxs-lookup"><span data-stu-id="d85f8-122">Visual Studio displays a list of project templates in the center section of the window.</span></span> <span data-ttu-id="d85f8-123">Vyberte **knihovnu služeb WCF**.</span><span class="sxs-lookup"><span data-stu-id="d85f8-123">Select **WCF Service Library**.</span></span>

      > [!NOTE]
      > <span data-ttu-id="d85f8-124">Pokud nevidíte kategorii šablony projektu **WCF,** bude pravděpodobně nutné nainstalovat součást **Windows Communication Foundation** sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d85f8-124">If you don't see the **WCF** project template category, you may need to install the **Windows Communication Foundation** component of Visual Studio.</span></span> <span data-ttu-id="d85f8-125">V dialogovém okně **Nový projekt** vyberte na levé straně odkaz Otevřít instalační program sady **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="d85f8-125">In the **New Project** dialog box, select the **Open Visual Studio Installer** link on the left side.</span></span> <span data-ttu-id="d85f8-126">Vyberte kartu **Jednotlivé součásti** a v kategorii **Aktivity vývoje** vyberte a vyberte **Windows Communication Foundation.**</span><span class="sxs-lookup"><span data-stu-id="d85f8-126">Select the **Individual components** tab, and then find and select **Windows Communication Foundation** under the **Development activities** category.</span></span> <span data-ttu-id="d85f8-127">Chcete-li začít instalovat komponentu, zvolte **Změnit.**</span><span class="sxs-lookup"><span data-stu-id="d85f8-127">Choose **Modify** to begin installing the component.</span></span>

   3. <span data-ttu-id="d85f8-128">V dolní části okna zadejte *GettingStartedLib* pro **název** a *GettingStarted* pro **název řešení**.</span><span class="sxs-lookup"><span data-stu-id="d85f8-128">In the bottom section of the window, enter *GettingStartedLib* for the **Name** and *GettingStarted* for the **Solution name**.</span></span>

   4. <span data-ttu-id="d85f8-129">Vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="d85f8-129">Select **OK**.</span></span>

      <span data-ttu-id="d85f8-130">Visual Studio vytvoří projekt, který má tři soubory: *IService1.cs* (nebo *IService1.vb* pro projekt jazyka), *Service1.cs* (nebo *Service1.vb* pro projekt jazyka Visual Basic) a *App.config*. Visual Studio definuje tyto soubory takto:</span><span class="sxs-lookup"><span data-stu-id="d85f8-130">Visual Studio creates the project, which has three files: *IService1.cs* (or *IService1.vb* for a Visual Basic project), *Service1.cs* (or *Service1.vb* for a Visual Basic project), and *App.config*. Visual Studio defines these files as follows:</span></span>
      - <span data-ttu-id="d85f8-131">Soubor *IService1* obsahuje výchozí definici servisní smlouvy.</span><span class="sxs-lookup"><span data-stu-id="d85f8-131">The *IService1* file contains the default definition of the service contract.</span></span>
      - <span data-ttu-id="d85f8-132">Soubor *Service1* obsahuje výchozí implementaci servisní smlouvy.</span><span class="sxs-lookup"><span data-stu-id="d85f8-132">The *Service1* file contains the default implementation of the service contract.</span></span>
      - <span data-ttu-id="d85f8-133">Soubor *App.config* obsahuje informace o konfiguraci potřebné k načtení výchozí služby pomocí nástroje Host služby WCF sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d85f8-133">The *App.config* file contains the configuration info needed to load the default service with the Visual Studio WCF Service Host tool.</span></span> <span data-ttu-id="d85f8-134">Další informace o nástroji WCF Service Host naleznete v tématu [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).</span><span class="sxs-lookup"><span data-stu-id="d85f8-134">For more information about the WCF Service Host tool, see [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).</span></span>

      > [!NOTE]
      > <span data-ttu-id="d85f8-135">Pokud jste nainstalovali Visual Studio s nastavením prostředí pro vývojáře jazyka, řešení může být skryté.</span><span class="sxs-lookup"><span data-stu-id="d85f8-135">If you installed Visual Studio with Visual Basic developer environment settings, the solution might be hidden.</span></span> <span data-ttu-id="d85f8-136">Pokud se jedná o tento případ, vyberte **možnosti** z nabídky **Nástroje** a v okně **Možnosti** vyberte**Projekty** **a obecně řešení.** > </span><span class="sxs-lookup"><span data-stu-id="d85f8-136">If this is the case, select **Options** from the **Tools** menu, then select **Projects and Solutions** > **General** in the **Options** window.</span></span> <span data-ttu-id="d85f8-137">Vyberte **možnost Vždy zobrazit řešení**.</span><span class="sxs-lookup"><span data-stu-id="d85f8-137">Select **Always show solution**.</span></span> <span data-ttu-id="d85f8-138">Ověřte také, zda je vybrána možnost **Uložit nové projekty při vytvoření.**</span><span class="sxs-lookup"><span data-stu-id="d85f8-138">Also, verify that **Save new projects when created** is selected.</span></span>

3. <span data-ttu-id="d85f8-139">V **Průzkumníku řešení**otevřete soubor **IService1.cs** nebo **IService1.vb** a nahraďte jeho kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="d85f8-139">From **Solution Explorer**, open the **IService1.cs** or **IService1.vb** file, and replace its code with the following code:</span></span>

    ```csharp
    using System;
    using System.ServiceModel;

    namespace GettingStartedLib
    {
            [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
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
    }
    ```

    ```vb
    Imports System.ServiceModel

    Namespace GettingStartedLib

        <ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _
        Public Interface ICalculator

            <OperationContract()> _
            Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double
        End Interface
    End Namespace
    ```

     <span data-ttu-id="d85f8-140">Tato smlouva definuje online kalkulačku.</span><span class="sxs-lookup"><span data-stu-id="d85f8-140">This contract defines an online calculator.</span></span> <span data-ttu-id="d85f8-141">Všimněte `ICalculator` si, že <xref:System.ServiceModel.ServiceContractAttribute> rozhraní je `ServiceContract`označeno atributem (zjednodušeno jako ).</span><span class="sxs-lookup"><span data-stu-id="d85f8-141">Notice the `ICalculator` interface is marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute (simplified as `ServiceContract`).</span></span> <span data-ttu-id="d85f8-142">Tento atribut definuje obor názvů, aby se název smlouvy rozpodomoval.</span><span class="sxs-lookup"><span data-stu-id="d85f8-142">This attribute defines a namespace to disambiguate the contract name.</span></span> <span data-ttu-id="d85f8-143">Kód označí každou <xref:System.ServiceModel.OperationContractAttribute> operaci kalkulačky `OperationContract`atributem (zjednodušeným jako).</span><span class="sxs-lookup"><span data-stu-id="d85f8-143">The code marks each calculator operation with the <xref:System.ServiceModel.OperationContractAttribute> attribute (simplified as `OperationContract`).</span></span>

## <a name="next-steps"></a><span data-ttu-id="d85f8-144">Další kroky</span><span class="sxs-lookup"><span data-stu-id="d85f8-144">Next steps</span></span>

<span data-ttu-id="d85f8-145">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="d85f8-145">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="d85f8-146">Vytvořte projekt knihovny služeb WCF.</span><span class="sxs-lookup"><span data-stu-id="d85f8-146">Create a WCF Service Library project.</span></span>
> - <span data-ttu-id="d85f8-147">Definujte rozhraní servisní smlouvy.</span><span class="sxs-lookup"><span data-stu-id="d85f8-147">Define a service contract interface.</span></span>

<span data-ttu-id="d85f8-148">Přejdete k dalšímu kurzu, který se dozvíte, jak implementovat servisní smlouvu WCF.</span><span class="sxs-lookup"><span data-stu-id="d85f8-148">Advance to the next tutorial to learn how to implement the WCF service contract.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d85f8-149">Kurz: Implementace smlouvy o poskytování služeb WCF</span><span class="sxs-lookup"><span data-stu-id="d85f8-149">Tutorial: Implement a WCF service contract</span></span>](how-to-implement-a-wcf-contract.md)
