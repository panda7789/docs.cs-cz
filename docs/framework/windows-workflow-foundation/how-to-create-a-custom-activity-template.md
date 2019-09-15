---
title: 'Postupy: Vytvoření vlastní šablony aktivity'
ms.date: 03/30/2017
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
ms.openlocfilehash: 4ec84658dbe3039a4d7d714f8da183e6a5eb6ca4
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989715"
---
# <a name="how-to-create-a-custom-activity-template"></a><span data-ttu-id="8ead0-102">Postupy: Vytvoření vlastní šablony aktivity</span><span class="sxs-lookup"><span data-stu-id="8ead0-102">How to: Create a Custom Activity Template</span></span>

<span data-ttu-id="8ead0-103">Vlastní šablony aktivit slouží k přizpůsobení konfigurace aktivit, včetně vlastních složených aktivit, aby uživatelé nemuseli vytvářet jednotlivé aktivity jednotlivě a nakonfigurovali jejich vlastnosti a další nastavení ručně.</span><span class="sxs-lookup"><span data-stu-id="8ead0-103">Custom activity templates are used to customize the configuration of activities, including custom composite activities, so that users do not have to create each activity individually and configure their properties and other settings manually.</span></span> <span data-ttu-id="8ead0-104">Tyto vlastní šablony mohou být k dispozici v sadě **nástrojů** na [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] nebo v přehostujícím návrháři, ze kterých je uživatelé mohou přetahovat na předkonfigurovaný návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="8ead0-104">These custom templates can be made available in the **Toolbox** on the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] or from a rehosted designer, from which users can drag them onto the preconfigured design surface.</span></span> [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]<span data-ttu-id="8ead0-105">dodává se dobrými příklady takových šablon: [Návrhář šablon SendAndReceiveReply](/visualstudio/workflow-designer/sendandreceivereply-template-designer) a [Návrhář šablon ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer) v kategorii [Návrháři aktivity zasílání zpráv](/visualstudio/workflow-designer/messaging-activity-designers) .</span><span class="sxs-lookup"><span data-stu-id="8ead0-105">ships with good examples of such templates: the [SendAndReceiveReply Template Designer](/visualstudio/workflow-designer/sendandreceivereply-template-designer) and the [ReceiveAndSendReply Template Designer](/visualstudio/workflow-designer/receiveandsendreply-template-designer) in the [Messaging Activity Designers](/visualstudio/workflow-designer/messaging-activity-designers) category.</span></span>

 <span data-ttu-id="8ead0-106">První postup v tomto tématu popisuje, jak vytvořit šablonu vlastní aktivity pro aktivitu **zpoždění** a druhá procedura stručně popisuje, jak ji zpřístupnit v [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] nástroji, abyste ověřili, že vlastní šablona funguje.</span><span class="sxs-lookup"><span data-stu-id="8ead0-106">The first procedure in this topic describes how to create a custom activity template for a **Delay** activity and the second procedure describes briefly how to make it available in a [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] to verify that the custom template works.</span></span>

 <span data-ttu-id="8ead0-107">Vlastní šablony aktivit musí implementovat <xref:System.Activities.Presentation.IActivityTemplateFactory>.</span><span class="sxs-lookup"><span data-stu-id="8ead0-107">Custom activity templates must implement the <xref:System.Activities.Presentation.IActivityTemplateFactory>.</span></span> <span data-ttu-id="8ead0-108">Rozhraní má jedinou <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> metodu, se kterou můžete vytvořit a nakonfigurovat instance aktivit použité v šabloně.</span><span class="sxs-lookup"><span data-stu-id="8ead0-108">The interface has a single <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> method with which you can create and configure the activity instances used in the template.</span></span>

## <a name="to-create-a-template-for-the-delay-activity"></a><span data-ttu-id="8ead0-109">Vytvoření šablony pro aktivitu zpoždění</span><span class="sxs-lookup"><span data-stu-id="8ead0-109">To create a template for the Delay activity</span></span>

1. <span data-ttu-id="8ead0-110">Spusťte Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="8ead0-110">Start Visual Studio 2010.</span></span>

2. <span data-ttu-id="8ead0-111">V nabídce **soubor** přejděte na příkaz **Nový**a vyberte možnost **projekt**.</span><span class="sxs-lookup"><span data-stu-id="8ead0-111">On the **File** menu, point to **New**, and then select **Project**.</span></span>

     <span data-ttu-id="8ead0-112">**Nový projekt** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="8ead0-112">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="8ead0-113">V podokně **typy projektů** vyberte **pracovní postup** z **vizuálních C#**  projektů nebo skupin **Visual Basic** v závislosti na jazykové předvolbách.</span><span class="sxs-lookup"><span data-stu-id="8ead0-113">In the **Project Types** pane, select **Workflow** from either the **Visual C#** projects or **Visual Basic** groupings depending on your language preference.</span></span>

4. <span data-ttu-id="8ead0-114">V podokně **šablony** vyberte **Knihovna aktivit**.</span><span class="sxs-lookup"><span data-stu-id="8ead0-114">In the **Templates** pane, select **Activity Library**.</span></span>

5. <span data-ttu-id="8ead0-115">Do pole **název** zadejte `DelayActivityTemplate`.</span><span class="sxs-lookup"><span data-stu-id="8ead0-115">In the **Name** box, enter `DelayActivityTemplate`.</span></span>

6. <span data-ttu-id="8ead0-116">Přijměte výchozí hodnoty v textových polích **umístění** a **název řešení** a potom klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="8ead0-116">Accept the defaults in the **Location** and **Solution name** text boxes, and then click **OK**.</span></span>

7. <span data-ttu-id="8ead0-117">V **Průzkumník řešení** klikněte pravým tlačítkem na adresář odkazy projektu DelayActivityTemplate a výběrem možnosti **Přidat odkaz** otevřete dialogové okno **Přidat odkaz** .</span><span class="sxs-lookup"><span data-stu-id="8ead0-117">Right-click the References directory of the DelayActivityTemplate project in **Solution Explorer** and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>

8. <span data-ttu-id="8ead0-118">Přejděte na kartu **.NET** a vyberte **PresentationFramework** ze sloupce **název součásti** na levé straně a kliknutím na **OK** přidejte odkaz na soubor PresentationFramework. dll.</span><span class="sxs-lookup"><span data-stu-id="8ead0-118">Go to the **.NET** tab and select **PresentationFramework** from the **Component Name** column on the left and click **OK** to add a reference to the PresentationFramework.dll file.</span></span>

9. <span data-ttu-id="8ead0-119">Opakujte tento postup, chcete-li přidat odkazy na soubory System. Activities. Presentation. dll a WindowsBase. dll.</span><span class="sxs-lookup"><span data-stu-id="8ead0-119">Repeat this procedure to add references to the System.Activities.Presentation.dll and the WindowsBase.dll files.</span></span>

10. <span data-ttu-id="8ead0-120">Klikněte pravým tlačítkem myši na projekt DelayActivityTemplate v **Průzkumník řešení** a zvolte možnost **Přidat** a poté **Nová položka** . tím otevřete dialogové okno **Přidat novou položku** .</span><span class="sxs-lookup"><span data-stu-id="8ead0-120">Right-click the DelayActivityTemplate project in **Solution Explorer** and choose **Add** and then **New Item** to open the **Add New Item** dialog box.</span></span>

11. <span data-ttu-id="8ead0-121">Vyberte šablonu **třídy** , pojmenujte ji MyDelayTemplate a pak klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="8ead0-121">Select the **Class** template, name it MyDelayTemplate, and then click **OK**.</span></span>

12. <span data-ttu-id="8ead0-122">Otevřete soubor MyDelayTemplate.cs a přidejte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="8ead0-122">Open the MyDelayTemplate.cs file and add the following statements.</span></span>

    ```csharp
    //Namespaces added
    using System.Activities;
    using System.Activities.Statements;
    using System.Activities.Presentation;
    using System.Windows;
    ```

13. <span data-ttu-id="8ead0-123">Implementujte `MyDelayActivity` třídu spoužitímnásledujícíhokódu.<xref:System.Activities.Presentation.IActivityTemplateFactory></span><span class="sxs-lookup"><span data-stu-id="8ead0-123">Implement the <xref:System.Activities.Presentation.IActivityTemplateFactory> with the `MyDelayActivity` class with the following code.</span></span> <span data-ttu-id="8ead0-124">Tím se nakonfiguruje zpoždění na dobu 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="8ead0-124">This configures the delay to have a duration of 10 seconds.</span></span>

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

14. <span data-ttu-id="8ead0-125">Vyberte **Sestavit řešení** z nabídky **sestavení** pro vygenerování souboru DelayActivityTemplate. dll.</span><span class="sxs-lookup"><span data-stu-id="8ead0-125">Select **Build Solution** from the **Build** menu to generate the DelayActivityTemplate.dll file.</span></span>

### <a name="to-make-the-template-available-in-a-workflow-designer"></a><span data-ttu-id="8ead0-126">Zpřístupnění šablony ve Návrhář postupu provádění</span><span class="sxs-lookup"><span data-stu-id="8ead0-126">To make the template available in a Workflow Designer</span></span>

1. <span data-ttu-id="8ead0-127">V **Průzkumník řešení** klikněte pravým tlačítkem na řešení DelayActivityTemplate a zvolte **Přidat** a pak **Nový projekt** . otevře se dialogové okno **Přidat nový projekt** .</span><span class="sxs-lookup"><span data-stu-id="8ead0-127">Right-click the DelayActivityTemplate solution in **Solution Explorer** and choose **Add** and then **New Project** to open the **Add New Project** dialog box.</span></span>

2. <span data-ttu-id="8ead0-128">Vyberte šablonu **Konzolová aplikace pracovního postupu** , pojmenujte ji `CustomActivityTemplateApp`a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="8ead0-128">Select the **Workflow Console Application** template, name it `CustomActivityTemplateApp`, and then click **OK**.</span></span>

3. <span data-ttu-id="8ead0-129">V **Průzkumník řešení** klikněte pravým tlačítkem na adresář odkazy projektu CustomActivityTemplateApp a výběrem možnosti **Přidat odkaz** otevřete dialogové okno **Přidat odkaz** .</span><span class="sxs-lookup"><span data-stu-id="8ead0-129">Right-click the References directory of the CustomActivityTemplateApp project in **Solution Explorer** and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>

4. <span data-ttu-id="8ead0-130">Přejděte na kartu **projekty** a vyberte **DelayActivityTemplate** ze sloupce **název projektu** na levé straně a kliknutím na **OK** přidejte odkaz na soubor DelayActivityTemplate. dll, který jste vytvořili v prvním postupu.</span><span class="sxs-lookup"><span data-stu-id="8ead0-130">Go to the **Projects** tab and select **DelayActivityTemplate** from the **Project Name** column on the left and click **OK** to add a reference to the DelayActivityTemplate.dll file that you created in the first procedure.</span></span>

5. <span data-ttu-id="8ead0-131">V **Průzkumník řešení** klikněte pravým tlačítkem na projekt CustomActivityTemplateApp a vyberte **sestavit** pro zkompilování aplikace.</span><span class="sxs-lookup"><span data-stu-id="8ead0-131">Right-click the CustomActivityTemplateApp project in **Solution Explorer** and choose **Build** to compile the application.</span></span>

6. <span data-ttu-id="8ead0-132">V **Průzkumník řešení** klikněte pravým tlačítkem na projekt CustomActivityTemplateApp a vyberte **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="8ead0-132">Right-click the CustomActivityTemplateApp project in **Solution Explorer** and choose **Set as Startup Project**.</span></span>

7. <span data-ttu-id="8ead0-133">Vyberte možnost **Spustit bez ladění** z nabídky **ladění** a stisknutím libovolné klávesy pokračujte po zobrazení výzvy z okna cmd. exe.</span><span class="sxs-lookup"><span data-stu-id="8ead0-133">Select **Start Without Debugging** from the **Debug** menu and press any key to continue when prompted from the cmd.exe window.</span></span>

8. <span data-ttu-id="8ead0-134">Otevřete soubor Workflow1. XAML a otevřete **sadu nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="8ead0-134">Open the Workflow1.xaml file and open the **Toolbox**.</span></span>

9. <span data-ttu-id="8ead0-135">Vyhledejte šablonu **MyDelayActivity** v kategorii **DelayActivityTemplate** .</span><span class="sxs-lookup"><span data-stu-id="8ead0-135">Locate the **MyDelayActivity** template in the **DelayActivityTemplate** category.</span></span> <span data-ttu-id="8ead0-136">Přetáhněte ji na návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="8ead0-136">Drag it onto the design surface.</span></span> <span data-ttu-id="8ead0-137">V okně **vlastnosti** potvrďte, že `Duration` vlastnost byla nastavena na 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="8ead0-137">Confirm in the **Properties** window that the `Duration` property has been set to 10 seconds.</span></span>

## <a name="example"></a><span data-ttu-id="8ead0-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="8ead0-138">Example</span></span>
 <span data-ttu-id="8ead0-139">Soubor MyDelayActivity.cs by měl obsahovat následující kód.</span><span class="sxs-lookup"><span data-stu-id="8ead0-139">The MyDelayActivity.cs file should contain the following code.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8ead0-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8ead0-140">See also</span></span>

- <xref:System.Activities.Presentation.IActivityTemplateFactory>
- [<span data-ttu-id="8ead0-141">Přizpůsobení prostředí pro návrh pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="8ead0-141">Customizing the Workflow Design Experience</span></span>](customizing-the-workflow-design-experience.md)
