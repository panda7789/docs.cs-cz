---
title: "Postupy: Přidávání ovládacích prvků bez uživatelského rozhraní do formulářů Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
f1_keywords: NonVisualSelection
helpviewer_keywords:
- invisible controls [Windows Forms]
- Windows Forms controls, adding to form
- controls [Windows Forms], nonvisual
- Windows Forms controls, nonvisual
- nonvisual controls [Windows Forms]
ms.assetid: 52134d9c-cff6-4eed-8e2b-3d5eb3bd494e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7deea3aca390ebfa4cc1fcbf16a0e898301ae434
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-controls-without-a-user-interface-to-windows-forms"></a><span data-ttu-id="33d77-102">Postupy: Přidávání ovládacích prvků bez uživatelského rozhraní do formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="33d77-102">How to: Add Controls Without a User Interface to Windows Forms</span></span>
<span data-ttu-id="33d77-103">Nevizuální ovládací prvek (nebo součást) poskytuje funkce, které vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="33d77-103">A nonvisual control (or component) provides functionality to your application.</span></span> <span data-ttu-id="33d77-104">Na rozdíl od jiných ovládacích prvků součástí neposkytují uživatelské rozhraní pro uživatele a proto není nutné zobrazit na povrchu Návrhář formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="33d77-104">Unlike other controls, components do not provide a user interface to the user and thus do not need to be displayed on the Windows Forms Designer surface.</span></span> <span data-ttu-id="33d77-105">Když součást je přidán do formuláře, zobrazí Návrhář formulářů Windows s možností změny velikosti panelu v dolní části formuláře, kde jsou zobrazeny všechny součásti.</span><span class="sxs-lookup"><span data-stu-id="33d77-105">When a component is added to a form, the Windows Forms Designer displays a resizable tray at the bottom of the form where all components are displayed.</span></span> <span data-ttu-id="33d77-106">Po přidání ovládacího prvku do komponent, můžete vybrat součásti a nastavit jeho vlastnosti, stejně jako další ovládací prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="33d77-106">Once a control has been added to the component tray, you can select the component and set its properties as you would any other control on the form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="33d77-107">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="33d77-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="33d77-108">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="33d77-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="33d77-109">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="33d77-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-a-component-to-a-windows-form"></a><span data-ttu-id="33d77-110">Chcete-li přidat součást na formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="33d77-110">To add a component to a Windows Form</span></span>  
  
1.  <span data-ttu-id="33d77-111">Otevřete formulář.</span><span class="sxs-lookup"><span data-stu-id="33d77-111">Open the form.</span></span> <span data-ttu-id="33d77-112">Podrobnosti najdete v tématu [postupy: zobrazení Windows Forms v návrháři](http://msdn.microsoft.com/en-us/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).</span><span class="sxs-lookup"><span data-stu-id="33d77-112">For details, see [How to: Display Windows Forms in the Designer](http://msdn.microsoft.com/en-us/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).</span></span>  
  
2.  <span data-ttu-id="33d77-113">V **sada nástrojů**, klikněte na komponentu a přetáhněte ji do svého formuláře.</span><span class="sxs-lookup"><span data-stu-id="33d77-113">In the **Toolbox**, click a component and drag it to your form.</span></span>  
  
     <span data-ttu-id="33d77-114">Na hlavním panelu součást se zobrazí příslušné součásti.</span><span class="sxs-lookup"><span data-stu-id="33d77-114">Your component appears in the component tray.</span></span>  
  
 <span data-ttu-id="33d77-115">Kromě toho součásti lze přidat do formuláře za běhu.</span><span class="sxs-lookup"><span data-stu-id="33d77-115">Furthermore, components can be added to a form at run time.</span></span> <span data-ttu-id="33d77-116">Toto je běžný scénář, zvlášť, protože součásti nemají výraz visual, na rozdíl od ovládací prvky, které mají uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="33d77-116">This is a common scenario, especially because components do not have a visual expression, unlike controls that have a user interface.</span></span> <span data-ttu-id="33d77-117">V příkladu níže <xref:System.Windows.Forms.Timer> přidání komponenty v době běhu.</span><span class="sxs-lookup"><span data-stu-id="33d77-117">In the example below, a <xref:System.Windows.Forms.Timer> component is added at run time.</span></span> <span data-ttu-id="33d77-118">(Všimněte si, že [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] obsahuje řadu různých časovače; v takovém případě pomocí Windows Forms <xref:System.Windows.Forms.Timer> součásti.</span><span class="sxs-lookup"><span data-stu-id="33d77-118">(Note that [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] contains a number of different timers; in this case, use a Windows Forms <xref:System.Windows.Forms.Timer> component.</span></span> <span data-ttu-id="33d77-119">Další informace o různých časovače v [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], najdete v části [Úvod do serverové časovače](http://msdn.microsoft.com/en-us/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).)</span><span class="sxs-lookup"><span data-stu-id="33d77-119">For more information about the different timers in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], see [Introduction to Server-Based Timers](http://msdn.microsoft.com/en-us/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).)</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="33d77-120">Součásti mají často prvek specifické vlastnosti, které musejí být nastaveny pro součást efektivní fungování.</span><span class="sxs-lookup"><span data-stu-id="33d77-120">Components often have control-specific properties that must be set for the component to function effectively.</span></span> <span data-ttu-id="33d77-121">U <xref:System.Windows.Forms.Timer> níže uvedené součásti, nastavíte `Interval` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="33d77-121">In the case of the <xref:System.Windows.Forms.Timer> component below, you set the `Interval` property.</span></span> <span data-ttu-id="33d77-122">Ujistěte se, při přidávání součástí do projektu, že nastavíte vlastnosti potřebné pro tuto součást.</span><span class="sxs-lookup"><span data-stu-id="33d77-122">Be sure, when adding components to your project, that you set the properties necessary for that component.</span></span>  
  
#### <a name="to-add-a-component-to-a-windows-form-programmatically"></a><span data-ttu-id="33d77-123">Chcete-li přidat součást na formuláři Windows prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="33d77-123">To add a component to a Windows Form programmatically</span></span>  
  
1.  <span data-ttu-id="33d77-124">Vytvoření instance <xref:System.Windows.Forms.Timer> – třída v kódu.</span><span class="sxs-lookup"><span data-stu-id="33d77-124">Create an instance of the <xref:System.Windows.Forms.Timer> class in code.</span></span>  
  
2.  <span data-ttu-id="33d77-125">Nastavte `Interval` vlastnosti k určení doby mezi rysky časovač.</span><span class="sxs-lookup"><span data-stu-id="33d77-125">Set the `Interval` property to determine the time between ticks of the timer.</span></span>  
  
3.  <span data-ttu-id="33d77-126">Nakonfigurujte všechny nezbytné vlastnosti pro příslušné součásti.</span><span class="sxs-lookup"><span data-stu-id="33d77-126">Configure any other necessary properties for your component.</span></span>  
  
     <span data-ttu-id="33d77-127">Následující kód ukazuje vytvoření <xref:System.Windows.Forms.Timer> s jeho `Interval` sadu vlastností.</span><span class="sxs-lookup"><span data-stu-id="33d77-127">The following code shows the creation of a <xref:System.Windows.Forms.Timer> with its `Interval` property set.</span></span>  
  
    ```vb  
    Public Sub CreateTimer()  
       Dim timerKeepTrack As New System.Windows.Forms.Timer  
       timerKeepTrack.Interval = 1000  
    End Sub  
    ```  
  
    ```csharp  
    public void createTimer()  
    {  
       System.Windows.Forms.Timer timerKeepTrack = new  
           System.Windows.Forms.Timer();  
       timerKeepTrack.Interval = 1000;  
    }  
    ```  
  
    ```cpp  
    public:  
       void createTimer()  
       {  
          System::Windows::Forms::Timer^ timerKeepTrack = gcnew  
             System::Windows::Forms::Timer();  
          timerKeepTrack->Interval = 1000;  
       }  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="33d77-128">Pod položkou škodlivý UserControl mohou být vystaveny místního počítače k ohrožení zabezpečení přes síť.</span><span class="sxs-lookup"><span data-stu-id="33d77-128">You might expose your local computer to a security risk through the network by referencing a malicious UserControl.</span></span> <span data-ttu-id="33d77-129">To může být pouze o problém v případě osoba se zlými úmysly vytváření škodlivé vlastního ovládacího prvku, za nímž následuje jste omylem ho přidáte do projektu.</span><span class="sxs-lookup"><span data-stu-id="33d77-129">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33d77-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="33d77-130">See Also</span></span>  
 [<span data-ttu-id="33d77-131">Ovládací prvky Windows Forms</span><span class="sxs-lookup"><span data-stu-id="33d77-131">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="33d77-132">Postupy: Přidání ovládacích prvků do formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="33d77-132">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [<span data-ttu-id="33d77-133">Postupy: Přidání ovládacích prvků ActiveX do formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="33d77-133">How to: Add ActiveX Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md)  
 [<span data-ttu-id="33d77-134">Postupy: kopírování ovládacích prvků mezi formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="33d77-134">How to: Copy Controls Between Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-copy-controls-between-windows-forms.md)  
 [<span data-ttu-id="33d77-135">Umístění ovládacích prvků ve formulářích Windows</span><span class="sxs-lookup"><span data-stu-id="33d77-135">Putting Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)  
 [<span data-ttu-id="33d77-136">Popisování jednotlivých Windows Forms – ovládací prvky a zajišťování zástupců pro tyto</span><span class="sxs-lookup"><span data-stu-id="33d77-136">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="33d77-137">Ovládací prvky používané ve formulářích Windows</span><span class="sxs-lookup"><span data-stu-id="33d77-137">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="33d77-138">Windows Forms – ovládací prvky podle funkce</span><span class="sxs-lookup"><span data-stu-id="33d77-138">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
