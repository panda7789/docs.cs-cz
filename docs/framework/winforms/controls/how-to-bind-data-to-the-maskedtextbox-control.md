---
title: 'Postupy: Vytvoření vazby dat k ovládacímu prvku MaskedTextBox'
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
ms.openlocfilehash: ebc8eaf63c6b5280961a80ef11afb919810dbdb8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761367"
---
# <a name="how-to-bind-data-to-the-maskedtextbox-control"></a>Postupy: Vytvoření vazby dat k ovládacímu prvku MaskedTextBox
Můžete svázat data <xref:System.Windows.Forms.MaskedTextBox> řídit stejně jako na jakýkoli jiný ovládací prvek Windows Forms. Ale pokud formátu vašich dat v databázi neodpovídá formátu očekávaném definicí maska, je potřeba změnit formát data. Následující postup ukazuje, jak to udělat <xref:System.Windows.Forms.Binding.Format> a <xref:System.Windows.Forms.Binding.Parse> události <xref:System.Windows.Forms.Binding> třídy k zobrazení samostatné telefonní číslo a Telefon rozšíření databázová pole jako jedno pole upravitelné.  
  
 Následující postup vyžaduje, abyste měli přístup k databázi SQL serveru s ukázkovou databází Northwind nainstalované.  
  
### <a name="to-bind-data-to-a-maskedtextbox-control"></a>Vazba dat k ovládacímu prvku MaskedTextBox  
  
1. Vytvoření nového projektu Windows Forms.  
  
2. Přetáhněte dva <xref:System.Windows.Forms.TextBox> ovládací prvky do formuláře; je název `FirstName` a `LastName`.  
  
3. Přetáhněte <xref:System.Windows.Forms.MaskedTextBox> ovládací prvek do formuláře; pojmenujte ji `PhoneMask`.  
  
4. Nastavte <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> vlastnost `PhoneMask` k `(000) 000-0000 x9999`.  
  
5. Přidáte že následující obor názvů naimportuje do formuláře.  
  
    ```csharp  
    using System.Data.SqlClient;  
    ```  
  
    ```vb  
    Imports System.Data.SqlClient  
    ```  
  
6. Klikněte pravým tlačítkem na formuláři a zvolte **zobrazit kód**. Tento kód umístíte kamkoli do vaší třídy formuláře.  
  
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
  
7. Přidání obslužné rutiny událostí pro <xref:System.Windows.Forms.Binding.Format> a <xref:System.Windows.Forms.Binding.Parse> události zkombinovat a oddělit `PhoneNumber` a `Extension` pole z vázaného <xref:System.Data.DataSet>.  
  
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
  
8. Přidejte dva <xref:System.Windows.Forms.Button> ovládací prvky do formuláře. Pojmenujte je `previousButton` a `nextButton`. Klikněte dvakrát na každé tlačítko pro přidání <xref:System.Windows.Forms.Control.Click> obslužné rutiny události a vyplňte obslužné rutiny událostí, jak je znázorněno v následujícím příkladu kódu.  
  
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
  
9. Spusťte ukázku. Upravit data a použít **předchozí** a **Další** tlačítek a uvidíte, že data se ukládají správně do <xref:System.Data.DataSet>.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu je celý kód informacích, které je výsledkem dokončení předchozího postupu.  
  
 [!code-cpp[MaskedTextBoxData#1](~/samples/snippets/cpp/VS_Snippets_Winforms/MaskedTextBoxData/cpp/form1.cpp#1)]
 [!code-csharp[MaskedTextBoxData#1](~/samples/snippets/csharp/VS_Snippets_Winforms/MaskedTextBoxData/CS/form1.cs#1)]
 [!code-vb[MaskedTextBoxData#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/MaskedTextBoxData/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
- Vytvoření Vizuálu C# nebo projektu jazyka Visual Basic.  
  
- Přidat <xref:System.Windows.Forms.TextBox> a <xref:System.Windows.Forms.MaskedTextBox> ovládacích prvků do formuláře, jak je popsáno v předchozím postupu.  
  
- Otevření souboru se zdrojovým kódem pro výchozí formuláře projektu.  
  
- Zdrojový kód v tomto souboru nahraďte kód uvedený v předchozí části "Kód".  
  
- Zkompilujte aplikaci.  
  
## <a name="see-also"></a>Viz také:

- [Návod: Práce s ovládacím prvkem MaskedTextBox](walkthrough-working-with-the-maskedtextbox-control.md)
