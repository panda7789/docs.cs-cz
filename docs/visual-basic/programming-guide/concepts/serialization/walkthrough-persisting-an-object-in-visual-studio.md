---
title: Uchování objektu v sadě Visual Studio (Visual Basic)
ms.date: 07/20/2015
ms.assetid: f1d0b562-e349-4dce-ab5f-c05108467030
ms.openlocfilehash: 55ad2049003baaed26f4db909ae466aefdd161e1
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59303346"
---
# <a name="walkthrough-persisting-an-object-in-visual-studio-visual-basic"></a>Návod: Uchování objektu v sadě Visual Studio (Visual Basic)
V době návrhu, je možné nastavit na výchozí hodnoty vlastností objektu, všechny hodnoty zadané v době běhu budou ztraceny, pokud objekt je zničen. Serializace můžete použít k uchování dat objektu mezi instancemi, které vám umožní uložení hodnot a načíst je další čas, který je vytvořena instance objektu.  
  
> [!NOTE]
>  V jazyce Visual Basic, uložte jednoduchá dat, jako je název nebo číslo, můžete `My.Settings` objektu. Další informace najdete v tématu [My.Settings – objekt](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
 V tomto návodu vytvoříte jednoduchou `Loan` objektu a zachovat data do souboru. Když znovu vytvoříte objekt se budou ze souboru načítat data.  
  
> [!IMPORTANT]
>  Tento příklad vytvoří nový soubor, pokud soubor již neexistuje. Pokud aplikace musí vytvořit soubor, musí tuto aplikaci `Create` oprávnění pro složku. Oprávnění jsou nastavená pomocí seznamů řízení přístupu. Pokud soubor již existuje, aplikace potřebuje pouze `Write` oprávnění, nižší oprávnění. Kde je to možné, je bezpečnější vytvořit soubor při nasazení a udělit pouze `Read` oprávnění do jednoho souboru (místo vytvořit oprávnění pro složku). Navíc je bezpečnější zapsat data do uživatelské složky než do kořenové složky nebo ve složce Program Files.  
  
> [!IMPORTANT]
>  V tomto příkladu ukládá data do binární hodnoty. Tyto formáty by neměla používat pro citlivá data, jako jsou hesla nebo informace o platební kartě.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, klikněte na tlačítko **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-loan-object"></a>Vytvoření objektu půjčky  
 Prvním krokem je vytvoření `Loan` třídy a testovací aplikaci, která používá třídu.  
  
### <a name="to-create-the-loan-class"></a>Chcete-li vytvořit třídu půjčky  
  
1. Vytvořte nový projekt knihovny tříd s názvem "LoanClass". Další informace najdete v tématu [vytváření řešení a projekty](https://docs.microsoft.com/visualstudio/ide/creating-solutions-and-projects).  
  
2. V **Průzkumníka řešení**, otevřete místní nabídku pro soubor Class1 a zvolte **přejmenovat**. Přejmenujte soubor na `Loan` a stiskněte klávesu ENTER. Přejmenování souboru se také přejmenujte třídu na `Loan`.  
  
3. Přidejte následující veřejné členy do třídy:  
  
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
  
1. Chcete-li přidat projekt aplikace Windows Forms do vašeho řešení na **souboru** nabídce zvolte **přidat**,**nový projekt**.  
  
2. V **přidat nový projekt** dialogového okna zvolte **formulářová aplikace Windows**a zadejte `LoanApp` jako název projektu a pak klikněte na tlačítko **OK** zavřete dialogové okno .  
  
3. V **Průzkumníka řešení**, vyberte projekt LoanApp.  
  
4. Na **projektu** nabídce zvolte **nastavit jako spouštěný projekt**.  
  
5. Na **projektu** nabídce zvolte **přidat odkaz**.  
  
6. V **přidat odkaz** dialogového okna zvolte **projekty** kartu a pak zvolte projekt LoanClass.  
  
7. Kliknutím na **OK** zavřete dialogové okno.  
  
8. V návrháři, přidejte čtyři <xref:System.Windows.Forms.TextBox> ovládací prvky do formuláře.  
  
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
  
10. Přidat obslužnou rutinu události pro `PropertyChanged` událostí do formuláře pomocí následujícího kódu:  
  
    ```vb  
    Public Sub CustomerPropertyChanged(  
          ByVal sender As Object,  
          ByVal e As System.ComponentModel.PropertyChangedEventArgs  
        ) Handles TestLoan.PropertyChanged  
  
        MsgBox(e.PropertyName & " has been changed.")  
    End Sub  
    ```  
  
 V tomto okamžiku můžete sestavte a spusťte aplikaci. Všimněte si, že výchozí hodnoty z `Loan` třídy se zobrazí v textových polích. Zkuste změnit hodnotu úrokové sazby 7.5 na 7.1 a potom ukončete aplikaci a spustíte jej znovu – hodnota nastaví na výchozí hodnotu 7.5.  
  
 V praxi úrokové sazby změnit pravidelně, ale ne nutně pokaždé, když je aplikace spuštěna. Místo toho uživatel aktualizovat úrokové sazby pokaždé, když je aplikace spuštěná, je lepší zachovat nejnovější úrokové sazby mezi instancemi aplikace. V dalším kroku se přesně to provést přidáním serializace do třídy půjčky.  
  
## <a name="using-serialization-to-persist-the-object"></a>Pomocí serializace k uchování objektu  
 Aby bylo možné zachovat hodnoty pro třídu půjček, musíte nejprve označte třídu `Serializable` atribut.  
  
### <a name="to-mark-a-class-as-serializable"></a>Chcete-li označit třídu jako serializovatelný  
  
-   Změňte deklaraci třídy pro třídu půjčky následujícím způsobem:  
  
    ```vb  
    <Serializable()>  
    Public Class Loan  
    ```  
  
 `Serializable` Atribut oznamuje kompilátoru, že všechno, co ve třídě, můžete nastavit jako trvalý, do souboru. Vzhledem k tomu, `PropertyChanged` událost zpracovává objektem formuláře Windows, nejde ho serializovat. `NonSerialized` Atribut lze použít k označení členy třídy, které by neměly být trvalé.  
  
### <a name="to-prevent-a-member-from-being-serialized"></a>Chcete-li zabránit serializována člena  
  
-   Změna deklarace `PropertyChanged` událostí následujícím způsobem:  
  
    ```vb  
    <NonSerialized()>  
    Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
      Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
    ```  
  
 Dalším krokem je přidání Serializační kód do aplikace LoanApp. K serializaci třídy a zápis do souboru, kterou použijete <xref:System.IO> a <xref:System.Xml.Serialization> obory názvů. Abyste nemuseli zadávat plně kvalifikované názvy, můžete přidat odkazy na knihovny tříd nezbytné.  
  
### <a name="to-add-references-to-namespaces"></a>Chcete-li přidat odkazy na obory názvů  
  
-   Přidejte následující příkazy k hornímu okraji `Form1` třídy:  
  
    ```vb  
    Imports System.IO  
    Imports System.Runtime.Serialization.Formatters.Binary  
    ```  
  
     V tomto případě používáte binární formátovací modul k uložení objektu v binárním formátu.  
  
 Dalším krokem je přidání kódu k deserializaci objektu ze souboru při vytvoření objektu.  
  
### <a name="to-deserialize-an-object"></a>K deserializaci objektu  
  
1. Přidejte konstanty do třídy pro název souboru serializovaná data.  
  
    ```vb  
    Const FileName As String = "..\..\SavedLoan.bin"  
    ```  
  
2. Změňte kód v `Form1_Load` procedury události následujícím způsobem:  
  
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
  
     Všimněte si, že nejprve musíte zkontrolovat, zda soubor existuje. Pokud existuje, vytvořit <xref:System.IO.Stream> třídy ke čtení binárního souboru a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> třídy pro převod souboru. Také je potřeba převést z typu datový proud na typ objektu půjčky.  
  
 Dále je nutné přidat kód pro uložení údaje zadávané do textových polí `Loan` třídy a pak musí serializovat třídu do souboru.  
  
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
  
 V tomto okamžiku můžete znovu sestavte a spusťte aplikaci. Na začátku zobrazí výchozí hodnoty v textových polích. Pokuste se změnit hodnoty a zadejte název do textového pole čtvrtý. Ukončete aplikaci a znovu jej spusťte. Všimněte si, že nové hodnoty teď budou zobrazovat v textových polích.  
  
## <a name="see-also"></a>Viz také:

- [Serializace (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
- [Příručka k programování v jazyce Visual Basic](../../../../visual-basic/programming-guide/index.md)
