---
title: Uchování objektů v sadě Visual Studio (Visual Basic)
ms.date: 07/20/2015
ms.assetid: f1d0b562-e349-4dce-ab5f-c05108467030
ms.openlocfilehash: 2523aefc90e22fe79f22e90d8da68c35c8dd24b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-persisting-an-object-in-visual-studio-visual-basic"></a>Návod: Uchování objektu v sadě Visual Studio (Visual Basic)
I když můžete nastavit vlastnosti objektu na výchozí hodnoty v době návrhu, všechny hodnoty zadané v době běhu jsou ztraceny, když objekt zničena. Serializace můžete použít k uchování dat objektu mezi instance, které umožňuje ukládat hodnoty a je načtou při příštím vytvoření instance objektu.  
  
> [!NOTE]
>  V jazyce Visual Basic pro ukládání dat jednoduché, jako je název nebo číslo, můžete použít `My.Settings` objektu. Další informace najdete v tématu [My.Settings – objekt](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
 V tomto návodu vytvoříte jednoduchou `Loan` objektu a zachovat data do souboru. Když znovu vytvoříte objekt se budou ze souboru načítat data.  
  
> [!IMPORTANT]
>  Tento příklad vytvoří nový soubor, pokud soubor již neexistuje. Pokud aplikace musí vytvořit soubor, aplikace musí `Create` oprávnění pro složku. Oprávnění jsou nastavená pomocí seznamů řízení přístupu. Pokud soubor již existuje, aplikace potřebuje pouze `Write` oprávnění, nižší úrovní oprávnění. Pokud je to možné, je bezpečnější k vytvoření tohoto souboru během nasazení a udělit pouze `Read` oprávnění do jednoho souboru (a nikoli vytvořit oprávnění pro složku). Navíc je bezpečnější zapsat data do složek uživatele než do kořenové složky nebo ve složce Program Files.  
  
> [!IMPORTANT]
>  V tomto příkladu jsou binární data. Tyto formáty by nemělo být použito pro citlivých dat, třeba hesla nebo informace o kreditní kartě.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, klikněte na tlačítko **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení prostředí Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-loan-object"></a>Vytvoření objektu úvěr  
 Prvním krokem je vytvoření `Loan` třídy a testovací aplikace, který používá třídu.  
  
### <a name="to-create-the-loan-class"></a>Pro vytvoření třídy úvěr  
  
1.  Vytvoření nového projektu knihovny tříd a pojmenujte ji "LoanClass". Další informace najdete v tématu [vytváření řešení a projekty](http://docs.microsoft.com/visualstudio/ide/creating-solutions-and-projects).  
  
2.  V **Průzkumníku řešení**, otevřete místní nabídku pro soubor Class1 a zvolte **přejmenovat**. Přejmenujte soubor `Loan` a stiskněte klávesu ENTER. Přejmenování souboru také přejmenuje třídy pro `Loan`.  
  
3.  Přidejte následující veřejné členy do třídy:  
  
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
  
 Budete také muset vytvořit jednoduchou aplikaci, která používá `Loan` třídy.  
  
### <a name="to-create-a-test-application"></a>Chcete-li vytvořit testovací aplikace  
  
1.  Přidat projekt aplikace Windows Forms do vašeho řešení na **soubor** nabídce zvolte **přidat**,**nový projekt**.  
  
2.  V **přidat nový projekt** dialogovém okně vyberte **formulářové aplikace Windows**a zadejte `LoanApp` jako název projektu a klikněte na tlačítko **OK** zavřete dialogové okno .  
  
3.  V **Průzkumníku**, zvolte LoanApp projektu.  
  
4.  Na **projektu** nabídce zvolte **nastavit jako spouštěný projekt**.  
  
5.  Na **projektu** nabídky, zvolte **přidat odkaz na**.  
  
6.  V **přidat odkaz na** dialogovém okně vyberte **projekty** kartě a pak zvolte projekt LoanClass.  
  
7.  Klikněte na tlačítko **OK** zavřete dialogové okno.  
  
8.  V Návrháři přidat čtyři <xref:System.Windows.Forms.TextBox> ovládacích prvků formuláře.  
  
9. V Editoru kódu přidejte následující kód:  
  
    ```vb  
    Private WithEvents TestLoan As New LoanClass.Loan(10000.0, 0.075, 36, "Neil Black")  
  
    Private Sub Form1_Load() Handles MyBase.Load  
        TextBox1.Text = TestLoan.LoanAmount.ToString  
        TextBox2.Text = TestLoan.InterestRate.ToString  
        TextBox3.Text = TestLoan.Term.ToString  
        TextBox4.Text = TestLoan.Customer  
    End Sub  
    ```  
  
10. Přidání obslužné rutiny události pro `PropertyChanged` událostí do formuláře pomocí následujícího kódu:  
  
    ```vb  
    Public Sub CustomerPropertyChanged(  
          ByVal sender As Object,  
          ByVal e As System.ComponentModel.PropertyChangedEventArgs  
        ) Handles TestLoan.PropertyChanged  
  
        MsgBox(e.PropertyName & " has been changed.")  
    End Sub  
    ```  
  
 V tomto okamžiku můžete sestavit a spustit aplikaci. Všimněte si, že výchozí hodnoty z `Loan` třída zobrazí v textových polích. Zkuste změňte hodnotu úrokové z 7.5 na 7.1 a pak ukončete aplikaci a potom ho spusťte znovu – hodnota obnoví na výchozí 7.5.  
  
 V praxi úrokové sazby změnit pravidelně, ale nemusí nutně prokázat pokaždé, když je aplikace spuštěna. Místo provedení uživatel aktualizovat úrokovou sazbu pokaždé, když je aplikace spuštěná, je lepší zachovat nejnovější úrokové sazby mezi instancemi aplikace. V dalším kroku můžete se přesně k tomu přidáním serializace k třídě úvěr.  
  
## <a name="using-serialization-to-persist-the-object"></a>Pomocí serializace k uchování objektu  
 Chcete-li zachovat hodnoty pro třídy úvěr, je nejprve třeba označit třídu pomocí `Serializable` atribut.  
  
### <a name="to-mark-a-class-as-serializable"></a>Označit jako serializovatelné třídy  
  
-   Změna deklaraci třídy pro třídu úvěr následujícím způsobem:  
  
    ```vb  
    <Serializable()>  
    Public Class Loan  
    ```  
  
 `Serializable` Atribut říká kompilátoru, že všechno ve třídě, můžete nastavit jako trvalý, do souboru. Protože `PropertyChanged` událost je zpracovávána objektem formuláře Windows, nelze jej serializovat. `NonSerialized` Atribut slouží k označení členy třídy, které by neměly být trvalé.  
  
### <a name="to-prevent-a-member-from-being-serialized"></a>Abyste zabránili serializována člena  
  
-   Změňte deklaraci pro `PropertyChanged` událostí následujícím způsobem:  
  
    ```vb  
    <NonSerialized()>  
    Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
      Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
    ```  
  
 Dalším krokem je přidejte do aplikace LoanApp kód serializace. Abyste mohli serializaci třídy a zapisovat do souboru, bude používat <xref:System.IO> a <xref:System.Xml.Serialization> obory názvů. Abyste se vyhnuli, zadejte plně kvalifikované názvy, můžete přidat odkazy na knihovny potřebné tříd.  
  
### <a name="to-add-references-to-namespaces"></a>Chcete-li přidat odkazy na obory názvů  
  
-   Přidejte následující příkazy do horní části `Form1` třídy:  
  
    ```vb  
    Imports System.IO  
    Imports System.Runtime.Serialization.Formatters.Binary  
    ```  
  
     V tomto případě používáte binární formátovací modul k uložení objektu v binárním formátu.  
  
 Dalším krokem je přidání kódu k deserializaci objektu ze souboru při vytvoření objektu.  
  
### <a name="to-deserialize-an-object"></a>K deserializaci objektu  
  
1.  Přidejte do třídy pro název souboru serializovaná data konstanta.  
  
    ```vb  
    Const FileName As String = "..\..\SavedLoan.bin"  
    ```  
  
2.  Změňte kód v `Form1_Load` události postupu následujícím způsobem:  
  
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
  
     Všimněte si, že je nejprve nutné zkontrolovat, zda soubor existuje. Pokud existuje, vytvoření <xref:System.IO.Stream> třídy číst binární soubor a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> třída přeložit soubor. Také musíte převést na typ objektu úvěr typ datového proudu.  
  
 Dále je nutné přidat kód uložit data zadaná v textových polích k `Loan` třída a pak musí serializovat třídu do souboru.  
  
### <a name="to-save-the-data-and-serialize-the-class"></a>Chcete uložit data a serializaci třídy  
  
-   Přidejte následující kód, který `Form1_FormClosing` procedury události:  
  
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
  
 V tomto okamžiku můžete znovu sestavit a spustit aplikaci. Do textových polí v počátečním stavu, zobrazí výchozí hodnoty. Zkuste změnit hodnoty a zadejte název do textového pole čtvrtý. Zavřete aplikaci a znovu jej spusťte. Všimněte si, že nové hodnoty se nyní zobrazí v textových polích.  
  
## <a name="see-also"></a>Viz také  
 [Serializace (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)  
 [Průvodce programováním v jazyce Visual Basic](../../../../visual-basic/programming-guide/index.md)
