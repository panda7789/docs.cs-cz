---
title: Použití aktivity interoperability v pracovním postupu rozhraní .NET Framework 4
ms.date: 03/30/2017
ms.assetid: 9bb747f0-eb33-4f70-84cd-317382372dcd
ms.openlocfilehash: 02eeaf5bb7ff484ba5982197fc395e247cd5a87f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43528107"
---
# <a name="using-the-interop-activity-in-a-net-framework-4-workflow"></a><span data-ttu-id="118f5-102">Použití aktivity interoperability v pracovním postupu rozhraní .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="118f5-102">Using the Interop Activity in a .NET Framework 4 Workflow</span></span>
<span data-ttu-id="118f5-103">Aktivity vytvořené pomocí [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] nebo [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] lze použít v [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] pracovního postupu pomocí <xref:System.Activities.Statements.Interop> aktivity.</span><span class="sxs-lookup"><span data-stu-id="118f5-103">Activities created using [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] or [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] can be used in a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow by using the <xref:System.Activities.Statements.Interop> activity.</span></span> <span data-ttu-id="118f5-104">Toto téma obsahuje přehled používání <xref:System.Activities.Statements.Interop> aktivity.</span><span class="sxs-lookup"><span data-stu-id="118f5-104">This topic provides an overview of using the <xref:System.Activities.Statements.Interop> activity.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="118f5-105"><xref:System.Activities.Statements.Interop> Aktivity se nezobrazí v panelu nástrojů návrháře postupu, pokud projekt pracovního postupu neobsahuje jeho **Cílová architektura** nastavení **rozhraní .net Framework 4** nebo novější.</span><span class="sxs-lookup"><span data-stu-id="118f5-105">The <xref:System.Activities.Statements.Interop> activity does not appear in the workflow designer toolbox unless the workflow's project has its **Target Framework** setting set to **.Net Framework 4** or later.</span></span>  
  
## <a name="using-the-interop-activity-in-net-framework-45-workflows"></a><span data-ttu-id="118f5-106">Použití aktivity interoperability v pracovních postupech rozhraní .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="118f5-106">Using the Interop Activity in .NET Framework 4.5 Workflows</span></span>  
 <span data-ttu-id="118f5-107">V tomto tématu [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] obsahující vytvoření knihovny aktivit `DiscountCalculator` aktivity.</span><span class="sxs-lookup"><span data-stu-id="118f5-107">In this topic, a [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] activity library is created that contains a `DiscountCalculator` activity.</span></span> <span data-ttu-id="118f5-108">`DiscountCalculator` Vypočítá a uplatnit tak slevu na základě částky nákupu a skládá se z <xref:System.Workflow.Activities.SequenceActivity> , která obsahuje <xref:System.Workflow.Activities.PolicyActivity>.</span><span class="sxs-lookup"><span data-stu-id="118f5-108">The `DiscountCalculator` calculates a discount based on a purchase amount and consists of a <xref:System.Workflow.Activities.SequenceActivity> that contains a <xref:System.Workflow.Activities.PolicyActivity>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="118f5-109">[!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] Používá aktivita vytvořená v tomto tématu <xref:System.Workflow.Activities.PolicyActivity> implementovat logiku aktivity.</span><span class="sxs-lookup"><span data-stu-id="118f5-109">The [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] activity created in this topic uses a <xref:System.Workflow.Activities.PolicyActivity> to implement the logic of the activity.</span></span> <span data-ttu-id="118f5-110">To není nutné používat vlastní [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] aktivity nebo <xref:System.Activities.Statements.Interop> aktivitu, chcete-li použít pravidla v [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="118f5-110">It is not required to use a custom [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] activity or the <xref:System.Activities.Statements.Interop> activity in order to use rules in a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow.</span></span> <span data-ttu-id="118f5-111">Příklad použití pravidel v [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] pracovního postupu bez použití <xref:System.Activities.Statements.Interop> aktivity, najdete v článku [aktivita Policy v rozhraní .NET Framework 4.5](../../../docs/framework/windows-workflow-foundation/samples/policy-activity-in-net-framework-4-5.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="118f5-111">For an example of using rules in a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow without using the <xref:System.Activities.Statements.Interop> activity, see the [Policy Activity in .NET Framework 4.5](../../../docs/framework/windows-workflow-foundation/samples/policy-activity-in-net-framework-4-5.md) sample.</span></span>  
  
#### <a name="to-create-the-net-framework-35-activity-library-project"></a><span data-ttu-id="118f5-112">Vytvoření projektu knihovny aktivit rozhraní .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="118f5-112">To create the .NET Framework 3.5 activity library project</span></span>  
  
1.  <span data-ttu-id="118f5-113">Otevřít [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] a vyberte **nový** a potom **projektu...**</span><span class="sxs-lookup"><span data-stu-id="118f5-113">Open [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] and select **New** and then **Project…**</span></span> <span data-ttu-id="118f5-114">z **souboru** nabídky.</span><span class="sxs-lookup"><span data-stu-id="118f5-114">from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="118f5-115">Rozbalte **ostatní typy projektů** uzlu **nainstalované šablony** podokně a vyberte **řešení sady Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="118f5-115">Expand the **Other Project Types** node in the **Installed Templates** pane and select **Visual Studio Solutions**.</span></span>  
  
3.  <span data-ttu-id="118f5-116">Vyberte **prázdné řešení** z **řešení sady Visual Studio** seznamu.</span><span class="sxs-lookup"><span data-stu-id="118f5-116">Select **Blank Solution** from the **Visual Studio Solutions** list.</span></span> <span data-ttu-id="118f5-117">Typ `PolicyInteropDemo` v **název** pole a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="118f5-117">Type `PolicyInteropDemo` in the **Name** box and click **OK**.</span></span>  
  
4.  <span data-ttu-id="118f5-118">Klikněte pravým tlačítkem na **PolicyInteropDemo** v **Průzkumníka řešení** a vyberte **přidat** a potom **nový projekt...** .</span><span class="sxs-lookup"><span data-stu-id="118f5-118">Right-click **PolicyInteropDemo** in **Solution Explorer** and select **Add** and then **New Project…**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="118f5-119">Pokud **Průzkumníka řešení** okno není viditelný, vyberte **Průzkumníka řešení** z **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="118f5-119">If the **Solution Explorer** window is not visible, select **Solution Explorer** from the **View** menu.</span></span>  
  
5.  <span data-ttu-id="118f5-120">V **nainstalované šablony** seznamu vyberte **Visual C#** a potom **pracovního postupu**.</span><span class="sxs-lookup"><span data-stu-id="118f5-120">In the **Installed Templates** list, select **Visual C#** and then **Workflow**.</span></span> <span data-ttu-id="118f5-121">Vyberte **rozhraní .NET Framework 3.5** z rozhraní .NET Framework verze rozevíracího seznamu a pak vyberte **knihovny aktivit pracovních postupů** z **šablony** seznamu.</span><span class="sxs-lookup"><span data-stu-id="118f5-121">Select **.NET Framework 3.5** from the .NET Framework version drop-down list, and then select **Workflow Activity Library** from the **Templates** list.</span></span>  
  
6.  <span data-ttu-id="118f5-122">Typ `PolicyActivityLibrary` v **název** pole a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="118f5-122">Type `PolicyActivityLibrary` in the **Name** box and click **OK**.</span></span>  
  
7.  <span data-ttu-id="118f5-123">Klikněte pravým tlačítkem na **Activity1.cs** v **Průzkumníka řešení** a vyberte **odstranit**.</span><span class="sxs-lookup"><span data-stu-id="118f5-123">Right-click **Activity1.cs** in **Solution Explorer** and select **Delete**.</span></span> <span data-ttu-id="118f5-124">Klikněte na tlačítko **OK** potvrďte.</span><span class="sxs-lookup"><span data-stu-id="118f5-124">Click **OK** to confirm.</span></span>  
  
#### <a name="to-create-the-discountcalculator-activity"></a><span data-ttu-id="118f5-125">Vytvořit aktivitu DiscountCalculator</span><span class="sxs-lookup"><span data-stu-id="118f5-125">To create the DiscountCalculator activity</span></span>  
  
1.  <span data-ttu-id="118f5-126">Klikněte pravým tlačítkem na **PolicyActivityLibrary** v **Průzkumníka řešení** a vyberte **přidat** a potom **aktivit...** .</span><span class="sxs-lookup"><span data-stu-id="118f5-126">Right-click **PolicyActivityLibrary** in **Solution Explorer** and select **Add** and then **Activity…**.</span></span>  
  
2.  <span data-ttu-id="118f5-127">Vyberte **aktivita (s rozdělením kódu)** z **položky Visual C#** seznamu.</span><span class="sxs-lookup"><span data-stu-id="118f5-127">Select **Activity (with code separation)** from the **Visual C# Items** list.</span></span> <span data-ttu-id="118f5-128">Typ `DiscountCalculator` v **název** pole a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="118f5-128">Type `DiscountCalculator` in the **Name** box and click **OK**.</span></span>  
  
3.  <span data-ttu-id="118f5-129">Klikněte pravým tlačítkem na **DiscountCalculator.xoml** v **Průzkumníka řešení** a vyberte **zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="118f5-129">Right-click **DiscountCalculator.xoml** in **Solution Explorer** and select **View Code**.</span></span>  
  
4.  <span data-ttu-id="118f5-130">Přidejte následující tři vlastnosti, které chcete `DiscountCalculator` třídy.</span><span class="sxs-lookup"><span data-stu-id="118f5-130">Add the following three properties to the `DiscountCalculator` class.</span></span>  
  
    ```csharp  
    public partial class DiscountCalculator : SequenceActivity  
    {  
        public double Subtotal { get; set; }  
        public double DiscountPercent { get; set; }  
        public double Total { get; set; }  
    }  
    ```  
  
5.  <span data-ttu-id="118f5-131">Klikněte pravým tlačítkem na **DiscountCalculator.xoml** v **Průzkumníka řešení** a vyberte **Návrhář zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="118f5-131">Right-click **DiscountCalculator.xoml** in **Solution Explorer** and select **View Designer**.</span></span>  
  
6.  <span data-ttu-id="118f5-132">Přetáhněte **zásady** aktivita z **v3.0 pracovního postupu Windows** část **nástrojů** a umístěte jej do **DiscountCalculator** aktivity .</span><span class="sxs-lookup"><span data-stu-id="118f5-132">Drag a **Policy** activity from the **Windows Workflow v3.0** section of the **Toolbox** and drop it in the **DiscountCalculator** activity.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="118f5-133">Pokud **nástrojů** okno není viditelný, vyberte **nástrojů** z **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="118f5-133">If the **Toolbox** window is not visible, select **Toolbox** from the **View** menu.</span></span>  
  
#### <a name="to-configure-the-rules"></a><span data-ttu-id="118f5-134">Konfigurace pravidla</span><span class="sxs-lookup"><span data-stu-id="118f5-134">To configure the rules</span></span>  
  
1.  <span data-ttu-id="118f5-135">Klikněte na nově přidaných **zásady** aktivity vyberte, pokud ještě není vybraná.</span><span class="sxs-lookup"><span data-stu-id="118f5-135">Click the newly added **Policy** activity to select it, if it is not already selected.</span></span>  
  
2.  <span data-ttu-id="118f5-136">Klikněte na tlačítko **RuleSetReference** vlastnost **vlastnosti** okno ho vyberte a klikněte na tlačítko se třemi tečkami napravo od vlastnost.</span><span class="sxs-lookup"><span data-stu-id="118f5-136">Click the **RuleSetReference** property in the **Properties** window to select it, and click the ellipsis button to the right of the property.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="118f5-137">Pokud **vlastnosti** okno se nezobrazuje, vyberte **okno vlastností** z **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="118f5-137">If the **Properties** window is not visible, choose **Properties Window** from the **View** menu.</span></span>  
  
3.  <span data-ttu-id="118f5-138">Vyberte **na nový...** .</span><span class="sxs-lookup"><span data-stu-id="118f5-138">Select **Click New…**.</span></span>  
  
4.  <span data-ttu-id="118f5-139">Klikněte na tlačítko **přidat pravidlo**.</span><span class="sxs-lookup"><span data-stu-id="118f5-139">Click **Add Rule**.</span></span>  
  
5.  <span data-ttu-id="118f5-140">Zadejte následující výraz do **podmínku** pole.</span><span class="sxs-lookup"><span data-stu-id="118f5-140">Type the following expression into the **Condition** box.</span></span>  
  
    ```  
    this.Subtotal >= 50 && this.Subtotal < 100  
    ```  
  
6.  <span data-ttu-id="118f5-141">Zadejte následující výraz do **pak akce** pole.</span><span class="sxs-lookup"><span data-stu-id="118f5-141">Type the following expression into the **Then Actions** box.</span></span>  
  
    ```  
    this.DiscountPercent = 0.075  
    ```  
  
7.  <span data-ttu-id="118f5-142">Klikněte na tlačítko **přidat pravidlo**.</span><span class="sxs-lookup"><span data-stu-id="118f5-142">Click **Add Rule**.</span></span>  
  
8.  <span data-ttu-id="118f5-143">Zadejte následující výraz do **podmínku** pole.</span><span class="sxs-lookup"><span data-stu-id="118f5-143">Type the following expression into the **Condition** box.</span></span>  
  
    ```  
    this.Subtotal >= 100  
    ```  
  
9. <span data-ttu-id="118f5-144">Zadejte následující výraz do **pak akce** pole.</span><span class="sxs-lookup"><span data-stu-id="118f5-144">Type the following expression into the **Then Actions** box.</span></span>  
  
    ```  
    this.DiscountPercent = 0.15  
    ```  
  
10. <span data-ttu-id="118f5-145">Klikněte na tlačítko **přidat pravidlo**.</span><span class="sxs-lookup"><span data-stu-id="118f5-145">Click **Add Rule**.</span></span>  
  
11. <span data-ttu-id="118f5-146">Zadejte následující výraz do **podmínku** pole.</span><span class="sxs-lookup"><span data-stu-id="118f5-146">Type the following expression into the **Condition** box.</span></span>  
  
    ```  
    this.DiscountPercent > 0  
    ```  
  
12. <span data-ttu-id="118f5-147">Zadejte následující výraz do **pak akce** pole.</span><span class="sxs-lookup"><span data-stu-id="118f5-147">Type the following expression into the **Then Actions** box.</span></span>  
  
    ```  
    this.Total = this.Subtotal - this.Subtotal * this.DiscountPercent  
    ```  
  
13. <span data-ttu-id="118f5-148">Zadejte následující výraz do **Else akce** pole.</span><span class="sxs-lookup"><span data-stu-id="118f5-148">Type the following expression into the **Else Actions** box.</span></span>  
  
    ```  
    this.Total = this.Subtotal  
    ```  
  
14. <span data-ttu-id="118f5-149">Klikněte na tlačítko **OK** zavřete **editoru nastavte pravidlo** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="118f5-149">Click **OK** to close the **Rule Set Editor** dialog box.</span></span>  
  
15. <span data-ttu-id="118f5-150">Ujistěte se, že nově vytvořené <xref:System.Workflow.Activities.Rules.RuleSet> výběru v **název** seznamu a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="118f5-150">Ensure that the newly-created <xref:System.Workflow.Activities.Rules.RuleSet> is selected in the **Name** list, and click **OK**.</span></span>  
  
16. <span data-ttu-id="118f5-151">Stiskněte kombinaci kláves CTRL + SHIFT + B, abyste mohli sestavit řešení.</span><span class="sxs-lookup"><span data-stu-id="118f5-151">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
 <span data-ttu-id="118f5-152">Přidaná do pravidla `DiscountCalculator` aktivity v tomto postupu jsou uvedeny v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="118f5-152">The rules added to the `DiscountCalculator` activity in this procedure are shown in the following code example.</span></span>  
  
```  
Rule1: IF this.Subtotal >= 50 && this.Subtotal < 100   
       THEN this.DiscountPercent = 0.075   
  
Rule2: IF this. Subtotal >= 100   
       THEN this.DiscountPercent = 0.15   
  
Rule3: IF this.DiscountPercent > 0   
       THEN this.Total = this.Subtotal - this.Subtotal * this.DiscountPercent   
       ELSE this.Total = this.Subtotal  
```  
  
 <span data-ttu-id="118f5-153">Když <xref:System.Workflow.Activities.PolicyActivity> spustí tyto tři pravidla vyhodnotit a upravit `Subtotal`, `DiscountPercent`, a `Total` hodnoty vlastností `DiscountCalculator` aktivity pro výpočet požadovaného slevy.</span><span class="sxs-lookup"><span data-stu-id="118f5-153">When the <xref:System.Workflow.Activities.PolicyActivity> executes, these three rules evaluate and modify the `Subtotal`, `DiscountPercent`, and `Total` property values of the `DiscountCalculator` activity to calculate the desired discount.</span></span>  
  
## <a name="using-the-discountcalculator-activity-with-the-interop-activity"></a><span data-ttu-id="118f5-154">Použití aktivity DiscountCalculator pomocí aktivity interoperability</span><span class="sxs-lookup"><span data-stu-id="118f5-154">Using the DiscountCalculator Activity with the Interop Activity</span></span>  
 <span data-ttu-id="118f5-155">Použít `DiscountCalculator` aktivity uvnitř [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] pracovního postupu, <xref:System.Activities.Statements.Interop> aktivita se používá.</span><span class="sxs-lookup"><span data-stu-id="118f5-155">To use the `DiscountCalculator` activity inside a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow, the <xref:System.Activities.Statements.Interop> activity is used.</span></span> <span data-ttu-id="118f5-156">V této části dva pracovní postupy jsou vytvářeny, jeden pomocí kódu a pomocí návrháře pracovních postupů, které ukazují, jak používat <xref:System.Activities.Statements.Interop> aktivitu `DiscountCalculator` aktivity.</span><span class="sxs-lookup"><span data-stu-id="118f5-156">In this section two workflows are created, one using code and one using the workflow designer, which show how to use the <xref:System.Activities.Statements.Interop> activity with the `DiscountCalculator` activity.</span></span> <span data-ttu-id="118f5-157">Stejné hostitelské aplikace se používá pro obě pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="118f5-157">The same host application is used for both workflows.</span></span>  
  
#### <a name="to-create-the-host-application"></a><span data-ttu-id="118f5-158">Chcete-li vytvořit hostitelskou aplikaci</span><span class="sxs-lookup"><span data-stu-id="118f5-158">To create the host application</span></span>  
  
1.  <span data-ttu-id="118f5-159">Klikněte pravým tlačítkem na **PolicyInteropDemo** v **Průzkumníka řešení** a vyberte **přidat**a potom **nový projekt...** .</span><span class="sxs-lookup"><span data-stu-id="118f5-159">Right-click **PolicyInteropDemo** in **Solution Explorer** and select **Add**, and then **New Project…**.</span></span>  
  
2.  <span data-ttu-id="118f5-160">Ujistěte se, že **rozhraní .NET Framework 4.5** je vybrali v rozevíracím seznamu verzi rozhraní .NET Framework a vyberte **Konzolová aplikace pracovního postupu** z **položky Visual C#** seznamu.</span><span class="sxs-lookup"><span data-stu-id="118f5-160">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list, and select  **Workflow Console Application** from the **Visual C# Items** list.</span></span>  
  
3.  <span data-ttu-id="118f5-161">Typ `PolicyInteropHost` do **název** pole a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="118f5-161">Type `PolicyInteropHost` into the **Name** box and click **OK**.</span></span>  
  
4.  <span data-ttu-id="118f5-162">Klikněte pravým tlačítkem na **PolicyInteropHost** v **Průzkumníka řešení** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="118f5-162">Right-click **PolicyInteropHost** in **Solution Explorer** and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="118f5-163">V **Cílová architektura** rozevírací seznamu, změnit výběr z **rozhraní .NET Framework 4 Client Profile** k **rozhraní .NET Framework 4.5**.</span><span class="sxs-lookup"><span data-stu-id="118f5-163">In the **Target framework** drop-down list, change the selection from **.NET Framework 4 Client Profile** to **.NET Framework 4.5**.</span></span> <span data-ttu-id="118f5-164">Klikněte na tlačítko **Ano** potvrďte.</span><span class="sxs-lookup"><span data-stu-id="118f5-164">Click **Yes** to confirm.</span></span>  
  
6.  <span data-ttu-id="118f5-165">Klikněte pravým tlačítkem na **PolicyInteropHost** v **Průzkumníka řešení** a vyberte **přidat odkaz...** .</span><span class="sxs-lookup"><span data-stu-id="118f5-165">Right-click **PolicyInteropHost** in **Solution Explorer** and select **Add Reference…**.</span></span>  
  
7.  <span data-ttu-id="118f5-166">Vyberte **PolicyActivityLibrary** z **projekty** kartě a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="118f5-166">Select **PolicyActivityLibrary** from the **Projects** tab and click **OK**.</span></span>  
  
8.  <span data-ttu-id="118f5-167">Klikněte pravým tlačítkem na **PolicyInteropHost** v **Průzkumníka řešení** a vyberte **přidat odkaz...** .</span><span class="sxs-lookup"><span data-stu-id="118f5-167">Right-click **PolicyInteropHost** in **Solution Explorer** and select **Add Reference…**.</span></span>  
  
9. <span data-ttu-id="118f5-168">Vyberte **System.Workflow.Activities**, **System.Workflow.ComponentModel**a potom **System.Workflow.Runtime** z **.NET**kartě a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="118f5-168">Select **System.Workflow.Activities**, **System.Workflow.ComponentModel**, and then **System.Workflow.Runtime** from the **.NET** tab and click **OK**.</span></span>  
  
10. <span data-ttu-id="118f5-169">Klikněte pravým tlačítkem na **PolicyInteropHost** v **Průzkumníka řešení** a vyberte **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="118f5-169">Right-click **PolicyInteropHost** in **Solution Explorer** and select **Set as StartUp Project**.</span></span>  
  
11. <span data-ttu-id="118f5-170">Stiskněte kombinaci kláves CTRL + SHIFT + B, abyste mohli sestavit řešení.</span><span class="sxs-lookup"><span data-stu-id="118f5-170">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
### <a name="using-the-interop-activity-in-code"></a><span data-ttu-id="118f5-171">Použití aktivity interoperability v kódu</span><span class="sxs-lookup"><span data-stu-id="118f5-171">Using the Interop Activity in Code</span></span>  
 <span data-ttu-id="118f5-172">V tomto příkladu se vytvoří pomocí kódu, který obsahuje definici pracovního postupu <xref:System.Activities.Statements.Interop> aktivity a `DiscountCalculator` aktivity.</span><span class="sxs-lookup"><span data-stu-id="118f5-172">In this example, a workflow definition is created using code that contains the <xref:System.Activities.Statements.Interop> activity and the `DiscountCalculator` activity.</span></span> <span data-ttu-id="118f5-173">Tento pracovní postup je vyvolán pomocí <xref:System.Activities.WorkflowInvoker> a výsledky vyhodnocení pravidla se zapisují do konzoly pomocí <xref:System.Activities.Statements.WriteLine> aktivity.</span><span class="sxs-lookup"><span data-stu-id="118f5-173">This workflow is invoked using <xref:System.Activities.WorkflowInvoker> and the results of the rule evaluation are written to the console using a <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
##### <a name="to-use-the-interop-activity-in-code"></a><span data-ttu-id="118f5-174">Použití aktivity interoperability v kódu</span><span class="sxs-lookup"><span data-stu-id="118f5-174">To use the Interop activity in code</span></span>  
  
1.  <span data-ttu-id="118f5-175">Klikněte pravým tlačítkem na **Program.cs** v **Průzkumníka řešení** a vyberte **zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="118f5-175">Right-click **Program.cs** in **Solution Explorer** and select **View Code**.</span></span>  
  
2.  <span data-ttu-id="118f5-176">Přidejte následující `using` příkazu v horní části souboru.</span><span class="sxs-lookup"><span data-stu-id="118f5-176">Add the following `using` statement at the top of the file.</span></span>  
  
    ```csharp  
    using PolicyActivityLibrary;  
    ```  
  
3.  <span data-ttu-id="118f5-177">Odebrat obsah `Main` metodu a nahraďte následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="118f5-177">Remove the contents of the `Main` method and replace with the following code.</span></span>  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        CalculateDiscountUsingCodeWorkflow();  
    }  
    ```  
  
4.  <span data-ttu-id="118f5-178">Vytvoření nové metody v `Program` třídu s názvem `CalculateDiscountUsingCodeWorkflow` , který obsahuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="118f5-178">Create a new method in the `Program` class called `CalculateDiscountUsingCodeWorkflow` that contains the following code.</span></span>  
  
    ```csharp  
    static void CalculateDiscountUsingCodeWorkflow()  
    {  
        Variable<double> Subtotal = new Variable<double>  
        {  
            Default = 75.99,  
            Name = "Subtotal"  
        };  
  
        Variable<double> DiscountPercent = new Variable<double>  
        {  
            Name = "DiscountPercent"  
        };  
  
        Variable<double> Total = new Variable<double>  
        {  
            Name = "Total"  
        };  
  
        Activity wf = new Sequence  
        {  
            Variables = { Subtotal, DiscountPercent, Total },  
            Activities =   
            {  
                new Interop  
                {  
                    ActivityType = typeof(DiscountCalculator),  
                    ActivityProperties =   
                    {  
                        { "Subtotal", new InArgument<double>(Subtotal) },  
                        { "DiscountPercentOut", new OutArgument<double>(DiscountPercent) },  
                        { "TotalOut", new OutArgument<double>(Total) }  
                    }  
                },  
                new WriteLine  
                {  
                    Text =  new InArgument<string>(env =>   
                        string.Format("Subtotal: {0:C}, Discount {1}%, Total {2:C}",   
                        Subtotal.Get(env), DiscountPercent.Get(env) * 100, Total.Get(env)))  
                }  
            }  
        };  
  
        WorkflowInvoker.Invoke(wf);  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="118f5-179">`Subtotal`, `DiscountPercent`, A `Total` vlastnosti `DiscountCalculator` aktivity jsou prezentované jako argumenty <xref:System.Activities.Statements.Interop> aktivity a pracovní postup vázaná na místní proměnné v <xref:System.Activities.Statements.Interop> aktivity <xref:System.Activities.Statements.Interop.ActivityProperties%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="118f5-179">The `Subtotal`, `DiscountPercent`, and `Total` properties of the `DiscountCalculator` activity are surfaced as arguments of the <xref:System.Activities.Statements.Interop> activity, and bound to local workflow variables in the <xref:System.Activities.Statements.Interop> activity’s <xref:System.Activities.Statements.Interop.ActivityProperties%2A> collection.</span></span> <span data-ttu-id="118f5-180">`Subtotal` se přidá jako <xref:System.Activities.ArgumentDirection.In> argument protože `Subtotal` data budou téci do <xref:System.Activities.Statements.Interop> aktivitu, a `DiscountPercent` a `Total` jsou přidány jako <xref:System.Activities.ArgumentDirection.Out> argumenty vzhledem k tomu, že svá data toky z celkového počtu <xref:System.Activities.Statements.Interop> aktivity.</span><span class="sxs-lookup"><span data-stu-id="118f5-180">`Subtotal` is added as an <xref:System.Activities.ArgumentDirection.In> argument because the `Subtotal` data flows into the <xref:System.Activities.Statements.Interop> activity, and `DiscountPercent` and `Total` are added as <xref:System.Activities.ArgumentDirection.Out> arguments because their data flows out of the <xref:System.Activities.Statements.Interop> activity.</span></span> <span data-ttu-id="118f5-181">Všimněte si, že dva <xref:System.Activities.ArgumentDirection.Out> argumenty se dají s názvy `DiscountPercentOut` a `TotalOut` k označení, že představují <xref:System.Activities.ArgumentDirection.Out> argumenty.</span><span class="sxs-lookup"><span data-stu-id="118f5-181">Note that the two <xref:System.Activities.ArgumentDirection.Out> arguments are added with the names `DiscountPercentOut` and `TotalOut` to indicate that they represent <xref:System.Activities.ArgumentDirection.Out> arguments.</span></span> <span data-ttu-id="118f5-182">`DiscountCalculator` Type je zadaný jako <xref:System.Activities.Statements.Interop> aktivity <xref:System.Activities.Statements.Interop.ActivityType%2A>.</span><span class="sxs-lookup"><span data-stu-id="118f5-182">The `DiscountCalculator` type is specified as the <xref:System.Activities.Statements.Interop> activity’s <xref:System.Activities.Statements.Interop.ActivityType%2A>.</span></span>  
  
5.  <span data-ttu-id="118f5-183">Stisknutím kláves CTRL + F5 sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="118f5-183">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="118f5-184">Nahraďte různé hodnoty `Subtotal` hodnotu k otestování slevu na různé úrovně poskytovaných `DiscountCalculator` aktivity.</span><span class="sxs-lookup"><span data-stu-id="118f5-184">Substitute different values for the `Subtotal` value to test out the different discount levels provided by the `DiscountCalculator` activity.</span></span>  
  
    ```csharp  
    Variable<double> Subtotal = new Variable<double>  
    {  
        Default = 75.99, // Change this value.  
        Name = "Subtotal"  
    };  
    ```  
  
### <a name="using-the-interop-activity-in-the-workflow-designer"></a><span data-ttu-id="118f5-185">Použití aktivity interoperability v Návrháři postupu provádění</span><span class="sxs-lookup"><span data-stu-id="118f5-185">Using the Interop Activity in the Workflow Designer</span></span>  
 <span data-ttu-id="118f5-186">V tomto příkladu se vytvoří pracovní postup pomocí návrháře postupu provádění.</span><span class="sxs-lookup"><span data-stu-id="118f5-186">In this example, a workflow is created using the workflow designer.</span></span> <span data-ttu-id="118f5-187">Tento pracovní postup má stejnou funkci jako předchozí příklad s výjimkou než místo <xref:System.Activities.Statements.WriteLine> aktivita k zobrazení slevy, hostitelské aplikace načte a zobrazí informace o slevy po dokončení pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="118f5-187">This workflow has the same functionality as the previous example, except than instead of using a <xref:System.Activities.Statements.WriteLine> activity to display the discount, the host application retrieves and displays the discount information when the workflow completes.</span></span> <span data-ttu-id="118f5-188">Také namísto použití místního pracovního postupu proměnné tak, aby obsahovala data, argumenty jsou vytvořené v Návrháři pracovních postupů a hodnoty jsou předány v z hostitele, když uživatel vyvolá pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="118f5-188">Also, instead of using local workflow variables to contain the data, arguments are created in the workflow designer and the values are passed in from the host when the workflow is invoked.</span></span>  
  
##### <a name="to-host-the-policyactivity-using-a-workflow-designer-created-workflow"></a><span data-ttu-id="118f5-189">K hostování aktivitě PolicyActivity pomocí návrháře postupu provádění vytvoření pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="118f5-189">To host the PolicyActivity using a Workflow Designer-created workflow</span></span>  
  
1.  <span data-ttu-id="118f5-190">Klikněte pravým tlačítkem na **Workflow1.xaml** v **Průzkumníka řešení** a vyberte **odstranit**.</span><span class="sxs-lookup"><span data-stu-id="118f5-190">Right-click **Workflow1.xaml** in **Solution Explorer** and select **Delete**.</span></span> <span data-ttu-id="118f5-191">Klikněte na tlačítko **OK** potvrďte.</span><span class="sxs-lookup"><span data-stu-id="118f5-191">Click **OK** to confirm.</span></span>  
  
2.  <span data-ttu-id="118f5-192">Klikněte pravým tlačítkem na **PolicyInteropHost** v **Průzkumníka řešení** a vyberte **přidat**, **novou položku...** .</span><span class="sxs-lookup"><span data-stu-id="118f5-192">Right-click **PolicyInteropHost** in **Solution Explorer** and select **Add**, **New Item…**.</span></span>  
  
3.  <span data-ttu-id="118f5-193">Rozbalte **položky Visual C#** uzel a vyberte možnost **pracovního postupu**.</span><span class="sxs-lookup"><span data-stu-id="118f5-193">Expand the **Visual C# Items** node and select **Workflow**.</span></span> <span data-ttu-id="118f5-194">Vyberte **aktivity** z **položky Visual C#** seznamu.</span><span class="sxs-lookup"><span data-stu-id="118f5-194">Select **Activity** from the **Visual C# Items** list.</span></span>  
  
4.  <span data-ttu-id="118f5-195">Typ `DiscountWorkflow` do **název** pole a klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="118f5-195">Type `DiscountWorkflow` into the **Name** box and click **Add**.</span></span>  
  
5.  <span data-ttu-id="118f5-196">Klikněte na tlačítko **argumenty** tlačítko v levém dolním rohu návrháře postupu provádění zobrazit **argumenty** podokně.</span><span class="sxs-lookup"><span data-stu-id="118f5-196">Click the **Arguments** button on the lower left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
6.  <span data-ttu-id="118f5-197">Klikněte na tlačítko **vytvořit Argument**.</span><span class="sxs-lookup"><span data-stu-id="118f5-197">Click **Create Argument**.</span></span>  
  
7.  <span data-ttu-id="118f5-198">Typ `Subtotal` do **název** vyberte **v** z **směr** rozevíracího seznamu, vyberte **Double** z **Typ argumentu** rozevíracího seznamu, a stiskněte klávesu ENTER, chcete-li uložit argument.</span><span class="sxs-lookup"><span data-stu-id="118f5-198">Type `Subtotal` into the **Name** box, select **In** from the **Direction** drop-down, select **Double** from the **Argument type** drop-down, and then press ENTER to save the argument.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="118f5-199">Pokud **Double** se nepoužívá **typ argumentu** rozevíracího seznamu vyberte **vyhledat typy...** , typ `System.Double` v **název typu** pole a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="118f5-199">If **Double** is not in the **Argument type** drop-down list, select **Browse for Types …**, type `System.Double` in the **Type Name** box, and click **OK**.</span></span>  
  
8.  <span data-ttu-id="118f5-200">Klikněte na tlačítko **vytvořit Argument**.</span><span class="sxs-lookup"><span data-stu-id="118f5-200">Click **Create Argument**.</span></span>  
  
9. <span data-ttu-id="118f5-201">Typ `DiscountPercent` do **název** vyberte **si** z **směr** rozevíracího seznamu, vyberte **Double** z **Typ argumentu** rozevíracího seznamu, a stiskněte klávesu ENTER, chcete-li uložit argument.</span><span class="sxs-lookup"><span data-stu-id="118f5-201">Type `DiscountPercent` into the **Name** box, select **Out** from the **Direction** drop-down, select **Double** from the **Argument type** drop-down, and then press ENTER to save the argument.</span></span>  
  
10. <span data-ttu-id="118f5-202">Klikněte na tlačítko **vytvořit Argument**.</span><span class="sxs-lookup"><span data-stu-id="118f5-202">Click **Create Argument**.</span></span>  
  
11. <span data-ttu-id="118f5-203">Typ `Total` do **název** vyberte **si** z **směr** rozevíracího seznamu, vyberte **Double** z **Typ argumentu** rozevíracího seznamu, a stiskněte klávesu ENTER, chcete-li uložit argument.</span><span class="sxs-lookup"><span data-stu-id="118f5-203">Type `Total` into the **Name** box, select **Out** from the **Direction** drop-down, select **Double** from the **Argument type** drop-down, and then press ENTER to save the argument.</span></span>  
  
12. <span data-ttu-id="118f5-204">Klikněte na tlačítko **argumenty** tlačítko v levém dolním rohu návrháře postupu provádění, zavřete **argumenty** podokně.</span><span class="sxs-lookup"><span data-stu-id="118f5-204">Click the **Arguments** button on the lower left side of the workflow designer to close the **Arguments** pane.</span></span>  
  
13. <span data-ttu-id="118f5-205">Přetáhněte **pořadí** aktivita z **tok řízení** část **nástrojů** a umístěte jej na plochu návrháře pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="118f5-205">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the workflow designer surface.</span></span>  
  
14. <span data-ttu-id="118f5-206">Přetáhněte **zprostředkovatele komunikace s objekty** aktivita z **migrace** část **nástrojů** a umístěte jej do **pořadí** aktivity.</span><span class="sxs-lookup"><span data-stu-id="118f5-206">Drag an **Interop** activity from the **Migration** section of the **Toolbox** and drop it in the **Sequence** activity.</span></span>  
  
15. <span data-ttu-id="118f5-207">Klikněte na tlačítko **zprostředkovatele komunikace s objekty** aktivity **klikněte na tlačítko Procházet...**</span><span class="sxs-lookup"><span data-stu-id="118f5-207">Click the **Interop** activity on the **Click to browse…**</span></span> <span data-ttu-id="118f5-208">Popisek, zadejte **DiscountCalculator** v **název typu** pole a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="118f5-208">label, type **DiscountCalculator** in the **Type Name** box, and click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="118f5-209">Když <xref:System.Activities.Statements.Interop> je aktivita přidána do pracovního postupu a `DiscountCalculator` type je zadaný jako jeho <xref:System.Activities.Statements.Interop.ActivityType%2A>, <xref:System.Activities.Statements.Interop> aktivita poskytuje tři <xref:System.Activities.ArgumentDirection.In> argumenty a tři <xref:System.Activities.ArgumentDirection.Out> argumenty, které představují tři public vlastnosti `DiscountCalculator` aktivity.</span><span class="sxs-lookup"><span data-stu-id="118f5-209">When the <xref:System.Activities.Statements.Interop> activity is added to the workflow and the `DiscountCalculator` type is specified as its <xref:System.Activities.Statements.Interop.ActivityType%2A>, the <xref:System.Activities.Statements.Interop> activity exposes three <xref:System.Activities.ArgumentDirection.In> arguments and three <xref:System.Activities.ArgumentDirection.Out> arguments that represent the three public properties of the `DiscountCalculator` activity.</span></span> <span data-ttu-id="118f5-210"><xref:System.Activities.ArgumentDirection.In> Argumentů mají stejný název jako tři veřejné vlastnosti a tři <xref:System.Activities.ArgumentDirection.Out> argumentů mají stejné názvy s **si** připojeným k názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="118f5-210">The <xref:System.Activities.ArgumentDirection.In> arguments have the same name as the three public properties, and the three <xref:System.Activities.ArgumentDirection.Out> arguments have the same names with **Out** appended to the property name.</span></span> <span data-ttu-id="118f5-211">V následujících krocích argumenty pracovní postup vytvořený v předchozích krocích jsou vázány na <xref:System.Activities.Statements.Interop> argumenty aktivity.</span><span class="sxs-lookup"><span data-stu-id="118f5-211">In the following steps, the workflow arguments created in the previous steps are bound to the <xref:System.Activities.Statements.Interop> activity’s arguments.</span></span>  
  
16. <span data-ttu-id="118f5-212">Typ `DiscountPercent` do **zadejte výraz jazyka VB.** napravo od pole **DiscountPercentOut** vlastnosti a stiskněte klávesu TAB.</span><span class="sxs-lookup"><span data-stu-id="118f5-212">Type `DiscountPercent` into the **Enter a VB expression** box to the right of the **DiscountPercentOut** property and press TAB.</span></span>  
  
17. <span data-ttu-id="118f5-213">Typ `Subtotal` do **zadejte výraz jazyka VB.** napravo od pole **Mezisoučet** vlastnosti a stiskněte klávesu TAB.</span><span class="sxs-lookup"><span data-stu-id="118f5-213">Type `Subtotal` into the **Enter a VB expression** box to the right of the **Subtotal** property and press TAB.</span></span>  
  
18. <span data-ttu-id="118f5-214">Typ `Total` do **zadejte výraz jazyka VB.** napravo od pole **TotalOut** vlastnosti a stiskněte klávesu TAB.</span><span class="sxs-lookup"><span data-stu-id="118f5-214">Type `Total` into the **Enter a VB expression** box to the right of the **TotalOut** property and press TAB.</span></span>  
  
19. <span data-ttu-id="118f5-215">Klikněte pravým tlačítkem na **Program.cs** v **Průzkumníka řešení** a vyberte **zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="118f5-215">Right-click **Program.cs** in **Solution Explorer** and select **View Code**.</span></span>  
  
20. <span data-ttu-id="118f5-216">Přidejte následující `using` příkazu v horní části souboru.</span><span class="sxs-lookup"><span data-stu-id="118f5-216">Add the following `using` statement at the top of the file.</span></span>  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
21. <span data-ttu-id="118f5-217">Odkomentujte volání `CalculateDiscountInCode` metodu `Main` metoda a přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="118f5-217">Comment out the call to the `CalculateDiscountInCode` method in the `Main` method and add the following code.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="118f5-218">Pokud jste neřídil předchozího postupu a výchozí `Main` kód je k dispozici, nahradí obsah `Main` následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="118f5-218">If you did not follow the previous procedure and the default `Main` code is present, replace the contents of `Main` with the following code.</span></span>  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        CalculateDiscountUsingDesignerWorkflow();  
        //CalculateDiscountUsingCodeWorkflow();  
    }  
    ```  
  
22. <span data-ttu-id="118f5-219">Vytvoření nové metody v `Program` třídu s názvem `CalculateDiscountUsingDesignerWorkflow` , který obsahuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="118f5-219">Create a new method in the `Program` class called `CalculateDiscountUsingDesignerWorkflow` that contains the following code.</span></span>  
  
    ```csharp  
    static void CalculateDiscountUsingDesignerWorkflow()  
    {  
        double SubtotalValue = 125.99;  
        Dictionary<string, object> wfargs = new Dictionary<string, object>  
        {  
            {"Subtotal", SubtotalValue}  
        };  
  
        Activity wf = new DiscountWorkflow();  
  
        IDictionary<string, object> outputs =  
            WorkflowInvoker.Invoke(wf, wfargs);  
  
        Console.WriteLine("Subtotal: {0:C}, Discount {1}%, Total {2:C}",  
            SubtotalValue, (double)outputs["DiscountPercent"] * 100,  
            outputs["Total"]);  
    }  
    ```  
  
23. <span data-ttu-id="118f5-220">Stisknutím kláves CTRL + F5 sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="118f5-220">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="118f5-221">Pokud chcete zadat jinou `Subtotal` amount, změňte hodnotu vlastnosti `SubtotalValue` v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="118f5-221">To specify a different `Subtotal` amount, change the value of `SubtotalValue` in the following code.</span></span>  
  
    ```csharp  
    double SubtotalValue = 125.99; // Change this value.  
    ```  
  
## <a name="rules-features-overview"></a><span data-ttu-id="118f5-222">Přehled funkcí pravidla</span><span class="sxs-lookup"><span data-stu-id="118f5-222">Rules Features Overview</span></span>  
 <span data-ttu-id="118f5-223">[!INCLUDE[wf1](../../../includes/wf1-md.md)] Stroj pravidel poskytuje podporu pro zpracování pravidel na základě priority způsobem s podporou pro řetězení vpřed.</span><span class="sxs-lookup"><span data-stu-id="118f5-223">The [!INCLUDE[wf1](../../../includes/wf1-md.md)] rules engine provides support for processing rules in a priority-based manner with support for forward chaining.</span></span> <span data-ttu-id="118f5-224">Pravidla může být vyhodnocen pro jednu položku nebo položky v kolekci.</span><span class="sxs-lookup"><span data-stu-id="118f5-224">Rules can be evaluated for a single item or for items in a collection.</span></span> <span data-ttu-id="118f5-225">Přehled pravidel a informace o funkcích konkrétními pravidly najdete v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="118f5-225">For an overview of rules and information on specific rules functionality, please refer to the following table.</span></span>  
  
|<span data-ttu-id="118f5-226">Funkce pravidel</span><span class="sxs-lookup"><span data-stu-id="118f5-226">Rules Feature</span></span>|<span data-ttu-id="118f5-227">Dokumentace</span><span class="sxs-lookup"><span data-stu-id="118f5-227">Documentation</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="118f5-228">Přehled pravidel</span><span class="sxs-lookup"><span data-stu-id="118f5-228">Rules Overview</span></span>|[<span data-ttu-id="118f5-229">Úvod do pravidla modul Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="118f5-229">Introduction to the Windows Workflow Foundation Rules Engine</span></span>](https://go.microsoft.com/fwlink/?LinkID=152836)|  
|<span data-ttu-id="118f5-230">Sady pravidel</span><span class="sxs-lookup"><span data-stu-id="118f5-230">RuleSet</span></span>|<span data-ttu-id="118f5-231">[Použití sady pravidel v pracovních postupech](https://go.microsoft.com/fwlink/?LinkId=178516) a <xref:System.Workflow.Activities.Rules.RuleSet></span><span class="sxs-lookup"><span data-stu-id="118f5-231">[Using RuleSets in Workflows](https://go.microsoft.com/fwlink/?LinkId=178516) and <xref:System.Workflow.Activities.Rules.RuleSet></span></span>|  
|<span data-ttu-id="118f5-232">Vyhodnocení pravidel</span><span class="sxs-lookup"><span data-stu-id="118f5-232">Evaluation of Rules</span></span>|[<span data-ttu-id="118f5-233">Vyhodnocení pravidla v sady pravidel</span><span class="sxs-lookup"><span data-stu-id="118f5-233">Rules Evaluation in RuleSets</span></span>](https://go.microsoft.com/fwlink/?LinkId=178517)|  
|<span data-ttu-id="118f5-234">Pravidla řetězení</span><span class="sxs-lookup"><span data-stu-id="118f5-234">Rules Chaining</span></span>|<span data-ttu-id="118f5-235">[Vpřed řetězení ovládací prvek](https://go.microsoft.com/fwlink/?LinkId=178518) a [vpřed řetězení pravidel](https://go.microsoft.com/fwlink/?LinkId=178519)</span><span class="sxs-lookup"><span data-stu-id="118f5-235">[Forward Chaining Control](https://go.microsoft.com/fwlink/?LinkId=178518) and [Forward Chaining of Rules](https://go.microsoft.com/fwlink/?LinkId=178519)</span></span>|  
|<span data-ttu-id="118f5-236">Zpracování kolekce pravidel</span><span class="sxs-lookup"><span data-stu-id="118f5-236">Processing Collections in Rules</span></span>|[<span data-ttu-id="118f5-237">Zpracování kolekce pravidel</span><span class="sxs-lookup"><span data-stu-id="118f5-237">Processing Collections in Rules</span></span>](https://go.microsoft.com/fwlink/?LinkId=178520)|  
|<span data-ttu-id="118f5-238">Pomocí aktivitě PolicyActivity</span><span class="sxs-lookup"><span data-stu-id="118f5-238">Using the PolicyActivity</span></span>|<span data-ttu-id="118f5-239">[Použití aktivity aktivitě PolicyActivity](https://go.microsoft.com/fwlink/?LinkId=178521) a <xref:System.Workflow.Activities.PolicyActivity></span><span class="sxs-lookup"><span data-stu-id="118f5-239">[Using the PolicyActivity Activity](https://go.microsoft.com/fwlink/?LinkId=178521) and <xref:System.Workflow.Activities.PolicyActivity></span></span>|  
  
 <span data-ttu-id="118f5-240">Pracovní postupy vytvořené v [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] nepoužívejte všechna pravidla funkcí poskytovaných službou [!INCLUDE[wf1](../../../includes/wf1-md.md)], jako je například deklarativní aktivita podmínky a podmíněné aktivity, jako <xref:System.Workflow.Activities.ConditionedActivityGroup> a <xref:System.Workflow.Activities.ReplicatorActivity>.</span><span class="sxs-lookup"><span data-stu-id="118f5-240">Workflows created in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] do not use all of the rules features provided by [!INCLUDE[wf1](../../../includes/wf1-md.md)], such as declarative activity conditions and conditional activities such as the <xref:System.Workflow.Activities.ConditionedActivityGroup> and <xref:System.Workflow.Activities.ReplicatorActivity>.</span></span> <span data-ttu-id="118f5-241">Pokud je to nutné, tato funkce je dostupná pro pracovní postupy vytvořené pomocí [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] a [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="118f5-241">If required, this functionality is available for workflows created using [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] and [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)].</span></span> <span data-ttu-id="118f5-242">Další informace najdete v tématu [pokyny k migraci](../../../docs/framework/windows-workflow-foundation/migration-guidance.md).</span><span class="sxs-lookup"><span data-stu-id="118f5-242">For more information, see [Migration Guidance](../../../docs/framework/windows-workflow-foundation/migration-guidance.md).</span></span>
