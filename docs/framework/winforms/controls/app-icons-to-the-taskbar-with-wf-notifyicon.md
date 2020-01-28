---
title: Přidání ikon aplikace na hlavní panel se součástí NotifyIcon
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- TrayIcon
helpviewer_keywords:
- status area icons
- icons [Windows Forms], adding to taskbar
- NotifyIcon component
- taskbar [Windows Forms], adding icons
ms.assetid: d28c0fe6-aaf2-4df7-ad74-928d861a8510
ms.openlocfilehash: 46b50ecaabe75dba08fea922d7b5639031692269
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746245"
---
# <a name="how-to-add-application-icons-to-the-taskbar-with-the-windows-forms-notifyicon-component"></a><span data-ttu-id="b6714-102">Postupy: Přidání ikon aplikací do TaskBar se součástí Windows Forms NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="b6714-102">How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component</span></span>

<span data-ttu-id="b6714-103">Komponenta model Windows Forms <xref:System.Windows.Forms.NotifyIcon> zobrazí v oznamovací oblasti hlavního panelu jednu ikonu.</span><span class="sxs-lookup"><span data-stu-id="b6714-103">The Windows Forms <xref:System.Windows.Forms.NotifyIcon> component displays a single icon in the status notification area of the taskbar.</span></span> <span data-ttu-id="b6714-104">Chcete-li zobrazit více ikon ve stavové oblasti, je nutné mít na formuláři více <xref:System.Windows.Forms.NotifyIcon>ch součástí.</span><span class="sxs-lookup"><span data-stu-id="b6714-104">To display multiple icons in the status area, you must have multiple <xref:System.Windows.Forms.NotifyIcon> components on your form.</span></span> <span data-ttu-id="b6714-105">Chcete-li nastavit ikonu zobrazenou pro ovládací prvek, použijte vlastnost <xref:System.Windows.Forms.NotifyIcon.Icon%2A>.</span><span class="sxs-lookup"><span data-stu-id="b6714-105">To set the icon displayed for a control, use the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property.</span></span> <span data-ttu-id="b6714-106">Můžete také napsat kód v obslužné rutině události <xref:System.Windows.Forms.NotifyIcon.DoubleClick>, aby k nějakému problému došlo, když uživatel dvakrát klikne na ikonu.</span><span class="sxs-lookup"><span data-stu-id="b6714-106">You can also write code in the <xref:System.Windows.Forms.NotifyIcon.DoubleClick> event handler so that something happens when the user double-clicks the icon.</span></span> <span data-ttu-id="b6714-107">Můžete například vytvořit dialogové okno pro uživatele, aby se nakonfiguroval proces na pozadí reprezentovaný ikonou.</span><span class="sxs-lookup"><span data-stu-id="b6714-107">For example, you could make a dialog box appear for the user to configure the background process represented by the icon.</span></span>

> [!NOTE]
> <span data-ttu-id="b6714-108">Komponenta <xref:System.Windows.Forms.NotifyIcon> se používá pouze pro účely oznámení, aby bylo možné upozornit uživatele, že došlo k akci nebo události, nebo došlo ke změně stavu nějakého řazení.</span><span class="sxs-lookup"><span data-stu-id="b6714-108">The <xref:System.Windows.Forms.NotifyIcon> component is used for notification purposes only, to alert users that an action or event has occurred or there has been a change in status of some sort.</span></span> <span data-ttu-id="b6714-109">Pro standardní interakci s aplikacemi byste měli použít nabídky, panely nástrojů a jiné prvky uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b6714-109">You should use menus, toolbars, and other user-interface elements for standard interaction with applications.</span></span>

### <a name="to-set-the-icon"></a><span data-ttu-id="b6714-110">Nastavení ikony</span><span class="sxs-lookup"><span data-stu-id="b6714-110">To set the icon</span></span>

1. <span data-ttu-id="b6714-111">Přiřaďte hodnotu k vlastnosti <xref:System.Windows.Forms.NotifyIcon.Icon%2A>.</span><span class="sxs-lookup"><span data-stu-id="b6714-111">Assign a value to the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property.</span></span> <span data-ttu-id="b6714-112">Hodnota musí být typu `System.Drawing.Icon` a může být načtena ze souboru. ico.</span><span class="sxs-lookup"><span data-stu-id="b6714-112">The value must be of type `System.Drawing.Icon` and can be loaded from an .ico file.</span></span> <span data-ttu-id="b6714-113">Můžete určit soubor ikony v kódu nebo kliknutím na tlačítko se třemi tečkami (![tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual Studio.](./media/visual-studio-ellipsis-button.png)) vedle vlastnosti <xref:System.Windows.Forms.NotifyIcon.Icon%2A> v okně **vlastnosti** a pak tento soubor vybrat v dialogovém okně **otevřít** , které se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="b6714-113">You can specify the icon file in code or by clicking the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property in the **Properties** window, and then selecting the file in the **Open** dialog box that appears.</span></span>

2. <span data-ttu-id="b6714-114">Nastavte <xref:System.Windows.Forms.NotifyIcon.Visible%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="b6714-114">Set the <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property to `true`.</span></span>

3. <span data-ttu-id="b6714-115">Vlastnost <xref:System.Windows.Forms.NotifyIcon.Text%2A> nastavte na odpovídající řetězec popisu tlačítka.</span><span class="sxs-lookup"><span data-stu-id="b6714-115">Set the <xref:System.Windows.Forms.NotifyIcon.Text%2A> property to an appropriate ToolTip string.</span></span>

     <span data-ttu-id="b6714-116">V následujícím příkladu kódu je cesta nastavená pro umístění ikony složka **dokumenty** .</span><span class="sxs-lookup"><span data-stu-id="b6714-116">In the following code example, the path set for the location of the icon is the **My Documents** folder.</span></span> <span data-ttu-id="b6714-117">Toto umístění se používá, protože můžete předpokládat, že většina počítačů, na kterých běží operační systém Windows, bude obsahovat tuto složku.</span><span class="sxs-lookup"><span data-stu-id="b6714-117">This location is used because you can assume that most computers running the Windows operating system will include this folder.</span></span> <span data-ttu-id="b6714-118">Volba tohoto umístění také umožňuje uživatelům s minimálními úrovněmi přístupu k systému bezpečně spustit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b6714-118">Choosing this location also enables users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="b6714-119">Následující příklad vyžaduje formulář s již přidaným ovládacím prvkem <xref:System.Windows.Forms.NotifyIcon>.</span><span class="sxs-lookup"><span data-stu-id="b6714-119">The following example requires a form with a <xref:System.Windows.Forms.NotifyIcon> control already added.</span></span> <span data-ttu-id="b6714-120">Také vyžaduje soubor ikony s názvem `Icon.ico`.</span><span class="sxs-lookup"><span data-stu-id="b6714-120">It also requires an icon file named `Icon.ico`.</span></span>

    ```vb
    ' You should replace the bold icon in the sample below
    ' with an icon of your own choosing.
    NotifyIcon1.Icon = New _
       System.Drawing.Icon(System.Environment.GetFolderPath _
       (System.Environment.SpecialFolder.Personal) _
       & "\Icon.ico")
    NotifyIcon1.Visible = True
    NotifyIcon1.Text = "Antivirus program"
    ```

    ```csharp
    // You should replace the bold icon in the sample below
    // with an icon of your own choosing.
    // Note the escape character used (@) when specifying the path.
    notifyIcon1.Icon =
       new System.Drawing.Icon (System.Environment.GetFolderPath
       (System.Environment.SpecialFolder.Personal)
       + @"\Icon.ico");
    notifyIcon1.Visible = true;
    notifyIcon1.Text = "Antivirus program";
    ```

    ```cpp
    // You should replace the bold icon in the sample below
    // with an icon of your own choosing.
    notifyIcon1->Icon = gcnew
       System::Drawing::Icon(String::Concat
       (System::Environment::GetFolderPath
       (System::Environment::SpecialFolder::Personal),
       "\\Icon.ico"));
    notifyIcon1->Visible = true;
    notifyIcon1->Text = "Antivirus program";
    ```

## <a name="see-also"></a><span data-ttu-id="b6714-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b6714-121">See also</span></span>

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [<span data-ttu-id="b6714-122">Postupy: Přidružení místní nabídky ke komponentě Windows Forms NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="b6714-122">How to: Associate a Shortcut Menu with a Windows Forms NotifyIcon Component</span></span>](how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component.md)
- [<span data-ttu-id="b6714-123">Komponenta NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="b6714-123">NotifyIcon Component</span></span>](notifyicon-component-windows-forms.md)
- [<span data-ttu-id="b6714-124">Přehled komponenty NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="b6714-124">NotifyIcon Component Overview</span></span>](notifyicon-component-overview-windows-forms.md)
