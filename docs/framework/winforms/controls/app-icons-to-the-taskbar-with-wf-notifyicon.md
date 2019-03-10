---
title: 'Postupy: Přidání ikon aplikací do TaskBar s komponentou Windows Forms NotifyIcon'
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
ms.openlocfilehash: 04f6b98a2206371a2838b3a6952feeafcd788309
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714252"
---
# <a name="how-to-add-application-icons-to-the-taskbar-with-the-windows-forms-notifyicon-component"></a><span data-ttu-id="28768-102">Postupy: Přidání ikon aplikací do TaskBar s komponentou Windows Forms NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="28768-102">How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component</span></span>
<span data-ttu-id="28768-103">Windows Forms <xref:System.Windows.Forms.NotifyIcon> součást zobrazuje jednu ikonu v oznamovací oblasti na hlavním panelu Stav.</span><span class="sxs-lookup"><span data-stu-id="28768-103">The Windows Forms <xref:System.Windows.Forms.NotifyIcon> component displays a single icon in the status notification area of the taskbar.</span></span> <span data-ttu-id="28768-104">Chcete-li zobrazit více ikony ve stavové oblasti, musí mít více <xref:System.Windows.Forms.NotifyIcon> komponenty na formuláři.</span><span class="sxs-lookup"><span data-stu-id="28768-104">To display multiple icons in the status area, you must have multiple <xref:System.Windows.Forms.NotifyIcon> components on your form.</span></span> <span data-ttu-id="28768-105">Pokud chcete nastavit ikony zobrazené pro ovládací prvek, použijte <xref:System.Windows.Forms.NotifyIcon.Icon%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="28768-105">To set the icon displayed for a control, use the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property.</span></span> <span data-ttu-id="28768-106">Můžete také napsat kód <xref:System.Windows.Forms.NotifyIcon.DoubleClick> obslužná rutina události tak, že něco se stane, když uživatel dvakrát klikne na ikonu.</span><span class="sxs-lookup"><span data-stu-id="28768-106">You can also write code in the <xref:System.Windows.Forms.NotifyIcon.DoubleClick> event handler so that something happens when the user double-clicks the icon.</span></span> <span data-ttu-id="28768-107">Například může vytvořit dialogové okno se zobrazí uživateli konfigurovat proces na pozadí, který je reprezentován ikonou.</span><span class="sxs-lookup"><span data-stu-id="28768-107">For example, you could make a dialog box appear for the user to configure the background process represented by the icon.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="28768-108"><xref:System.Windows.Forms.NotifyIcon> Komponenty se používá oznámení pouze pro účely, které uživatele upozorní, akce nebo událostí došlo k chybě nebo došlo ke změně stavu nějaké.</span><span class="sxs-lookup"><span data-stu-id="28768-108">The <xref:System.Windows.Forms.NotifyIcon> component is used for notification purposes only, to alert users that an action or event has occurred or there has been a change in status of some sort.</span></span> <span data-ttu-id="28768-109">Abyste používali nabídky, panely nástrojů a další prvky uživatelského rozhraní pro standardní interakce s aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="28768-109">You should use menus, toolbars, and other user-interface elements for standard interaction with applications.</span></span>  
  
### <a name="to-set-the-icon"></a><span data-ttu-id="28768-110">Chcete-li nastavit ikonu</span><span class="sxs-lookup"><span data-stu-id="28768-110">To set the icon</span></span>  
  
1.  <span data-ttu-id="28768-111">Přiřaďte hodnotu <xref:System.Windows.Forms.NotifyIcon.Icon%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="28768-111">Assign a value to the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property.</span></span> <span data-ttu-id="28768-112">Hodnota musí být typu `System.Drawing.Icon` a ze souboru .ico, který lze načíst.</span><span class="sxs-lookup"><span data-stu-id="28768-112">The value must be of type `System.Drawing.Icon` and can be loaded from an .ico file.</span></span> <span data-ttu-id="28768-113">Můžete určit soubor ikony v kódu nebo kliknutím na tlačítko se třemi tečkami (![VisualStudioEllipsesButton snímek obrazovky](../media/vbellipsesbutton.png "vbEllipsesButton")) vedle položky <xref:System.Windows.Forms.NotifyIcon.Icon%2A> vlastnost  **Vlastnosti** okna a pak vyberete soubor v **otevřít** dialogové okno, které se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="28768-113">You can specify the icon file in code or by clicking the ellipsis button (![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property in the **Properties** window, and then selecting the file in the **Open** dialog box that appears.</span></span>  
  
2.  <span data-ttu-id="28768-114">Nastavte <xref:System.Windows.Forms.NotifyIcon.Visible%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="28768-114">Set the <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property to `true`.</span></span>  
  
3.  <span data-ttu-id="28768-115">Nastavte <xref:System.Windows.Forms.NotifyIcon.Text%2A> vlastnosti k odpovídající řetězec popisku.</span><span class="sxs-lookup"><span data-stu-id="28768-115">Set the <xref:System.Windows.Forms.NotifyIcon.Text%2A> property to an appropriate ToolTip string.</span></span>  
  
     <span data-ttu-id="28768-116">V následujícím příkladu kódu nastavena cesta pro umístění ikony **dokumenty** složky.</span><span class="sxs-lookup"><span data-stu-id="28768-116">In the following code example, the path set for the location of the icon is the **My Documents** folder.</span></span> <span data-ttu-id="28768-117">Toto umístění se používá, protože můžete předpokládat, že většina počítačů s operačním systémem Windows bude obsahovat této složky.</span><span class="sxs-lookup"><span data-stu-id="28768-117">This location is used because you can assume that most computers running the Windows operating system will include this folder.</span></span> <span data-ttu-id="28768-118">Výběrem tohoto umístění taky umožňuje uživatelům s úrovní přístupu minimální systém bezpečně spouštět aplikace.</span><span class="sxs-lookup"><span data-stu-id="28768-118">Choosing this location also enables users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="28768-119">V následujícím příkladu vyžaduje formulář s <xref:System.Windows.Forms.NotifyIcon> ovládací prvek již přidán.</span><span class="sxs-lookup"><span data-stu-id="28768-119">The following example requires a form with a <xref:System.Windows.Forms.NotifyIcon> control already added.</span></span> <span data-ttu-id="28768-120">Také budete potřebovat soubor ikony s názvem `Icon.ico`.</span><span class="sxs-lookup"><span data-stu-id="28768-120">It also requires an icon file named `Icon.ico`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="28768-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="28768-121">See also</span></span>
- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [<span data-ttu-id="28768-122">Postupy: Přidružení místní nabídky s komponentou Windows Forms NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="28768-122">How to: Associate a Shortcut Menu with a Windows Forms NotifyIcon Component</span></span>](how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component.md)
- [<span data-ttu-id="28768-123">Komponenta NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="28768-123">NotifyIcon Component</span></span>](notifyicon-component-windows-forms.md)
- [<span data-ttu-id="28768-124">Přehled komponenty NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="28768-124">NotifyIcon Component Overview</span></span>](notifyicon-component-overview-windows-forms.md)
