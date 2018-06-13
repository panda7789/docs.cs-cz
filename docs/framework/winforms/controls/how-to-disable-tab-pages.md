---
title: 'Postupy: Zákaz stránek karet'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tab pages [Windows Forms], hiding in forms
- TabControl control [Windows Forms], disabling pages
ms.assetid: adcc6618-8a34-4ee1-bbe3-47e732de6a59
ms.openlocfilehash: 94d8522a71fcd565ae8f994d73ffe4c46fcf7ce3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534264"
---
# <a name="how-to-disable-tab-pages"></a><span data-ttu-id="e04e6-102">Postupy: Zákaz stránek karet</span><span class="sxs-lookup"><span data-stu-id="e04e6-102">How to: Disable Tab Pages</span></span>
<span data-ttu-id="e04e6-103">V některých případech můžete omezit přístup k datům, která je k dispozici v rámci vaší aplikace Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e04e6-103">On some occasions, you will want to restrict access to data that is available within your Windows Forms application.</span></span> <span data-ttu-id="e04e6-104">Příkladem toho může být v případě, že se data zobrazí na kartě stránkách ovládacího prvku karta; Správce může mít informace na kartě stránky, kterou chcete omezit hosta nebo nižší úrovně uživatelů.</span><span class="sxs-lookup"><span data-stu-id="e04e6-104">One example of this might be when you have data displayed in the tab pages of a tab control; administrators could have information on a tab page that you would want to restrict from guest or lower-level users.</span></span>  
  
### <a name="to-disable-tab-pages-programmatically"></a><span data-ttu-id="e04e6-105">Chcete-li zákaz stránek karet prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="e04e6-105">To disable tab pages programmatically</span></span>  
  
1.  <span data-ttu-id="e04e6-106">Napsat kód pro zpracování ovládacího prvku karta <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> událostí.</span><span class="sxs-lookup"><span data-stu-id="e04e6-106">Write code to handle the tab control's <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event.</span></span> <span data-ttu-id="e04e6-107">Toto je událost, která se vyvolá, když uživatel přepíná z jedné karty na další.</span><span class="sxs-lookup"><span data-stu-id="e04e6-107">This is the event that is raised when the user switches from one tab to the next.</span></span>  
  
2.  <span data-ttu-id="e04e6-108">Zkontrolujte přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="e04e6-108">Check credentials.</span></span> <span data-ttu-id="e04e6-109">V závislosti na informace uvedené, můžete před povolením uživateli zobrazit kartu zkontrolovat uživatelské jméno, které se uživatel přihlásí pomocí nebo jiné formy přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="e04e6-109">Depending upon the information presented, you may want to check the user name the user has logged in with or some other form of credentials before allowing the user to view the tab.</span></span>  
  
3.  <span data-ttu-id="e04e6-110">Pokud uživatel má příslušná pověření, zobrazí kartu označeného.</span><span class="sxs-lookup"><span data-stu-id="e04e6-110">If the user has appropriate credentials, display the tab that was clicked.</span></span> <span data-ttu-id="e04e6-111">Pokud uživatel nemá příslušná pověření, zobrazit okno se zprávou nebo některé jiné uživatelské rozhraní, což indikuje, že se nemají přístup a vraťte na kartu počáteční.</span><span class="sxs-lookup"><span data-stu-id="e04e6-111">If the user does not have appropriate credentials, display a message box or some other user interface indicating that they do not have access, and return to the initial tab.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e04e6-112">Pokud implementujete tuto funkci v provozních aplikací, můžete tuto kontrolu můžete provést přihlašovacích údajů během formuláře <xref:System.Windows.Forms.Form.Load> událostí.</span><span class="sxs-lookup"><span data-stu-id="e04e6-112">When you implement this functionality in your production applications, you can perform this credential check during the form's <xref:System.Windows.Forms.Form.Load> event.</span></span> <span data-ttu-id="e04e6-113">To vám umožní skrýt kartě předtím, než se zobrazí všechny uživatelské rozhraní, což je mnoho čištění přístup k programování.</span><span class="sxs-lookup"><span data-stu-id="e04e6-113">This will allow you to hide the tab before any user interface is shown, which is a much cleaner approach to programming.</span></span> <span data-ttu-id="e04e6-114">Metoda použitá níže (Kontrola přihlašovací údaje a zakázání kartě během <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> událostí) je pro ilustraci.</span><span class="sxs-lookup"><span data-stu-id="e04e6-114">The methodology used below (checking credentials and disabling the tab during the <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event) is for illustrative purposes.</span></span>  
  
4.  <span data-ttu-id="e04e6-115">Pokud máte více než dvou karet, zobrazte stránky karty liší od originálu.</span><span class="sxs-lookup"><span data-stu-id="e04e6-115">Optionally, if you have more than two tab pages, display a tab page different from the original.</span></span>  
  
     <span data-ttu-id="e04e6-116">V příkladu níže <xref:System.Windows.Forms.CheckBox> řízení se používá místo kontrola přihlašovací údaje, jako kritéria pro přístup ke kartě se liší podle aplikace.</span><span class="sxs-lookup"><span data-stu-id="e04e6-116">In the example below, a <xref:System.Windows.Forms.CheckBox> control is used in lieu of checking the credentials, as the criteria for access to the tab will vary by application.</span></span> <span data-ttu-id="e04e6-117">Když <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> událost se vyvolá, pokud je hodnota true, zkontrolujte pověření (to znamená, že je zaškrtnuto zaškrtávací políčko) a je vybraná karta `TabPage2` (karta s důvěrné informace v tomto příkladu), pak `TabPage2` se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="e04e6-117">When the <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event is raised, if the credential check is true (that is, the check box is checked) and the selected tab is `TabPage2` (the tab with the confidential information, in this example), then `TabPage2` is displayed.</span></span> <span data-ttu-id="e04e6-118">V opačném `TabPage3` se zobrazí a zobrazí se okno se zprávou uživateli, označující neměl správná přístupová oprávnění.</span><span class="sxs-lookup"><span data-stu-id="e04e6-118">Otherwise, `TabPage3` is displayed and a message box is shown to the user, indicating they did not have appropriate access privileges.</span></span> <span data-ttu-id="e04e6-119">Následující kód předpokládá formulář s <xref:System.Windows.Forms.CheckBox> ovládací prvek (`CredentialCheck`) a <xref:System.Windows.Forms.TabControl> ovládacího prvku pomocí stránky tří karet.</span><span class="sxs-lookup"><span data-stu-id="e04e6-119">The code below assumes a form with a <xref:System.Windows.Forms.CheckBox> control (`CredentialCheck`) and a <xref:System.Windows.Forms.TabControl> control with three tab pages.</span></span>  
  
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
  
     <span data-ttu-id="e04e6-120">(Visual C#, Visual C++) Vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="e04e6-120">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.tabControl1.SelectedIndexChanged +=   
       new System.EventHandler(this.tabControl1_SelectedIndexChanged);  
    ```  
  
    ```cpp  
    this->tabControl1->SelectedIndexChanged +=  
       gcnew System::EventHandler(this, &Form1::tabControl1_SelectedIndexChanged);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e04e6-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="e04e6-121">See Also</span></span>  
 [<span data-ttu-id="e04e6-122">Přehled ovládacího prvku TabControl</span><span class="sxs-lookup"><span data-stu-id="e04e6-122">TabControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [<span data-ttu-id="e04e6-123">Postupy: Přidání ovládacího prvku na kartu</span><span class="sxs-lookup"><span data-stu-id="e04e6-123">How to: Add a Control to a Tab Page</span></span>](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)  
 [<span data-ttu-id="e04e6-124">Postupy: Přidání a odebrání karet pomocí ovládacího prvku Windows Forms TabControl</span><span class="sxs-lookup"><span data-stu-id="e04e6-124">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)  
 [<span data-ttu-id="e04e6-125">Postupy: Změna vzhledu Windows Forms TabControl</span><span class="sxs-lookup"><span data-stu-id="e04e6-125">How to: Change the Appearance of the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
