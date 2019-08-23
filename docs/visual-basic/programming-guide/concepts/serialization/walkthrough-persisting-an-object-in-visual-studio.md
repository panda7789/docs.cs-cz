---
title: Zachování objektu v aplikaci Visual Studio (Visual Basic)
ms.date: 07/20/2015
ms.assetid: f1d0b562-e349-4dce-ab5f-c05108467030
ms.openlocfilehash: 6f25c2a6f06b56dcbb5ba7e63165d06ff77d9ca8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937366"
---
# <a name="walkthrough-persisting-an-object-in-visual-studio-visual-basic"></a>Návod: Zachování objektu v aplikaci Visual Studio (Visual Basic)
I když můžete nastavit vlastnosti objektu na výchozí hodnoty v době návrhu, budou při zničení objektu ztraceny všechny hodnoty zadané v době běhu. Můžete použít serializaci k uchování dat objektu mezi instancemi, což umožňuje ukládat hodnoty a načíst je při příštím vytvoření instance objektu.  
  
> [!NOTE]
> V Visual Basic pro ukládání jednoduchých dat, jako je název nebo číslo, můžete použít `My.Settings` objekt. Další informace najdete v tématu [objekt My. Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
 V tomto návodu vytvoříte jednoduchý `Loan` objekt a zachová jeho data do souboru. Po opětovném vytvoření objektu načtěte data ze souboru.  
  
> [!IMPORTANT]
> Tento příklad vytvoří nový soubor, pokud soubor ještě neexistuje. Pokud aplikace musí vytvořit soubor, musí `Create` mít tato aplikace oprávnění pro tuto složku. Oprávnění se nastavují pomocí seznamů řízení přístupu. Pokud soubor již existuje, aplikace potřebuje pouze `Write` oprávnění a menší oprávnění. Pokud je to možné, je bezpečnější vytvořit soubor během nasazení a udělit `Read` oprávnění pouze k jednomu souboru (místo oprávnění k vytvoření složky). Je také bezpečnější zapsat data do složek uživatele než do kořenové složky nebo do složky Program Files.  
  
> [!IMPORTANT]
> Tento příklad ukládá data v binárním souboru. Tyto formáty by se neměly používat pro citlivá data, jako jsou hesla nebo informace o kreditních kartách.  
  
> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, klikněte na položku **Nastavení importu a exportu** v nabídce **nástroje** . Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-loan-object"></a>Vytvoření objektu výpůjčky  
 Prvním krokem je vytvoření `Loan` třídy a testovací aplikace, která používá třídu.  
  
### <a name="to-create-the-loan-class"></a>Vytvoření třídy výpůjčky  
  
1. Vytvořte nový projekt knihovny tříd a pojmenujte ho "LoanClass". Další informace najdete v tématu [vytváření řešení a projektů](https://docs.microsoft.com/visualstudio/ide/creating-solutions-and-projects).  
  
2. V **Průzkumník řešení**otevřete místní nabídku pro soubor Class1 a vyberte možnost **Přejmenovat**. Přejmenujte soubor `Loan` na a stiskněte klávesu ENTER. Přejmenováním souboru dojde také k přejmenování třídy na `Loan`.  
  
3. Do třídy přidejte následující veřejné členy:  
  
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
  
 Také budete muset vytvořit jednoduchou aplikaci, která používá `Loan` třídu.  
  
### <a name="to-create-a-test-application"></a>Vytvoření testovací aplikace  
  
1. Chcete-li do řešení přidat projekt aplikace model Windows Forms, vyberte v nabídce **soubor** možnost **Přidat**,**Nový projekt**.  
  
2. V dialogovém okně **Přidat nový projekt** zvolte možnost **model Windows Forms aplikace**a zadejte `LoanApp` název projektu a potom kliknutím na tlačítko **OK** zavřete dialogové okno.  
  
3. V **Průzkumník řešení**vyberte projekt LoanApp.  
  
4. V nabídce **projekt** vyberte možnost **nastavit jako spouštěný projekt**.  
  
5. Na **projektu** nabídce zvolte **přidat odkaz**.  
  
6. V dialogovém okně **Přidat odkaz** zvolte kartu **projekty** a pak zvolte projekt LoanClass.  
  
7. Kliknutím na **OK** zavřete dialogové okno.  
  
8. V Návrháři přidejte do formuláře čtyři <xref:System.Windows.Forms.TextBox> ovládací prvky.  
  
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
  
10. Přidejte obslužnou rutinu události pro `PropertyChanged` událost do formuláře pomocí následujícího kódu:  
  
    ```vb  
    Public Sub CustomerPropertyChanged(  
          ByVal sender As Object,  
          ByVal e As System.ComponentModel.PropertyChangedEventArgs  
        ) Handles TestLoan.PropertyChanged  
  
        MsgBox(e.PropertyName & " has been changed.")  
    End Sub  
    ```  
  
 V tomto okamžiku můžete sestavit a spustit aplikaci. Všimněte si, že výchozí hodnoty z `Loan` třídy se zobrazí v textových polích. Zkuste změnit hodnotu úrokového tarifu z 7,5 na 7,1 a pak aplikaci zavřít a znovu spustit – hodnota se vrátí k výchozí hodnotě 7,5.  
  
 V reálném světě se úrokové sazby pravidelně mění, ale nemusí nutně pokaždé, když je aplikace spuštěná. Místo toho, aby uživatel aktualizoval úrokovou sazbu při každém spuštění aplikace, je lepší zachovat nejnovější úrokovou sazbu mezi instancemi aplikace. V dalším kroku provedete to tak, že do třídy výpůjčky přidáte serializaci.  
  
## <a name="using-serialization-to-persist-the-object"></a>Zachování objektu pomocí serializace  
 Aby bylo možné zachovat hodnoty pro třídu výpůjčky, musíte nejprve označit třídu `Serializable` atributem.  
  
### <a name="to-mark-a-class-as-serializable"></a>Označení třídy jako serializovatelný  
  
- Změňte deklaraci třídy pro třídu výpůjčky následujícím způsobem:  
  
    ```vb  
    <Serializable()>  
    Public Class Loan  
    ```  
  
 `Serializable` Atribut instruuje kompilátor, že všechno ve třídě lze trvale uložit do souboru. Vzhledem k tomu, že událostjezpracovánaobjektemformulářeWindows,nemůžebýtserializována.`PropertyChanged` `NonSerialized` Atribut lze použít k označení členů třídy, které by neměly být trvalé.  
  
### <a name="to-prevent-a-member-from-being-serialized"></a>Zamezení serializaci člena  
  
- Změňte deklaraci pro `PropertyChanged` událost následujícím způsobem:  
  
    ```vb  
    <NonSerialized()>  
    Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
      Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
    ```  
  
 Dalším krokem je přidání kódu serializace do aplikace LoanApp. Aby bylo možné serializovat třídu a zapsat ji do souboru, budete používat <xref:System.IO> obory názvů a. <xref:System.Xml.Serialization> Chcete-li se vyhnout psaní plně kvalifikovaných názvů, můžete přidat odkazy na potřebné knihovny tříd.  
  
### <a name="to-add-references-to-namespaces"></a>Přidání odkazů na obory názvů  
  
- Do horní části `Form1` třídy přidejte následující příkazy:  
  
    ```vb  
    Imports System.IO  
    Imports System.Runtime.Serialization.Formatters.Binary  
    ```  
  
     V tomto případě používáte binární formátovací modul pro uložení objektu v binárním formátu.  
  
 Dalším krokem je přidání kódu k deserializaci objektu ze souboru při vytvoření objektu.  
  
### <a name="to-deserialize-an-object"></a>K deserializaci objektu  
  
1. Do třídy přidejte konstantu pro název souboru serializovaných dat.  
  
    ```vb  
    Const FileName As String = "..\..\SavedLoan.bin"  
    ```  
  
2. Upravte kód v `Form1_Load` proceduře události následujícím způsobem:  
  
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
  
     Všimněte si, že nejdřív musíte ověřit, že soubor existuje. Pokud existuje, vytvořte <xref:System.IO.Stream> třídu pro čtení binárního souboru <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> a třídu pro překlad souboru. Také je nutné převést typ datového proudu na typ objektu výpůjčky.  
  
 Dále je nutné přidat kód pro uložení dat zadaných do textových polí do `Loan` třídy a poté je nutné třídu serializovat do souboru.  
  
### <a name="to-save-the-data-and-serialize-the-class"></a>Uložení dat a serializace třídy  
  
- Do `Form1_FormClosing` procedury události přidejte následující kód:  
  
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
  
 V tuto chvíli můžete znovu sestavit a spustit aplikaci. Zpočátku se výchozí hodnoty zobrazí v textových polích. Zkuste změnit hodnoty a do čtvrtého textového pole zadejte název. Ukončete aplikaci a pak ji znovu spusťte. Všimněte si, že nové hodnoty se nyní zobrazí v textových polích.  
  
## <a name="see-also"></a>Viz také:

- [Serializace (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
- [Průvodce programováním Visual Basic](../../../../visual-basic/programming-guide/index.md)
