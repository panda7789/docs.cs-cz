---
title: 'Postupy: Vytvoření vlastní šablony aktivity'
ms.date: 03/30/2017
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
ms.openlocfilehash: f910d1367c941dbc319421d402cae8f4194872e5
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715257"
---
# <a name="how-to-create-a-custom-activity-template"></a><span data-ttu-id="283a8-102">Postupy: Vytvoření vlastní šablony aktivity</span><span class="sxs-lookup"><span data-stu-id="283a8-102">How to: Create a Custom Activity Template</span></span>

<span data-ttu-id="283a8-103">Vlastní šablony aktivit slouží k přizpůsobení konfigurace aktivit, včetně vlastních složených aktivit, aby uživatelé nemuseli vytvářet jednotlivé aktivity jednotlivě a nakonfigurovali jejich vlastnosti a další nastavení ručně.</span><span class="sxs-lookup"><span data-stu-id="283a8-103">Custom activity templates are used to customize the configuration of activities, including custom composite activities, so that users do not have to create each activity individually and configure their properties and other settings manually.</span></span> <span data-ttu-id="283a8-104">Tyto vlastní šablony mohou být k dispozici v sadě **nástrojů** na Návrhář postupu provádění systému Windows nebo v přehostujícím návrháři, ze kterých je uživatelé mohou přetáhnout na předem nakonfigurovanou návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="283a8-104">These custom templates can be made available in the **Toolbox** on the Windows Workflow Designer or from a rehosted designer, from which users can drag them onto the preconfigured design surface.</span></span> <span data-ttu-id="283a8-105">Návrhář postupu provádění lodí s dobrými příklady takových šablon: [Návrhář šablony SendAndReceiveReply](/visualstudio/workflow-designer/sendandreceivereply-template-designer) a [Návrhář šablon ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer) v kategorii [Návrháři aktivity zasílání zpráv](/visualstudio/workflow-designer/messaging-activity-designers) .</span><span class="sxs-lookup"><span data-stu-id="283a8-105">Workflow Designer ships with good examples of such templates: the [SendAndReceiveReply Template Designer](/visualstudio/workflow-designer/sendandreceivereply-template-designer) and the [ReceiveAndSendReply Template Designer](/visualstudio/workflow-designer/receiveandsendreply-template-designer) in the [Messaging Activity Designers](/visualstudio/workflow-designer/messaging-activity-designers) category.</span></span>

 <span data-ttu-id="283a8-106">První postup v tomto tématu popisuje, jak vytvořit šablonu vlastní aktivity pro aktivitu **zpoždění** a druhá procedura stručně popisuje, jak ji zpřístupnit v Návrhář postupu provádění, abyste ověřili, že vlastní šablona funguje.</span><span class="sxs-lookup"><span data-stu-id="283a8-106">The first procedure in this topic describes how to create a custom activity template for a **Delay** activity and the second procedure describes briefly how to make it available in a Workflow Designer to verify that the custom template works.</span></span>

 <span data-ttu-id="283a8-107">Vlastní šablony aktivit musí implementovat <xref:System.Activities.Presentation.IActivityTemplateFactory>.</span><span class="sxs-lookup"><span data-stu-id="283a8-107">Custom activity templates must implement the <xref:System.Activities.Presentation.IActivityTemplateFactory>.</span></span> <span data-ttu-id="283a8-108">Rozhraní má jednu <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> metodu, pomocí které můžete vytvořit a nakonfigurovat instance aktivit použité v šabloně.</span><span class="sxs-lookup"><span data-stu-id="283a8-108">The interface has a single <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> method with which you can create and configure the activity instances used in the template.</span></span>

## <a name="to-create-a-template-for-the-delay-activity"></a><span data-ttu-id="283a8-109">Vytvoření šablony pro aktivitu zpoždění</span><span class="sxs-lookup"><span data-stu-id="283a8-109">To create a template for the Delay activity</span></span>

1. <span data-ttu-id="283a8-110">Spusťte Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="283a8-110">Start Visual Studio 2010.</span></span>

2. <span data-ttu-id="283a8-111">V nabídce **soubor** přejděte na příkaz **Nový**a vyberte možnost **projekt**.</span><span class="sxs-lookup"><span data-stu-id="283a8-111">On the **File** menu, point to **New**, and then select **Project**.</span></span>

     <span data-ttu-id="283a8-112">Otevře se dialogové okno **Nový projekt** .</span><span class="sxs-lookup"><span data-stu-id="283a8-112">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="283a8-113">V podokně **typy projektů** vyberte **pracovní postup** z **vizuálních C#**  projektů nebo skupin **Visual Basic** v závislosti na jazykové předvolbách.</span><span class="sxs-lookup"><span data-stu-id="283a8-113">In the **Project Types** pane, select **Workflow** from either the **Visual C#** projects or **Visual Basic** groupings depending on your language preference.</span></span>

4. <span data-ttu-id="283a8-114">V podokně **šablony** vyberte **Knihovna aktivit**.</span><span class="sxs-lookup"><span data-stu-id="283a8-114">In the **Templates** pane, select **Activity Library**.</span></span>

5. <span data-ttu-id="283a8-115">Do pole **název** zadejte `DelayActivityTemplate`.</span><span class="sxs-lookup"><span data-stu-id="283a8-115">In the **Name** box, enter `DelayActivityTemplate`.</span></span>

6. <span data-ttu-id="283a8-116">Přijměte výchozí hodnoty v textových polích **umístění** a **název řešení** a potom klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="283a8-116">Accept the defaults in the **Location** and **Solution name** text boxes, and then click **OK**.</span></span>

7. <span data-ttu-id="283a8-117">V **Průzkumník řešení** klikněte pravým tlačítkem na adresář odkazy projektu DelayActivityTemplate a výběrem možnosti **Přidat odkaz** otevřete dialogové okno **Přidat odkaz** .</span><span class="sxs-lookup"><span data-stu-id="283a8-117">Right-click the References directory of the DelayActivityTemplate project in **Solution Explorer** and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>

8. <span data-ttu-id="283a8-118">Přejděte na kartu **.NET** a vyberte **PresentationFramework** ze sloupce **název součásti** na levé straně a kliknutím na **OK** přidejte odkaz na soubor PresentationFramework. dll.</span><span class="sxs-lookup"><span data-stu-id="283a8-118">Go to the **.NET** tab and select **PresentationFramework** from the **Component Name** column on the left and click **OK** to add a reference to the PresentationFramework.dll file.</span></span>

9. <span data-ttu-id="283a8-119">Opakujte tento postup, chcete-li přidat odkazy na soubory System. Activities. Presentation. dll a WindowsBase. dll.</span><span class="sxs-lookup"><span data-stu-id="283a8-119">Repeat this procedure to add references to the System.Activities.Presentation.dll and the WindowsBase.dll files.</span></span>

10. <span data-ttu-id="283a8-120">Klikněte pravým tlačítkem myši na projekt DelayActivityTemplate v **Průzkumník řešení** a zvolte možnost **Přidat** a poté **Nová položka** . tím otevřete dialogové okno **Přidat novou položku** .</span><span class="sxs-lookup"><span data-stu-id="283a8-120">Right-click the DelayActivityTemplate project in **Solution Explorer** and choose **Add** and then **New Item** to open the **Add New Item** dialog box.</span></span>

11. <span data-ttu-id="283a8-121">Vyberte šablonu **třídy** , pojmenujte ji MyDelayTemplate a pak klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="283a8-121">Select the **Class** template, name it MyDelayTemplate, and then click **OK**.</span></span>

12. <span data-ttu-id="283a8-122">Otevřete soubor MyDelayTemplate.cs a přidejte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="283a8-122">Open the MyDelayTemplate.cs file and add the following statements.</span></span>

    ```csharp
    //Namespaces added
    using System.Activities;
    using System.Activities.Statements;
    using System.Activities.Presentation;
    using System.Windows;
    ```

13. <span data-ttu-id="283a8-123">Implementujte <xref:System.Activities.Presentation.IActivityTemplateFactory> pomocí `MyDelayActivity` třídy s následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="283a8-123">Implement the <xref:System.Activities.Presentation.IActivityTemplateFactory> with the `MyDelayActivity` class with the following code.</span></span> <span data-ttu-id="283a8-124">Tím se nakonfiguruje zpoždění na dobu 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="283a8-124">This configures the delay to have a duration of 10 seconds.</span></span>

    ```csharp
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

14. <span data-ttu-id="283a8-125">Vyberte **Sestavit řešení** z nabídky **sestavení** pro vygenerování souboru DelayActivityTemplate. dll.</span><span class="sxs-lookup"><span data-stu-id="283a8-125">Select **Build Solution** from the **Build** menu to generate the DelayActivityTemplate.dll file.</span></span>

### <a name="to-make-the-template-available-in-a-workflow-designer"></a><span data-ttu-id="283a8-126">Zpřístupnění šablony ve Návrhář postupu provádění</span><span class="sxs-lookup"><span data-stu-id="283a8-126">To make the template available in a Workflow Designer</span></span>

1. <span data-ttu-id="283a8-127">V **Průzkumník řešení** klikněte pravým tlačítkem na řešení DelayActivityTemplate a zvolte **Přidat** a pak **Nový projekt** . otevře se dialogové okno **Přidat nový projekt** .</span><span class="sxs-lookup"><span data-stu-id="283a8-127">Right-click the DelayActivityTemplate solution in **Solution Explorer** and choose **Add** and then **New Project** to open the **Add New Project** dialog box.</span></span>

2. <span data-ttu-id="283a8-128">Vyberte šablonu **Konzolová aplikace pracovního postupu** , pojmenujte ji `CustomActivityTemplateApp`a potom klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="283a8-128">Select the **Workflow Console Application** template, name it `CustomActivityTemplateApp`, and then click **OK**.</span></span>

3. <span data-ttu-id="283a8-129">V **Průzkumník řešení** klikněte pravým tlačítkem na adresář odkazy projektu CustomActivityTemplateApp a výběrem možnosti **Přidat odkaz** otevřete dialogové okno **Přidat odkaz** .</span><span class="sxs-lookup"><span data-stu-id="283a8-129">Right-click the References directory of the CustomActivityTemplateApp project in **Solution Explorer** and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>

4. <span data-ttu-id="283a8-130">Přejděte na kartu **projekty** a vyberte **DelayActivityTemplate** ze sloupce **název projektu** na levé straně a kliknutím na **OK** přidejte odkaz na soubor DelayActivityTemplate. dll, který jste vytvořili v prvním postupu.</span><span class="sxs-lookup"><span data-stu-id="283a8-130">Go to the **Projects** tab and select **DelayActivityTemplate** from the **Project Name** column on the left and click **OK** to add a reference to the DelayActivityTemplate.dll file that you created in the first procedure.</span></span>

5. <span data-ttu-id="283a8-131">V **Průzkumník řešení** klikněte pravým tlačítkem na projekt CustomActivityTemplateApp a vyberte **sestavit** pro zkompilování aplikace.</span><span class="sxs-lookup"><span data-stu-id="283a8-131">Right-click the CustomActivityTemplateApp project in **Solution Explorer** and choose **Build** to compile the application.</span></span>

6. <span data-ttu-id="283a8-132">V **Průzkumník řešení** klikněte pravým tlačítkem na projekt CustomActivityTemplateApp a vyberte **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="283a8-132">Right-click the CustomActivityTemplateApp project in **Solution Explorer** and choose **Set as Startup Project**.</span></span>

7. <span data-ttu-id="283a8-133">Vyberte možnost **Spustit bez ladění** z nabídky **ladění** a stisknutím libovolné klávesy pokračujte po zobrazení výzvy z okna cmd. exe.</span><span class="sxs-lookup"><span data-stu-id="283a8-133">Select **Start Without Debugging** from the **Debug** menu and press any key to continue when prompted from the cmd.exe window.</span></span>

8. <span data-ttu-id="283a8-134">Otevřete soubor Workflow1. XAML a otevřete **sadu nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="283a8-134">Open the Workflow1.xaml file and open the **Toolbox**.</span></span>

9. <span data-ttu-id="283a8-135">Vyhledejte šablonu **MyDelayActivity** v kategorii **DelayActivityTemplate** .</span><span class="sxs-lookup"><span data-stu-id="283a8-135">Locate the **MyDelayActivity** template in the **DelayActivityTemplate** category.</span></span> <span data-ttu-id="283a8-136">Přetáhněte ji na návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="283a8-136">Drag it onto the design surface.</span></span> <span data-ttu-id="283a8-137">V okně **vlastnosti** potvrďte, že vlastnost `Duration` byla nastavena na 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="283a8-137">Confirm in the **Properties** window that the `Duration` property has been set to 10 seconds.</span></span>

## <a name="example"></a><span data-ttu-id="283a8-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="283a8-138">Example</span></span>
 <span data-ttu-id="283a8-139">Soubor MyDelayActivity.cs by měl obsahovat následující kód.</span><span class="sxs-lookup"><span data-stu-id="283a8-139">The MyDelayActivity.cs file should contain the following code.</span></span>

```csharp
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

## <a name="see-also"></a><span data-ttu-id="283a8-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="283a8-140">See also</span></span>

- <xref:System.Activities.Presentation.IActivityTemplateFactory>
- [<span data-ttu-id="283a8-141">Přizpůsobení prostředí pro návrh pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="283a8-141">Customizing the Workflow Design Experience</span></span>](customizing-the-workflow-design-experience.md)
