---
title: "Návod: Uchování objektu v sadě Visual Studio (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: get-started-article
ms.assetid: a544ce46-ee25-49da-afd4-457a3d59bf63
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7b1a3fc377875ee25baa0718a25b5ac509822154
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-persisting-an-object-in-visual-studio-c"></a>Návod: Uchování objektu v sadě Visual Studio (C#)
I když můžete nastavit vlastnosti objektu na výchozí hodnoty v době návrhu, všechny hodnoty zadané v době běhu jsou ztraceny, když objekt zničena. Serializace můžete použít k uchování dat objektu mezi instance, které umožňuje ukládat hodnoty a je načtou při příštím vytvoření instance objektu.  
  
 V tomto návodu vytvoříte jednoduchou `Loan` objektu a zachovat data do souboru. Když znovu vytvoříte objekt se budou ze souboru načítat data.  
  
> [!IMPORTANT]
>  Tento příklad vytvoří nový soubor, pokud soubor již neexistuje. Pokud aplikace musí vytvořit soubor, aplikace musí `Create` oprávnění pro složku. Oprávnění jsou nastavená pomocí seznamů řízení přístupu. Pokud soubor již existuje, aplikace potřebuje pouze `Write` oprávnění, nižší úrovní oprávnění. Pokud je to možné, je bezpečnější k vytvoření tohoto souboru během nasazení a udělit pouze `Read` oprávnění do jednoho souboru (a nikoli vytvořit oprávnění pro složku). Navíc je bezpečnější zapsat data do složek uživatele než do kořenové složky nebo ve složce Program Files.  
  
> [!IMPORTANT]
>  Tento příklad ukládá data v binárním formátu souboru. Tyto formáty by nemělo být použito pro citlivých dat, třeba hesla nebo informace o kreditní kartě.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, klikněte na tlačítko **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-loan-object"></a>Vytvoření objektu úvěr  
 Prvním krokem je vytvoření `Loan` třídy a testovací aplikace, který používá třídu.  
  
### <a name="to-create-the-loan-class"></a>Pro vytvoření třídy úvěr  
  
1.  Vytvoření nového projektu knihovny tříd a pojmenujte ji "LoanClass". Další informace najdete v tématu [vytváření řešení a projekty](/visualstudio/ide/creating-solutions-and-projects).  
  
2.  V **Průzkumníku řešení**, otevřete místní nabídku pro soubor Class1 a zvolte **přejmenovat**. Přejmenujte soubor `Loan` a stiskněte klávesu ENTER. Přejmenování souboru také přejmenuje třídy pro `Loan`.  
  
3.  Přidejte následující veřejné členy do třídy:  
  
    ```csharp  
    public class Loan : System.ComponentModel.INotifyPropertyChanged  
    {  
        public double LoanAmount {get; set;}  
        public double InterestRate {get; set;}  
        public int Term {get; set;}  
  
        private string p_Customer;  
        public string Customer  
        {  
            get { return p_Customer; }  
            set   
            {  
                p_Customer = value;  
                PropertyChanged(this,  
                  new System.ComponentModel.PropertyChangedEventArgs("Customer"));  
            }  
        }  
  
        public event System.ComponentModel.PropertyChangedEventHandler PropertyChanged;  
  
        public Loan(double loanAmount,  
                    double interestRate,  
                    int term,  
                    string customer)  
        {  
            this.LoanAmount = loanAmount;  
            this.InterestRate = interestRate;  
            this.Term = term;  
            p_Customer = customer;  
        }  
    }  
    ```  
  
 Budete také muset vytvořit jednoduchou aplikaci, která používá `Loan` třídy.  
  
### <a name="to-create-a-test-application"></a>Chcete-li vytvořit testovací aplikace  
  
1.  Přidat projekt aplikace Windows Forms do vašeho řešení na **soubor** nabídce zvolte **přidat**, **nový projekt**.  
  
2.  V **přidat nový projekt** dialogovém okně vyberte **formulářové aplikace Windows**a zadejte `LoanApp` jako název projektu a klikněte na tlačítko **OK** zavřete dialogové okno .  
  
3.  V **Průzkumníku**, zvolte LoanApp projektu.  
  
4.  Na **projektu** nabídce zvolte **nastavit jako spouštěný projekt**.  
  
5.  Na **projektu** nabídky, zvolte **přidat odkaz na**.  
  
6.  V **přidat odkaz na** dialogovém okně vyberte **projekty** kartě a pak zvolte projekt LoanClass.  
  
7.  Klikněte na tlačítko **OK** zavřete dialogové okno.  
  
8.  V Návrháři přidat čtyři <xref:System.Windows.Forms.TextBox> ovládacích prvků formuláře.  
  
9. V Editoru kódu přidejte následující kód:  
  
    ```csharp  
    private LoanClass.Loan TestLoan = new LoanClass.Loan(10000.0, 0.075, 36, "Neil Black");  
  
    private void Form1_Load(object sender, EventArgs e)  
    {  
        textBox1.Text = TestLoan.LoanAmount.ToString();  
        textBox2.Text = TestLoan.InterestRate.ToString();  
        textBox3.Text = TestLoan.Term.ToString();  
        textBox4.Text = TestLoan.Customer;  
    }  
    ```  
  
10. Přidání obslužné rutiny události pro `PropertyChanged` událostí do formuláře pomocí následujícího kódu:  
  
    ```csharp  
    private void CustomerPropertyChanged(object sender,   
        System.ComponentModel.PropertyChangedEventArgs e)  
    {  
        MessageBox.Show(e.PropertyName + " has been changed.");  
    }  
    ```  
  
 V tomto okamžiku můžete sestavit a spustit aplikaci. Všimněte si, že výchozí hodnoty z `Loan` třída zobrazí v textových polích. Zkuste změňte hodnotu úrokové z 7.5 na 7.1 a pak ukončete aplikaci a potom ho spusťte znovu – hodnota obnoví na výchozí 7.5.  
  
 V praxi úrokové sazby změnit pravidelně, ale nemusí nutně prokázat pokaždé, když je aplikace spuštěna. Místo provedení uživatel aktualizovat úrokovou sazbu pokaždé, když je aplikace spuštěná, je lepší zachovat nejnovější úrokové sazby mezi instancemi aplikace. V dalším kroku můžete se přesně k tomu přidáním serializace k třídě úvěr.  
  
## <a name="using-serialization-to-persist-the-object"></a>Pomocí serializace k uchování objektu  
 Chcete-li zachovat hodnoty pro třídy úvěr, je nejprve třeba označit třídu pomocí `Serializable` atribut.  
  
### <a name="to-mark-a-class-as-serializable"></a>Označit jako serializovatelné třídy  
  
-   Změna deklaraci třídy pro třídu úvěr následujícím způsobem:  
  
    ```csharp  
    [Serializable()]  
    public class Loan : System.ComponentModel.INotifyPropertyChanged  
    {  
    ```  
  
 `Serializable` Atribut říká kompilátoru, že všechno ve třídě, můžete nastavit jako trvalý, do souboru. Protože `PropertyChanged` událost je zpracovávána objektem formuláře Windows, nelze jej serializovat. `NonSerialized` Atribut slouží k označení členy třídy, které by neměly být trvalé.  
  
### <a name="to-prevent-a-member-from-being-serialized"></a>Abyste zabránili serializována člena  
  
-   Změňte deklaraci pro `PropertyChanged` událostí následujícím způsobem:  
  
    ```csharp  
    [field: NonSerialized()]  
    public event System.ComponentModel.PropertyChangedEventHandler PropertyChanged;  
    ```  
  
 Dalším krokem je přidejte do aplikace LoanApp kód serializace. Abyste mohli serializaci třídy a zapisovat do souboru, bude používat <xref:System.IO> a <xref:System.Xml.Serialization> obory názvů. Abyste se vyhnuli, zadejte plně kvalifikované názvy, můžete přidat odkazy na knihovny potřebné tříd.  
  
### <a name="to-add-references-to-namespaces"></a>Chcete-li přidat odkazy na obory názvů  
  
-   Přidejte následující příkazy do horní části `Form1` třídy:  
  
    ```csharp  
    using System.IO;  
    using System.Runtime.Serialization.Formatters.Binary;  
    ```  
  
     V tomto případě používáte binární formátovací modul k uložení objektu v binárním formátu.  
  
 Dalším krokem je přidání kódu k deserializaci objektu ze souboru při vytvoření objektu.  
  
### <a name="to-deserialize-an-object"></a>K deserializaci objektu  
  
1.  Přidejte do třídy pro název souboru serializovaná data konstanta.  
  
    ```csharp  
    const string FileName = @"..\..\SavedLoan.bin";  
    ```  
  
2.  Změňte kód v `Form1_Load` události postupu následujícím způsobem:  
  
    ```csharp  
    private LoanClass.Loan TestLoan = new LoanClass.Loan(10000.0, 0.075, 36, "Neil Black");  
  
    private void Form1_Load(object sender, EventArgs e)  
    {  
        if (File.Exists(FileName))  
        {  
            Stream TestFileStream = File.OpenRead(FileName);  
            BinaryFormatter deserializer = new BinaryFormatter();  
            TestLoan = (LoanClass.Loan)deserializer.Deserialize(TestFileStream);  
            TestFileStream.Close();  
        }  
  
        TestLoan.PropertyChanged += this.CustomerPropertyChanged;  
  
        textBox1.Text = TestLoan.LoanAmount.ToString();  
        textBox2.Text = TestLoan.InterestRate.ToString();  
        textBox3.Text = TestLoan.Term.ToString();  
        textBox4.Text = TestLoan.Customer;  
    }  
    ```  
  
     Všimněte si, že je nejprve nutné zkontrolovat, zda soubor existuje. Pokud existuje, vytvoření <xref:System.IO.Stream> třídy číst binární soubor a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> třída přeložit soubor. Také musíte převést na typ objektu úvěr typ datového proudu.  
  
 Dále je nutné přidat kód uložit data zadaná v textových polích k `Loan` třída a pak musí serializovat třídu do souboru.  
  
### <a name="to-save-the-data-and-serialize-the-class"></a>Chcete uložit data a serializaci třídy  
  
-   Přidejte následující kód, který `Form1_FormClosing` procedury události:  
  
    ```csharp  
    private void Form1_FormClosing(object sender, FormClosingEventArgs e)  
    {  
        TestLoan.LoanAmount = Convert.ToDouble(textBox1.Text);  
        TestLoan.InterestRate = Convert.ToDouble(textBox2.Text);  
        TestLoan.Term = Convert.ToInt32(textBox3.Text);  
        TestLoan.Customer = textBox4.Text;  
  
        Stream TestFileStream = File.Create(FileName);  
        BinaryFormatter serializer = new BinaryFormatter();  
        serializer.Serialize(TestFileStream, TestLoan);  
        TestFileStream.Close();  
    }  
    ```  
  
 V tomto okamžiku můžete znovu sestavit a spustit aplikaci. Do textových polí v počátečním stavu, zobrazí výchozí hodnoty. Zkuste změnit hodnoty a zadejte název do textového pole čtvrtý. Zavřete aplikaci a znovu jej spusťte. Všimněte si, že nové hodnoty se nyní zobrazí v textových polích.  
  
## <a name="see-also"></a>Viz také  
 [Serializace (C# )](../../../../csharp/programming-guide/concepts/serialization/index.md)  
 [Průvodce programováním v jazyce C#](../../../../csharp/programming-guide/index.md)
