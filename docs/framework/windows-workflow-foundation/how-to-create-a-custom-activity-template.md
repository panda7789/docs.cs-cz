---
title: 'Postupy: vytvoření vlastní šablony aktivity'
ms.date: 03/30/2017
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
ms.openlocfilehash: 87acf0d084154c9c3e5cbc97da4af9821709f0a5
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50044837"
---
# <a name="how-to-create-a-custom-activity-template"></a><span data-ttu-id="9c71a-102">Postupy: vytvoření vlastní šablony aktivity</span><span class="sxs-lookup"><span data-stu-id="9c71a-102">How to: Create a Custom Activity Template</span></span>

<span data-ttu-id="9c71a-103">Vlastní aktivita šablony slouží k přizpůsobení konfigurace aktivit, včetně vlastních složených aktivit, tak, aby uživatelé nebudou mít k vytvoření každé aktivity jednotlivě a nakonfigurovat jejich vlastnosti a další nastavení ručně.</span><span class="sxs-lookup"><span data-stu-id="9c71a-103">Custom activity templates are used to customize the configuration of activities, including custom composite activities, so that users do not have to create each activity individually and configure their properties and other settings manually.</span></span> <span data-ttu-id="9c71a-104">Tyto vlastní šablony může být k dispozici v **nástrojů** na [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] nebo v návrháři se změněným hostováním, ze kterého uživatelé můžete přetáhnout na předem návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="9c71a-104">These custom templates can be made available in the **Toolbox** on the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] or from a rehosted designer, from which users can drag them onto the preconfigured design surface.</span></span> [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] <span data-ttu-id="9c71a-105">dodává se sadou dobrým příkladem takové šablony: [návrhář šablony SendAndReceiveReply](/visualstudio/workflow-designer/sendandreceivereply-template-designer) a [návrhář šablony ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer) v [návrháři aktivit zasílání zpráv](/visualstudio/workflow-designer/messaging-activity-designers) kategorie.</span><span class="sxs-lookup"><span data-stu-id="9c71a-105">ships with good examples of such templates: the [SendAndReceiveReply Template Designer](/visualstudio/workflow-designer/sendandreceivereply-template-designer) and the [ReceiveAndSendReply Template Designer](/visualstudio/workflow-designer/receiveandsendreply-template-designer) in the [Messaging Activity Designers](/visualstudio/workflow-designer/messaging-activity-designers) category.</span></span>

 <span data-ttu-id="9c71a-106">První postup v tomto tématu popisuje, jak vytvořit vlastní šablony aktivity pro **zpoždění** aktivity a druhý postup popisuje stručně ho zpřístupní v [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] k ověření, zda funguje vlastní šablonu.</span><span class="sxs-lookup"><span data-stu-id="9c71a-106">The first procedure in this topic describes how to create a custom activity template for a **Delay** activity and the second procedure describes briefly how to make it available in a [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] to verify that the custom template works.</span></span>

 <span data-ttu-id="9c71a-107">Vlastní aktivita šablony musí implementovat <xref:System.Activities.Presentation.IActivityTemplateFactory>.</span><span class="sxs-lookup"><span data-stu-id="9c71a-107">Custom activity templates must implement the <xref:System.Activities.Presentation.IActivityTemplateFactory>.</span></span> <span data-ttu-id="9c71a-108">Rozhraní má jediný <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> metodu, pomocí kterého můžete vytvořit a nakonfigurovat instance aktivit použít v šabloně.</span><span class="sxs-lookup"><span data-stu-id="9c71a-108">The interface has a single <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> method with which you can create and configure the activity instances used in the template.</span></span>

## <a name="to-create-a-template-for-the-delay-activity"></a><span data-ttu-id="9c71a-109">Vytvoření šablony aktivity Delay</span><span class="sxs-lookup"><span data-stu-id="9c71a-109">To create a template for the Delay activity</span></span>

1.  <span data-ttu-id="9c71a-110">Spusťte sadu Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="9c71a-110">Start Visual Studio 2010.</span></span>

2.  <span data-ttu-id="9c71a-111">Na **souboru** nabídky, přejděte k **nový**a pak vyberte **projektu**.</span><span class="sxs-lookup"><span data-stu-id="9c71a-111">On the **File** menu, point to **New**, and then select **Project**.</span></span>

     <span data-ttu-id="9c71a-112">**Nový projekt** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="9c71a-112">The **New Project** dialog box opens.</span></span>

3.  <span data-ttu-id="9c71a-113">V **typy projektů** vyberte **pracovního postupu** buď z **Visual C#** projekty nebo **jazyka Visual Basic** seskupení v závislosti na vaší preferovaný jazyk.</span><span class="sxs-lookup"><span data-stu-id="9c71a-113">In the **Project Types** pane, select **Workflow** from either the **Visual C#** projects or **Visual Basic** groupings depending on your language preference.</span></span>

4.  <span data-ttu-id="9c71a-114">V **šablony** vyberte **knihovny aktivit**.</span><span class="sxs-lookup"><span data-stu-id="9c71a-114">In the **Templates** pane, select **Activity Library**.</span></span>

5.  <span data-ttu-id="9c71a-115">V **název** zadejte `DelayActivityTemplate`.</span><span class="sxs-lookup"><span data-stu-id="9c71a-115">In the **Name** box, enter `DelayActivityTemplate`.</span></span>

6.  <span data-ttu-id="9c71a-116">Přijměte výchozí hodnoty v **umístění** a **název řešení** textová pole a pak klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="9c71a-116">Accept the defaults in the **Location** and **Solution name** text boxes, and then click **OK**.</span></span>

7.  <span data-ttu-id="9c71a-117">Klikněte pravým tlačítkem na adresář odkazy projektu DelayActivityTemplate v **Průzkumníka řešení** a zvolte **přidat odkaz** otevřít **přidat odkaz** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="9c71a-117">Right-click the References directory of the DelayActivityTemplate project in **Solution Explorer** and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>

8.  <span data-ttu-id="9c71a-118">Přejděte na **.NET** kartě a vyberte **PresentationFramework** z **název komponenty** sloupce na levé straně a klikněte na **OK** přidat odkaz do souboru knihovně PresentationFramework.dll.</span><span class="sxs-lookup"><span data-stu-id="9c71a-118">Go to the **.NET** tab and select **PresentationFramework** from the **Component Name** column on the left and click **OK** to add a reference to the PresentationFramework.dll file.</span></span>

9. <span data-ttu-id="9c71a-119">Opakujte tento postup pro přidání odkazů System.Activities.Presentation.dll a knihovně WindowsBase.dll soubory.</span><span class="sxs-lookup"><span data-stu-id="9c71a-119">Repeat this procedure to add references to the System.Activities.Presentation.dll and the WindowsBase.dll files.</span></span>

10. <span data-ttu-id="9c71a-120">Klikněte pravým tlačítkem na projekt DelayActivityTemplate v **Průzkumníka řešení** a zvolte **přidat** a potom **nová položka** otevřít **přidat novou položku**dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="9c71a-120">Right-click the DelayActivityTemplate project in **Solution Explorer** and choose **Add** and then **New Item** to open the **Add New Item** dialog box.</span></span>

11. <span data-ttu-id="9c71a-121">Vyberte **třídy** šablony, pojmenujte ho MyDelayTemplate a potom klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="9c71a-121">Select the **Class** template, name it MyDelayTemplate, and then click **OK**.</span></span>

12. <span data-ttu-id="9c71a-122">Otevřete soubor MyDelayTemplate.cs a přidejte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="9c71a-122">Open the MyDelayTemplate.cs file and add the following statements.</span></span>

    ```
    //Namespaces added
    using System.Activities;
    using System.Activities.Statements;
    using System.Activities.Presentation;
    using System.Windows;
    ```

13. <span data-ttu-id="9c71a-123">Implementace <xref:System.Activities.Presentation.IActivityTemplateFactory> s `MyDelayActivity` třídy následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="9c71a-123">Implement the <xref:System.Activities.Presentation.IActivityTemplateFactory> with the `MyDelayActivity` class with the following code.</span></span> <span data-ttu-id="9c71a-124">Tím se nakonfiguruje zpoždění Doba trvání 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="9c71a-124">This configures the delay to have a duration of 10 seconds.</span></span>

    ```
    public sealed class MyDelayActivity : IActivityTemplateFactory
    {
        public Activity Create(System.Windows.DependencyObject target)
        {
            return new System.Activities.Statements.Delay
            {
                DisplayName = "DelayActivityTemplate",
                Duration = new TimeSpan(0, 0, 10)

            };
        }
    }
    ```

14. <span data-ttu-id="9c71a-125">Vyberte **sestavit řešení** z **sestavení** nabídky ke generování souboru DelayActivityTemplate.dll.</span><span class="sxs-lookup"><span data-stu-id="9c71a-125">Select **Build Solution** from the **Build** menu to generate the DelayActivityTemplate.dll file.</span></span>

### <a name="to-make-the-template-available-in-a-workflow-designer"></a><span data-ttu-id="9c71a-126">Chcete-li šablonu zpřístupnit v Návrháři pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="9c71a-126">To make the template available in a Workflow Designer</span></span>

1.  <span data-ttu-id="9c71a-127">Klikněte pravým tlačítkem na řešení DelayActivityTemplate v **Průzkumníka řešení** a zvolte **přidat** a potom **nový projekt** otevřít **přidat nový projekt** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="9c71a-127">Right-click the DelayActivityTemplate solution in **Solution Explorer** and choose **Add** and then **New Project** to open the **Add New Project** dialog box.</span></span>

2.  <span data-ttu-id="9c71a-128">Vyberte **Konzolová aplikace pracovního postupu** šablony, pojmenujte ho `CustomActivityTemplateApp`a potom klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="9c71a-128">Select the **Workflow Console Application** template, name it `CustomActivityTemplateApp`, and then click **OK**.</span></span>

3.  <span data-ttu-id="9c71a-129">Klikněte pravým tlačítkem na adresář odkazy projektu CustomActivityTemplateApp v **Průzkumníka řešení** a zvolte **přidat odkaz** otevřít **přidat odkaz** dialogového okna pole.</span><span class="sxs-lookup"><span data-stu-id="9c71a-129">Right-click the References directory of the CustomActivityTemplateApp project in **Solution Explorer** and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>

4.  <span data-ttu-id="9c71a-130">Přejděte na **projekty** kartě a vyberte **DelayActivityTemplate** z **název projektu** sloupce na levé straně a klikněte na **OK** přidáte odkaz na soubor DelayActivityTemplate.dll, který jste vytvořili v prvním postupu.</span><span class="sxs-lookup"><span data-stu-id="9c71a-130">Go to the **Projects** tab and select **DelayActivityTemplate** from the **Project Name** column on the left and click **OK** to add a reference to the DelayActivityTemplate.dll file that you created in the first procedure.</span></span>

5.  <span data-ttu-id="9c71a-131">Klikněte pravým tlačítkem na projekt CustomActivityTemplateApp v **Průzkumníka řešení** a zvolte **sestavení** pro kompilaci aplikace.</span><span class="sxs-lookup"><span data-stu-id="9c71a-131">Right-click the CustomActivityTemplateApp project in **Solution Explorer** and choose **Build** to compile the application.</span></span>

6.  <span data-ttu-id="9c71a-132">Klikněte pravým tlačítkem na projekt CustomActivityTemplateApp v **Průzkumníka řešení** a zvolte **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="9c71a-132">Right-click the CustomActivityTemplateApp project in **Solution Explorer** and choose **Set as Startup Project**.</span></span>

7.  <span data-ttu-id="9c71a-133">Vyberte **spustit bez ladění** z **ladění** nabídky a stisknutím libovolné klávesy pokračovat po zobrazení výzvy v okně cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="9c71a-133">Select **Start Without Debugging** from the **Debug** menu and press any key to continue when prompted from the cmd.exe window.</span></span>

8.  <span data-ttu-id="9c71a-134">Otevřete soubor Workflow1.xaml a otevřít **nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="9c71a-134">Open the Workflow1.xaml file and open the **Toolbox**.</span></span>

9. <span data-ttu-id="9c71a-135">Vyhledejte **MyDelayActivity** šablony **DelayActivityTemplate** kategorie.</span><span class="sxs-lookup"><span data-stu-id="9c71a-135">Locate the **MyDelayActivity** template in the **DelayActivityTemplate** category.</span></span> <span data-ttu-id="9c71a-136">Přetáhněte jej na návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="9c71a-136">Drag it onto the design surface.</span></span> <span data-ttu-id="9c71a-137">Potvrďte v **vlastnosti** okna, která `Duration` vlastnost byla nastavena na 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="9c71a-137">Confirm in the **Properties** window that the `Duration` property has been set to 10 seconds.</span></span>

## <a name="example"></a><span data-ttu-id="9c71a-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="9c71a-138">Example</span></span>
 <span data-ttu-id="9c71a-139">Soubor MyDelayActivity.cs by měl obsahovat následující kód.</span><span class="sxs-lookup"><span data-stu-id="9c71a-139">The MyDelayActivity.cs file should contain the following code.</span></span>

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;

//Namespaces added
using System.Activities;
using System.Activities.Statements;
using System.Activities.Presentation;
using System.Windows;

namespace DelayActivityTemplate
{
    public sealed class MyDelayActivity : IActivityTemplateFactory
    {
        public Activity Create(System.Windows.DependencyObject target)
        {
            return new System.Activities.Statements.Delay
            {
                DisplayName = "DelayActivityTemplate",
                Duration = new TimeSpan(0, 0, 10)

            };
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="9c71a-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="9c71a-140">See Also</span></span>

- <xref:System.Activities.Presentation.IActivityTemplateFactory>
- [<span data-ttu-id="9c71a-141">Přizpůsobení prostředí pro návrh pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="9c71a-141">Customizing the Workflow Design Experience</span></span>](../../../docs/framework/windows-workflow-foundation/customizing-the-workflow-design-experience.md)