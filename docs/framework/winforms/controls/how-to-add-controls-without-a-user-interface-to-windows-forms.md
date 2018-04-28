---
title: 'Postupy: Přidávání ovládacích prvků bez uživatelského rozhraní do formulářů Windows'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- NonVisualSelection
helpviewer_keywords:
- invisible controls [Windows Forms]
- Windows Forms controls, adding to form
- controls [Windows Forms], nonvisual
- Windows Forms controls, nonvisual
- nonvisual controls [Windows Forms]
ms.assetid: 52134d9c-cff6-4eed-8e2b-3d5eb3bd494e
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e900c1c34f69531a14cfa11803ef5a6afb4783c6
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-add-controls-without-a-user-interface-to-windows-forms"></a><span data-ttu-id="7db64-102">Postupy: Přidávání ovládacích prvků bez uživatelského rozhraní do formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="7db64-102">How to: Add Controls Without a User Interface to Windows Forms</span></span>
<span data-ttu-id="7db64-103">Nevizuální ovládací prvek (nebo součást) poskytuje funkce, které vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="7db64-103">A nonvisual control (or component) provides functionality to your application.</span></span> <span data-ttu-id="7db64-104">Na rozdíl od jiných ovládacích prvků součástí neposkytují uživatelské rozhraní pro uživatele a proto není nutné zobrazit na povrchu Návrhář formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="7db64-104">Unlike other controls, components do not provide a user interface to the user and thus do not need to be displayed on the Windows Forms Designer surface.</span></span> <span data-ttu-id="7db64-105">Když součást je přidán do formuláře, zobrazí Návrhář formulářů Windows s možností změny velikosti panelu v dolní části formuláře, kde jsou zobrazeny všechny součásti.</span><span class="sxs-lookup"><span data-stu-id="7db64-105">When a component is added to a form, the Windows Forms Designer displays a resizable tray at the bottom of the form where all components are displayed.</span></span> <span data-ttu-id="7db64-106">Po přidání ovládacího prvku do komponent, můžete vybrat součásti a nastavit jeho vlastnosti, stejně jako další ovládací prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="7db64-106">Once a control has been added to the component tray, you can select the component and set its properties as you would any other control on the form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7db64-107">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="7db64-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="7db64-108">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="7db64-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="7db64-109">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="7db64-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-a-component-to-a-windows-form"></a><span data-ttu-id="7db64-110">Chcete-li přidat součást na formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="7db64-110">To add a component to a Windows Form</span></span>  
  
1.  <span data-ttu-id="7db64-111">Otevřete formulář.</span><span class="sxs-lookup"><span data-stu-id="7db64-111">Open the form.</span></span> <span data-ttu-id="7db64-112">Podrobnosti najdete v tématu [postupy: zobrazení Windows Forms v návrháři](http://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).</span><span class="sxs-lookup"><span data-stu-id="7db64-112">For details, see [How to: Display Windows Forms in the Designer](http://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).</span></span>  
  
2.  <span data-ttu-id="7db64-113">V **sada nástrojů**, klikněte na komponentu a přetáhněte ji do svého formuláře.</span><span class="sxs-lookup"><span data-stu-id="7db64-113">In the **Toolbox**, click a component and drag it to your form.</span></span>  
  
     <span data-ttu-id="7db64-114">Na hlavním panelu součást se zobrazí příslušné součásti.</span><span class="sxs-lookup"><span data-stu-id="7db64-114">Your component appears in the component tray.</span></span>  
  
 <span data-ttu-id="7db64-115">Kromě toho součásti lze přidat do formuláře za běhu.</span><span class="sxs-lookup"><span data-stu-id="7db64-115">Furthermore, components can be added to a form at run time.</span></span> <span data-ttu-id="7db64-116">Toto je běžný scénář, zvlášť, protože součásti nemají výraz visual, na rozdíl od ovládací prvky, které mají uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7db64-116">This is a common scenario, especially because components do not have a visual expression, unlike controls that have a user interface.</span></span> <span data-ttu-id="7db64-117">V příkladu níže <xref:System.Windows.Forms.Timer> přidání komponenty v době běhu.</span><span class="sxs-lookup"><span data-stu-id="7db64-117">In the example below, a <xref:System.Windows.Forms.Timer> component is added at run time.</span></span> <span data-ttu-id="7db64-118">(Všimněte si, že Visual Studio obsahuje několik různých časovače; v takovém případě pomocí Windows Forms <xref:System.Windows.Forms.Timer> součásti.</span><span class="sxs-lookup"><span data-stu-id="7db64-118">(Note that Visual Studio contains a number of different timers; in this case, use a Windows Forms <xref:System.Windows.Forms.Timer> component.</span></span> <span data-ttu-id="7db64-119">Další informace o různých časovače v sadě Visual Studio najdete v tématu [Úvod do serverové časovače](http://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).)</span><span class="sxs-lookup"><span data-stu-id="7db64-119">For more information about the different timers in Visual Studio, see [Introduction to Server-Based Timers](http://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).)</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="7db64-120">Součásti mají často prvek specifické vlastnosti, které musejí být nastaveny pro součást efektivní fungování.</span><span class="sxs-lookup"><span data-stu-id="7db64-120">Components often have control-specific properties that must be set for the component to function effectively.</span></span> <span data-ttu-id="7db64-121">U <xref:System.Windows.Forms.Timer> níže uvedené součásti, nastavíte `Interval` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7db64-121">In the case of the <xref:System.Windows.Forms.Timer> component below, you set the `Interval` property.</span></span> <span data-ttu-id="7db64-122">Ujistěte se, při přidávání součástí do projektu, že nastavíte vlastnosti potřebné pro tuto součást.</span><span class="sxs-lookup"><span data-stu-id="7db64-122">Be sure, when adding components to your project, that you set the properties necessary for that component.</span></span>  
  
#### <a name="to-add-a-component-to-a-windows-form-programmatically"></a><span data-ttu-id="7db64-123">Chcete-li přidat součást na formuláři Windows prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="7db64-123">To add a component to a Windows Form programmatically</span></span>  
  
1.  <span data-ttu-id="7db64-124">Vytvoření instance <xref:System.Windows.Forms.Timer> – třída v kódu.</span><span class="sxs-lookup"><span data-stu-id="7db64-124">Create an instance of the <xref:System.Windows.Forms.Timer> class in code.</span></span>  
  
2.  <span data-ttu-id="7db64-125">Nastavte `Interval` vlastnosti k určení doby mezi rysky časovač.</span><span class="sxs-lookup"><span data-stu-id="7db64-125">Set the `Interval` property to determine the time between ticks of the timer.</span></span>  
  
3.  <span data-ttu-id="7db64-126">Nakonfigurujte všechny nezbytné vlastnosti pro příslušné součásti.</span><span class="sxs-lookup"><span data-stu-id="7db64-126">Configure any other necessary properties for your component.</span></span>  
  
     <span data-ttu-id="7db64-127">Následující kód ukazuje vytvoření <xref:System.Windows.Forms.Timer> s jeho `Interval` sadu vlastností.</span><span class="sxs-lookup"><span data-stu-id="7db64-127">The following code shows the creation of a <xref:System.Windows.Forms.Timer> with its `Interval` property set.</span></span>  
  
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
    >  <span data-ttu-id="7db64-128">Pod položkou škodlivý UserControl mohou být vystaveny místního počítače k ohrožení zabezpečení přes síť.</span><span class="sxs-lookup"><span data-stu-id="7db64-128">You might expose your local computer to a security risk through the network by referencing a malicious UserControl.</span></span> <span data-ttu-id="7db64-129">To může být pouze o problém v případě osoba se zlými úmysly vytváření škodlivé vlastního ovládacího prvku, za nímž následuje jste omylem ho přidáte do projektu.</span><span class="sxs-lookup"><span data-stu-id="7db64-129">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7db64-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="7db64-130">See Also</span></span>  
 [<span data-ttu-id="7db64-131">Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="7db64-131">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="7db64-132">Postupy: Přidávání ovládacích prvků do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7db64-132">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [<span data-ttu-id="7db64-133">Postupy: Přidávání ovládacích prvků ActiveX do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7db64-133">How to: Add ActiveX Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md)  
 [<span data-ttu-id="7db64-134">Postupy: Kopírování ovládacích prvků mezi formuláři Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7db64-134">How to: Copy Controls Between Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-copy-controls-between-windows-forms.md)  
 [<span data-ttu-id="7db64-135">Vkládání ovládacích prvků do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7db64-135">Putting Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)  
 [<span data-ttu-id="7db64-136">Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky</span><span class="sxs-lookup"><span data-stu-id="7db64-136">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="7db64-137">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7db64-137">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="7db64-138">Ovládací prvky Windows Forms podle funkce</span><span class="sxs-lookup"><span data-stu-id="7db64-138">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
