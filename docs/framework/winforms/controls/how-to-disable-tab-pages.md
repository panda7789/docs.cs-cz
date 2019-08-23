---
title: 'Postupy: Zakázání karet'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tab pages [Windows Forms], hiding in forms
- TabControl control [Windows Forms], disabling pages
ms.assetid: adcc6618-8a34-4ee1-bbe3-47e732de6a59
ms.openlocfilehash: 888228c28dce591b237be16b6a321afee0105208
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967140"
---
# <a name="how-to-disable-tab-pages"></a><span data-ttu-id="fd492-102">Postupy: Zakázání karet</span><span class="sxs-lookup"><span data-stu-id="fd492-102">How to: Disable Tab Pages</span></span>
<span data-ttu-id="fd492-103">V některých případech budete chtít omezit přístup k datům, která jsou k dispozici v rámci vaší aplikace model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="fd492-103">On some occasions, you will want to restrict access to data that is available within your Windows Forms application.</span></span> <span data-ttu-id="fd492-104">Příkladem může být, když máte data zobrazená na kartách ovládacího prvku karta; Správci mohou mít informace na stránce karet, které byste chtěli omezit od uživatelů typu Host nebo nižší úrovně.</span><span class="sxs-lookup"><span data-stu-id="fd492-104">One example of this might be when you have data displayed in the tab pages of a tab control; administrators could have information on a tab page that you would want to restrict from guest or lower-level users.</span></span>  
  
### <a name="to-disable-tab-pages-programmatically"></a><span data-ttu-id="fd492-105">Chcete-li zakázat stránky karet programově</span><span class="sxs-lookup"><span data-stu-id="fd492-105">To disable tab pages programmatically</span></span>  
  
1. <span data-ttu-id="fd492-106">Napište kód pro zpracování <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> události ovládacího prvku karta.</span><span class="sxs-lookup"><span data-stu-id="fd492-106">Write code to handle the tab control's <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event.</span></span> <span data-ttu-id="fd492-107">Toto je událost, která je vyvolána, když uživatel přepne z jedné karty na další.</span><span class="sxs-lookup"><span data-stu-id="fd492-107">This is the event that is raised when the user switches from one tab to the next.</span></span>  
  
2. <span data-ttu-id="fd492-108">Ověřte přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="fd492-108">Check credentials.</span></span> <span data-ttu-id="fd492-109">V závislosti na informacích, které jsou k dispozici, můžete chtít ověřit, že uživatel se přihlásil pomocí nebo jinou formu přihlašovacích údajů, než umožní uživateli zobrazit kartu.</span><span class="sxs-lookup"><span data-stu-id="fd492-109">Depending upon the information presented, you may want to check the user name the user has logged in with or some other form of credentials before allowing the user to view the tab.</span></span>  
  
3. <span data-ttu-id="fd492-110">Pokud má uživatel odpovídající přihlašovací údaje, zobrazte kartu, na kterou jste klikli.</span><span class="sxs-lookup"><span data-stu-id="fd492-110">If the user has appropriate credentials, display the tab that was clicked.</span></span> <span data-ttu-id="fd492-111">Pokud uživatel nemá příslušná pověření, zobrazí okno se zprávou nebo jiné uživatelské rozhraní, které indikuje, že nemají přístup, a vrátí se na úvodní kartu.</span><span class="sxs-lookup"><span data-stu-id="fd492-111">If the user does not have appropriate credentials, display a message box or some other user interface indicating that they do not have access, and return to the initial tab.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="fd492-112">Při implementaci této funkce v produkčních aplikacích můžete tuto kontrolu přihlašovacích údajů provést během <xref:System.Windows.Forms.Form.Load> události formuláře.</span><span class="sxs-lookup"><span data-stu-id="fd492-112">When you implement this functionality in your production applications, you can perform this credential check during the form's <xref:System.Windows.Forms.Form.Load> event.</span></span> <span data-ttu-id="fd492-113">To vám umožní Skrýt kartu před zobrazením libovolného uživatelského rozhraní, což je mnohem čistší přístup k programování.</span><span class="sxs-lookup"><span data-stu-id="fd492-113">This will allow you to hide the tab before any user interface is shown, which is a much cleaner approach to programming.</span></span> <span data-ttu-id="fd492-114">Níže uvedená metodika (kontrola přihlašovacích údajů a zakázání karty během <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> události) je určena pro ilustrativní účely.</span><span class="sxs-lookup"><span data-stu-id="fd492-114">The methodology used below (checking credentials and disabling the tab during the <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event) is for illustrative purposes.</span></span>  
  
4. <span data-ttu-id="fd492-115">Případně, pokud máte více než dvě stránky karet, zobrazte stránku karet odlišnou od původní.</span><span class="sxs-lookup"><span data-stu-id="fd492-115">Optionally, if you have more than two tab pages, display a tab page different from the original.</span></span>  
  
     <span data-ttu-id="fd492-116">V následujícím <xref:System.Windows.Forms.CheckBox> příkladu se místo kontroly přihlašovacích údajů používá ovládací prvek, protože kritéria pro přístup k této kartě se budou lišit v závislosti na aplikaci.</span><span class="sxs-lookup"><span data-stu-id="fd492-116">In the example below, a <xref:System.Windows.Forms.CheckBox> control is used in lieu of checking the credentials, as the criteria for access to the tab will vary by application.</span></span> <span data-ttu-id="fd492-117">Je-li vyvolána `TabPage2` `TabPage2` událost, pokud je provedena kontrola přihlašovacích údajů (tj. zaškrtávací políčko je zaškrtnuto) a vybraná karta je (karta s důvěrnými informacemi v tomto příkladu), zobrazí se. <xref:System.Windows.Forms.TabControl.SelectedIndexChanged></span><span class="sxs-lookup"><span data-stu-id="fd492-117">When the <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event is raised, if the credential check is true (that is, the check box is checked) and the selected tab is `TabPage2` (the tab with the confidential information, in this example), then `TabPage2` is displayed.</span></span> <span data-ttu-id="fd492-118">V opačném případě se zobrazí okno se zprávou, že uživatel nemá příslušná přístupová oprávnění. `TabPage3`</span><span class="sxs-lookup"><span data-stu-id="fd492-118">Otherwise, `TabPage3` is displayed and a message box is shown to the user, indicating they did not have appropriate access privileges.</span></span> <span data-ttu-id="fd492-119">Níže uvedený kód předpokládá, že formulář má <xref:System.Windows.Forms.CheckBox> ovládací prvek`CredentialCheck`() a <xref:System.Windows.Forms.TabControl> ovládací prvek se třemi stránkami karet.</span><span class="sxs-lookup"><span data-stu-id="fd492-119">The code below assumes a form with a <xref:System.Windows.Forms.CheckBox> control (`CredentialCheck`) and a <xref:System.Windows.Forms.TabControl> control with three tab pages.</span></span>  
  
    ```vb  
    Private Sub TabControl1_SelectedIndexChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles TabControl1.SelectedIndexChanged  
       ' Check Credentials Here  
  
       If CredentialCheck.Checked = True And _   
       TabControl1.SelectedTab Is TabPage2 Then  
          TabControl1.SelectedTab = TabPage2  
       ElseIf CredentialCheck.Checked = False _   
       And TabControl1.SelectedTab Is TabPage2 Then  
          MessageBox.Show _   
         ("Unable to load tab. You have insufficient access privileges.")  
          TabControl1.SelectedTab = TabPage3  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void tabControl1_SelectedIndexChanged(object sender, System.EventArgs e)  
    {  
        // Check Credentials Here  
  
        if ((CredentialCheck.Checked == true) && (tabControl1.SelectedTab == tabPage2))   
        {  
            tabControl1.SelectedTab = tabPage2;  
        }  
        else if ((CredentialCheck.Checked == false) && (tabControl1.SelectedTab == tabPage2))  
        {  
            MessageBox.Show("Unable to load tab. You have insufficient access privileges.");  
            tabControl1.SelectedTab = tabPage3;  
        }  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void tabControl1_SelectedIndexChanged(  
          System::Object ^ sender,  
          System::EventArgs ^  e)  
       {  
          // Check Credentials Here  
          if ((CredentialCheck->Checked == true) &&  
              (tabControl1->SelectedTab == tabPage2))  
          {  
             tabControl1->SelectedTab = tabPage2;  
          }  
          else if ((CredentialCheck->Checked == false) &&  
                   (tabControl1->SelectedTab == tabPage2))  
          {  
             MessageBox::Show(String::Concat("Unable to load tab. ",  
                "You have insufficient access privileges."));  
             tabControl1->SelectedTab = tabPage3;  
          }  
       }  
    ```  
  
     <span data-ttu-id="fd492-120">(Vizuál C#, vizuál C++) Vložte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="fd492-120">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.tabControl1.SelectedIndexChanged +=   
       new System.EventHandler(this.tabControl1_SelectedIndexChanged);  
    ```  
  
    ```cpp  
    this->tabControl1->SelectedIndexChanged +=  
       gcnew System::EventHandler(this, &Form1::tabControl1_SelectedIndexChanged);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="fd492-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fd492-121">See also</span></span>

- [<span data-ttu-id="fd492-122">Přehled ovládacího prvku TabControl</span><span class="sxs-lookup"><span data-stu-id="fd492-122">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="fd492-123">Postupy: Přidání ovládacího prvku na stránku karty</span><span class="sxs-lookup"><span data-stu-id="fd492-123">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="fd492-124">Postupy: Přidání a odebrání karet pomocí model Windows Forms TabControl</span><span class="sxs-lookup"><span data-stu-id="fd492-124">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
- [<span data-ttu-id="fd492-125">Postupy: Změna vzhledu model Windows Forms TabControl</span><span class="sxs-lookup"><span data-stu-id="fd492-125">How to: Change the Appearance of the Windows Forms TabControl</span></span>](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
