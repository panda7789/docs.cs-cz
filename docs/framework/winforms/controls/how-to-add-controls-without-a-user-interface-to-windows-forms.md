---
title: 'Postupy: Přidání ovládacích prvků bez uživatelského rozhraní do formulářů Windows'
ms.date: 03/30/2017
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
ms.openlocfilehash: 26685ff0ff67ac3b7f1b9837cc71cfc0e683b292
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2019
ms.locfileid: "56442110"
---
# <a name="how-to-add-controls-without-a-user-interface-to-windows-forms"></a><span data-ttu-id="ffa45-102">Postupy: Přidání ovládacích prvků bez uživatelského rozhraní do formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="ffa45-102">How to: Add Controls Without a User Interface to Windows Forms</span></span>
<span data-ttu-id="ffa45-103">Nevizuální ovládací prvek (nebo komponenta) poskytuje funkce, které vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="ffa45-103">A nonvisual control (or component) provides functionality to your application.</span></span> <span data-ttu-id="ffa45-104">Na rozdíl od jiných ovládacích prvků součástí neposkytují uživatelského rozhraní pro uživatele a proto není potřeba zobrazovat na plochu návrháře formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="ffa45-104">Unlike other controls, components do not provide a user interface to the user and thus do not need to be displayed on the Windows Forms Designer surface.</span></span> <span data-ttu-id="ffa45-105">Při přidání komponenty do formuláře, zobrazí Návrhář formulářů Windows umožňující změnu velikosti na hlavním panelu v dolní části formuláře, ve kterém jsou zobrazeny všechny součásti.</span><span class="sxs-lookup"><span data-stu-id="ffa45-105">When a component is added to a form, the Windows Forms Designer displays a resizable tray at the bottom of the form where all components are displayed.</span></span> <span data-ttu-id="ffa45-106">Jakmile ovládací prvek byl přidán do panelu komponent, můžete vybrat komponentu a nastavit jeho vlastnosti, stejně jako jakýkoli jiný ovládací prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="ffa45-106">Once a control has been added to the component tray, you can select the component and set its properties as you would any other control on the form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ffa45-107">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="ffa45-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="ffa45-108">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="ffa45-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="ffa45-109">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="ffa45-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-a-component-to-a-windows-form"></a><span data-ttu-id="ffa45-110">K přidání komponenty do formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="ffa45-110">To add a component to a Windows Form</span></span>  
  
1.  <span data-ttu-id="ffa45-111">Otevřete formulář.</span><span class="sxs-lookup"><span data-stu-id="ffa45-111">Open the form.</span></span> <span data-ttu-id="ffa45-112">Podrobnosti najdete v tématu [jak: Zobrazení formulářů Windows v návrháři](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ffa45-112">For details, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>  
  
2.  <span data-ttu-id="ffa45-113">V **nástrojů**, klikněte na komponentu a přetáhněte ji do svého formuláře.</span><span class="sxs-lookup"><span data-stu-id="ffa45-113">In the **Toolbox**, click a component and drag it to your form.</span></span>  
  
     <span data-ttu-id="ffa45-114">V panelu komponent se zobrazí vaše komponenta.</span><span class="sxs-lookup"><span data-stu-id="ffa45-114">Your component appears in the component tray.</span></span>  
  
 <span data-ttu-id="ffa45-115">Kromě toho můžete přidávat součásti do formuláře v době běhu.</span><span class="sxs-lookup"><span data-stu-id="ffa45-115">Furthermore, components can be added to a form at run time.</span></span> <span data-ttu-id="ffa45-116">Totiž běžný scénář, zejména komponenty nemají visual výrazu, na rozdíl od ovládacích prvků, které mají uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ffa45-116">This is a common scenario, especially because components do not have a visual expression, unlike controls that have a user interface.</span></span> <span data-ttu-id="ffa45-117">V následujícím příkladu <xref:System.Windows.Forms.Timer> přidání komponenty v době běhu.</span><span class="sxs-lookup"><span data-stu-id="ffa45-117">In the example below, a <xref:System.Windows.Forms.Timer> component is added at run time.</span></span> <span data-ttu-id="ffa45-118">(Všimněte si, že Visual Studio obsahuje několik různých časovače; v takovém případě použijte prvku Windows Forms <xref:System.Windows.Forms.Timer> komponenty.</span><span class="sxs-lookup"><span data-stu-id="ffa45-118">(Note that Visual Studio contains a number of different timers; in this case, use a Windows Forms <xref:System.Windows.Forms.Timer> component.</span></span> <span data-ttu-id="ffa45-119">Další informace o různých časovače v sadě Visual Studio najdete v tématu [Úvod do serverových časovače](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).)</span><span class="sxs-lookup"><span data-stu-id="ffa45-119">For more information about the different timers in Visual Studio, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).)</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="ffa45-120">Součásti mají často vlastnosti specifické pro ovládací prvek, které musí být nastavena pro komponentu funkce efektivně.</span><span class="sxs-lookup"><span data-stu-id="ffa45-120">Components often have control-specific properties that must be set for the component to function effectively.</span></span> <span data-ttu-id="ffa45-121">V případě třídy <xref:System.Windows.Forms.Timer> součásti, můžete nastavit `Interval` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ffa45-121">In the case of the <xref:System.Windows.Forms.Timer> component below, you set the `Interval` property.</span></span> <span data-ttu-id="ffa45-122">Ujistěte se, při přidávání součástí do projektu, nastavit vlastnosti pro tuto součást.</span><span class="sxs-lookup"><span data-stu-id="ffa45-122">Be sure, when adding components to your project, that you set the properties necessary for that component.</span></span>  
  
#### <a name="to-add-a-component-to-a-windows-form-programmatically"></a><span data-ttu-id="ffa45-123">K přidání komponenty do formuláře Windows prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="ffa45-123">To add a component to a Windows Form programmatically</span></span>  
  
1.  <span data-ttu-id="ffa45-124">Vytvoření instance <xref:System.Windows.Forms.Timer> třídu v kódu.</span><span class="sxs-lookup"><span data-stu-id="ffa45-124">Create an instance of the <xref:System.Windows.Forms.Timer> class in code.</span></span>  
  
2.  <span data-ttu-id="ffa45-125">Nastavte `Interval` a určí čas mezi značkami časovače.</span><span class="sxs-lookup"><span data-stu-id="ffa45-125">Set the `Interval` property to determine the time between ticks of the timer.</span></span>  
  
3.  <span data-ttu-id="ffa45-126">Nakonfigurujte další nezbytné vlastnosti pro komponentu.</span><span class="sxs-lookup"><span data-stu-id="ffa45-126">Configure any other necessary properties for your component.</span></span>  
  
     <span data-ttu-id="ffa45-127">Následující kód ukazuje vytvoření objektu <xref:System.Windows.Forms.Timer> s jeho `Interval` sadu vlastností.</span><span class="sxs-lookup"><span data-stu-id="ffa45-127">The following code shows the creation of a <xref:System.Windows.Forms.Timer> with its `Interval` property set.</span></span>  
  
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
    >  <span data-ttu-id="ffa45-128">Pomocí odkazu na škodlivý uživatelský ovládací prvek může zveřejnit místního počítače k ohrožení zabezpečení prostřednictvím sítě.</span><span class="sxs-lookup"><span data-stu-id="ffa45-128">You might expose your local computer to a security risk through the network by referencing a malicious UserControl.</span></span> <span data-ttu-id="ffa45-129">To může být pouze v případě nežádoucí osoba vytváření škodlivé vlastního ovládacího prvku, za nímž následuje omylem přidání do projektu žádný problém.</span><span class="sxs-lookup"><span data-stu-id="ffa45-129">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffa45-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ffa45-130">See also</span></span>
- [<span data-ttu-id="ffa45-131">Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="ffa45-131">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)
- [<span data-ttu-id="ffa45-132">Postupy: Přidání ovládacích prvků do formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="ffa45-132">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
- [<span data-ttu-id="ffa45-133">Postupy: Přidávání ovládacích prvků ActiveX do formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="ffa45-133">How to: Add ActiveX Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md)
- [<span data-ttu-id="ffa45-134">Postupy: Kopírování ovládacích prvků mezi formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="ffa45-134">How to: Copy Controls Between Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-copy-controls-between-windows-forms.md)
- [<span data-ttu-id="ffa45-135">Vkládání ovládacích prvků do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ffa45-135">Putting Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)
- [<span data-ttu-id="ffa45-136">Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky</span><span class="sxs-lookup"><span data-stu-id="ffa45-136">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="ffa45-137">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ffa45-137">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="ffa45-138">Ovládací prvky Windows Forms podle funkce</span><span class="sxs-lookup"><span data-stu-id="ffa45-138">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
