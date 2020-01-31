---
title: Přidružení místní nabídky ke komponentě NotifyIcon
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
ms.openlocfilehash: 392c04f73feaec201033ad76f9419a0e070bec70
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742046"
---
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a><span data-ttu-id="236ea-102">Postupy: Přidružení místní nabídky k součásti Windows Forms NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="236ea-102">How to: Associate a Shortcut Menu with a Windows Forms NotifyIcon Component</span></span>
> [!NOTE]
> <span data-ttu-id="236ea-103">I když <xref:System.Windows.Forms.MenuStrip> a <xref:System.Windows.Forms.ContextMenuStrip> nahrazují a přidává funkce do <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu>ových ovládacích prvků předchozích verzí, <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> se uchovávají pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte.</span><span class="sxs-lookup"><span data-stu-id="236ea-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="236ea-104">Komponenta <xref:System.Windows.Forms.NotifyIcon> zobrazí ikonu v oznamovací oblasti hlavního panelu.</span><span class="sxs-lookup"><span data-stu-id="236ea-104">The <xref:System.Windows.Forms.NotifyIcon> component displays an icon in the status notification area of the taskbar.</span></span> <span data-ttu-id="236ea-105">Aplikace vám běžně umožní odeslat příkazy do aplikace, kterou představuje, kliknutím pravým tlačítkem myši na tuto ikonu.</span><span class="sxs-lookup"><span data-stu-id="236ea-105">Commonly, applications enable you to right-click this icon to send commands to the application it represents.</span></span> <span data-ttu-id="236ea-106">Tím, že přidružíte komponentu <xref:System.Windows.Forms.ContextMenu> ke komponentě <xref:System.Windows.Forms.NotifyIcon>, můžete tuto funkci přidat do svých aplikací.</span><span class="sxs-lookup"><span data-stu-id="236ea-106">By associating a <xref:System.Windows.Forms.ContextMenu> component with the <xref:System.Windows.Forms.NotifyIcon> component, you can add this functionality to your applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="236ea-107">Pokud chcete, aby byla aplikace minimalizována při spuštění při zobrazení instance <xref:System.Windows.Forms.NotifyIcon> komponenty na hlavním panelu, nastavte vlastnost <xref:System.Windows.Forms.Form.WindowState%2A> hlavního formuláře na hodnotu <xref:System.Windows.Forms.FormWindowState.Minimized> a ujistěte se, že vlastnost <xref:System.Windows.Forms.NotifyIcon.Visible%2A> komponenty <xref:System.Windows.Forms.NotifyIcon> je nastavena na hodnotu `true`.</span><span class="sxs-lookup"><span data-stu-id="236ea-107">If you want your application to be minimized at startup while displaying an instance of the <xref:System.Windows.Forms.NotifyIcon> component in the taskbar, set the main form's <xref:System.Windows.Forms.Form.WindowState%2A> property to <xref:System.Windows.Forms.FormWindowState.Minimized> and be sure the <xref:System.Windows.Forms.NotifyIcon> component's <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property is set to `true`.</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a><span data-ttu-id="236ea-108">Přidružení místní nabídky ke komponentě NotifyIcon v době návrhu</span><span class="sxs-lookup"><span data-stu-id="236ea-108">To associate a shortcut menu with the NotifyIcon component at design time</span></span>  
  
1. <span data-ttu-id="236ea-109">Přidejte do formuláře komponentu <xref:System.Windows.Forms.NotifyIcon> a nastavte důležité vlastnosti, jako jsou vlastnosti <xref:System.Windows.Forms.NotifyIcon.Icon%2A> a <xref:System.Windows.Forms.NotifyIcon.Visible%2A>.</span><span class="sxs-lookup"><span data-stu-id="236ea-109">Add a <xref:System.Windows.Forms.NotifyIcon> component to your form, and set the important properties, such as the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A> properties.</span></span>  
  
     <span data-ttu-id="236ea-110">Další informace najdete v tématu [Postup: přidání ikon aplikace na hlavní panel s model Windows Forms komponentou NotifyIcon](app-icons-to-the-taskbar-with-wf-notifyicon.md).</span><span class="sxs-lookup"><span data-stu-id="236ea-110">For more information, see [How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component](app-icons-to-the-taskbar-with-wf-notifyicon.md).</span></span>  
  
2. <span data-ttu-id="236ea-111">Přidejte <xref:System.Windows.Forms.ContextMenu>ovou komponentu do formuláře Windows.</span><span class="sxs-lookup"><span data-stu-id="236ea-111">Add a <xref:System.Windows.Forms.ContextMenu> component to your Windows Form.</span></span>  
  
     <span data-ttu-id="236ea-112">Přidejte položky nabídky do místní nabídky reprezentující příkazy, které mají být v době běhu k dispozici.</span><span class="sxs-lookup"><span data-stu-id="236ea-112">Add menu items to the shortcut menu representing the commands you want to make available at run time.</span></span> <span data-ttu-id="236ea-113">To je také dobrý čas pro přidání vylepšení nabídky do těchto položek nabídky, jako jsou přístupové klíče.</span><span class="sxs-lookup"><span data-stu-id="236ea-113">This is also a good time to add menu enhancements to these menu items, such as access keys.</span></span>  
  
3. <span data-ttu-id="236ea-114">Nastavte vlastnost <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> komponenty <xref:System.Windows.Forms.NotifyIcon> na místní nabídku, kterou jste přidali.</span><span class="sxs-lookup"><span data-stu-id="236ea-114">Set the <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> property of the <xref:System.Windows.Forms.NotifyIcon> component to the shortcut menu that you added.</span></span>  
  
     <span data-ttu-id="236ea-115">Když je tato vlastnost nastavená, zobrazí se místní nabídka při kliknutí na ikonu na hlavním panelu.</span><span class="sxs-lookup"><span data-stu-id="236ea-115">With this property set, the shortcut menu will be displayed when the icon on the taskbar is clicked.</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a><span data-ttu-id="236ea-116">Postup při přidružování místní nabídky k součásti NotifyIcon programově</span><span class="sxs-lookup"><span data-stu-id="236ea-116">To associate a shortcut menu with the NotifyIcon component programmatically</span></span>  
  
1. <span data-ttu-id="236ea-117">Vytvořte instanci třídy <xref:System.Windows.Forms.NotifyIcon> a třídu <xref:System.Windows.Forms.ContextMenu>, s jakýmkoli nastavením vlastností, které jsou nezbytné pro aplikaci (<xref:System.Windows.Forms.NotifyIcon.Icon%2A> a <xref:System.Windows.Forms.NotifyIcon.Visible%2A> vlastnosti pro součást <xref:System.Windows.Forms.NotifyIcon>, položky nabídky pro součást <xref:System.Windows.Forms.ContextMenu>).</span><span class="sxs-lookup"><span data-stu-id="236ea-117">Create an instance of the <xref:System.Windows.Forms.NotifyIcon> class and a <xref:System.Windows.Forms.ContextMenu> class, with whatever property settings are necessary for the application (<xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A> properties for the <xref:System.Windows.Forms.NotifyIcon> component, menu items for the <xref:System.Windows.Forms.ContextMenu> component).</span></span>  
  
2. <span data-ttu-id="236ea-118">Nastavte vlastnost <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> komponenty <xref:System.Windows.Forms.NotifyIcon> na místní nabídku, kterou jste přidali.</span><span class="sxs-lookup"><span data-stu-id="236ea-118">Set the <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> property of the <xref:System.Windows.Forms.NotifyIcon> component to the shortcut menu that you added.</span></span>  
  
     <span data-ttu-id="236ea-119">Když je tato vlastnost nastavená, zobrazí se místní nabídka při kliknutí na ikonu na hlavním panelu.</span><span class="sxs-lookup"><span data-stu-id="236ea-119">With this property set, the shortcut menu will be displayed when the icon on the taskbar is clicked.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="236ea-120">Následující příklad kódu vytvoří základní strukturu nabídky.</span><span class="sxs-lookup"><span data-stu-id="236ea-120">The following code example creates a basic menu structure.</span></span> <span data-ttu-id="236ea-121">Volby nabídky budete muset přizpůsobit na ty, které se vejdou do aplikace, kterou vyvíjíte.</span><span class="sxs-lookup"><span data-stu-id="236ea-121">You will need to customize the menu choices to those that fit the application you are developing.</span></span> <span data-ttu-id="236ea-122">Navíc budete chtít napsat kód, který bude zpracovávat události <xref:System.Windows.Forms.MenuItem.Click> pro tyto položky nabídky.</span><span class="sxs-lookup"><span data-stu-id="236ea-122">Additionally, you will want to write code to handle the <xref:System.Windows.Forms.MenuItem.Click> events for these menu items.</span></span>  
  
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
> <span data-ttu-id="236ea-123">Je nutné inicializovat `notifyIcon1` a `contextMenu1,`, které lze provést zahrnutím následujících příkazů do konstruktoru formuláře:</span><span class="sxs-lookup"><span data-stu-id="236ea-123">You must initialize `notifyIcon1` and `contextMenu1,` which you can do by including the following statements in the constructor of your form:</span></span>  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## <a name="see-also"></a><span data-ttu-id="236ea-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="236ea-124">See also</span></span>

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [<span data-ttu-id="236ea-125">Postupy: Přidání ikon aplikací do TaskBar s komponentou Windows Forms NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="236ea-125">How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component</span></span>](app-icons-to-the-taskbar-with-wf-notifyicon.md)
- [<span data-ttu-id="236ea-126">Komponenta NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="236ea-126">NotifyIcon Component</span></span>](notifyicon-component-windows-forms.md)
- [<span data-ttu-id="236ea-127">Přehled komponenty NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="236ea-127">NotifyIcon Component Overview</span></span>](notifyicon-component-overview-windows-forms.md)
