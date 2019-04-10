---
title: 'Kurz: Definování kontraktu služby Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: a1908339460191fcb81d03d45c56dd57b2cf4c4e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228390"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="5c4dc-102">Kurz: Definování kontraktu služby Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="5c4dc-102">Tutorial: Define a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="5c4dc-103">Tento kurz popisuje prvních pět úloh potřebných k vytvoření základní aplikace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="5c4dc-103">This tutorial describes the first of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="5c4dc-104">Přehled v kurzech, naleznete v tématu [kurzu: Začínáme s aplikacemi Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="5c4dc-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="5c4dc-105">Při vytváření služeb WCF je první úkol k definování kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="5c4dc-105">When you create a WCF service, your first task is to define a service contract.</span></span> <span data-ttu-id="5c4dc-106">Kontrakt služby specifikuje, jaké operace služba podporuje.</span><span class="sxs-lookup"><span data-stu-id="5c4dc-106">The service contract specifies what operations the service supports.</span></span> <span data-ttu-id="5c4dc-107">Operace můžete představit jako metodu webové služby.</span><span class="sxs-lookup"><span data-stu-id="5c4dc-107">An operation can be thought of as a Web service method.</span></span> <span data-ttu-id="5c4dc-108">Vytváření kontraktů služby tak, že definujete Vizuálu C# nebo rozhraní jazyka Visual Basic (VB).</span><span class="sxs-lookup"><span data-stu-id="5c4dc-108">You create service contracts by defining a Visual C# or Visual Basic (VB) interface.</span></span> <span data-ttu-id="5c4dc-109">Rozhraní má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="5c4dc-109">An interface has the following characteristics:</span></span>

- <span data-ttu-id="5c4dc-110">Každá metoda v rozhraní odpovídá konkrétní operaci služby.</span><span class="sxs-lookup"><span data-stu-id="5c4dc-110">Each method in the interface corresponds to a specific service operation.</span></span> 
- <span data-ttu-id="5c4dc-111">Pro každé rozhraní, musíte použít <xref:System.ServiceModel.ServiceContractAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="5c4dc-111">For each interface, you must apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span>
- <span data-ttu-id="5c4dc-112">Pro každou operaci/metodu, musíte použít <xref:System.ServiceModel.OperationContractAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="5c4dc-112">For each operation/method, you must apply the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span> 

<span data-ttu-id="5c4dc-113">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="5c4dc-113">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="5c4dc-114">Vytvoření **knihovny služby WCF** projektu.</span><span class="sxs-lookup"><span data-stu-id="5c4dc-114">Create a **WCF Service Library** project.</span></span>
> - <span data-ttu-id="5c4dc-115">Definujte rozhraní kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="5c4dc-115">Define a service contract interface.</span></span>

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a><span data-ttu-id="5c4dc-116">Vytvořte projekt knihovny služby WCF a definování rozhraní kontraktu služby</span><span class="sxs-lookup"><span data-stu-id="5c4dc-116">Create a WCF Service Library project and define a service contract interface</span></span>

1. <span data-ttu-id="5c4dc-117">Otevřít Visual Studio jako správce.</span><span class="sxs-lookup"><span data-stu-id="5c4dc-117">Open Visual Studio as an administrator.</span></span> <span data-ttu-id="5c4dc-118">Pokud chcete udělat, vyberte program sady Visual Studio v **Start** nabídky a pak vyberte **Další** > **spustit jako správce** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="5c4dc-118">To do so, select the Visual Studio program in the **Start** menu, and then select **More** > **Run as administrator** from the shortcut menu.</span></span>

2. <span data-ttu-id="5c4dc-119">Vytvoření **knihovny služby WCF** projektu.</span><span class="sxs-lookup"><span data-stu-id="5c4dc-119">Create a **WCF Service Library** project.</span></span>

   1. <span data-ttu-id="5c4dc-120">Z **souboru** nabídce vyberte možnost **nový** > **projektu**.</span><span class="sxs-lookup"><span data-stu-id="5c4dc-120">From the **File** menu, select **New** > **Project**.</span></span>

   2. <span data-ttu-id="5c4dc-121">V **nový projekt** na levé straně dialogového okna rozbalte **Visual C#** nebo **jazyka Visual Basic**a pak vyberte **WCF** kategorie.</span><span class="sxs-lookup"><span data-stu-id="5c4dc-121">In the **New Project** dialog, on the left-hand side, expand **Visual C#** or **Visual Basic**, and then select the **WCF** category.</span></span> <span data-ttu-id="5c4dc-122">Visual Studio zobrazí seznam šablon projektů v části System center okna.</span><span class="sxs-lookup"><span data-stu-id="5c4dc-122">Visual Studio displays a list of project templates in the center section of the window.</span></span> <span data-ttu-id="5c4dc-123">Vyberte **knihovny služby WCF**.</span><span class="sxs-lookup"><span data-stu-id="5c4dc-123">Select **WCF Service Library**.</span></span>

      > [!NOTE]
      > <span data-ttu-id="5c4dc-124">Pokud se nezobrazí **WCF** kategorii šablony projektu, budete muset nainstalovat **Windows Communication Foundation** komponentu sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5c4dc-124">If you don't see the **WCF** project template category, you may need to install the **Windows Communication Foundation** component of Visual Studio.</span></span> <span data-ttu-id="5c4dc-125">V **nový projekt** dialogové okno, vyberte **otevřít instalační program Visual Studio** odkazu na levé straně.</span><span class="sxs-lookup"><span data-stu-id="5c4dc-125">In the **New Project** dialog box, select the **Open Visual Studio Installer** link on the left side.</span></span> <span data-ttu-id="5c4dc-126">Vyberte **jednotlivé komponenty** kartu a potom najděte a vyberte **Windows Communication Foundation** pod **vývojových aktivit** kategorie.</span><span class="sxs-lookup"><span data-stu-id="5c4dc-126">Select the **Individual components** tab, and then find and select **Windows Communication Foundation** under the **Development activities** category.</span></span> <span data-ttu-id="5c4dc-127">Zvolte **změnit** zahájíte instalaci komponenty.</span><span class="sxs-lookup"><span data-stu-id="5c4dc-127">Choose **Modify** to begin installing the component.</span></span>

   3. <span data-ttu-id="5c4dc-128">V dolní části okna, zadejte *GettingStartedLib* pro **název** a *GettingStarted* pro **název řešení**.</span><span class="sxs-lookup"><span data-stu-id="5c4dc-128">In the bottom section of the window, enter *GettingStartedLib* for the **Name** and *GettingStarted* for the **Solution name**.</span></span> 

   4. <span data-ttu-id="5c4dc-129">Vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="5c4dc-129">Select **OK**.</span></span>

      <span data-ttu-id="5c4dc-130">Visual Studio vytvoří projekt, který má tři soubory: *IService1.cs* (nebo *IService1.vb* pro projekt jazyka Visual Basic), *Service1.cs* (nebo *Service1.vb* pro projekt jazyka Visual Basic), a  *App.config*. Visual Studio definuje tyto soubory následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="5c4dc-130">Visual Studio creates the project, which has three files: *IService1.cs* (or *IService1.vb* for a Visual Basic project), *Service1.cs* (or *Service1.vb* for a Visual Basic project), and *App.config*. Visual Studio defines these files as follows:</span></span> 
      - <span data-ttu-id="5c4dc-131">*IService1* soubor obsahuje výchozí definici kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="5c4dc-131">The *IService1* file contains the default definition of the service contract.</span></span> 
      - <span data-ttu-id="5c4dc-132">*Service1* soubor obsahuje výchozí implementace kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="5c4dc-132">The *Service1* file contains the default implementation of the service contract.</span></span> 
      - <span data-ttu-id="5c4dc-133">*App.config* soubor obsahuje informace o konfiguraci potřebné k načtení výchozí služby pomocí nástroje Visual Studio WCF služby hostitele.</span><span class="sxs-lookup"><span data-stu-id="5c4dc-133">The *App.config* file contains the configuration info needed to load the default service with the Visual Studio WCF Service Host tool.</span></span> <span data-ttu-id="5c4dc-134">Další informace o nástroji pro hostitele služby WCF najdete v tématu [hostitel služby WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).</span><span class="sxs-lookup"><span data-stu-id="5c4dc-134">For more information about the WCF Service Host tool, see [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).</span></span>

      > [!NOTE]
      > <span data-ttu-id="5c4dc-135">Pokud jste nainstalovali aplikaci Visual Studio pomocí nastavení prostředí pro vývojáře jazyka Visual Basic, může být skrytá řešení.</span><span class="sxs-lookup"><span data-stu-id="5c4dc-135">If you installed Visual Studio with Visual Basic developer environment settings, the solution might be hidden.</span></span> <span data-ttu-id="5c4dc-136">Pokud je to tento případ, vyberte **možnosti** z **nástroje** nabídce pak vyberte **projekty a řešení** > **Obecné** v **možnosti** okna.</span><span class="sxs-lookup"><span data-stu-id="5c4dc-136">If this is the case, select **Options** from the **Tools** menu, then select **Projects and Solutions** > **General** in the **Options** window.</span></span> <span data-ttu-id="5c4dc-137">Vyberte **vždy zobrazit řešení**.</span><span class="sxs-lookup"><span data-stu-id="5c4dc-137">Select **Always show solution**.</span></span> <span data-ttu-id="5c4dc-138">Kromě toho ověřte, že **uložit nové projekty při vytvoření** zaškrtnuto.</span><span class="sxs-lookup"><span data-stu-id="5c4dc-138">Also, verify that **Save new projects when created** is selected.</span></span>

3. <span data-ttu-id="5c4dc-139">Z **Průzkumníka řešení**, otevřete **IService1.cs** nebo **IService1.vb** souboru a jeho kódu nahraďte následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="5c4dc-139">From **Solution Explorer**, open the **IService1.cs** or **IService1.vb** file, and replace its code with the following code:</span></span>

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

     <span data-ttu-id="5c4dc-140">Tento kontrakt definuje online kalkulačku.</span><span class="sxs-lookup"><span data-stu-id="5c4dc-140">This contract defines an online calculator.</span></span> <span data-ttu-id="5c4dc-141">Všimněte si, že `ICalculator` rozhraní je označeno příznakem s <xref:System.ServiceModel.ServiceContractAttribute> atribut (zjednodušené jako `ServiceContract`).</span><span class="sxs-lookup"><span data-stu-id="5c4dc-141">Notice the `ICalculator` interface is marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute (simplified as `ServiceContract`).</span></span> <span data-ttu-id="5c4dc-142">Tento atribut definuje obor názvů k rozlišení názvu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="5c4dc-142">This attribute defines a namespace to disambiguate the contract name.</span></span> <span data-ttu-id="5c4dc-143">Kód označuje každá operace kalkulačky s <xref:System.ServiceModel.OperationContractAttribute> atribut (zjednodušené jako `OperationContract`).</span><span class="sxs-lookup"><span data-stu-id="5c4dc-143">The code marks each calculator operation with the <xref:System.ServiceModel.OperationContractAttribute> attribute (simplified as `OperationContract`).</span></span>

## <a name="next-steps"></a><span data-ttu-id="5c4dc-144">Další kroky</span><span class="sxs-lookup"><span data-stu-id="5c4dc-144">Next steps</span></span>

<span data-ttu-id="5c4dc-145">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="5c4dc-145">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="5c4dc-146">Vytvořte projekt knihovny služby WCF.</span><span class="sxs-lookup"><span data-stu-id="5c4dc-146">Create a WCF Service Library project.</span></span>
> - <span data-ttu-id="5c4dc-147">Definujte rozhraní kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="5c4dc-147">Define a service contract interface.</span></span>

<span data-ttu-id="5c4dc-148">Přejděte k dalšímu kurzu se naučíte implementace kontraktu služby WCF.</span><span class="sxs-lookup"><span data-stu-id="5c4dc-148">Advance to the next tutorial to learn how to implement the WCF service contract.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5c4dc-149">Kurz: Implementace kontraktu služby WCF</span><span class="sxs-lookup"><span data-stu-id="5c4dc-149">Tutorial: Implement a WCF service contract</span></span>](how-to-implement-a-wcf-contract.md)
