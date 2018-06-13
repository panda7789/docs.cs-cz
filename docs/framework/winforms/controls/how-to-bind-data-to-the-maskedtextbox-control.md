---
title: 'Postupy: Připojení dat k ovládacímu prvku MaskedTextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- MaskedTextBox control [Windows Forms]
- data binding [Windows Forms], MaskedTextBox control [Windows Forms]
- MaskedTextBox control [Windows Forms], binding data
ms.assetid: 34b29f07-e8df-48d4-b08b-53fcca524708
ms.openlocfilehash: 98d59e7443b51c17baafd05e6701c1418298b4a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530912"
---
# <a name="how-to-bind-data-to-the-maskedtextbox-control"></a><span data-ttu-id="d3296-102">Postupy: Připojení dat k ovládacímu prvku MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="d3296-102">How to: Bind Data to the MaskedTextBox Control</span></span>
<span data-ttu-id="d3296-103">Data lze vázat <xref:System.Windows.Forms.MaskedTextBox> řízení stejně jako všechny ostatní ovládací prvek Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d3296-103">You can bind data to a <xref:System.Windows.Forms.MaskedTextBox> control just as you can to any other Windows Forms control.</span></span> <span data-ttu-id="d3296-104">Ale pokud formátu vašich dat v databázi neodpovídá formátu očekávaném podle vaší definice maska, musíte změnit formát data.</span><span class="sxs-lookup"><span data-stu-id="d3296-104">However, if the format of your data in the database does not match the format expected by your mask definition, you will need to reformat the data.</span></span> <span data-ttu-id="d3296-105">Následující postup ukazuje, jak to provést pomocí <xref:System.Windows.Forms.Binding.Format> a <xref:System.Windows.Forms.Binding.Parse> události <xref:System.Windows.Forms.Binding> třída zobrazíte samostatné telefonní číslo a phone rozšíření databáze pole jako jediné pole upravitelné.</span><span class="sxs-lookup"><span data-stu-id="d3296-105">The following procedure demonstrates how to do this using the <xref:System.Windows.Forms.Binding.Format> and <xref:System.Windows.Forms.Binding.Parse> events of the <xref:System.Windows.Forms.Binding> class to display separate phone number and phone extension database fields as a single editable field.</span></span>  
  
 <span data-ttu-id="d3296-106">Následující postup vyžaduje, abyste měli přístup k databázi systému SQL Server s ukázková databáze Northwind nainstalována.</span><span class="sxs-lookup"><span data-stu-id="d3296-106">The following procedure requires that you have access to a SQL Server database with the Northwind sample database installed.</span></span>  
  
### <a name="to-bind-data-to-a-maskedtextbox-control"></a><span data-ttu-id="d3296-107">K vytvoření vazby dat k ovládacímu prvku MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="d3296-107">To bind data to a MaskedTextBox control</span></span>  
  
1.  <span data-ttu-id="d3296-108">Vytvoření nového projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d3296-108">Create a new Windows Forms project.</span></span>  
  
2.  <span data-ttu-id="d3296-109">Přetáhněte dva <xref:System.Windows.Forms.TextBox> ovládacích prvků do svého formuláře; název je `FirstName` a `LastName`.</span><span class="sxs-lookup"><span data-stu-id="d3296-109">Drag two <xref:System.Windows.Forms.TextBox> controls onto your form; name them `FirstName` and `LastName`.</span></span>  
  
3.  <span data-ttu-id="d3296-110">Přetáhněte <xref:System.Windows.Forms.MaskedTextBox> na svého formuláře ovládací prvek; název `PhoneMask`.</span><span class="sxs-lookup"><span data-stu-id="d3296-110">Drag a <xref:System.Windows.Forms.MaskedTextBox> control onto your form; name it `PhoneMask`.</span></span>  
  
4.  <span data-ttu-id="d3296-111">Nastavte <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> vlastnost `PhoneMask` k `(000) 000-0000 x9999`.</span><span class="sxs-lookup"><span data-stu-id="d3296-111">Set the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property of `PhoneMask` to `(000) 000-0000 x9999`.</span></span>  
  
5.  <span data-ttu-id="d3296-112">Přidejte že následující obor názvů naimportuje do formuláře.</span><span class="sxs-lookup"><span data-stu-id="d3296-112">Add the following namespace imports to the form.</span></span>  
  
    ```csharp  
    using System.Data.SqlClient;  
    ```  
  
    ```vb  
    Imports System.Data.SqlClient  
    ```  
  
6.  <span data-ttu-id="d3296-113">Klikněte pravým tlačítkem na formulář a zvolte **kód zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="d3296-113">Right-click the form and choose **View Code**.</span></span> <span data-ttu-id="d3296-114">Tento kód umístíte kamkoli do vaší třídy formuláře.</span><span class="sxs-lookup"><span data-stu-id="d3296-114">Place this code anywhere in your form class.</span></span>  
  
    ```csharp  
    Binding currentBinding, phoneBinding;  
    DataSet employeesTable = new DataSet();  
    SqlConnection sc;  
    SqlDataAdapter dataConnect;  
  
    private void Form1_Load(object sender, EventArgs e)  
    {  
        DoMaskBinding();  
    }  
  
    private void DoMaskBinding()  
    {  
        try  
        {  
            sc = new SqlConnection("Data Source=CLIENTUE;Initial Catalog=NORTHWIND;Integrated Security=SSPI");  
            sc.Open();  
        }  
        catch (Exception ex)  
        {  
            MessageBox.Show(ex.Message);  
            return;  
        }  
  
        dataConnect = new SqlDataAdapter("SELECT * FROM Employees", sc);  
        dataConnect.Fill(employeesTable, "Employees");  
  
        // Now bind MaskedTextBox to appropriate field. Note that we must create the Binding objects  
        // before adding them to the control - otherwise, we won't get a Format event on the   
        // initial load.   
        try  
        {  
            currentBinding = new Binding("Text", employeesTable, "Employees.FirstName");  
            firstName.DataBindings.Add(currentBinding);  
  
            currentBinding = new Binding("Text", employeesTable, "Employees.LastName");  
            lastName.DataBindings.Add(currentBinding);  
  
            phoneBinding =new Binding("Text", employeesTable, "Employees.HomePhone");  
            // We must add the event handlers before we bind, or the Format event will not get called  
            // for the first record.  
            phoneBinding.Format += new ConvertEventHandler(phoneBinding_Format);  
            phoneBinding.Parse += new ConvertEventHandler(phoneBinding_Parse);  
            phoneMask.DataBindings.Add(phoneBinding);  
        }  
        catch (Exception ex)  
        {  
            MessageBox.Show(ex.Message);  
            return;  
        }  
    }  
    ```  
  
    ```vb  
    Dim WithEvents CurrentBinding, PhoneBinding As Binding  
    Dim EmployeesTable As New DataSet()  
    Dim sc As SqlConnection  
    Dim DataConnect As SqlDataAdapter  
  
    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MyBase.Load  
        DoMaskedBinding()  
    End Sub  
  
    Private Sub DoMaskedBinding()  
        Try  
            sc = New SqlConnection("Data Source=SERVERNAME;Initial Catalog=NORTHWIND;Integrated Security=SSPI")  
            sc.Open()  
        Catch ex As Exception  
            MessageBox.Show(ex.Message)  
            Exit Sub  
        End Try  
  
        DataConnect = New SqlDataAdapter("SELECT * FROM Employees", sc)  
        DataConnect.Fill(EmployeesTable, "Employees")  
  
        ' Now bind MaskedTextBox to appropriate field. Note that we must create the Binding objects  
        ' before adding them to the control - otherwise, we won't get a Format event on the   
        ' initial load.  
        Try  
            CurrentBinding = New Binding("Text", EmployeesTable, "Employees.FirstName")  
            firstName.DataBindings.Add(CurrentBinding)  
            CurrentBinding = New Binding("Text", EmployeesTable, "Employees.LastName")  
            lastName.DataBindings.Add(CurrentBinding)  
            PhoneBinding = New Binding("Text", EmployeesTable, "Employees.HomePhone")  
            PhoneMask.DataBindings.Add(PhoneBinding)  
        Catch ex As Exception  
            MessageBox.Show(ex.Message)  
            Application.Exit()  
        End Try  
    End Sub  
    ```  
  
7.  <span data-ttu-id="d3296-115">Přidání obslužných rutin událostí pro <xref:System.Windows.Forms.Binding.Format> a <xref:System.Windows.Forms.Binding.Parse> události kombinovat a oddělte `PhoneNumber` a `Extension` pole z vázaného <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="d3296-115">Add event handlers for the <xref:System.Windows.Forms.Binding.Format> and <xref:System.Windows.Forms.Binding.Parse> events to combine and separate the `PhoneNumber` and `Extension` fields from the bound <xref:System.Data.DataSet>.</span></span>  
  
    ```csharp  
    private void phoneBinding_Format(Object sender, ConvertEventArgs e)  
    {  
        String ext;  
  
        DataRowView currentRow = (DataRowView)BindingContext[employeesTable, "Employees"].Current;  
        if (currentRow["Extension"] == null)   
        {  
            ext = "";  
        } else   
        {  
            ext = currentRow["Extension"].ToString();  
        }  
  
        e.Value = e.Value.ToString().Trim() + " x" + ext;  
    }  
  
    private void phoneBinding_Parse(Object sender, ConvertEventArgs e)  
    {  
        String phoneNumberAndExt = e.Value.ToString();  
  
        int extIndex = phoneNumberAndExt.IndexOf("x");  
        String ext = phoneNumberAndExt.Substring(extIndex).Trim();  
        String phoneNumber = phoneNumberAndExt.Substring(0, extIndex).Trim();  
  
        //Get the current binding object, and set the new extension manually.   
        DataRowView currentRow = (DataRowView)BindingContext[employeesTable, "Employees"].Current;  
        // Remove the "x" from the extension.  
        currentRow["Extension"] = ext.Substring(1);  
  
        //Return the phone number.  
        e.Value = phoneNumber;  
    }  
    ```  
  
    ```vb  
    Private Sub PhoneBinding_Format(ByVal sender As Object, ByVal e As ConvertEventArgs) Handles PhoneBinding.Format  
        Dim Ext As String  
  
        Dim CurrentRow As DataRowView = CType(Me.BindingContext(EmployeesTable, "Employees").Current, DataRowView)  
        If (CurrentRow("Extension") Is Nothing) Then  
            Ext = ""  
        Else  
            Ext = CurrentRow("Extension").ToString()  
        End If  
  
        e.Value = e.Value.ToString().Trim() & " x" & Ext  
    End Sub  
  
    Private Sub PhoneBinding_Parse(ByVal sender As Object, ByVal e As ConvertEventArgs) Handles PhoneBinding.Parse  
        Dim PhoneNumberAndExt As String = e.Value.ToString()  
  
        Dim ExtIndex As Integer = PhoneNumberAndExt.IndexOf("x")  
        Dim Ext As String = PhoneNumberAndExt.Substring(ExtIndex).Trim()  
        Dim PhoneNumber As String = PhoneNumberAndExt.Substring(0, ExtIndex).Trim()  
  
        ' Get the current binding object, and set the new extension manually.   
        Dim CurrentRow As DataRowView = CType(Me.BindingContext(EmployeesTable, "Employees").Current, DataRowView)  
        ' Remove the "x" from the extension.  
        CurrentRow("Extension") = CObj(Ext.Substring(1))  
  
        ' Return the phone number.  
        e.Value = PhoneNumber  
    End Sub  
    ```  
  
8.  <span data-ttu-id="d3296-116">Přidejte dva <xref:System.Windows.Forms.Button> ovládacích prvků formuláře.</span><span class="sxs-lookup"><span data-stu-id="d3296-116">Add two <xref:System.Windows.Forms.Button> controls to the form.</span></span> <span data-ttu-id="d3296-117">Název je `previousButton` a `nextButton`.</span><span class="sxs-lookup"><span data-stu-id="d3296-117">Name them `previousButton` and `nextButton`.</span></span> <span data-ttu-id="d3296-118">Klikněte dvakrát na každé tlačítko Přidat <xref:System.Windows.Forms.Control.Click> obslužné rutiny události a vyplňte obslužné rutiny událostí, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="d3296-118">Double-click each button to add a <xref:System.Windows.Forms.Control.Click> event handler, and fill in the event handlers as shown in the following code example.</span></span>  
  
    ```csharp  
    private void previousButton_Click(object sender, EventArgs e)  
    {  
        BindingContext[employeesTable, "Employees"].Position = BindingContext[employeesTable, "Employees"].Position - 1;  
    }  
  
    private void nextButton_Click(object sender, EventArgs e)  
    {  
        BindingContext[employeesTable, "Employees"].Position = BindingContext[employeesTable, "Employees"].Position + 1;  
    }  
    ```  
  
    ```vb  
    Private Sub PreviousButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles PreviousButton.Click  
        Me.BindingContext(EmployeesTable, "Employees").Position = Me.BindingContext(EmployeesTable, "Employees").Position - 1  
    End Sub  
  
    Private Sub NextButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles NextButton.Click  
        Me.BindingContext(EmployeesTable, "Employees").Position = Me.BindingContext(EmployeesTable, "Employees").Position + 1  
    End Sub  
    ```  
  
9. <span data-ttu-id="d3296-119">Spusťte ukázku.</span><span class="sxs-lookup"><span data-stu-id="d3296-119">Run the sample.</span></span> <span data-ttu-id="d3296-120">Upravit data a pomocí **předchozí** a **Další** tlačítek a uvidíte, že jsou data správně uložena do <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="d3296-120">Edit the data, and use the **Previous** and **Next** buttons to see that the data is properly persisted to the <xref:System.Data.DataSet>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3296-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="d3296-121">Example</span></span>  
 <span data-ttu-id="d3296-122">Následující příklad kódu je úplná kód výpis které je výsledkem dokončení předchozího postupu.</span><span class="sxs-lookup"><span data-stu-id="d3296-122">The following code example is the full code listing that results from completing the previous procedure.</span></span>  
  
 [!code-cpp[MaskedTextBoxData#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/MaskedTextBoxData/cpp/form1.cpp#1)]
 [!code-csharp[MaskedTextBoxData#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/MaskedTextBoxData/CS/form1.cs#1)]
 [!code-vb[MaskedTextBoxData#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/MaskedTextBoxData/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d3296-123">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="d3296-123">Compiling the Code</span></span>  
  
-   <span data-ttu-id="d3296-124">Vytvoření projektu jazyka Visual C# nebo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d3296-124">Create a Visual C# or Visual Basic project.</span></span>  
  
-   <span data-ttu-id="d3296-125">Přidat <xref:System.Windows.Forms.TextBox> a <xref:System.Windows.Forms.MaskedTextBox> ovládací prvky na formuláři, jak je popsáno v předchozím postupu.</span><span class="sxs-lookup"><span data-stu-id="d3296-125">Add the <xref:System.Windows.Forms.TextBox> and <xref:System.Windows.Forms.MaskedTextBox> controls to the form, as described in the previous procedure.</span></span>  
  
-   <span data-ttu-id="d3296-126">Otevření souboru se zdrojovým kódem pro projektu výchozího formuláře.</span><span class="sxs-lookup"><span data-stu-id="d3296-126">Open the source code file for the project's default form.</span></span>  
  
-   <span data-ttu-id="d3296-127">Zdrojový kód v tomto souboru nahraďte kód uvedené v předchozí části "Kódu".</span><span class="sxs-lookup"><span data-stu-id="d3296-127">Replace the source code in this file with the code listed in the previous "Code" section.</span></span>  
  
-   <span data-ttu-id="d3296-128">Kompilace aplikace.</span><span class="sxs-lookup"><span data-stu-id="d3296-128">Compile the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3296-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="d3296-129">See Also</span></span>  
 [<span data-ttu-id="d3296-130">Návod: Práce s ovládacím prvkem MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="d3296-130">Walkthrough: Working with the MaskedTextBox Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-working-with-the-maskedtextbox-control.md)
