---
title: 'Postupy: Přidružení místní nabídky ke komponentě Windows Forms NotifyIcon'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- context menus [Windows Forms], for background processes
- NotifyIcon component [Windows Forms], associating shortcut menus
- shortcut menus [Windows Forms], for background processes
ms.assetid: d68f3926-08d3-4f7d-949f-1981b29cf188
ms.openlocfilehash: 702a848631ce45c0efcb8eadfdf64074b454ac7d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097987"
---
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a><span data-ttu-id="30358-102">Postupy: Přidružení místní nabídky ke komponentě Windows Forms NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="30358-102">How to: Associate a Shortcut Menu with a Windows Forms NotifyIcon Component</span></span>
> [!NOTE]
>  <span data-ttu-id="30358-103">I když <xref:System.Windows.Forms.MenuStrip> a <xref:System.Windows.Forms.ContextMenuStrip> nahradit a přidání funkce, které <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> ovládací prvky z předchozích verzí <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> se zachovají pro zpětnou kompatibilitu a budoucí použití, pokud se rozhodnete.</span><span class="sxs-lookup"><span data-stu-id="30358-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="30358-104"><xref:System.Windows.Forms.NotifyIcon> Komponenty zobrazuje ikonu v oznamovací oblasti na hlavním panelu Stav.</span><span class="sxs-lookup"><span data-stu-id="30358-104">The <xref:System.Windows.Forms.NotifyIcon> component displays an icon in the status notification area of the taskbar.</span></span> <span data-ttu-id="30358-105">Běžně aplikace vám umožňují klikněte pravým tlačítkem na tuto ikonu odesílat příkazy do aplikace, kterou představuje.</span><span class="sxs-lookup"><span data-stu-id="30358-105">Commonly, applications enable you to right-click this icon to send commands to the application it represents.</span></span> <span data-ttu-id="30358-106">Tím, že přidružíte <xref:System.Windows.Forms.ContextMenu> komponentu s <xref:System.Windows.Forms.NotifyIcon> komponentu, můžou dodat tuto funkci pro vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="30358-106">By associating a <xref:System.Windows.Forms.ContextMenu> component with the <xref:System.Windows.Forms.NotifyIcon> component, you can add this functionality to your applications.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30358-107">Pokud chcete při zobrazování instance minimalizaci při spuštění aplikace <xref:System.Windows.Forms.NotifyIcon> komponenty na hlavním panelu nastavit hlavní formulář <xref:System.Windows.Forms.Form.WindowState%2A> vlastnost <xref:System.Windows.Forms.FormWindowState.Minimized> a ujistěte se, <xref:System.Windows.Forms.NotifyIcon> komponenty <xref:System.Windows.Forms.NotifyIcon.Visible%2A> vlastnost je nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="30358-107">If you want your application to be minimized at startup while displaying an instance of the <xref:System.Windows.Forms.NotifyIcon> component in the taskbar, set the main form's <xref:System.Windows.Forms.Form.WindowState%2A> property to <xref:System.Windows.Forms.FormWindowState.Minimized> and be sure the <xref:System.Windows.Forms.NotifyIcon> component's <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property is set to `true`.</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a><span data-ttu-id="30358-108">Chcete-li přidružení místní nabídky ke komponentě NotifyIcon v době návrhu</span><span class="sxs-lookup"><span data-stu-id="30358-108">To associate a shortcut menu with the NotifyIcon component at design time</span></span>  
  
1.  <span data-ttu-id="30358-109">Přidat <xref:System.Windows.Forms.NotifyIcon> komponentu do formuláře a nastavte důležité vlastnosti, jako je třeba <xref:System.Windows.Forms.NotifyIcon.Icon%2A> a <xref:System.Windows.Forms.NotifyIcon.Visible%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="30358-109">Add a <xref:System.Windows.Forms.NotifyIcon> component to your form, and set the important properties, such as the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A> properties.</span></span>  
  
     <span data-ttu-id="30358-110">Další informace najdete v tématu [jak: Přidání ikon aplikací do TaskBar se Windows Forms NotifyIcon – komponenta](app-icons-to-the-taskbar-with-wf-notifyicon.md).</span><span class="sxs-lookup"><span data-stu-id="30358-110">For more information, see [How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component](app-icons-to-the-taskbar-with-wf-notifyicon.md).</span></span>  
  
2.  <span data-ttu-id="30358-111">Přidat <xref:System.Windows.Forms.ContextMenu> komponentu do formuláře Windows.</span><span class="sxs-lookup"><span data-stu-id="30358-111">Add a <xref:System.Windows.Forms.ContextMenu> component to your Windows Form.</span></span>  
  
     <span data-ttu-id="30358-112">Přidání položek nabídky do místní nabídky představující příkazy, že které chcete zpřístupnit v době běhu.</span><span class="sxs-lookup"><span data-stu-id="30358-112">Add menu items to the shortcut menu representing the commands you want to make available at run time.</span></span> <span data-ttu-id="30358-113">Toto je vhodná doba k přidání vylepšení nabídky do těchto položek nabídky, jako jsou přístupové klíče.</span><span class="sxs-lookup"><span data-stu-id="30358-113">This is also a good time to add menu enhancements to these menu items, such as access keys.</span></span>  
  
3.  <span data-ttu-id="30358-114">Nastavte <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> vlastnost <xref:System.Windows.Forms.NotifyIcon> komponentu do místní nabídky, kterou jste přidali.</span><span class="sxs-lookup"><span data-stu-id="30358-114">Set the <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> property of the <xref:System.Windows.Forms.NotifyIcon> component to the shortcut menu that you added.</span></span>  
  
     <span data-ttu-id="30358-115">S touto sadou vlastností v místní nabídce se zobrazí po kliknutí na ikonu na hlavním panelu.</span><span class="sxs-lookup"><span data-stu-id="30358-115">With this property set, the shortcut menu will be displayed when the icon on the taskbar is clicked.</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a><span data-ttu-id="30358-116">Chcete-li přidružení místní nabídky ke komponentě NotifyIcon prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="30358-116">To associate a shortcut menu with the NotifyIcon component programmatically</span></span>  
  
1.  <span data-ttu-id="30358-117">Vytvoření instance <xref:System.Windows.Forms.NotifyIcon> třídy a <xref:System.Windows.Forms.ContextMenu> třídy s jakékoli nastavení vlastností jsou nezbytné pro aplikaci (<xref:System.Windows.Forms.NotifyIcon.Icon%2A> a <xref:System.Windows.Forms.NotifyIcon.Visible%2A> vlastnosti <xref:System.Windows.Forms.NotifyIcon> komponenty, položky nabídky pro <xref:System.Windows.Forms.ContextMenu> komponenta).</span><span class="sxs-lookup"><span data-stu-id="30358-117">Create an instance of the <xref:System.Windows.Forms.NotifyIcon> class and a <xref:System.Windows.Forms.ContextMenu> class, with whatever property settings are necessary for the application (<xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A> properties for the <xref:System.Windows.Forms.NotifyIcon> component, menu items for the <xref:System.Windows.Forms.ContextMenu> component).</span></span>  
  
2.  <span data-ttu-id="30358-118">Nastavte <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> vlastnost <xref:System.Windows.Forms.NotifyIcon> komponentu do místní nabídky, kterou jste přidali.</span><span class="sxs-lookup"><span data-stu-id="30358-118">Set the <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> property of the <xref:System.Windows.Forms.NotifyIcon> component to the shortcut menu that you added.</span></span>  
  
     <span data-ttu-id="30358-119">S touto sadou vlastností v místní nabídce se zobrazí po kliknutí na ikonu na hlavním panelu.</span><span class="sxs-lookup"><span data-stu-id="30358-119">With this property set, the shortcut menu will be displayed when the icon on the taskbar is clicked.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="30358-120">Následující příklad kódu vytvoří struktura základní nabídky.</span><span class="sxs-lookup"><span data-stu-id="30358-120">The following code example creates a basic menu structure.</span></span> <span data-ttu-id="30358-121">Je potřeba upravit možnosti nabídek na ty, které odpovídají aplikaci, kterou vyvíjíte.</span><span class="sxs-lookup"><span data-stu-id="30358-121">You will need to customize the menu choices to those that fit the application you are developing.</span></span> <span data-ttu-id="30358-122">Kromě toho můžete napsat kód pro zpracování <xref:System.Windows.Forms.MenuItem.Click> události pro tyto položky nabídky.</span><span class="sxs-lookup"><span data-stu-id="30358-122">Additionally, you will want to write code to handle the <xref:System.Windows.Forms.MenuItem.Click> events for these menu items.</span></span>  
  
    ```vb  
    Public ContextMenu1 As New ContextMenu  
    Public NotifyIcon1 As New NotifyIcon  
  
    Public Sub CreateIconMenuStructure()  
       ' Add menu items to shortcut menu.  
       ContextMenu1.MenuItems.Add("&Open Application")  
       ContextMenu1.MenuItems.Add("S&uspend Application")  
       ContextMenu1.MenuItems.Add("E&xit")  
  
       ' Set properties of NotifyIcon component.  
       NotifyIcon1.Icon = New System.Drawing.Icon _   
          (System.Environment.GetFolderPath _   
          (System.Environment.SpecialFolder.Personal)  _   
          & "\Icon.ico")  
       NotifyIcon1.Text = "Right-click me!"  
       NotifyIcon1.Visible = True  
       NotifyIcon1.ContextMenu = ContextMenu1  
    End Sub  
    ```  
  
```csharp  
public NotifyIcon notifyIcon1 = new NotifyIcon();  
public ContextMenu contextMenu1 = new ContextMenu();  
  
public void createIconMenuStructure()  
{  
   // Add menu items to shortcut menu.  
   contextMenu1.MenuItems.Add("&Open Application");  
   contextMenu1.MenuItems.Add("S&uspend Application");  
   contextMenu1.MenuItems.Add("E&xit");  
  
   // Set properties of NotifyIcon component.  
   notifyIcon1.Icon = new System.Drawing.Icon  
      (System.Environment.GetFolderPath  
      (System.Environment.SpecialFolder.Personal)  
      + @"\Icon.ico");  
   notifyIcon1.Visible = true;  
   notifyIcon1.Text = "Right-click me!";  
   notifyIcon1.Visible = true;  
   notifyIcon1.ContextMenu = contextMenu1;  
}  
```  
  
```cpp  
public:  
   System::Windows::Forms::NotifyIcon ^ notifyIcon1;  
   System::Windows::Forms::ContextMenu ^ contextMenu1;  
  
   void createIconMenuStructure()  
   {  
      // Add menu items to shortcut menu.  
      contextMenu1->MenuItems->Add("&Open Application");  
      contextMenu1->MenuItems->Add("S&uspend Application");  
      contextMenu1->MenuItems->Add("E&xit");  
  
      // Set properties of NotifyIcon component.  
      notifyIcon1->Icon = gcnew System::Drawing::Icon  
          (String::Concat(System::Environment::GetFolderPath  
          (System::Environment::SpecialFolder::Personal),  
          "\\Icon.ico"));  
      notifyIcon1->Text = "Right-click me!";  
      notifyIcon1->Visible = true;  
      notifyIcon1->ContextMenu = contextMenu1;  
   }  
```  
  
> [!NOTE]
>  <span data-ttu-id="30358-123">Je třeba inicializovat `notifyIcon1` a `contextMenu1,` což lze provést přidáním následující příkazy v konstruktoru formuláře:</span><span class="sxs-lookup"><span data-stu-id="30358-123">You must initialize `notifyIcon1` and `contextMenu1,` which you can do by including the following statements in the constructor of your form:</span></span>  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## <a name="see-also"></a><span data-ttu-id="30358-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="30358-124">See also</span></span>

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [<span data-ttu-id="30358-125">Postupy: Přidání ikon aplikací do TaskBar s komponentou Windows Forms NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="30358-125">How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component</span></span>](app-icons-to-the-taskbar-with-wf-notifyicon.md)
- [<span data-ttu-id="30358-126">Komponenta NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="30358-126">NotifyIcon Component</span></span>](notifyicon-component-windows-forms.md)
- [<span data-ttu-id="30358-127">Přehled komponenty NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="30358-127">NotifyIcon Component Overview</span></span>](notifyicon-component-overview-windows-forms.md)
