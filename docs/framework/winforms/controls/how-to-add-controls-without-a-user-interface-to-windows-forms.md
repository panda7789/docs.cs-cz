---
title: Přidání ovládacích prvků bez uživatelského rozhraní
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
ms.openlocfilehash: 43f13b4f009fcd6e5d82fa2c00113a77d48877b6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744754"
---
# <a name="how-to-add-controls-without-a-user-interface-to-windows-forms"></a><span data-ttu-id="bc65a-102">Postupy: Přidávání ovládacích prvků bez uživatelského rozhraní do formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="bc65a-102">How to: Add Controls Without a User Interface to Windows Forms</span></span>

<span data-ttu-id="bc65a-103">Nevizuální ovládací prvek (nebo komponenta) poskytuje vaší aplikaci funkce.</span><span class="sxs-lookup"><span data-stu-id="bc65a-103">A nonvisual control (or component) provides functionality to your application.</span></span> <span data-ttu-id="bc65a-104">Na rozdíl od jiných ovládacích prvků komponenty neposkytují uživatelské rozhraní uživateli, a proto nemusí být zobrazeny na Návrhář formulářů ploše.</span><span class="sxs-lookup"><span data-stu-id="bc65a-104">Unlike other controls, components do not provide a user interface to the user and thus do not need to be displayed on the Windows Forms Designer surface.</span></span> <span data-ttu-id="bc65a-105">Když je do formuláře přidána součást, Návrhář formulářů zobrazí v dolní části formuláře, kde jsou zobrazeny všechny komponenty, zásobník s možností změny velikosti.</span><span class="sxs-lookup"><span data-stu-id="bc65a-105">When a component is added to a form, the Windows Forms Designer displays a resizable tray at the bottom of the form where all components are displayed.</span></span> <span data-ttu-id="bc65a-106">Po přidání ovládacího prvku do zásobníku komponenty můžete vybrat komponentu a nastavit její vlastnosti stejným způsobem jako jakýkoli jiný ovládací prvek ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="bc65a-106">Once a control has been added to the component tray, you can select the component and set its properties as you would any other control on the form.</span></span>

## <a name="add-a-component-to-a-windows-form"></a><span data-ttu-id="bc65a-107">Přidání komponenty do formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="bc65a-107">Add a component to a Windows Form</span></span>

1. <span data-ttu-id="bc65a-108">Otevřete formulář v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bc65a-108">Open the form in Visual Studio.</span></span> <span data-ttu-id="bc65a-109">Podrobnosti naleznete v tématu [How to: Display model Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="bc65a-109">For details, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>

2. <span data-ttu-id="bc65a-110">V sadě **nástrojů**klikněte na součást a přetáhněte ji do formuláře.</span><span class="sxs-lookup"><span data-stu-id="bc65a-110">In the **Toolbox**, click a component and drag it to your form.</span></span>

     <span data-ttu-id="bc65a-111">Vaše komponenta se zobrazí v zásobníku součásti.</span><span class="sxs-lookup"><span data-stu-id="bc65a-111">Your component appears in the component tray.</span></span>

<span data-ttu-id="bc65a-112">Kromě toho je možné přidat komponenty do formuláře za běhu.</span><span class="sxs-lookup"><span data-stu-id="bc65a-112">Furthermore, components can be added to a form at run time.</span></span> <span data-ttu-id="bc65a-113">Toto je běžný scénář, zejména protože komponenty nemají vizuální výraz, na rozdíl od ovládacích prvků, které mají uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bc65a-113">This is a common scenario, especially because components do not have a visual expression, unlike controls that have a user interface.</span></span> <span data-ttu-id="bc65a-114">V následujícím příkladu je přidána komponenta <xref:System.Windows.Forms.Timer> v době běhu.</span><span class="sxs-lookup"><span data-stu-id="bc65a-114">In the example below, a <xref:System.Windows.Forms.Timer> component is added at run time.</span></span> <span data-ttu-id="bc65a-115">(Všimněte si, že Visual Studio obsahuje několik různých časovačů. v takovém případě použijte komponentu model Windows Forms <xref:System.Windows.Forms.Timer>.</span><span class="sxs-lookup"><span data-stu-id="bc65a-115">(Note that Visual Studio contains a number of different timers; in this case, use a Windows Forms <xref:System.Windows.Forms.Timer> component.</span></span> <span data-ttu-id="bc65a-116">Další informace o různých časovačích v aplikaci Visual Studio naleznete v tématu [Úvod do časovačů na serveru](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).)</span><span class="sxs-lookup"><span data-stu-id="bc65a-116">For more information about the different timers in Visual Studio, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).)</span></span>

> [!CAUTION]
> <span data-ttu-id="bc65a-117">Komponenty mají často vlastnosti specifické pro ovládací prvky, které je třeba nastavit, aby součást fungovala efektivně.</span><span class="sxs-lookup"><span data-stu-id="bc65a-117">Components often have control-specific properties that must be set for the component to function effectively.</span></span> <span data-ttu-id="bc65a-118">V případě <xref:System.Windows.Forms.Timer> komponenty níže nastavte vlastnost `Interval`.</span><span class="sxs-lookup"><span data-stu-id="bc65a-118">In the case of the <xref:System.Windows.Forms.Timer> component below, you set the `Interval` property.</span></span> <span data-ttu-id="bc65a-119">Ujistěte se, že při přidávání součástí do projektu jste nastavili vlastnosti nezbytné pro danou součást.</span><span class="sxs-lookup"><span data-stu-id="bc65a-119">Be sure, when adding components to your project, that you set the properties necessary for that component.</span></span>

## <a name="add-a-component-to-a-windows-form-programmatically"></a><span data-ttu-id="bc65a-120">Programové přidání komponenty do formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="bc65a-120">Add a component to a Windows Form programmatically</span></span>

1. <span data-ttu-id="bc65a-121">Vytvoří instanci třídy <xref:System.Windows.Forms.Timer> v kódu.</span><span class="sxs-lookup"><span data-stu-id="bc65a-121">Create an instance of the <xref:System.Windows.Forms.Timer> class in code.</span></span>

2. <span data-ttu-id="bc65a-122">Nastavením vlastnosti `Interval` určíte dobu mezi takty časovače.</span><span class="sxs-lookup"><span data-stu-id="bc65a-122">Set the `Interval` property to determine the time between ticks of the timer.</span></span>

3. <span data-ttu-id="bc65a-123">Nakonfigurujte všechny další nezbytné vlastnosti pro komponentu.</span><span class="sxs-lookup"><span data-stu-id="bc65a-123">Configure any other necessary properties for your component.</span></span>

     <span data-ttu-id="bc65a-124">Následující kód ukazuje vytvoření <xref:System.Windows.Forms.Timer> s nastavenou vlastností `Interval`.</span><span class="sxs-lookup"><span data-stu-id="bc65a-124">The following code shows the creation of a <xref:System.Windows.Forms.Timer> with its `Interval` property set.</span></span>

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
    > <span data-ttu-id="bc65a-125">Místní počítač můžete vystavit bezpečnostnímu riziku prostřednictvím sítě odkazem na škodlivý prvek UserControl.</span><span class="sxs-lookup"><span data-stu-id="bc65a-125">You might expose your local computer to a security risk through the network by referencing a malicious UserControl.</span></span> <span data-ttu-id="bc65a-126">To by mělo být obavy jenom v případě, že by škodlivá osoba vytvořila škodlivý vlastní ovládací prvek, a pak ji nepřidali do projektu omylem.</span><span class="sxs-lookup"><span data-stu-id="bc65a-126">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="bc65a-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bc65a-127">See also</span></span>

- [<span data-ttu-id="bc65a-128">Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="bc65a-128">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="bc65a-129">Postupy: Přidávání ovládacích prvků do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bc65a-129">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
- [<span data-ttu-id="bc65a-130">Postupy: Přidávání ovládacích prvků ActiveX do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bc65a-130">How to: Add ActiveX Controls to Windows Forms</span></span>](how-to-add-activex-controls-to-windows-forms.md)
- [<span data-ttu-id="bc65a-131">Vkládání ovládacích prvků do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bc65a-131">Putting Controls on Windows Forms</span></span>](putting-controls-on-windows-forms.md)
- [<span data-ttu-id="bc65a-132">Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky</span><span class="sxs-lookup"><span data-stu-id="bc65a-132">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="bc65a-133">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bc65a-133">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="bc65a-134">Ovládací prvky Windows Forms podle funkce</span><span class="sxs-lookup"><span data-stu-id="bc65a-134">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
