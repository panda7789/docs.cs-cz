---
title: Uchování objektu v sadě Visual Studio
ms.date: 07/20/2015
ms.assetid: f1d0b562-e349-4dce-ab5f-c05108467030
ms.openlocfilehash: fbd342c929e8519571c0f6bb76d4091efcfe4476
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350400"
---
# <a name="walkthrough-persisting-an-object-in-visual-studio-visual-basic"></a><span data-ttu-id="b1b27-102">Walkthrough: Persisting an Object in Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1b27-102">Walkthrough: Persisting an Object in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="b1b27-103">Although you can set an object's properties to default values at design time, any values entered at run time are lost when the object is destroyed.</span><span class="sxs-lookup"><span data-stu-id="b1b27-103">Although you can set an object's properties to default values at design time, any values entered at run time are lost when the object is destroyed.</span></span> <span data-ttu-id="b1b27-104">You can use serialization to persist an object's data between instances, which enables you to store values and retrieve them the next time that the object is instantiated.</span><span class="sxs-lookup"><span data-stu-id="b1b27-104">You can use serialization to persist an object's data between instances, which enables you to store values and retrieve them the next time that the object is instantiated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b1b27-105">In Visual Basic, to store simple data, such as a name or number, you can use the `My.Settings` object.</span><span class="sxs-lookup"><span data-stu-id="b1b27-105">In Visual Basic, to store simple data, such as a name or number, you can use the `My.Settings` object.</span></span> <span data-ttu-id="b1b27-106">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="b1b27-106">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
 <span data-ttu-id="b1b27-107">In this walkthrough, you will create a simple `Loan` object and persist its data to a file.</span><span class="sxs-lookup"><span data-stu-id="b1b27-107">In this walkthrough, you will create a simple `Loan` object and persist its data to a file.</span></span> <span data-ttu-id="b1b27-108">You will then retrieve the data from the file when you re-create the object.</span><span class="sxs-lookup"><span data-stu-id="b1b27-108">You will then retrieve the data from the file when you re-create the object.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b1b27-109">This example creates a new file, if the file does not already exist.</span><span class="sxs-lookup"><span data-stu-id="b1b27-109">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="b1b27-110">If an application must create a file, that application must `Create` permission for the folder.</span><span class="sxs-lookup"><span data-stu-id="b1b27-110">If an application must create a file, that application must `Create` permission for the folder.</span></span> <span data-ttu-id="b1b27-111">Permissions are set by using access control lists.</span><span class="sxs-lookup"><span data-stu-id="b1b27-111">Permissions are set by using access control lists.</span></span> <span data-ttu-id="b1b27-112">If the file already exists, the application needs only `Write` permission, a lesser permission.</span><span class="sxs-lookup"><span data-stu-id="b1b27-112">If the file already exists, the application needs only `Write` permission, a lesser permission.</span></span> <span data-ttu-id="b1b27-113">Where possible, it is more secure to create the file during deployment, and only grant `Read` permissions to a single file (instead of Create permissions for a folder).</span><span class="sxs-lookup"><span data-stu-id="b1b27-113">Where possible, it is more secure to create the file during deployment, and only grant `Read` permissions to a single file (instead of Create permissions for a folder).</span></span> <span data-ttu-id="b1b27-114">Also, it is more secure to write data to user folders than to the root folder or the Program Files folder.</span><span class="sxs-lookup"><span data-stu-id="b1b27-114">Also, it is more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b1b27-115">This example stores data in a binary.</span><span class="sxs-lookup"><span data-stu-id="b1b27-115">This example stores data in a binary.</span></span> <span data-ttu-id="b1b27-116">These formats should not be used for sensitive data, such as passwords or credit-card information.</span><span class="sxs-lookup"><span data-stu-id="b1b27-116">These formats should not be used for sensitive data, such as passwords or credit-card information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b1b27-117">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="b1b27-117">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="b1b27-118">To change your settings, click **Import and Export Settings** on the **Tools** menu.</span><span class="sxs-lookup"><span data-stu-id="b1b27-118">To change your settings, click **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="b1b27-119">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="b1b27-119">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-loan-object"></a><span data-ttu-id="b1b27-120">Creating the Loan Object</span><span class="sxs-lookup"><span data-stu-id="b1b27-120">Creating the Loan Object</span></span>  
 <span data-ttu-id="b1b27-121">The first step is to create a `Loan` class and a test application that uses the class.</span><span class="sxs-lookup"><span data-stu-id="b1b27-121">The first step is to create a `Loan` class and a test application that uses the class.</span></span>  
  
### <a name="to-create-the-loan-class"></a><span data-ttu-id="b1b27-122">To create the Loan class</span><span class="sxs-lookup"><span data-stu-id="b1b27-122">To create the Loan class</span></span>  
  
1. <span data-ttu-id="b1b27-123">Create a new Class Library project and name it "LoanClass".</span><span class="sxs-lookup"><span data-stu-id="b1b27-123">Create a new Class Library project and name it "LoanClass".</span></span> <span data-ttu-id="b1b27-124">For more information, see [Creating Solutions and Projects](https://docs.microsoft.com/visualstudio/ide/creating-solutions-and-projects).</span><span class="sxs-lookup"><span data-stu-id="b1b27-124">For more information, see [Creating Solutions and Projects](https://docs.microsoft.com/visualstudio/ide/creating-solutions-and-projects).</span></span>  
  
2. <span data-ttu-id="b1b27-125">In **Solution Explorer**, open the shortcut menu for the Class1 file and choose **Rename**.</span><span class="sxs-lookup"><span data-stu-id="b1b27-125">In **Solution Explorer**, open the shortcut menu for the Class1 file and choose **Rename**.</span></span> <span data-ttu-id="b1b27-126">Rename the file to `Loan` and press ENTER.</span><span class="sxs-lookup"><span data-stu-id="b1b27-126">Rename the file to `Loan` and press ENTER.</span></span> <span data-ttu-id="b1b27-127">Renaming the file will also rename the class to `Loan`.</span><span class="sxs-lookup"><span data-stu-id="b1b27-127">Renaming the file will also rename the class to `Loan`.</span></span>  
  
3. <span data-ttu-id="b1b27-128">Add the following public members to the class:</span><span class="sxs-lookup"><span data-stu-id="b1b27-128">Add the following public members to the class:</span></span>  
  
    ```vb  
    Public Class Loan  
        Implements System.ComponentModel.INotifyPropertyChanged  
  
        Public Property LoanAmount As Double  
        Public Property InterestRate As Double  
        Public Property Term As Integer  
  
        Private p_Customer As String  
        Public Property Customer As String  
            Get  
                Return p_Customer  
            End Get  
            Set(ByVal value As String)  
                p_Customer = value  
                RaiseEvent PropertyChanged(Me,  
                  New System.ComponentModel.PropertyChangedEventArgs("Customer"))  
            End Set  
        End Property  
  
        Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
          Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
  
        Public Sub New(ByVal loanAmount As Double,  
                       ByVal interestRate As Double,  
                       ByVal term As Integer,  
                       ByVal customer As String)  
  
            Me.LoanAmount = loanAmount  
            Me.InterestRate = interestRate  
            Me.Term = term  
            p_Customer = customer  
        End Sub  
    End Class  
    ```  
  
 <span data-ttu-id="b1b27-129">You will also have to create a simple application that uses the `Loan` class.</span><span class="sxs-lookup"><span data-stu-id="b1b27-129">You will also have to create a simple application that uses the `Loan` class.</span></span>  
  
### <a name="to-create-a-test-application"></a><span data-ttu-id="b1b27-130">To create a test application</span><span class="sxs-lookup"><span data-stu-id="b1b27-130">To create a test application</span></span>  
  
1. <span data-ttu-id="b1b27-131">To add a Windows Forms Application project to your solution, on the **File** menu, choose **Add**,**New Project**.</span><span class="sxs-lookup"><span data-stu-id="b1b27-131">To add a Windows Forms Application project to your solution, on the **File** menu, choose **Add**,**New Project**.</span></span>  
  
2. <span data-ttu-id="b1b27-132">In the **Add New Project** dialog box, choose **Windows Forms Application**, and enter `LoanApp` as the name of the project, and then click **OK** to close the dialog box.</span><span class="sxs-lookup"><span data-stu-id="b1b27-132">In the **Add New Project** dialog box, choose **Windows Forms Application**, and enter `LoanApp` as the name of the project, and then click **OK** to close the dialog box.</span></span>  
  
3. <span data-ttu-id="b1b27-133">In **Solution Explorer**, choose the LoanApp project.</span><span class="sxs-lookup"><span data-stu-id="b1b27-133">In **Solution Explorer**, choose the LoanApp project.</span></span>  
  
4. <span data-ttu-id="b1b27-134">On the **Project** menu, choose **Set as StartUp Project**.</span><span class="sxs-lookup"><span data-stu-id="b1b27-134">On the **Project** menu, choose **Set as StartUp Project**.</span></span>  
  
5. <span data-ttu-id="b1b27-135">On the **Project** menu, choose **Add Reference**.</span><span class="sxs-lookup"><span data-stu-id="b1b27-135">On the **Project** menu, choose **Add Reference**.</span></span>  
  
6. <span data-ttu-id="b1b27-136">In the **Add Reference** dialog box, choose the **Projects** tab and then choose the LoanClass project.</span><span class="sxs-lookup"><span data-stu-id="b1b27-136">In the **Add Reference** dialog box, choose the **Projects** tab and then choose the LoanClass project.</span></span>  
  
7. <span data-ttu-id="b1b27-137">Click **OK** to close the dialog box.</span><span class="sxs-lookup"><span data-stu-id="b1b27-137">Click **OK** to close the dialog box.</span></span>  
  
8. <span data-ttu-id="b1b27-138">In the designer, add four <xref:System.Windows.Forms.TextBox> controls to the form.</span><span class="sxs-lookup"><span data-stu-id="b1b27-138">In the designer, add four <xref:System.Windows.Forms.TextBox> controls to the form.</span></span>  
  
9. <span data-ttu-id="b1b27-139">V Editoru kódu přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="b1b27-139">In the Code Editor, add the following code:</span></span>  
  
    ```vb  
    Private WithEvents TestLoan As New LoanClass.Loan(10000.0, 0.075, 36, "Neil Black")  
  
    Private Sub Form1_Load() Handles MyBase.Load  
        TextBox1.Text = TestLoan.LoanAmount.ToString  
        TextBox2.Text = TestLoan.InterestRate.ToString  
        TextBox3.Text = TestLoan.Term.ToString  
        TextBox4.Text = TestLoan.Customer  
    End Sub  
    ```  
  
10. <span data-ttu-id="b1b27-140">Add an event handler for the `PropertyChanged` event to the form by using the following code:</span><span class="sxs-lookup"><span data-stu-id="b1b27-140">Add an event handler for the `PropertyChanged` event to the form by using the following code:</span></span>  
  
    ```vb  
    Public Sub CustomerPropertyChanged(  
          ByVal sender As Object,  
          ByVal e As System.ComponentModel.PropertyChangedEventArgs  
        ) Handles TestLoan.PropertyChanged  
  
        MsgBox(e.PropertyName & " has been changed.")  
    End Sub  
    ```  
  
 <span data-ttu-id="b1b27-141">At this point, you can build and run the application.</span><span class="sxs-lookup"><span data-stu-id="b1b27-141">At this point, you can build and run the application.</span></span> <span data-ttu-id="b1b27-142">Note that the default values from the `Loan` class appear in the text boxes.</span><span class="sxs-lookup"><span data-stu-id="b1b27-142">Note that the default values from the `Loan` class appear in the text boxes.</span></span> <span data-ttu-id="b1b27-143">Try to change the interest-rate value from 7.5 to 7.1, and then close the application and run it again—the value reverts to the default of 7.5.</span><span class="sxs-lookup"><span data-stu-id="b1b27-143">Try to change the interest-rate value from 7.5 to 7.1, and then close the application and run it again—the value reverts to the default of 7.5.</span></span>  
  
 <span data-ttu-id="b1b27-144">In the real world, interest rates change periodically, but not necessarily every time that the application is run.</span><span class="sxs-lookup"><span data-stu-id="b1b27-144">In the real world, interest rates change periodically, but not necessarily every time that the application is run.</span></span> <span data-ttu-id="b1b27-145">Rather than making the user update the interest rate every time that the application runs, it is better to preserve the most recent interest rate between instances of the application.</span><span class="sxs-lookup"><span data-stu-id="b1b27-145">Rather than making the user update the interest rate every time that the application runs, it is better to preserve the most recent interest rate between instances of the application.</span></span> <span data-ttu-id="b1b27-146">In the next step, you will do just that by adding serialization to the Loan class.</span><span class="sxs-lookup"><span data-stu-id="b1b27-146">In the next step, you will do just that by adding serialization to the Loan class.</span></span>  
  
## <a name="using-serialization-to-persist-the-object"></a><span data-ttu-id="b1b27-147">Using Serialization to Persist the Object</span><span class="sxs-lookup"><span data-stu-id="b1b27-147">Using Serialization to Persist the Object</span></span>  
 <span data-ttu-id="b1b27-148">In order to persist the values for the Loan class, you must first mark the class with the `Serializable` attribute.</span><span class="sxs-lookup"><span data-stu-id="b1b27-148">In order to persist the values for the Loan class, you must first mark the class with the `Serializable` attribute.</span></span>  
  
### <a name="to-mark-a-class-as-serializable"></a><span data-ttu-id="b1b27-149">To mark a class as serializable</span><span class="sxs-lookup"><span data-stu-id="b1b27-149">To mark a class as serializable</span></span>  
  
- <span data-ttu-id="b1b27-150">Change the class declaration for the Loan class as follows:</span><span class="sxs-lookup"><span data-stu-id="b1b27-150">Change the class declaration for the Loan class as follows:</span></span>  
  
    ```vb  
    <Serializable()>  
    Public Class Loan  
    ```  
  
 <span data-ttu-id="b1b27-151">The `Serializable` attribute tells the compiler that everything in the class can be persisted to a file.</span><span class="sxs-lookup"><span data-stu-id="b1b27-151">The `Serializable` attribute tells the compiler that everything in the class can be persisted to a file.</span></span> <span data-ttu-id="b1b27-152">Because the `PropertyChanged` event is handled by a Windows Form object, it cannot be serialized.</span><span class="sxs-lookup"><span data-stu-id="b1b27-152">Because the `PropertyChanged` event is handled by a Windows Form object, it cannot be serialized.</span></span> <span data-ttu-id="b1b27-153">The `NonSerialized` attribute can be used to mark class members that should not be persisted.</span><span class="sxs-lookup"><span data-stu-id="b1b27-153">The `NonSerialized` attribute can be used to mark class members that should not be persisted.</span></span>  
  
### <a name="to-prevent-a-member-from-being-serialized"></a><span data-ttu-id="b1b27-154">To prevent a member from being serialized</span><span class="sxs-lookup"><span data-stu-id="b1b27-154">To prevent a member from being serialized</span></span>  
  
- <span data-ttu-id="b1b27-155">Change the declaration for the `PropertyChanged` event as follows:</span><span class="sxs-lookup"><span data-stu-id="b1b27-155">Change the declaration for the `PropertyChanged` event as follows:</span></span>  
  
    ```vb  
    <NonSerialized()>  
    Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
      Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
    ```  
  
 <span data-ttu-id="b1b27-156">The next step is to add the serialization code to the LoanApp application.</span><span class="sxs-lookup"><span data-stu-id="b1b27-156">The next step is to add the serialization code to the LoanApp application.</span></span> <span data-ttu-id="b1b27-157">In order to serialize the class and write it to a file, you will use the <xref:System.IO> and <xref:System.Xml.Serialization> namespaces.</span><span class="sxs-lookup"><span data-stu-id="b1b27-157">In order to serialize the class and write it to a file, you will use the <xref:System.IO> and <xref:System.Xml.Serialization> namespaces.</span></span> <span data-ttu-id="b1b27-158">To avoid typing the fully qualified names, you can add references to the necessary class libraries.</span><span class="sxs-lookup"><span data-stu-id="b1b27-158">To avoid typing the fully qualified names, you can add references to the necessary class libraries.</span></span>  
  
### <a name="to-add-references-to-namespaces"></a><span data-ttu-id="b1b27-159">To add references to namespaces</span><span class="sxs-lookup"><span data-stu-id="b1b27-159">To add references to namespaces</span></span>  
  
- <span data-ttu-id="b1b27-160">Add the following statements to the top of the `Form1` class:</span><span class="sxs-lookup"><span data-stu-id="b1b27-160">Add the following statements to the top of the `Form1` class:</span></span>  
  
    ```vb  
    Imports System.IO  
    Imports System.Runtime.Serialization.Formatters.Binary  
    ```  
  
     <span data-ttu-id="b1b27-161">In this case, you are using a binary formatter to save the object in a binary format.</span><span class="sxs-lookup"><span data-stu-id="b1b27-161">In this case, you are using a binary formatter to save the object in a binary format.</span></span>  
  
 <span data-ttu-id="b1b27-162">The next step is to add code to deserialize the object from the file when the object is created.</span><span class="sxs-lookup"><span data-stu-id="b1b27-162">The next step is to add code to deserialize the object from the file when the object is created.</span></span>  
  
### <a name="to-deserialize-an-object"></a><span data-ttu-id="b1b27-163">K deserializaci objektu</span><span class="sxs-lookup"><span data-stu-id="b1b27-163">To deserialize an object</span></span>  
  
1. <span data-ttu-id="b1b27-164">Add a constant to the class for the serialized data's file name.</span><span class="sxs-lookup"><span data-stu-id="b1b27-164">Add a constant to the class for the serialized data's file name.</span></span>  
  
    ```vb  
    Const FileName As String = "..\..\SavedLoan.bin"  
    ```  
  
2. <span data-ttu-id="b1b27-165">Modify the code in the `Form1_Load` event procedure as follows:</span><span class="sxs-lookup"><span data-stu-id="b1b27-165">Modify the code in the `Form1_Load` event procedure as follows:</span></span>  
  
    ```vb  
    Private WithEvents TestLoan As New LoanClass.Loan(10000.0, 0.075, 36, "Neil Black")  
  
    Private Sub Form1_Load() Handles MyBase.Load  
        If File.Exists(FileName) Then  
            Dim TestFileStream As Stream = File.OpenRead(FileName)  
            Dim deserializer As New BinaryFormatter  
            TestLoan = CType(deserializer.Deserialize(TestFileStream), LoanClass.Loan)  
            TestFileStream.Close()  
        End If  
  
        AddHandler TestLoan.PropertyChanged, AddressOf Me.CustomerPropertyChanged  
  
        TextBox1.Text = TestLoan.LoanAmount.ToString  
        TextBox2.Text = TestLoan.InterestRate.ToString  
        TextBox3.Text = TestLoan.Term.ToString  
        TextBox4.Text = TestLoan.Customer  
    End Sub  
    ```  
  
     <span data-ttu-id="b1b27-166">Note that you first must check that the file exists.</span><span class="sxs-lookup"><span data-stu-id="b1b27-166">Note that you first must check that the file exists.</span></span> <span data-ttu-id="b1b27-167">If it exists, create a <xref:System.IO.Stream> class to read the binary file and a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> class to translate the file.</span><span class="sxs-lookup"><span data-stu-id="b1b27-167">If it exists, create a <xref:System.IO.Stream> class to read the binary file and a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> class to translate the file.</span></span> <span data-ttu-id="b1b27-168">You also need to convert from the stream type to the Loan object type.</span><span class="sxs-lookup"><span data-stu-id="b1b27-168">You also need to convert from the stream type to the Loan object type.</span></span>  
  
 <span data-ttu-id="b1b27-169">Next you must add code to save the data entered in the text boxes to the `Loan` class, and then you must serialize the class to a file.</span><span class="sxs-lookup"><span data-stu-id="b1b27-169">Next you must add code to save the data entered in the text boxes to the `Loan` class, and then you must serialize the class to a file.</span></span>  
  
### <a name="to-save-the-data-and-serialize-the-class"></a><span data-ttu-id="b1b27-170">To save the data and serialize the class</span><span class="sxs-lookup"><span data-stu-id="b1b27-170">To save the data and serialize the class</span></span>  
  
- <span data-ttu-id="b1b27-171">Add the following code to the `Form1_FormClosing` event procedure:</span><span class="sxs-lookup"><span data-stu-id="b1b27-171">Add the following code to the `Form1_FormClosing` event procedure:</span></span>  
  
    ```vb  
    Private Sub Form1_FormClosing() Handles MyBase.FormClosing  
        TestLoan.LoanAmount = CDbl(TextBox1.Text)  
        TestLoan.InterestRate = CDbl(TextBox2.Text)  
        TestLoan.Term = CInt(TextBox3.Text)  
        TestLoan.Customer = TextBox4.Text  
  
        Dim TestFileStream As Stream = File.Create(FileName)  
        Dim serializer As New BinaryFormatter  
        serializer.Serialize(TestFileStream, TestLoan)  
        TestFileStream.Close()  
    End Sub  
    ```  
  
 <span data-ttu-id="b1b27-172">At this point, you can again build and run the application.</span><span class="sxs-lookup"><span data-stu-id="b1b27-172">At this point, you can again build and run the application.</span></span> <span data-ttu-id="b1b27-173">Initially, the default values appear in the text boxes.</span><span class="sxs-lookup"><span data-stu-id="b1b27-173">Initially, the default values appear in the text boxes.</span></span> <span data-ttu-id="b1b27-174">Try to change the values and enter a name in the fourth text box.</span><span class="sxs-lookup"><span data-stu-id="b1b27-174">Try to change the values and enter a name in the fourth text box.</span></span> <span data-ttu-id="b1b27-175">Close the application and then run it again.</span><span class="sxs-lookup"><span data-stu-id="b1b27-175">Close the application and then run it again.</span></span> <span data-ttu-id="b1b27-176">Note that the new values now appear in the text boxes.</span><span class="sxs-lookup"><span data-stu-id="b1b27-176">Note that the new values now appear in the text boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1b27-177">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1b27-177">See also</span></span>

- [<span data-ttu-id="b1b27-178">Serialization (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1b27-178">Serialization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
- [<span data-ttu-id="b1b27-179">Visual Basic Programming Guide</span><span class="sxs-lookup"><span data-stu-id="b1b27-179">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
