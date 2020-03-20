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
ms.openlocfilehash: 0cbb239e24b254c37c453486590185e934adf482
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142170"
---
# <a name="how-to-bind-data-to-the-maskedtextbox-control"></a><span data-ttu-id="c66b3-102">Postupy: Připojení dat k ovládacímu prvku MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="c66b3-102">How to: Bind Data to the MaskedTextBox Control</span></span>
<span data-ttu-id="c66b3-103">Data můžete svázat <xref:System.Windows.Forms.MaskedTextBox> s ovládacím prvkem stejně jako jakýkoli jiný ovládací prvek windows forms.</span><span class="sxs-lookup"><span data-stu-id="c66b3-103">You can bind data to a <xref:System.Windows.Forms.MaskedTextBox> control just as you can to any other Windows Forms control.</span></span> <span data-ttu-id="c66b3-104">Pokud však formát dat v databázi neodpovídá formátu očekávanému definicí masky, bude nutné data přeformátovat.</span><span class="sxs-lookup"><span data-stu-id="c66b3-104">However, if the format of your data in the database does not match the format expected by your mask definition, you will need to reformat the data.</span></span> <span data-ttu-id="c66b3-105">Následující postup ukazuje, jak to <xref:System.Windows.Forms.Binding.Format> provést <xref:System.Windows.Forms.Binding.Parse> pomocí <xref:System.Windows.Forms.Binding> a události třídy k zobrazení samostatné telefonní číslo a telefonní rozšíření databázová pole jako jediné upravitelné pole.</span><span class="sxs-lookup"><span data-stu-id="c66b3-105">The following procedure demonstrates how to do this using the <xref:System.Windows.Forms.Binding.Format> and <xref:System.Windows.Forms.Binding.Parse> events of the <xref:System.Windows.Forms.Binding> class to display separate phone number and phone extension database fields as a single editable field.</span></span>  
  
 <span data-ttu-id="c66b3-106">Následující postup vyžaduje, abyste měli přístup k databázi serveru SQL Server s nainstalovanou ukázkovou databází Northwind.</span><span class="sxs-lookup"><span data-stu-id="c66b3-106">The following procedure requires that you have access to a SQL Server database with the Northwind sample database installed.</span></span>  
  
### <a name="to-bind-data-to-a-maskedtextbox-control"></a><span data-ttu-id="c66b3-107">Vazba dat s ovládacím prvkem MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="c66b3-107">To bind data to a MaskedTextBox control</span></span>  
  
1. <span data-ttu-id="c66b3-108">Vytvořte nový projekt Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c66b3-108">Create a new Windows Forms project.</span></span>  
  
2. <span data-ttu-id="c66b3-109">Přetáhněte <xref:System.Windows.Forms.TextBox> dva ovládací prvky do formuláře. pojmenovat `FirstName` `LastName`a .</span><span class="sxs-lookup"><span data-stu-id="c66b3-109">Drag two <xref:System.Windows.Forms.TextBox> controls onto your form; name them `FirstName` and `LastName`.</span></span>  
  
3. <span data-ttu-id="c66b3-110">Přetáhněte <xref:System.Windows.Forms.MaskedTextBox> ovládací prvek do formuláře. pojmenujte jej `PhoneMask`.</span><span class="sxs-lookup"><span data-stu-id="c66b3-110">Drag a <xref:System.Windows.Forms.MaskedTextBox> control onto your form; name it `PhoneMask`.</span></span>  
  
4. <span data-ttu-id="c66b3-111">Nastavte <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> vlastnost `PhoneMask` na `(000) 000-0000 x9999`.</span><span class="sxs-lookup"><span data-stu-id="c66b3-111">Set the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property of `PhoneMask` to `(000) 000-0000 x9999`.</span></span>  
  
5. <span data-ttu-id="c66b3-112">Přidejte do formuláře následující importy oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c66b3-112">Add the following namespace imports to the form.</span></span>  
  
    ```csharp  
    using System.Data.SqlClient;  
    ```  
  
    ```vb  
    Imports System.Data.SqlClient  
    ```  
  
6. <span data-ttu-id="c66b3-113">Klikněte pravým tlačítkem myši na formulář a zvolte **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="c66b3-113">Right-click the form and choose **View Code**.</span></span> <span data-ttu-id="c66b3-114">Umístěte tento kód kdekoli ve třídě formuláře.</span><span class="sxs-lookup"><span data-stu-id="c66b3-114">Place this code anywhere in your form class.</span></span>  
  
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
  
7. <span data-ttu-id="c66b3-115">Přidejte obslužné rutiny událostí `PhoneNumber` `Extension` pro události <xref:System.Data.DataSet> <xref:System.Windows.Forms.Binding.Format> a <xref:System.Windows.Forms.Binding.Parse> zkombinujte a oddělte pole a od vázaného .</span><span class="sxs-lookup"><span data-stu-id="c66b3-115">Add event handlers for the <xref:System.Windows.Forms.Binding.Format> and <xref:System.Windows.Forms.Binding.Parse> events to combine and separate the `PhoneNumber` and `Extension` fields from the bound <xref:System.Data.DataSet>.</span></span>  
  
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
  
8. <span data-ttu-id="c66b3-116">Přidejte <xref:System.Windows.Forms.Button> do formuláře dva ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="c66b3-116">Add two <xref:System.Windows.Forms.Button> controls to the form.</span></span> <span data-ttu-id="c66b3-117">Pojmenujte je `previousButton` a `nextButton`.</span><span class="sxs-lookup"><span data-stu-id="c66b3-117">Name them `previousButton` and `nextButton`.</span></span> <span data-ttu-id="c66b3-118">Poklepáním na každé <xref:System.Windows.Forms.Control.Click> tlačítko přidejte obslužnou rutinu události a vyplňte obslužné rutiny událostí, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="c66b3-118">Double-click each button to add a <xref:System.Windows.Forms.Control.Click> event handler, and fill in the event handlers as shown in the following code example.</span></span>  
  
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
  
9. <span data-ttu-id="c66b3-119">Spusťte ukázku.</span><span class="sxs-lookup"><span data-stu-id="c66b3-119">Run the sample.</span></span> <span data-ttu-id="c66b3-120">Upravte data a pomocí tlačítek **Předchozí** a **Další** zjistíte, že <xref:System.Data.DataSet>data jsou správně zachována na .</span><span class="sxs-lookup"><span data-stu-id="c66b3-120">Edit the data, and use the **Previous** and **Next** buttons to see that the data is properly persisted to the <xref:System.Data.DataSet>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c66b3-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="c66b3-121">Example</span></span>  
 <span data-ttu-id="c66b3-122">Následující příklad kódu je úplný kód výpis, který vyplývá z dokončení předchozího postupu.</span><span class="sxs-lookup"><span data-stu-id="c66b3-122">The following code example is the full code listing that results from completing the previous procedure.</span></span>  
  
 [!code-cpp[MaskedTextBoxData#1](~/samples/snippets/cpp/VS_Snippets_Winforms/MaskedTextBoxData/cpp/form1.cpp#1)]
 [!code-csharp[MaskedTextBoxData#1](~/samples/snippets/csharp/VS_Snippets_Winforms/MaskedTextBoxData/CS/form1.cs#1)]
 [!code-vb[MaskedTextBoxData#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/MaskedTextBoxData/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c66b3-123">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="c66b3-123">Compiling the Code</span></span>  
  
- <span data-ttu-id="c66b3-124">Vytvořte projekt Visual C# nebo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c66b3-124">Create a Visual C# or Visual Basic project.</span></span>  
  
- <span data-ttu-id="c66b3-125">Přidejte <xref:System.Windows.Forms.TextBox> <xref:System.Windows.Forms.MaskedTextBox> ovládací prvky a do formuláře, jak je popsáno v předchozím postupu.</span><span class="sxs-lookup"><span data-stu-id="c66b3-125">Add the <xref:System.Windows.Forms.TextBox> and <xref:System.Windows.Forms.MaskedTextBox> controls to the form, as described in the previous procedure.</span></span>  
  
- <span data-ttu-id="c66b3-126">Otevřete soubor zdrojového kódu pro výchozí formulář projektu.</span><span class="sxs-lookup"><span data-stu-id="c66b3-126">Open the source code file for the project's default form.</span></span>  
  
- <span data-ttu-id="c66b3-127">Nahraďte zdrojový kód v tomto souboru kódem uvedeným v předchozí části "Kód".</span><span class="sxs-lookup"><span data-stu-id="c66b3-127">Replace the source code in this file with the code listed in the previous "Code" section.</span></span>  
  
- <span data-ttu-id="c66b3-128">Zkompilujte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c66b3-128">Compile the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c66b3-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="c66b3-129">See also</span></span>

- [<span data-ttu-id="c66b3-130">Návod: Práce s ovládacím prvkem MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="c66b3-130">Walkthrough: Working with the MaskedTextBox Control</span></span>](walkthrough-working-with-the-maskedtextbox-control.md)
