---
title: "Uchování objektů v sadě Visual Studio (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: f1d0b562-e349-4dce-ab5f-c05108467030
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 838038fd873c3a841fd83d30df1c7b3e27fe697f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-persisting-an-object-in-visual-studio-visual-basic"></a><span data-ttu-id="e2ac9-102">Návod: Uchování objektu v sadě Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2ac9-102">Walkthrough: Persisting an Object in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="e2ac9-103">I když můžete nastavit vlastnosti objektu na výchozí hodnoty v době návrhu, všechny hodnoty zadané v době běhu jsou ztraceny, když objekt zničena.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-103">Although you can set an object's properties to default values at design time, any values entered at run time are lost when the object is destroyed.</span></span> <span data-ttu-id="e2ac9-104">Serializace můžete použít k uchování dat objektu mezi instance, které umožňuje ukládat hodnoty a je načtou při příštím vytvoření instance objektu.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-104">You can use serialization to persist an object's data between instances, which enables you to store values and retrieve them the next time that the object is instantiated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e2ac9-105">V jazyce Visual Basic pro ukládání dat jednoduché, jako je název nebo číslo, můžete použít `My.Settings` objektu.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-105">In Visual Basic, to store simple data, such as a name or number, you can use the `My.Settings` object.</span></span> <span data-ttu-id="e2ac9-106">Další informace najdete v tématu [My.Settings – objekt](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="e2ac9-106">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
 <span data-ttu-id="e2ac9-107">V tomto návodu vytvoříte jednoduchou `Loan` objektu a zachovat data do souboru.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-107">In this walkthrough, you will create a simple `Loan` object and persist its data to a file.</span></span> <span data-ttu-id="e2ac9-108">Když znovu vytvoříte objekt se budou ze souboru načítat data.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-108">You will then retrieve the data from the file when you re-create the object.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e2ac9-109">Tento příklad vytvoří nový soubor, pokud soubor již neexistuje.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-109">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="e2ac9-110">Pokud aplikace musí vytvořit soubor, aplikace musí `Create` oprávnění pro složku.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-110">If an application must create a file, that application must `Create` permission for the folder.</span></span> <span data-ttu-id="e2ac9-111">Oprávnění jsou nastavená pomocí seznamů řízení přístupu.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-111">Permissions are set by using access control lists.</span></span> <span data-ttu-id="e2ac9-112">Pokud soubor již existuje, aplikace potřebuje pouze `Write` oprávnění, nižší úrovní oprávnění.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-112">If the file already exists, the application needs only `Write` permission, a lesser permission.</span></span> <span data-ttu-id="e2ac9-113">Pokud je to možné, je bezpečnější k vytvoření tohoto souboru během nasazení a udělit pouze `Read` oprávnění do jednoho souboru (a nikoli vytvořit oprávnění pro složku).</span><span class="sxs-lookup"><span data-stu-id="e2ac9-113">Where possible, it is more secure to create the file during deployment, and only grant `Read` permissions to a single file (instead of Create permissions for a folder).</span></span> <span data-ttu-id="e2ac9-114">Navíc je bezpečnější zapsat data do složek uživatele než do kořenové složky nebo ve složce Program Files.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-114">Also, it is more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e2ac9-115">V tomto příkladu jsou binární data.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-115">This example stores data in a binary.</span></span> <span data-ttu-id="e2ac9-116">Tyto formáty by nemělo být použito pro citlivých dat, třeba hesla nebo informace o kreditní kartě.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-116">These formats should not be used for sensitive data, such as passwords or credit-card information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e2ac9-117">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-117">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="e2ac9-118">Chcete-li změnit nastavení, klikněte na tlačítko **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-118">To change your settings, click **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="e2ac9-119">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="e2ac9-119">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-loan-object"></a><span data-ttu-id="e2ac9-120">Vytvoření objektu úvěr</span><span class="sxs-lookup"><span data-stu-id="e2ac9-120">Creating the Loan Object</span></span>  
 <span data-ttu-id="e2ac9-121">Prvním krokem je vytvoření `Loan` třídy a testovací aplikace, který používá třídu.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-121">The first step is to create a `Loan` class and a test application that uses the class.</span></span>  
  
### <a name="to-create-the-loan-class"></a><span data-ttu-id="e2ac9-122">Pro vytvoření třídy úvěr</span><span class="sxs-lookup"><span data-stu-id="e2ac9-122">To create the Loan class</span></span>  
  
1.  <span data-ttu-id="e2ac9-123">Vytvoření nového projektu knihovny tříd a pojmenujte ji "LoanClass".</span><span class="sxs-lookup"><span data-stu-id="e2ac9-123">Create a new Class Library project and name it "LoanClass".</span></span> <span data-ttu-id="e2ac9-124">Další informace najdete v tématu [vytváření řešení a projekty](http://docs.microsoft.com/visualstudio/ide/creating-solutions-and-projects).</span><span class="sxs-lookup"><span data-stu-id="e2ac9-124">For more information, see [Creating Solutions and Projects](http://docs.microsoft.com/visualstudio/ide/creating-solutions-and-projects).</span></span>  
  
2.  <span data-ttu-id="e2ac9-125">V **Průzkumníku řešení**, otevřete místní nabídku pro soubor Class1 a zvolte **přejmenovat**.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-125">In **Solution Explorer**, open the shortcut menu for the Class1 file and choose **Rename**.</span></span> <span data-ttu-id="e2ac9-126">Přejmenujte soubor `Loan` a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-126">Rename the file to `Loan` and press ENTER.</span></span> <span data-ttu-id="e2ac9-127">Přejmenování souboru také přejmenuje třídy pro `Loan`.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-127">Renaming the file will also rename the class to `Loan`.</span></span>  
  
3.  <span data-ttu-id="e2ac9-128">Přidejte následující veřejné členy do třídy:</span><span class="sxs-lookup"><span data-stu-id="e2ac9-128">Add the following public members to the class:</span></span>  
  
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
  
 <span data-ttu-id="e2ac9-129">Budete také muset vytvořit jednoduchou aplikaci, která používá `Loan` třídy.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-129">You will also have to create a simple application that uses the `Loan` class.</span></span>  
  
### <a name="to-create-a-test-application"></a><span data-ttu-id="e2ac9-130">Chcete-li vytvořit testovací aplikace</span><span class="sxs-lookup"><span data-stu-id="e2ac9-130">To create a test application</span></span>  
  
1.  <span data-ttu-id="e2ac9-131">Přidat projekt aplikace Windows Forms do vašeho řešení na **soubor** nabídce zvolte **přidat**,**nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-131">To add a Windows Forms Application project to your solution, on the **File** menu, choose **Add**,**New Project**.</span></span>  
  
2.  <span data-ttu-id="e2ac9-132">V **přidat nový projekt** dialogovém okně vyberte **formulářové aplikace Windows**a zadejte `LoanApp` jako název projektu a klikněte na tlačítko **OK** zavřete dialogové okno .</span><span class="sxs-lookup"><span data-stu-id="e2ac9-132">In the **Add New Project** dialog box, choose **Windows Forms Application**, and enter `LoanApp` as the name of the project, and then click **OK** to close the dialog box.</span></span>  
  
3.  <span data-ttu-id="e2ac9-133">V **Průzkumníku**, zvolte LoanApp projektu.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-133">In **Solution Explorer**, choose the LoanApp project.</span></span>  
  
4.  <span data-ttu-id="e2ac9-134">Na **projektu** nabídce zvolte **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-134">On the **Project** menu, choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="e2ac9-135">Na **projektu** nabídky, zvolte **přidat odkaz na**.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-135">On the **Project** menu, choose **Add Reference**.</span></span>  
  
6.  <span data-ttu-id="e2ac9-136">V **přidat odkaz na** dialogovém okně vyberte **projekty** kartě a pak zvolte projekt LoanClass.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-136">In the **Add Reference** dialog box, choose the **Projects** tab and then choose the LoanClass project.</span></span>  
  
7.  <span data-ttu-id="e2ac9-137">Klikněte na tlačítko **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-137">Click **OK** to close the dialog box.</span></span>  
  
8.  <span data-ttu-id="e2ac9-138">V Návrháři přidat čtyři <xref:System.Windows.Forms.TextBox> ovládacích prvků formuláře.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-138">In the designer, add four <xref:System.Windows.Forms.TextBox> controls to the form.</span></span>  
  
9. <span data-ttu-id="e2ac9-139">V Editoru kódu přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="e2ac9-139">In the Code Editor, add the following code:</span></span>  
  
    ```vb  
    Private WithEvents TestLoan As New LoanClass.Loan(10000.0, 0.075, 36, "Neil Black")  
  
    Private Sub Form1_Load() Handles MyBase.Load  
        TextBox1.Text = TestLoan.LoanAmount.ToString  
        TextBox2.Text = TestLoan.InterestRate.ToString  
        TextBox3.Text = TestLoan.Term.ToString  
        TextBox4.Text = TestLoan.Customer  
    End Sub  
    ```  
  
10. <span data-ttu-id="e2ac9-140">Přidání obslužné rutiny události pro `PropertyChanged` událostí do formuláře pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="e2ac9-140">Add an event handler for the `PropertyChanged` event to the form by using the following code:</span></span>  
  
    ```vb  
    Public Sub CustomerPropertyChanged(  
          ByVal sender As Object,  
          ByVal e As System.ComponentModel.PropertyChangedEventArgs  
        ) Handles TestLoan.PropertyChanged  
  
        MsgBox(e.PropertyName & " has been changed.")  
    End Sub  
    ```  
  
 <span data-ttu-id="e2ac9-141">V tomto okamžiku můžete sestavit a spustit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-141">At this point, you can build and run the application.</span></span> <span data-ttu-id="e2ac9-142">Všimněte si, že výchozí hodnoty z `Loan` třída zobrazí v textových polích.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-142">Note that the default values from the `Loan` class appear in the text boxes.</span></span> <span data-ttu-id="e2ac9-143">Zkuste změňte hodnotu úrokové z 7.5 na 7.1 a pak ukončete aplikaci a potom ho spusťte znovu – hodnota obnoví na výchozí 7.5.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-143">Try to change the interest-rate value from 7.5 to 7.1, and then close the application and run it again—the value reverts to the default of 7.5.</span></span>  
  
 <span data-ttu-id="e2ac9-144">V praxi úrokové sazby změnit pravidelně, ale nemusí nutně prokázat pokaždé, když je aplikace spuštěna.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-144">In the real world, interest rates change periodically, but not necessarily every time that the application is run.</span></span> <span data-ttu-id="e2ac9-145">Místo provedení uživatel aktualizovat úrokovou sazbu pokaždé, když je aplikace spuštěná, je lepší zachovat nejnovější úrokové sazby mezi instancemi aplikace.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-145">Rather than making the user update the interest rate every time that the application runs, it is better to preserve the most recent interest rate between instances of the application.</span></span> <span data-ttu-id="e2ac9-146">V dalším kroku můžete se přesně k tomu přidáním serializace k třídě úvěr.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-146">In the next step, you will do just that by adding serialization to the Loan class.</span></span>  
  
## <a name="using-serialization-to-persist-the-object"></a><span data-ttu-id="e2ac9-147">Pomocí serializace k uchování objektu</span><span class="sxs-lookup"><span data-stu-id="e2ac9-147">Using Serialization to Persist the Object</span></span>  
 <span data-ttu-id="e2ac9-148">Chcete-li zachovat hodnoty pro třídy úvěr, je nejprve třeba označit třídu pomocí `Serializable` atribut.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-148">In order to persist the values for the Loan class, you must first mark the class with the `Serializable` attribute.</span></span>  
  
### <a name="to-mark-a-class-as-serializable"></a><span data-ttu-id="e2ac9-149">Označit jako serializovatelné třídy</span><span class="sxs-lookup"><span data-stu-id="e2ac9-149">To mark a class as serializable</span></span>  
  
-   <span data-ttu-id="e2ac9-150">Změna deklaraci třídy pro třídu úvěr následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="e2ac9-150">Change the class declaration for the Loan class as follows:</span></span>  
  
    ```vb  
    <Serializable()>  
    Public Class Loan  
    ```  
  
 <span data-ttu-id="e2ac9-151">`Serializable` Atribut říká kompilátoru, že všechno ve třídě, můžete nastavit jako trvalý, do souboru.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-151">The `Serializable` attribute tells the compiler that everything in the class can be persisted to a file.</span></span> <span data-ttu-id="e2ac9-152">Protože `PropertyChanged` událost je zpracovávána objektem formuláře Windows, nelze jej serializovat.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-152">Because the `PropertyChanged` event is handled by a Windows Form object, it cannot be serialized.</span></span> <span data-ttu-id="e2ac9-153">`NonSerialized` Atribut slouží k označení členy třídy, které by neměly být trvalé.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-153">The `NonSerialized` attribute can be used to mark class members that should not be persisted.</span></span>  
  
### <a name="to-prevent-a-member-from-being-serialized"></a><span data-ttu-id="e2ac9-154">Abyste zabránili serializována člena</span><span class="sxs-lookup"><span data-stu-id="e2ac9-154">To prevent a member from being serialized</span></span>  
  
-   <span data-ttu-id="e2ac9-155">Změňte deklaraci pro `PropertyChanged` událostí následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="e2ac9-155">Change the declaration for the `PropertyChanged` event as follows:</span></span>  
  
    ```vb  
    <NonSerialized()>  
    Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
      Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
    ```  
  
 <span data-ttu-id="e2ac9-156">Dalším krokem je přidejte do aplikace LoanApp kód serializace.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-156">The next step is to add the serialization code to the LoanApp application.</span></span> <span data-ttu-id="e2ac9-157">Abyste mohli serializaci třídy a zapisovat do souboru, bude používat <xref:System.IO> a <xref:System.Xml.Serialization> obory názvů.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-157">In order to serialize the class and write it to a file, you will use the <xref:System.IO> and <xref:System.Xml.Serialization> namespaces.</span></span> <span data-ttu-id="e2ac9-158">Abyste se vyhnuli, zadejte plně kvalifikované názvy, můžete přidat odkazy na knihovny potřebné tříd.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-158">To avoid typing the fully qualified names, you can add references to the necessary class libraries.</span></span>  
  
### <a name="to-add-references-to-namespaces"></a><span data-ttu-id="e2ac9-159">Chcete-li přidat odkazy na obory názvů</span><span class="sxs-lookup"><span data-stu-id="e2ac9-159">To add references to namespaces</span></span>  
  
-   <span data-ttu-id="e2ac9-160">Přidejte následující příkazy do horní části `Form1` třídy:</span><span class="sxs-lookup"><span data-stu-id="e2ac9-160">Add the following statements to the top of the `Form1` class:</span></span>  
  
    ```vb  
    Imports System.IO  
    Imports System.Runtime.Serialization.Formatters.Binary  
    ```  
  
     <span data-ttu-id="e2ac9-161">V tomto případě používáte binární formátovací modul k uložení objektu v binárním formátu.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-161">In this case, you are using a binary formatter to save the object in a binary format.</span></span>  
  
 <span data-ttu-id="e2ac9-162">Dalším krokem je přidání kódu k deserializaci objektu ze souboru při vytvoření objektu.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-162">The next step is to add code to deserialize the object from the file when the object is created.</span></span>  
  
### <a name="to-deserialize-an-object"></a><span data-ttu-id="e2ac9-163">K deserializaci objektu</span><span class="sxs-lookup"><span data-stu-id="e2ac9-163">To deserialize an object</span></span>  
  
1.  <span data-ttu-id="e2ac9-164">Přidejte do třídy pro název souboru serializovaná data konstanta.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-164">Add a constant to the class for the serialized data's file name.</span></span>  
  
    ```vb  
    Const FileName As String = "..\..\SavedLoan.bin"  
    ```  
  
2.  <span data-ttu-id="e2ac9-165">Změňte kód v `Form1_Load` události postupu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="e2ac9-165">Modify the code in the `Form1_Load` event procedure as follows:</span></span>  
  
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
  
     <span data-ttu-id="e2ac9-166">Všimněte si, že je nejprve nutné zkontrolovat, zda soubor existuje.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-166">Note that you first must check that the file exists.</span></span> <span data-ttu-id="e2ac9-167">Pokud existuje, vytvoření <xref:System.IO.Stream> třídy číst binární soubor a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> třída přeložit soubor.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-167">If it exists, create a <xref:System.IO.Stream> class to read the binary file and a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> class to translate the file.</span></span> <span data-ttu-id="e2ac9-168">Také musíte převést na typ objektu úvěr typ datového proudu.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-168">You also need to convert from the stream type to the Loan object type.</span></span>  
  
 <span data-ttu-id="e2ac9-169">Dále je nutné přidat kód uložit data zadaná v textových polích k `Loan` třída a pak musí serializovat třídu do souboru.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-169">Next you must add code to save the data entered in the text boxes to the `Loan` class, and then you must serialize the class to a file.</span></span>  
  
### <a name="to-save-the-data-and-serialize-the-class"></a><span data-ttu-id="e2ac9-170">Chcete uložit data a serializaci třídy</span><span class="sxs-lookup"><span data-stu-id="e2ac9-170">To save the data and serialize the class</span></span>  
  
-   <span data-ttu-id="e2ac9-171">Přidejte následující kód, který `Form1_FormClosing` procedury události:</span><span class="sxs-lookup"><span data-stu-id="e2ac9-171">Add the following code to the `Form1_FormClosing` event procedure:</span></span>  
  
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
  
 <span data-ttu-id="e2ac9-172">V tomto okamžiku můžete znovu sestavit a spustit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-172">At this point, you can again build and run the application.</span></span> <span data-ttu-id="e2ac9-173">Do textových polí v počátečním stavu, zobrazí výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-173">Initially, the default values appear in the text boxes.</span></span> <span data-ttu-id="e2ac9-174">Zkuste změnit hodnoty a zadejte název do textového pole čtvrtý.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-174">Try to change the values and enter a name in the fourth text box.</span></span> <span data-ttu-id="e2ac9-175">Zavřete aplikaci a znovu jej spusťte.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-175">Close the application and then run it again.</span></span> <span data-ttu-id="e2ac9-176">Všimněte si, že nové hodnoty se nyní zobrazí v textových polích.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-176">Note that the new values now appear in the text boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2ac9-177">Viz také</span><span class="sxs-lookup"><span data-stu-id="e2ac9-177">See Also</span></span>  
 [<span data-ttu-id="e2ac9-178">Serializace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2ac9-178">Serialization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/index.md)  
 [<span data-ttu-id="e2ac9-179">Průvodce programováním v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e2ac9-179">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
