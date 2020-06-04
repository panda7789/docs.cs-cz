---
title: Uchování objektu v sadě Visual Studio
ms.date: 07/20/2015
ms.assetid: f1d0b562-e349-4dce-ab5f-c05108467030
ms.openlocfilehash: e4eaf87c99ea1577d7f3ca40e628c00cc2700511
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413126"
---
# <a name="walkthrough-persisting-an-object-in-visual-studio-visual-basic"></a><span data-ttu-id="40989-102">Návod: uchování objektu v aplikaci Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40989-102">Walkthrough: Persisting an Object in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="40989-103">I když můžete nastavit vlastnosti objektu na výchozí hodnoty v době návrhu, budou při zničení objektu ztraceny všechny hodnoty zadané v době běhu.</span><span class="sxs-lookup"><span data-stu-id="40989-103">Although you can set an object's properties to default values at design time, any values entered at run time are lost when the object is destroyed.</span></span> <span data-ttu-id="40989-104">Můžete použít serializaci k uchování dat objektu mezi instancemi, což umožňuje ukládat hodnoty a načíst je při příštím vytvoření instance objektu.</span><span class="sxs-lookup"><span data-stu-id="40989-104">You can use serialization to persist an object's data between instances, which enables you to store values and retrieve them the next time that the object is instantiated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40989-105">V Visual Basic pro ukládání jednoduchých dat, jako je název nebo číslo, můžete použít `My.Settings` objekt.</span><span class="sxs-lookup"><span data-stu-id="40989-105">In Visual Basic, to store simple data, such as a name or number, you can use the `My.Settings` object.</span></span> <span data-ttu-id="40989-106">Další informace najdete v tématu [objekt My. Settings](../../../language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="40989-106">For more information, see [My.Settings Object](../../../language-reference/objects/my-settings-object.md).</span></span>  
  
 <span data-ttu-id="40989-107">V tomto návodu vytvoříte jednoduchý objekt a zachová `Loan` jeho data do souboru.</span><span class="sxs-lookup"><span data-stu-id="40989-107">In this walkthrough, you will create a simple `Loan` object and persist its data to a file.</span></span> <span data-ttu-id="40989-108">Po opětovném vytvoření objektu načtěte data ze souboru.</span><span class="sxs-lookup"><span data-stu-id="40989-108">You will then retrieve the data from the file when you re-create the object.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="40989-109">Tento příklad vytvoří nový soubor, pokud soubor ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="40989-109">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="40989-110">Pokud aplikace musí vytvořit soubor, musí mít tato aplikace `Create` oprávnění pro tuto složku.</span><span class="sxs-lookup"><span data-stu-id="40989-110">If an application must create a file, that application must `Create` permission for the folder.</span></span> <span data-ttu-id="40989-111">Oprávnění se nastavují pomocí seznamů řízení přístupu.</span><span class="sxs-lookup"><span data-stu-id="40989-111">Permissions are set by using access control lists.</span></span> <span data-ttu-id="40989-112">Pokud soubor již existuje, aplikace potřebuje pouze `Write` oprávnění a menší oprávnění.</span><span class="sxs-lookup"><span data-stu-id="40989-112">If the file already exists, the application needs only `Write` permission, a lesser permission.</span></span> <span data-ttu-id="40989-113">Pokud je to možné, je bezpečnější vytvořit soubor během nasazení a udělit `Read` oprávnění pouze k jednomu souboru (místo oprávnění k vytvoření složky).</span><span class="sxs-lookup"><span data-stu-id="40989-113">Where possible, it is more secure to create the file during deployment, and only grant `Read` permissions to a single file (instead of Create permissions for a folder).</span></span> <span data-ttu-id="40989-114">Je také bezpečnější zapsat data do složek uživatele než do kořenové složky nebo do složky Program Files.</span><span class="sxs-lookup"><span data-stu-id="40989-114">Also, it is more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="40989-115">Tento příklad ukládá data v binárním souboru.</span><span class="sxs-lookup"><span data-stu-id="40989-115">This example stores data in a binary.</span></span> <span data-ttu-id="40989-116">Tyto formáty by se neměly používat pro citlivá data, jako jsou hesla nebo informace o kreditních kartách.</span><span class="sxs-lookup"><span data-stu-id="40989-116">These formats should not be used for sensitive data, such as passwords or credit-card information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40989-117">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="40989-117">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="40989-118">Chcete-li změnit nastavení, klikněte na položku **Nastavení importu a exportu** v nabídce **nástroje** .</span><span class="sxs-lookup"><span data-stu-id="40989-118">To change your settings, click **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="40989-119">Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="40989-119">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-loan-object"></a><span data-ttu-id="40989-120">Vytvoření objektu výpůjčky</span><span class="sxs-lookup"><span data-stu-id="40989-120">Creating the Loan Object</span></span>  
 <span data-ttu-id="40989-121">Prvním krokem je vytvoření `Loan` třídy a testovací aplikace, která používá třídu.</span><span class="sxs-lookup"><span data-stu-id="40989-121">The first step is to create a `Loan` class and a test application that uses the class.</span></span>  
  
### <a name="to-create-the-loan-class"></a><span data-ttu-id="40989-122">Vytvoření třídy výpůjčky</span><span class="sxs-lookup"><span data-stu-id="40989-122">To create the Loan class</span></span>  
  
1. <span data-ttu-id="40989-123">Vytvořte nový projekt knihovny tříd a pojmenujte ho "LoanClass".</span><span class="sxs-lookup"><span data-stu-id="40989-123">Create a new Class Library project and name it "LoanClass".</span></span> <span data-ttu-id="40989-124">Další informace najdete v tématu [vytváření řešení a projektů](https://docs.microsoft.com/visualstudio/ide/creating-solutions-and-projects).</span><span class="sxs-lookup"><span data-stu-id="40989-124">For more information, see [Creating Solutions and Projects](https://docs.microsoft.com/visualstudio/ide/creating-solutions-and-projects).</span></span>  
  
2. <span data-ttu-id="40989-125">V **Průzkumník řešení**otevřete místní nabídku pro soubor Class1 a vyberte možnost **Přejmenovat**.</span><span class="sxs-lookup"><span data-stu-id="40989-125">In **Solution Explorer**, open the shortcut menu for the Class1 file and choose **Rename**.</span></span> <span data-ttu-id="40989-126">Přejmenujte soubor na `Loan` a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="40989-126">Rename the file to `Loan` and press ENTER.</span></span> <span data-ttu-id="40989-127">Přejmenováním souboru dojde také k přejmenování třídy na `Loan` .</span><span class="sxs-lookup"><span data-stu-id="40989-127">Renaming the file will also rename the class to `Loan`.</span></span>  
  
3. <span data-ttu-id="40989-128">Do třídy přidejte následující veřejné členy:</span><span class="sxs-lookup"><span data-stu-id="40989-128">Add the following public members to the class:</span></span>  
  
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
  
 <span data-ttu-id="40989-129">Také budete muset vytvořit jednoduchou aplikaci, která používá `Loan` třídu.</span><span class="sxs-lookup"><span data-stu-id="40989-129">You will also have to create a simple application that uses the `Loan` class.</span></span>  
  
### <a name="to-create-a-test-application"></a><span data-ttu-id="40989-130">Vytvoření testovací aplikace</span><span class="sxs-lookup"><span data-stu-id="40989-130">To create a test application</span></span>  
  
1. <span data-ttu-id="40989-131">Chcete-li do řešení přidat projekt aplikace model Windows Forms, vyberte v nabídce **soubor** možnost **Přidat**,**Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="40989-131">To add a Windows Forms Application project to your solution, on the **File** menu, choose **Add**,**New Project**.</span></span>  
  
2. <span data-ttu-id="40989-132">V dialogovém okně **Přidat nový projekt** zvolte možnost **model Windows Forms aplikace**a zadejte `LoanApp` název projektu a potom kliknutím na tlačítko **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="40989-132">In the **Add New Project** dialog box, choose **Windows Forms Application**, and enter `LoanApp` as the name of the project, and then click **OK** to close the dialog box.</span></span>  
  
3. <span data-ttu-id="40989-133">V **Průzkumník řešení**vyberte projekt LoanApp.</span><span class="sxs-lookup"><span data-stu-id="40989-133">In **Solution Explorer**, choose the LoanApp project.</span></span>  
  
4. <span data-ttu-id="40989-134">V nabídce **projekt** vyberte možnost **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="40989-134">On the **Project** menu, choose **Set as StartUp Project**.</span></span>  
  
5. <span data-ttu-id="40989-135">V nabídce **projekt** klikněte na příkaz **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="40989-135">On the **Project** menu, choose **Add Reference**.</span></span>  
  
6. <span data-ttu-id="40989-136">V dialogovém okně **Přidat odkaz** zvolte kartu **projekty** a pak zvolte projekt LoanClass.</span><span class="sxs-lookup"><span data-stu-id="40989-136">In the **Add Reference** dialog box, choose the **Projects** tab and then choose the LoanClass project.</span></span>  
  
7. <span data-ttu-id="40989-137">Kliknutím na **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="40989-137">Click **OK** to close the dialog box.</span></span>  
  
8. <span data-ttu-id="40989-138">V Návrháři přidejte <xref:System.Windows.Forms.TextBox> do formuláře čtyři ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="40989-138">In the designer, add four <xref:System.Windows.Forms.TextBox> controls to the form.</span></span>  
  
9. <span data-ttu-id="40989-139">V Editoru kódu přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="40989-139">In the Code Editor, add the following code:</span></span>  
  
    ```vb  
    Private WithEvents TestLoan As New LoanClass.Loan(10000.0, 0.075, 36, "Neil Black")  
  
    Private Sub Form1_Load() Handles MyBase.Load  
        TextBox1.Text = TestLoan.LoanAmount.ToString  
        TextBox2.Text = TestLoan.InterestRate.ToString  
        TextBox3.Text = TestLoan.Term.ToString  
        TextBox4.Text = TestLoan.Customer  
    End Sub  
    ```  
  
10. <span data-ttu-id="40989-140">Přidejte obslužnou rutinu události pro `PropertyChanged` událost do formuláře pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="40989-140">Add an event handler for the `PropertyChanged` event to the form by using the following code:</span></span>  
  
    ```vb  
    Public Sub CustomerPropertyChanged(  
          ByVal sender As Object,  
          ByVal e As System.ComponentModel.PropertyChangedEventArgs  
        ) Handles TestLoan.PropertyChanged  
  
        MsgBox(e.PropertyName & " has been changed.")  
    End Sub  
    ```  
  
 <span data-ttu-id="40989-141">V tomto okamžiku můžete sestavit a spustit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="40989-141">At this point, you can build and run the application.</span></span> <span data-ttu-id="40989-142">Všimněte si, že výchozí hodnoty z `Loan` třídy se zobrazí v textových polích.</span><span class="sxs-lookup"><span data-stu-id="40989-142">Note that the default values from the `Loan` class appear in the text boxes.</span></span> <span data-ttu-id="40989-143">Zkuste změnit hodnotu úrokového tarifu z 7,5 na 7,1 a pak aplikaci zavřít a znovu spustit – hodnota se vrátí k výchozí hodnotě 7,5.</span><span class="sxs-lookup"><span data-stu-id="40989-143">Try to change the interest-rate value from 7.5 to 7.1, and then close the application and run it again—the value reverts to the default of 7.5.</span></span>  
  
 <span data-ttu-id="40989-144">V reálném světě se úrokové sazby pravidelně mění, ale nemusí nutně pokaždé, když je aplikace spuštěná.</span><span class="sxs-lookup"><span data-stu-id="40989-144">In the real world, interest rates change periodically, but not necessarily every time that the application is run.</span></span> <span data-ttu-id="40989-145">Místo toho, aby uživatel aktualizoval úrokovou sazbu při každém spuštění aplikace, je lepší zachovat nejnovější úrokovou sazbu mezi instancemi aplikace.</span><span class="sxs-lookup"><span data-stu-id="40989-145">Rather than making the user update the interest rate every time that the application runs, it is better to preserve the most recent interest rate between instances of the application.</span></span> <span data-ttu-id="40989-146">V dalším kroku provedete to tak, že do třídy výpůjčky přidáte serializaci.</span><span class="sxs-lookup"><span data-stu-id="40989-146">In the next step, you will do just that by adding serialization to the Loan class.</span></span>  
  
## <a name="using-serialization-to-persist-the-object"></a><span data-ttu-id="40989-147">Zachování objektu pomocí serializace</span><span class="sxs-lookup"><span data-stu-id="40989-147">Using Serialization to Persist the Object</span></span>  
 <span data-ttu-id="40989-148">Aby bylo možné zachovat hodnoty pro třídu výpůjčky, musíte nejprve označit třídu `Serializable` atributem.</span><span class="sxs-lookup"><span data-stu-id="40989-148">In order to persist the values for the Loan class, you must first mark the class with the `Serializable` attribute.</span></span>  
  
### <a name="to-mark-a-class-as-serializable"></a><span data-ttu-id="40989-149">Označení třídy jako serializovatelný</span><span class="sxs-lookup"><span data-stu-id="40989-149">To mark a class as serializable</span></span>  
  
- <span data-ttu-id="40989-150">Změňte deklaraci třídy pro třídu výpůjčky následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="40989-150">Change the class declaration for the Loan class as follows:</span></span>  
  
    ```vb  
    <Serializable()>  
    Public Class Loan  
    ```  
  
 <span data-ttu-id="40989-151">`Serializable`Atribut instruuje kompilátor, že všechno ve třídě lze trvale uložit do souboru.</span><span class="sxs-lookup"><span data-stu-id="40989-151">The `Serializable` attribute tells the compiler that everything in the class can be persisted to a file.</span></span> <span data-ttu-id="40989-152">Vzhledem k tomu, že `PropertyChanged` událost je zpracována objektem formuláře Windows, nemůže být serializována.</span><span class="sxs-lookup"><span data-stu-id="40989-152">Because the `PropertyChanged` event is handled by a Windows Form object, it cannot be serialized.</span></span> <span data-ttu-id="40989-153">`NonSerialized`Atribut lze použít k označení členů třídy, které by neměly být trvalé.</span><span class="sxs-lookup"><span data-stu-id="40989-153">The `NonSerialized` attribute can be used to mark class members that should not be persisted.</span></span>  
  
### <a name="to-prevent-a-member-from-being-serialized"></a><span data-ttu-id="40989-154">Zamezení serializaci člena</span><span class="sxs-lookup"><span data-stu-id="40989-154">To prevent a member from being serialized</span></span>  
  
- <span data-ttu-id="40989-155">Změňte deklaraci pro `PropertyChanged` událost následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="40989-155">Change the declaration for the `PropertyChanged` event as follows:</span></span>  
  
    ```vb  
    <NonSerialized()>  
    Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
      Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
    ```  
  
 <span data-ttu-id="40989-156">Dalším krokem je přidání kódu serializace do aplikace LoanApp.</span><span class="sxs-lookup"><span data-stu-id="40989-156">The next step is to add the serialization code to the LoanApp application.</span></span> <span data-ttu-id="40989-157">Aby bylo možné serializovat třídu a zapsat ji do souboru, budete používat <xref:System.IO> <xref:System.Xml.Serialization> obory názvů a.</span><span class="sxs-lookup"><span data-stu-id="40989-157">In order to serialize the class and write it to a file, you will use the <xref:System.IO> and <xref:System.Xml.Serialization> namespaces.</span></span> <span data-ttu-id="40989-158">Chcete-li se vyhnout psaní plně kvalifikovaných názvů, můžete přidat odkazy na potřebné knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="40989-158">To avoid typing the fully qualified names, you can add references to the necessary class libraries.</span></span>  
  
### <a name="to-add-references-to-namespaces"></a><span data-ttu-id="40989-159">Přidání odkazů na obory názvů</span><span class="sxs-lookup"><span data-stu-id="40989-159">To add references to namespaces</span></span>  
  
- <span data-ttu-id="40989-160">Do horní části třídy přidejte následující příkazy `Form1` :</span><span class="sxs-lookup"><span data-stu-id="40989-160">Add the following statements to the top of the `Form1` class:</span></span>  
  
    ```vb  
    Imports System.IO  
    Imports System.Runtime.Serialization.Formatters.Binary  
    ```  
  
     <span data-ttu-id="40989-161">V tomto případě používáte binární formátovací modul pro uložení objektu v binárním formátu.</span><span class="sxs-lookup"><span data-stu-id="40989-161">In this case, you are using a binary formatter to save the object in a binary format.</span></span>  
  
 <span data-ttu-id="40989-162">Dalším krokem je přidání kódu k deserializaci objektu ze souboru při vytvoření objektu.</span><span class="sxs-lookup"><span data-stu-id="40989-162">The next step is to add code to deserialize the object from the file when the object is created.</span></span>  
  
### <a name="to-deserialize-an-object"></a><span data-ttu-id="40989-163">K deserializaci objektu</span><span class="sxs-lookup"><span data-stu-id="40989-163">To deserialize an object</span></span>  
  
1. <span data-ttu-id="40989-164">Do třídy přidejte konstantu pro název souboru serializovaných dat.</span><span class="sxs-lookup"><span data-stu-id="40989-164">Add a constant to the class for the serialized data's file name.</span></span>  
  
    ```vb  
    Const FileName As String = "..\..\SavedLoan.bin"  
    ```  
  
2. <span data-ttu-id="40989-165">Upravte kód v `Form1_Load` proceduře události následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="40989-165">Modify the code in the `Form1_Load` event procedure as follows:</span></span>  
  
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
  
     <span data-ttu-id="40989-166">Všimněte si, že nejdřív musíte ověřit, že soubor existuje.</span><span class="sxs-lookup"><span data-stu-id="40989-166">Note that you first must check that the file exists.</span></span> <span data-ttu-id="40989-167">Pokud existuje, vytvořte <xref:System.IO.Stream> třídu pro čtení binárního souboru a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> třídu pro překlad souboru.</span><span class="sxs-lookup"><span data-stu-id="40989-167">If it exists, create a <xref:System.IO.Stream> class to read the binary file and a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> class to translate the file.</span></span> <span data-ttu-id="40989-168">Také je nutné převést typ datového proudu na typ objektu výpůjčky.</span><span class="sxs-lookup"><span data-stu-id="40989-168">You also need to convert from the stream type to the Loan object type.</span></span>  
  
 <span data-ttu-id="40989-169">Dále je nutné přidat kód pro uložení dat zadaných do textových polí do `Loan` třídy a poté je nutné třídu serializovat do souboru.</span><span class="sxs-lookup"><span data-stu-id="40989-169">Next you must add code to save the data entered in the text boxes to the `Loan` class, and then you must serialize the class to a file.</span></span>  
  
### <a name="to-save-the-data-and-serialize-the-class"></a><span data-ttu-id="40989-170">Uložení dat a serializace třídy</span><span class="sxs-lookup"><span data-stu-id="40989-170">To save the data and serialize the class</span></span>  
  
- <span data-ttu-id="40989-171">Do procedury události přidejte následující kód `Form1_FormClosing` :</span><span class="sxs-lookup"><span data-stu-id="40989-171">Add the following code to the `Form1_FormClosing` event procedure:</span></span>  
  
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
  
 <span data-ttu-id="40989-172">V tuto chvíli můžete znovu sestavit a spustit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="40989-172">At this point, you can again build and run the application.</span></span> <span data-ttu-id="40989-173">Zpočátku se výchozí hodnoty zobrazí v textových polích.</span><span class="sxs-lookup"><span data-stu-id="40989-173">Initially, the default values appear in the text boxes.</span></span> <span data-ttu-id="40989-174">Zkuste změnit hodnoty a do čtvrtého textového pole zadejte název.</span><span class="sxs-lookup"><span data-stu-id="40989-174">Try to change the values and enter a name in the fourth text box.</span></span> <span data-ttu-id="40989-175">Ukončete aplikaci a pak ji znovu spusťte.</span><span class="sxs-lookup"><span data-stu-id="40989-175">Close the application and then run it again.</span></span> <span data-ttu-id="40989-176">Všimněte si, že nové hodnoty se nyní zobrazí v textových polích.</span><span class="sxs-lookup"><span data-stu-id="40989-176">Note that the new values now appear in the text boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40989-177">Viz také</span><span class="sxs-lookup"><span data-stu-id="40989-177">See also</span></span>

- [<span data-ttu-id="40989-178">Serializace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40989-178">Serialization (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="40989-179">Příručka k programování v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="40989-179">Visual Basic Programming Guide</span></span>](../../index.md)
