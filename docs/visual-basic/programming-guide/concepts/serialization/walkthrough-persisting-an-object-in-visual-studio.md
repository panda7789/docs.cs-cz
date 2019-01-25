---
title: Uchování objektu v sadě Visual Studio (Visual Basic)
ms.date: 07/20/2015
ms.assetid: f1d0b562-e349-4dce-ab5f-c05108467030
ms.openlocfilehash: 002c5470765b33d038ab0fd463fcc6ccfdf6f109
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690433"
---
# <a name="walkthrough-persisting-an-object-in-visual-studio-visual-basic"></a><span data-ttu-id="7da33-102">Průvodce: Uchování objektu v sadě Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7da33-102">Walkthrough: Persisting an Object in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="7da33-103">V době návrhu, je možné nastavit na výchozí hodnoty vlastností objektu, všechny hodnoty zadané v době běhu budou ztraceny, pokud objekt je zničen.</span><span class="sxs-lookup"><span data-stu-id="7da33-103">Although you can set an object's properties to default values at design time, any values entered at run time are lost when the object is destroyed.</span></span> <span data-ttu-id="7da33-104">Serializace můžete použít k uchování dat objektu mezi instancemi, které vám umožní uložení hodnot a načíst je další čas, který je vytvořena instance objektu.</span><span class="sxs-lookup"><span data-stu-id="7da33-104">You can use serialization to persist an object's data between instances, which enables you to store values and retrieve them the next time that the object is instantiated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7da33-105">V jazyce Visual Basic, uložte jednoduchá dat, jako je název nebo číslo, můžete `My.Settings` objektu.</span><span class="sxs-lookup"><span data-stu-id="7da33-105">In Visual Basic, to store simple data, such as a name or number, you can use the `My.Settings` object.</span></span> <span data-ttu-id="7da33-106">Další informace najdete v tématu [My.Settings – objekt](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="7da33-106">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
 <span data-ttu-id="7da33-107">V tomto návodu vytvoříte jednoduchou `Loan` objektu a zachovat data do souboru.</span><span class="sxs-lookup"><span data-stu-id="7da33-107">In this walkthrough, you will create a simple `Loan` object and persist its data to a file.</span></span> <span data-ttu-id="7da33-108">Když znovu vytvoříte objekt se budou ze souboru načítat data.</span><span class="sxs-lookup"><span data-stu-id="7da33-108">You will then retrieve the data from the file when you re-create the object.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7da33-109">Tento příklad vytvoří nový soubor, pokud soubor již neexistuje.</span><span class="sxs-lookup"><span data-stu-id="7da33-109">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="7da33-110">Pokud aplikace musí vytvořit soubor, musí tuto aplikaci `Create` oprávnění pro složku.</span><span class="sxs-lookup"><span data-stu-id="7da33-110">If an application must create a file, that application must `Create` permission for the folder.</span></span> <span data-ttu-id="7da33-111">Oprávnění jsou nastavená pomocí seznamů řízení přístupu.</span><span class="sxs-lookup"><span data-stu-id="7da33-111">Permissions are set by using access control lists.</span></span> <span data-ttu-id="7da33-112">Pokud soubor již existuje, aplikace potřebuje pouze `Write` oprávnění, nižší oprávnění.</span><span class="sxs-lookup"><span data-stu-id="7da33-112">If the file already exists, the application needs only `Write` permission, a lesser permission.</span></span> <span data-ttu-id="7da33-113">Kde je to možné, je bezpečnější vytvořit soubor při nasazení a udělit pouze `Read` oprávnění do jednoho souboru (místo vytvořit oprávnění pro složku).</span><span class="sxs-lookup"><span data-stu-id="7da33-113">Where possible, it is more secure to create the file during deployment, and only grant `Read` permissions to a single file (instead of Create permissions for a folder).</span></span> <span data-ttu-id="7da33-114">Navíc je bezpečnější zapsat data do uživatelské složky než do kořenové složky nebo ve složce Program Files.</span><span class="sxs-lookup"><span data-stu-id="7da33-114">Also, it is more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7da33-115">V tomto příkladu ukládá data do binární hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7da33-115">This example stores data in a binary.</span></span> <span data-ttu-id="7da33-116">Tyto formáty by neměla používat pro citlivá data, jako jsou hesla nebo informace o platební kartě.</span><span class="sxs-lookup"><span data-stu-id="7da33-116">These formats should not be used for sensitive data, such as passwords or credit-card information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7da33-117">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="7da33-117">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="7da33-118">Chcete-li změnit nastavení, klikněte na tlačítko **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="7da33-118">To change your settings, click **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="7da33-119">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="7da33-119">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-loan-object"></a><span data-ttu-id="7da33-120">Vytvoření objektu půjčky</span><span class="sxs-lookup"><span data-stu-id="7da33-120">Creating the Loan Object</span></span>  
 <span data-ttu-id="7da33-121">Prvním krokem je vytvoření `Loan` třídy a testovací aplikaci, která používá třídu.</span><span class="sxs-lookup"><span data-stu-id="7da33-121">The first step is to create a `Loan` class and a test application that uses the class.</span></span>  
  
### <a name="to-create-the-loan-class"></a><span data-ttu-id="7da33-122">Chcete-li vytvořit třídu půjčky</span><span class="sxs-lookup"><span data-stu-id="7da33-122">To create the Loan class</span></span>  
  
1.  <span data-ttu-id="7da33-123">Vytvořte nový projekt knihovny tříd s názvem "LoanClass".</span><span class="sxs-lookup"><span data-stu-id="7da33-123">Create a new Class Library project and name it "LoanClass".</span></span> <span data-ttu-id="7da33-124">Další informace najdete v tématu [vytváření řešení a projekty](https://docs.microsoft.com/visualstudio/ide/creating-solutions-and-projects).</span><span class="sxs-lookup"><span data-stu-id="7da33-124">For more information, see [Creating Solutions and Projects](https://docs.microsoft.com/visualstudio/ide/creating-solutions-and-projects).</span></span>  
  
2.  <span data-ttu-id="7da33-125">V **Průzkumníka řešení**, otevřete místní nabídku pro soubor Class1 a zvolte **přejmenovat**.</span><span class="sxs-lookup"><span data-stu-id="7da33-125">In **Solution Explorer**, open the shortcut menu for the Class1 file and choose **Rename**.</span></span> <span data-ttu-id="7da33-126">Přejmenujte soubor na `Loan` a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="7da33-126">Rename the file to `Loan` and press ENTER.</span></span> <span data-ttu-id="7da33-127">Přejmenování souboru se také přejmenujte třídu na `Loan`.</span><span class="sxs-lookup"><span data-stu-id="7da33-127">Renaming the file will also rename the class to `Loan`.</span></span>  
  
3.  <span data-ttu-id="7da33-128">Přidejte následující veřejné členy do třídy:</span><span class="sxs-lookup"><span data-stu-id="7da33-128">Add the following public members to the class:</span></span>  
  
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
  
 <span data-ttu-id="7da33-129">Budete také muset vytvořit jednoduchou aplikaci, která používá `Loan` třídy.</span><span class="sxs-lookup"><span data-stu-id="7da33-129">You will also have to create a simple application that uses the `Loan` class.</span></span>  
  
### <a name="to-create-a-test-application"></a><span data-ttu-id="7da33-130">Chcete-li vytvořit testovací aplikace</span><span class="sxs-lookup"><span data-stu-id="7da33-130">To create a test application</span></span>  
  
1.  <span data-ttu-id="7da33-131">Chcete-li přidat projekt aplikace Windows Forms do vašeho řešení na **souboru** nabídce zvolte **přidat**,**nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="7da33-131">To add a Windows Forms Application project to your solution, on the **File** menu, choose **Add**,**New Project**.</span></span>  
  
2.  <span data-ttu-id="7da33-132">V **přidat nový projekt** dialogového okna zvolte **formulářová aplikace Windows**a zadejte `LoanApp` jako název projektu a pak klikněte na tlačítko **OK** zavřete dialogové okno .</span><span class="sxs-lookup"><span data-stu-id="7da33-132">In the **Add New Project** dialog box, choose **Windows Forms Application**, and enter `LoanApp` as the name of the project, and then click **OK** to close the dialog box.</span></span>  
  
3.  <span data-ttu-id="7da33-133">V **Průzkumníka řešení**, vyberte projekt LoanApp.</span><span class="sxs-lookup"><span data-stu-id="7da33-133">In **Solution Explorer**, choose the LoanApp project.</span></span>  
  
4.  <span data-ttu-id="7da33-134">Na **projektu** nabídce zvolte **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="7da33-134">On the **Project** menu, choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="7da33-135">Na **projektu** nabídce zvolte **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="7da33-135">On the **Project** menu, choose **Add Reference**.</span></span>  
  
6.  <span data-ttu-id="7da33-136">V **přidat odkaz** dialogového okna zvolte **projekty** kartu a pak zvolte projekt LoanClass.</span><span class="sxs-lookup"><span data-stu-id="7da33-136">In the **Add Reference** dialog box, choose the **Projects** tab and then choose the LoanClass project.</span></span>  
  
7.  <span data-ttu-id="7da33-137">Kliknutím na **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="7da33-137">Click **OK** to close the dialog box.</span></span>  
  
8.  <span data-ttu-id="7da33-138">V návrháři, přidejte čtyři <xref:System.Windows.Forms.TextBox> ovládací prvky do formuláře.</span><span class="sxs-lookup"><span data-stu-id="7da33-138">In the designer, add four <xref:System.Windows.Forms.TextBox> controls to the form.</span></span>  
  
9. <span data-ttu-id="7da33-139">V Editoru kódu přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="7da33-139">In the Code Editor, add the following code:</span></span>  
  
    ```vb  
    Private WithEvents TestLoan As New LoanClass.Loan(10000.0, 0.075, 36, "Neil Black")  
  
    Private Sub Form1_Load() Handles MyBase.Load  
        TextBox1.Text = TestLoan.LoanAmount.ToString  
        TextBox2.Text = TestLoan.InterestRate.ToString  
        TextBox3.Text = TestLoan.Term.ToString  
        TextBox4.Text = TestLoan.Customer  
    End Sub  
    ```  
  
10. <span data-ttu-id="7da33-140">Přidat obslužnou rutinu události pro `PropertyChanged` událostí do formuláře pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="7da33-140">Add an event handler for the `PropertyChanged` event to the form by using the following code:</span></span>  
  
    ```vb  
    Public Sub CustomerPropertyChanged(  
          ByVal sender As Object,  
          ByVal e As System.ComponentModel.PropertyChangedEventArgs  
        ) Handles TestLoan.PropertyChanged  
  
        MsgBox(e.PropertyName & " has been changed.")  
    End Sub  
    ```  
  
 <span data-ttu-id="7da33-141">V tomto okamžiku můžete sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7da33-141">At this point, you can build and run the application.</span></span> <span data-ttu-id="7da33-142">Všimněte si, že výchozí hodnoty z `Loan` třídy se zobrazí v textových polích.</span><span class="sxs-lookup"><span data-stu-id="7da33-142">Note that the default values from the `Loan` class appear in the text boxes.</span></span> <span data-ttu-id="7da33-143">Zkuste změnit hodnotu úrokové sazby 7.5 na 7.1 a potom ukončete aplikaci a spustíte jej znovu – hodnota nastaví na výchozí hodnotu 7.5.</span><span class="sxs-lookup"><span data-stu-id="7da33-143">Try to change the interest-rate value from 7.5 to 7.1, and then close the application and run it again—the value reverts to the default of 7.5.</span></span>  
  
 <span data-ttu-id="7da33-144">V praxi úrokové sazby změnit pravidelně, ale ne nutně pokaždé, když je aplikace spuštěna.</span><span class="sxs-lookup"><span data-stu-id="7da33-144">In the real world, interest rates change periodically, but not necessarily every time that the application is run.</span></span> <span data-ttu-id="7da33-145">Místo toho uživatel aktualizovat úrokové sazby pokaždé, když je aplikace spuštěná, je lepší zachovat nejnovější úrokové sazby mezi instancemi aplikace.</span><span class="sxs-lookup"><span data-stu-id="7da33-145">Rather than making the user update the interest rate every time that the application runs, it is better to preserve the most recent interest rate between instances of the application.</span></span> <span data-ttu-id="7da33-146">V dalším kroku se přesně to provést přidáním serializace do třídy půjčky.</span><span class="sxs-lookup"><span data-stu-id="7da33-146">In the next step, you will do just that by adding serialization to the Loan class.</span></span>  
  
## <a name="using-serialization-to-persist-the-object"></a><span data-ttu-id="7da33-147">Pomocí serializace k uchování objektu</span><span class="sxs-lookup"><span data-stu-id="7da33-147">Using Serialization to Persist the Object</span></span>  
 <span data-ttu-id="7da33-148">Aby bylo možné zachovat hodnoty pro třídu půjček, musíte nejprve označte třídu `Serializable` atribut.</span><span class="sxs-lookup"><span data-stu-id="7da33-148">In order to persist the values for the Loan class, you must first mark the class with the `Serializable` attribute.</span></span>  
  
### <a name="to-mark-a-class-as-serializable"></a><span data-ttu-id="7da33-149">Chcete-li označit třídu jako serializovatelný</span><span class="sxs-lookup"><span data-stu-id="7da33-149">To mark a class as serializable</span></span>  
  
-   <span data-ttu-id="7da33-150">Změňte deklaraci třídy pro třídu půjčky následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="7da33-150">Change the class declaration for the Loan class as follows:</span></span>  
  
    ```vb  
    <Serializable()>  
    Public Class Loan  
    ```  
  
 <span data-ttu-id="7da33-151">`Serializable` Atribut oznamuje kompilátoru, že všechno, co ve třídě, můžete nastavit jako trvalý, do souboru.</span><span class="sxs-lookup"><span data-stu-id="7da33-151">The `Serializable` attribute tells the compiler that everything in the class can be persisted to a file.</span></span> <span data-ttu-id="7da33-152">Vzhledem k tomu, `PropertyChanged` událost zpracovává objektem formuláře Windows, nejde ho serializovat.</span><span class="sxs-lookup"><span data-stu-id="7da33-152">Because the `PropertyChanged` event is handled by a Windows Form object, it cannot be serialized.</span></span> <span data-ttu-id="7da33-153">`NonSerialized` Atribut lze použít k označení členy třídy, které by neměly být trvalé.</span><span class="sxs-lookup"><span data-stu-id="7da33-153">The `NonSerialized` attribute can be used to mark class members that should not be persisted.</span></span>  
  
### <a name="to-prevent-a-member-from-being-serialized"></a><span data-ttu-id="7da33-154">Chcete-li zabránit serializována člena</span><span class="sxs-lookup"><span data-stu-id="7da33-154">To prevent a member from being serialized</span></span>  
  
-   <span data-ttu-id="7da33-155">Změna deklarace `PropertyChanged` událostí následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="7da33-155">Change the declaration for the `PropertyChanged` event as follows:</span></span>  
  
    ```vb  
    <NonSerialized()>  
    Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
      Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
    ```  
  
 <span data-ttu-id="7da33-156">Dalším krokem je přidání Serializační kód do aplikace LoanApp.</span><span class="sxs-lookup"><span data-stu-id="7da33-156">The next step is to add the serialization code to the LoanApp application.</span></span> <span data-ttu-id="7da33-157">K serializaci třídy a zápis do souboru, kterou použijete <xref:System.IO> a <xref:System.Xml.Serialization> obory názvů.</span><span class="sxs-lookup"><span data-stu-id="7da33-157">In order to serialize the class and write it to a file, you will use the <xref:System.IO> and <xref:System.Xml.Serialization> namespaces.</span></span> <span data-ttu-id="7da33-158">Abyste nemuseli zadávat plně kvalifikované názvy, můžete přidat odkazy na knihovny tříd nezbytné.</span><span class="sxs-lookup"><span data-stu-id="7da33-158">To avoid typing the fully qualified names, you can add references to the necessary class libraries.</span></span>  
  
### <a name="to-add-references-to-namespaces"></a><span data-ttu-id="7da33-159">Chcete-li přidat odkazy na obory názvů</span><span class="sxs-lookup"><span data-stu-id="7da33-159">To add references to namespaces</span></span>  
  
-   <span data-ttu-id="7da33-160">Přidejte následující příkazy k hornímu okraji `Form1` třídy:</span><span class="sxs-lookup"><span data-stu-id="7da33-160">Add the following statements to the top of the `Form1` class:</span></span>  
  
    ```vb  
    Imports System.IO  
    Imports System.Runtime.Serialization.Formatters.Binary  
    ```  
  
     <span data-ttu-id="7da33-161">V tomto případě používáte binární formátovací modul k uložení objektu v binárním formátu.</span><span class="sxs-lookup"><span data-stu-id="7da33-161">In this case, you are using a binary formatter to save the object in a binary format.</span></span>  
  
 <span data-ttu-id="7da33-162">Dalším krokem je přidání kódu k deserializaci objektu ze souboru při vytvoření objektu.</span><span class="sxs-lookup"><span data-stu-id="7da33-162">The next step is to add code to deserialize the object from the file when the object is created.</span></span>  
  
### <a name="to-deserialize-an-object"></a><span data-ttu-id="7da33-163">K deserializaci objektu</span><span class="sxs-lookup"><span data-stu-id="7da33-163">To deserialize an object</span></span>  
  
1.  <span data-ttu-id="7da33-164">Přidejte konstanty do třídy pro název souboru serializovaná data.</span><span class="sxs-lookup"><span data-stu-id="7da33-164">Add a constant to the class for the serialized data's file name.</span></span>  
  
    ```vb  
    Const FileName As String = "..\..\SavedLoan.bin"  
    ```  
  
2.  <span data-ttu-id="7da33-165">Změňte kód v `Form1_Load` procedury události následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="7da33-165">Modify the code in the `Form1_Load` event procedure as follows:</span></span>  
  
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
  
     <span data-ttu-id="7da33-166">Všimněte si, že nejprve musíte zkontrolovat, zda soubor existuje.</span><span class="sxs-lookup"><span data-stu-id="7da33-166">Note that you first must check that the file exists.</span></span> <span data-ttu-id="7da33-167">Pokud existuje, vytvořit <xref:System.IO.Stream> třídy ke čtení binárního souboru a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> třídy pro převod souboru.</span><span class="sxs-lookup"><span data-stu-id="7da33-167">If it exists, create a <xref:System.IO.Stream> class to read the binary file and a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> class to translate the file.</span></span> <span data-ttu-id="7da33-168">Také je potřeba převést z typu datový proud na typ objektu půjčky.</span><span class="sxs-lookup"><span data-stu-id="7da33-168">You also need to convert from the stream type to the Loan object type.</span></span>  
  
 <span data-ttu-id="7da33-169">Dále je nutné přidat kód pro uložení údaje zadávané do textových polí `Loan` třídy a pak musí serializovat třídu do souboru.</span><span class="sxs-lookup"><span data-stu-id="7da33-169">Next you must add code to save the data entered in the text boxes to the `Loan` class, and then you must serialize the class to a file.</span></span>  
  
### <a name="to-save-the-data-and-serialize-the-class"></a><span data-ttu-id="7da33-170">Chcete uložit data a serializaci třídy</span><span class="sxs-lookup"><span data-stu-id="7da33-170">To save the data and serialize the class</span></span>  
  
-   <span data-ttu-id="7da33-171">Přidejte následující kód, který `Form1_FormClosing` procedury události:</span><span class="sxs-lookup"><span data-stu-id="7da33-171">Add the following code to the `Form1_FormClosing` event procedure:</span></span>  
  
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
  
 <span data-ttu-id="7da33-172">V tomto okamžiku můžete znovu sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7da33-172">At this point, you can again build and run the application.</span></span> <span data-ttu-id="7da33-173">Na začátku zobrazí výchozí hodnoty v textových polích.</span><span class="sxs-lookup"><span data-stu-id="7da33-173">Initially, the default values appear in the text boxes.</span></span> <span data-ttu-id="7da33-174">Pokuste se změnit hodnoty a zadejte název do textového pole čtvrtý.</span><span class="sxs-lookup"><span data-stu-id="7da33-174">Try to change the values and enter a name in the fourth text box.</span></span> <span data-ttu-id="7da33-175">Ukončete aplikaci a znovu jej spusťte.</span><span class="sxs-lookup"><span data-stu-id="7da33-175">Close the application and then run it again.</span></span> <span data-ttu-id="7da33-176">Všimněte si, že nové hodnoty teď budou zobrazovat v textových polích.</span><span class="sxs-lookup"><span data-stu-id="7da33-176">Note that the new values now appear in the text boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7da33-177">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7da33-177">See also</span></span>
- [<span data-ttu-id="7da33-178">Serializace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7da33-178">Serialization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
- [<span data-ttu-id="7da33-179">Průvodce programováním v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7da33-179">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
