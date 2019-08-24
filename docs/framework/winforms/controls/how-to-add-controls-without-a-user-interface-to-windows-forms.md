---
title: 'Postupy: Přidávání ovládacích prvků bez uživatelského rozhraní do Windows Forms'
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
ms.openlocfilehash: bc1f844e5a2cf4d4f3b64ebf20e935f36ff85e12
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987090"
---
# <a name="how-to-add-controls-without-a-user-interface-to-windows-forms"></a><span data-ttu-id="e0e00-102">Postupy: Přidávání ovládacích prvků bez uživatelského rozhraní do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e0e00-102">How to: Add Controls Without a User Interface to Windows Forms</span></span>

<span data-ttu-id="e0e00-103">Nevizuální ovládací prvek (nebo komponenta) poskytuje vaší aplikaci funkce.</span><span class="sxs-lookup"><span data-stu-id="e0e00-103">A nonvisual control (or component) provides functionality to your application.</span></span> <span data-ttu-id="e0e00-104">Na rozdíl od jiných ovládacích prvků komponenty neposkytují uživatelské rozhraní uživateli, a proto nemusí být zobrazeny na Návrhář formulářů ploše.</span><span class="sxs-lookup"><span data-stu-id="e0e00-104">Unlike other controls, components do not provide a user interface to the user and thus do not need to be displayed on the Windows Forms Designer surface.</span></span> <span data-ttu-id="e0e00-105">Když je do formuláře přidána součást, Návrhář formulářů zobrazí v dolní části formuláře, kde jsou zobrazeny všechny komponenty, zásobník s možností změny velikosti.</span><span class="sxs-lookup"><span data-stu-id="e0e00-105">When a component is added to a form, the Windows Forms Designer displays a resizable tray at the bottom of the form where all components are displayed.</span></span> <span data-ttu-id="e0e00-106">Po přidání ovládacího prvku do zásobníku komponenty můžete vybrat komponentu a nastavit její vlastnosti stejným způsobem jako jakýkoli jiný ovládací prvek ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="e0e00-106">Once a control has been added to the component tray, you can select the component and set its properties as you would any other control on the form.</span></span>

## <a name="add-a-component-to-a-windows-form"></a><span data-ttu-id="e0e00-107">Přidání komponenty do formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="e0e00-107">Add a component to a Windows Form</span></span>

1. <span data-ttu-id="e0e00-108">Otevřete formulář v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e0e00-108">Open the form in Visual Studio.</span></span> <span data-ttu-id="e0e00-109">Podrobnosti najdete v tématu [How to: Zobrazit model Windows Forms v Návrháři](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e0e00-109">For details, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>

2. <span data-ttu-id="e0e00-110">V sadě **nástrojů**klikněte na součást a přetáhněte ji do formuláře.</span><span class="sxs-lookup"><span data-stu-id="e0e00-110">In the **Toolbox**, click a component and drag it to your form.</span></span>

     <span data-ttu-id="e0e00-111">Vaše komponenta se zobrazí v zásobníku součásti.</span><span class="sxs-lookup"><span data-stu-id="e0e00-111">Your component appears in the component tray.</span></span>

<span data-ttu-id="e0e00-112">Kromě toho je možné přidat komponenty do formuláře za běhu.</span><span class="sxs-lookup"><span data-stu-id="e0e00-112">Furthermore, components can be added to a form at run time.</span></span> <span data-ttu-id="e0e00-113">Toto je běžný scénář, zejména protože komponenty nemají vizuální výraz, na rozdíl od ovládacích prvků, které mají uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e0e00-113">This is a common scenario, especially because components do not have a visual expression, unlike controls that have a user interface.</span></span> <span data-ttu-id="e0e00-114">V následujícím <xref:System.Windows.Forms.Timer> příkladu je přidána komponenta v době běhu.</span><span class="sxs-lookup"><span data-stu-id="e0e00-114">In the example below, a <xref:System.Windows.Forms.Timer> component is added at run time.</span></span> <span data-ttu-id="e0e00-115">(Všimněte si, že Visual Studio obsahuje několik různých časovačů. v takovém případě použijte model Windows Forms <xref:System.Windows.Forms.Timer> komponentu.</span><span class="sxs-lookup"><span data-stu-id="e0e00-115">(Note that Visual Studio contains a number of different timers; in this case, use a Windows Forms <xref:System.Windows.Forms.Timer> component.</span></span> <span data-ttu-id="e0e00-116">Další informace o různých časovačích v aplikaci Visual Studio naleznete v tématu [Úvod do časovačů na serveru](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).)</span><span class="sxs-lookup"><span data-stu-id="e0e00-116">For more information about the different timers in Visual Studio, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).)</span></span>

> [!CAUTION]
> <span data-ttu-id="e0e00-117">Komponenty mají často vlastnosti specifické pro ovládací prvky, které je třeba nastavit, aby součást fungovala efektivně.</span><span class="sxs-lookup"><span data-stu-id="e0e00-117">Components often have control-specific properties that must be set for the component to function effectively.</span></span> <span data-ttu-id="e0e00-118">V případě <xref:System.Windows.Forms.Timer> komponenty níže `Interval` nastavte vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e0e00-118">In the case of the <xref:System.Windows.Forms.Timer> component below, you set the `Interval` property.</span></span> <span data-ttu-id="e0e00-119">Ujistěte se, že při přidávání součástí do projektu jste nastavili vlastnosti nezbytné pro danou součást.</span><span class="sxs-lookup"><span data-stu-id="e0e00-119">Be sure, when adding components to your project, that you set the properties necessary for that component.</span></span>

## <a name="add-a-component-to-a-windows-form-programmatically"></a><span data-ttu-id="e0e00-120">Programové přidání komponenty do formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="e0e00-120">Add a component to a Windows Form programmatically</span></span>

1. <span data-ttu-id="e0e00-121">Vytvoří instanci <xref:System.Windows.Forms.Timer> třídy v kódu.</span><span class="sxs-lookup"><span data-stu-id="e0e00-121">Create an instance of the <xref:System.Windows.Forms.Timer> class in code.</span></span>

2. <span data-ttu-id="e0e00-122">`Interval` Nastavte vlastnost tak, aby určovala dobu mezi takty časovače.</span><span class="sxs-lookup"><span data-stu-id="e0e00-122">Set the `Interval` property to determine the time between ticks of the timer.</span></span>

3. <span data-ttu-id="e0e00-123">Nakonfigurujte všechny další nezbytné vlastnosti pro komponentu.</span><span class="sxs-lookup"><span data-stu-id="e0e00-123">Configure any other necessary properties for your component.</span></span>

     <span data-ttu-id="e0e00-124">Následující kód ukazuje vytvoření a <xref:System.Windows.Forms.Timer> `Interval` s nastavenou vlastností.</span><span class="sxs-lookup"><span data-stu-id="e0e00-124">The following code shows the creation of a <xref:System.Windows.Forms.Timer> with its `Interval` property set.</span></span>

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
    > <span data-ttu-id="e0e00-125">Místní počítač můžete vystavit bezpečnostnímu riziku prostřednictvím sítě odkazem na škodlivý prvek UserControl.</span><span class="sxs-lookup"><span data-stu-id="e0e00-125">You might expose your local computer to a security risk through the network by referencing a malicious UserControl.</span></span> <span data-ttu-id="e0e00-126">To by mělo být obavy jenom v případě, že by škodlivá osoba vytvořila škodlivý vlastní ovládací prvek, a pak ji nepřidali do projektu omylem.</span><span class="sxs-lookup"><span data-stu-id="e0e00-126">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="e0e00-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e0e00-127">See also</span></span>

- [<span data-ttu-id="e0e00-128">Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="e0e00-128">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="e0e00-129">Postupy: Přidat ovládací prvky do model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e0e00-129">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
- [<span data-ttu-id="e0e00-130">Postupy: Přidat ovládací prvky ActiveX do model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e0e00-130">How to: Add ActiveX Controls to Windows Forms</span></span>](how-to-add-activex-controls-to-windows-forms.md)
- [<span data-ttu-id="e0e00-131">Vkládání ovládacích prvků do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e0e00-131">Putting Controls on Windows Forms</span></span>](putting-controls-on-windows-forms.md)
- [<span data-ttu-id="e0e00-132">Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky</span><span class="sxs-lookup"><span data-stu-id="e0e00-132">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="e0e00-133">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e0e00-133">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="e0e00-134">Ovládací prvky Windows Forms podle funkce</span><span class="sxs-lookup"><span data-stu-id="e0e00-134">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
