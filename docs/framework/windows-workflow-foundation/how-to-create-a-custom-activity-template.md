---
title: "Postupy: vytvoření vlastní aktivity šablony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 772ad2a7ea56001bf3ecba089e62d6bc0f59e5ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-custom-activity-template"></a><span data-ttu-id="781bf-102">Postupy: vytvoření vlastní aktivity šablony</span><span class="sxs-lookup"><span data-stu-id="781bf-102">How to: Create a Custom Activity Template</span></span>
<span data-ttu-id="781bf-103">Vlastní aktivity šablony slouží k přizpůsobení konfigurace aktivit, včetně vlastních složené aktivit, tak, aby uživatelé nebudou mít k vytvoření jednotlivě každou aktivitu a nakonfigurovat jejich vlastnosti a další nastavení ručně.</span><span class="sxs-lookup"><span data-stu-id="781bf-103">Custom activity templates are used to customize the configuration of activities, including custom composite activities, so that users do not have to create each activity individually and configure their properties and other settings manually.</span></span> <span data-ttu-id="781bf-104">Tyto vlastní šablony může být k dispozici v **sada nástrojů** na [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] nebo opětovné hostování nástroje návrháře, ze kterého uživatelů můžete přetáhnout na předkonfigurované návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="781bf-104">These custom templates can be made available in the **Toolbox** on the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] or from a rehosted designer, from which users can drag them onto the preconfigured design surface.</span></span> [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]<span data-ttu-id="781bf-105">se dodává s dobrým příkladem takové šablony: [SendAndReceiveReply Template Designer](/visualstudio/workflow-designer/sendandreceivereply-template-designer) a [ReceiveAndSendReply Template Designer](/visualstudio/workflow-designer/receiveandsendreply-template-designer) v [návrháře aktivitslužbyzasílánízpráv](/visualstudio/workflow-designer/messaging-activity-designers) kategorie.</span><span class="sxs-lookup"><span data-stu-id="781bf-105"> ships with good examples of such templates: the [SendAndReceiveReply Template Designer](/visualstudio/workflow-designer/sendandreceivereply-template-designer) and the [ReceiveAndSendReply Template Designer](/visualstudio/workflow-designer/receiveandsendreply-template-designer) in the [Messaging Activity Designers](/visualstudio/workflow-designer/messaging-activity-designers) category.</span></span>  
  
 <span data-ttu-id="781bf-106">První postup v tomto tématu popisuje, jak vytvořit šablonu vlastní aktivity pro **zpoždění** aktivity a druhý postup stručně popisuje postupy, aby byl k dispozici v [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] k ověření, že funguje vlastní šablony.</span><span class="sxs-lookup"><span data-stu-id="781bf-106">The first procedure in this topic describes how to create a custom activity template for a **Delay** activity and the second procedure describes briefly how to make it available in a [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] to verify that the custom template works.</span></span>  
  
 <span data-ttu-id="781bf-107">Musí implementovat vlastní aktivity šablony <xref:System.Activities.Presentation.IActivityTemplateFactory>.</span><span class="sxs-lookup"><span data-stu-id="781bf-107">Custom activity templates must implement the <xref:System.Activities.Presentation.IActivityTemplateFactory>.</span></span> <span data-ttu-id="781bf-108">Rozhraní má jeden <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> metodu, pomocí kterého můžete vytvořit a nakonfigurovat instance aktivit použít v šabloně.</span><span class="sxs-lookup"><span data-stu-id="781bf-108">The interface has a single <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> method with which you can create and configure the activity instances used in the template.</span></span>  
  
### <a name="to-create-a-template-for-the-delay-activity"></a><span data-ttu-id="781bf-109">Chcete-li vytvořit šablonu aktivity zpoždění</span><span class="sxs-lookup"><span data-stu-id="781bf-109">To create a template for the Delay activity</span></span>  
  
1.  <span data-ttu-id="781bf-110">Spustit [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="781bf-110">Start [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="781bf-111">Na **soubor** nabídky, přejděte na příkaz **nový**a potom vyberte **projektu**.</span><span class="sxs-lookup"><span data-stu-id="781bf-111">On the **File** menu, point to **New**, and then select **Project**.</span></span>  
  
     <span data-ttu-id="781bf-112">**Nový projekt** otevře se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="781bf-112">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="781bf-113">V **typy projektů** podokně, vyberte **pracovního postupu** buď z **Visual C#** projekty nebo **jazyka Visual Basic** seskupení v závislosti na vaší jazykové předvolby.</span><span class="sxs-lookup"><span data-stu-id="781bf-113">In the **Project Types** pane, select **Workflow** from either the **Visual C#** projects or **Visual Basic** groupings depending on your language preference.</span></span>  
  
4.  <span data-ttu-id="781bf-114">V **šablony** podokně, vyberte **knihovna aktivit**.</span><span class="sxs-lookup"><span data-stu-id="781bf-114">In the **Templates** pane, select **Activity Library**.</span></span>  
  
5.  <span data-ttu-id="781bf-115">V **název** zadejte `DelayActivityTemplate`.</span><span class="sxs-lookup"><span data-stu-id="781bf-115">In the **Name** box, enter `DelayActivityTemplate`.</span></span>  
  
6.  <span data-ttu-id="781bf-116">Přijměte výchozí hodnoty v **umístění** a **název řešení** textová pole a pak klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="781bf-116">Accept the defaults in the **Location** and **Solution name** text boxes, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="781bf-117">Klikněte pravým tlačítkem na adresář odkazů projektu DelayActivityTemplate v **Průzkumníku řešení** a zvolte **přidat odkaz na** otevřete **přidat odkaz na** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="781bf-117">Right-click the References directory of the DelayActivityTemplate project in **Solution Explorer** and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>  
  
8.  <span data-ttu-id="781bf-118">Přejděte na **.NET** a vyberte **PresentationFramework** z **název komponenty** sloupce na levé straně a klikněte na **OK** přidáním odkazu k souboru knihovně PresentationFramework.dll.</span><span class="sxs-lookup"><span data-stu-id="781bf-118">Go to the **.NET** tab and select **PresentationFramework** from the **Component Name** column on the left and click **OK** to add a reference to the PresentationFramework.dll file.</span></span>  
  
9. <span data-ttu-id="781bf-119">Opakujte tento postup, čímž přidáte odkazy System.Activities.Presentation.dll a knihovně WindowsBase.dll soubory.</span><span class="sxs-lookup"><span data-stu-id="781bf-119">Repeat this procedure to add references to the System.Activities.Presentation.dll and the WindowsBase.dll files.</span></span>  
  
10. <span data-ttu-id="781bf-120">Klikněte pravým tlačítkem na projekt DelayActivityTemplate **Průzkumníku řešení** a zvolte **přidat** a potom **nová položka** otevřete **přidat novou položku**dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="781bf-120">Right-click the DelayActivityTemplate project in **Solution Explorer** and choose **Add** and then **New Item** to open the **Add New Item** dialog box.</span></span>  
  
11. <span data-ttu-id="781bf-121">Vyberte **třída** název MyDelayTemplate šablony a pak klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="781bf-121">Select the **Class** template, name it MyDelayTemplate, and then click **OK**.</span></span>  
  
12. <span data-ttu-id="781bf-122">Otevřete soubor MyDelayTemplate.cs a přidejte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="781bf-122">Open the MyDelayTemplate.cs file and add the following statements.</span></span>  
  
    ```  
    //Namespaces added  
    using System.Activities;  
    using System.Activities.Statements;  
    using System.Activities.Presentation;  
    using System.Windows;  
    ```  
  
13. <span data-ttu-id="781bf-123">Implementace <xref:System.Activities.Presentation.IActivityTemplateFactory> s `MyDelayActivity` třídy následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="781bf-123">Implement the <xref:System.Activities.Presentation.IActivityTemplateFactory> with the `MyDelayActivity` class with the following code.</span></span> <span data-ttu-id="781bf-124">Tím se nakonfiguruje zpoždění tak, aby měl v délce 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="781bf-124">This configures the delay to have a duration of 10 seconds.</span></span>  
  
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
  
14. <span data-ttu-id="781bf-125">Vyberte **sestavit řešení** z **sestavení** nabídky pro generování souboru DelayActivityTemplate.dll.</span><span class="sxs-lookup"><span data-stu-id="781bf-125">Select **Build Solution** from the **Build** menu to generate the DelayActivityTemplate.dll file.</span></span>  
  
### <a name="to-make-the-template-available-in-a-workflow-designer"></a><span data-ttu-id="781bf-126">Chcete-li šablonu k dispozici v Návrháři pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="781bf-126">To make the template available in a Workflow Designer</span></span>  
  
1.  <span data-ttu-id="781bf-127">Klikněte pravým tlačítkem na řešení DelayActivityTemplate v **Průzkumníku řešení** a zvolte **přidat** a potom **nový projekt** otevřete **přidat nový projekt** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="781bf-127">Right-click the DelayActivityTemplate solution in **Solution Explorer** and choose **Add** and then **New Project** to open the **Add New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="781bf-128">Vyberte **pracovního postupu konzolové aplikace** šablony, pojmenujte ji `CustomActivityTemplateApp`a potom klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="781bf-128">Select the **Workflow Console Application** template, name it `CustomActivityTemplateApp`, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="781bf-129">Klikněte pravým tlačítkem na adresář odkazů projektu CustomActivityTemplateApp v **Průzkumníku řešení** a zvolte **přidat odkaz na** otevřete **přidat odkaz na** dialogové okno pole.</span><span class="sxs-lookup"><span data-stu-id="781bf-129">Right-click the References directory of the CustomActivityTemplateApp project in **Solution Explorer** and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>  
  
4.  <span data-ttu-id="781bf-130">Přejděte na **projekty** a vyberte **DelayActivityTemplate** z **název projektu** sloupce na levé straně a klikněte na **OK** přidat odkaz na soubor DelayActivityTemplate.dll, který jste vytvořili v prvním postupu.</span><span class="sxs-lookup"><span data-stu-id="781bf-130">Go to the **Projects** tab and select **DelayActivityTemplate** from the **Project Name** column on the left and click **OK** to add a reference to the DelayActivityTemplate.dll file that you created in the first procedure.</span></span>  
  
5.  <span data-ttu-id="781bf-131">Klikněte pravým tlačítkem na projekt CustomActivityTemplateApp **Průzkumníku řešení** a zvolte **sestavení** kompilace aplikace.</span><span class="sxs-lookup"><span data-stu-id="781bf-131">Right-click the CustomActivityTemplateApp project in **Solution Explorer** and choose **Build** to compile the application.</span></span>  
  
6.  <span data-ttu-id="781bf-132">Klikněte pravým tlačítkem na projekt CustomActivityTemplateApp **Průzkumníku řešení** a zvolte **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="781bf-132">Right-click the CustomActivityTemplateApp project in **Solution Explorer** and choose **Set as Startup Project**.</span></span>  
  
7.  <span data-ttu-id="781bf-133">Vyberte **spustit bez ladění** z **ladění** nabídky a stiskněte klávesu žádné klíče z okna cmd.exe pokračovat po zobrazení výzvy.</span><span class="sxs-lookup"><span data-stu-id="781bf-133">Select **Start Without Debugging** from the **Debug** menu and press any key to continue when prompted from the cmd.exe window.</span></span>  
  
8.  <span data-ttu-id="781bf-134">Otevřete soubor Workflow1.xaml a otevřete **sada nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="781bf-134">Open the Workflow1.xaml file and open the **Toolbox**.</span></span>  
  
9. <span data-ttu-id="781bf-135">Vyhledejte **MyDelayActivity** šablonu **DelayActivityTemplate** kategorie.</span><span class="sxs-lookup"><span data-stu-id="781bf-135">Locate the **MyDelayActivity** template in the **DelayActivityTemplate** category.</span></span> <span data-ttu-id="781bf-136">Přetáhněte ji na návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="781bf-136">Drag it onto the design surface.</span></span> <span data-ttu-id="781bf-137">Potvrďte v **vlastnosti** okno, `Duration` vlastnost byla nastavena na 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="781bf-137">Confirm in the **Properties** window that the `Duration` property has been set to 10 seconds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="781bf-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="781bf-138">Example</span></span>  
 <span data-ttu-id="781bf-139">Soubor MyDelayActivity.cs by měl obsahovat následující kód.</span><span class="sxs-lookup"><span data-stu-id="781bf-139">The MyDelayActivity.cs file should contain the following code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="781bf-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="781bf-140">See Also</span></span>  
 <xref:System.Activities.Presentation.IActivityTemplateFactory>  
 [<span data-ttu-id="781bf-141">Přizpůsobení prostředí pro návrh pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="781bf-141">Customizing the Workflow Design Experience</span></span>](../../../docs/framework/windows-workflow-foundation/customizing-the-workflow-design-experience.md)
