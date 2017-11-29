---
title: "Návod: Vložení typů z řízených sestavení v sadě Visual Studio (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56ed12ba-adff-4e9c-a668-7fcba80c4795
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4411b40d8ffbdf2b74c49152db675286d91b43ea
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-visual-basic"></a>Návod: Vložení typů z řízených sestavení v sadě Visual Studio (Visual Basic)
Pokud jste pro vložení informací o typu ze spravovaných sestavení se silným názvem, můžete volně spojte typy v aplikaci k dosažení nezávislost verze. To znamená váš program může být napsán používat typy z více verzí aplikace spravované knihovny aniž byste museli zopakovat pro každou verzi.  
  
 Typ vložení se často používá se spoluprací COM, jako je například aplikace, která používá objekty automatizace z aplikace Microsoft Office. Vložení informací o typu umožňuje ve stejném sestavení programu pro práci s různými verzemi nástroje Microsoft Office na různých počítačích. Však můžete použít také typu vložení v rámci řešení pro plně spravovaná.  
  
 Lze jej vkládat informace o typu ze sestavení, který má následující vlastnosti:  
  
-   Sestavení zpřístupní alespoň jeden veřejné rozhraní.  
  
-   Vložené rozhraní jsou opatřen poznámkou `ComImport` atribut a `Guid` atribut (a jedinečný identifikátor GUID).  
  
-   Sestavení je opatřen poznámkou `ImportedFromTypeLib` atribut nebo `PrimaryInteropAssembly` atribut a úroveň sestavení `Guid` atribut. (Ve výchozím nastavení, zahrnují šablony projektů Visual Basic úrovni sestavení `Guid` atributů.)  
  
 Po zadání veřejného rozhraní, která může být vložen, můžete vytvořit runtime třídy, které implementují těchto rozhraní. Program klienta můžete pak vložení informací o typu pro tyto rozhraní v době návrhu pomocí odkazování na sestavení, které obsahuje veřejné rozhraní a nastavení `Embed Interop Types` vlastnost odkazu na `True`. Jde o ekvivalent pomocí příkazového řádku kompilátoru a odkazování na sestavení s použitím `/link` – možnost kompilátoru. Program klienta pak můžete načíst instancí objektů vaší runtime, která je zadán jako těchto rozhraní. Pokud vytvoříte novou verzi vašeho sestavení silným názvem modulu runtime, není nutné zopakovat s sestavení aktualizované runtime program klienta. Místo toho program klienta budou nadále používat kteroukoli verzi modulu runtime sestavení je k dispozici, pomocí informací o vloženého typu pro veřejné rozhraní.  
  
 Vzhledem k tomu, že primární funkce typ vnoření je podpora vložení informací o typu ze sestavení vzájemné spolupráce COM, při vložení informací o typu ve plně spravovaná řešení platí následující omezení:  
  
-   Pouze atributy, které jsou specifické pro zprostředkovatele komunikace s objekty COM jsou vloženy; ostatní atributy se ignorují.  
  
-   Pokud typu používá obecné parametry a typ obecný parametr je vloženého typu, typu nelze použít v hranici sestavení. Při překročení hranici sestavení příklady volání metody z jiného sestavení nebo typ odvozování z typu definovaný v jiném sestavení.  
  
-   Konstanty nejsou vložena.  
  
-   <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> Třída nepodporuje vloženého typu jako klíč. Můžete implementovat vlastní typ slovníku pro podporu vloženého typu jako klíč.  
  
 V tomto návodu se postupujte takto:  
  
-   Vytvořte sestavení se silným názvem, který má veřejné rozhraní, který obsahuje informace o typu, kterou můžete vložit.  
  
-   Vytvořte sestavení silným názvem modulu runtime, který implementuje této veřejné rozhraní.  
  
-   Vytvořte program klienta, který se vloží informací o typu ze veřejné rozhraní a vytvoří instanci třídy ze sestavení modulu runtime.  
  
-   Upravit a znovu sestavte sestavení za běhu.  
  
-   Spusťte klientskou aplikaci, která v tématu, aby se používal novou verzi modulu runtime sestavení bez nutnosti její kompilace programu klienta.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-an-interface"></a>Vytváření rozhraní  
  
#### <a name="to-create-the-type-equivalence-interface-project"></a>Vytvoření projektu typu ekvivalenční rozhraní  
  
1.  V sadě Visual Studio na **soubor** nabídky, přejděte na příkaz **nový** a pak klikněte na **projektu**.  
  
2.  V **nový projekt** dialogovém **typy projektů** podokně, ujistěte se, že **Windows** je vybrána. Vyberte **knihovny tříd** v **šablony** podokně. V **název** zadejte `TypeEquivalenceInterface`a potom klikněte na **OK**. Vytvoření nového projektu.  
  
3.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na soubor Class1.vb a klikněte na **přejmenovat**. Přejmenujte soubor `ISampleInterface.vb` a stiskněte klávesu ENTER. Přejmenování souboru také přejmenuje třídy pro `ISampleInterface`. Tato třída bude reprezentovat veřejné rozhraní pro třídu.  
  
4.  Klikněte pravým tlačítkem na projekt TypeEquivalenceInterface a klikněte na tlačítko **vlastnosti**. Klikněte **zkompilovat** kartě. Nastavte výstupní cesta na některé platné místo ve svém vývojovém počítači, jako je třeba `C:\TypeEquivalenceSample`. Toto umístění se taky použije později v tomto návodu.  
  
5.  Při úpravách stále vlastností projektu, klikněte **podpisování** karta. Vyberte **podepsání sestavení** možnost. V **vyberte soubor klíče se silným názvem** seznamu, klikněte na tlačítko **< nová... >**. V **název souboru klíče** zadejte `key.snk`. Vymazat **chránit Moje soubor klíče s heslem** zaškrtávací políčko. Click **OK**.  
  
6.  Otevřete soubor ISampleInterface.vb. Přidejte následující kód do souboru třídy ISampleInterface k vytvoření rozhraní ISampleInterface.  
  
    ```vb  
    Imports System.Runtime.InteropServices  
  
    <ComImport()>  
    <Guid("8DA56996-A151-4136-B474-32784559F6DF")>  
    Public Interface ISampleInterface  
        Sub GetUserInput()  
        ReadOnly Property UserInput As String  
    End Interface  
    ```  
  
7.  Na **nástroje** nabídky, klikněte na tlačítko **vytvořit Guid**. V **vytvořit GUID** dialogové okno, klikněte na tlačítko **registru formátu** a pak klikněte na **kopie**. Klikněte na tlačítko **ukončení**.  
  
8.  V `Guid` atribut, odstraňte ukázka GUID a vložte identifikátor GUID, který jste zkopírovali ze **vytvořit GUID** dialogové okno. Odebrání zkopírovaný GUID složené závorky ({}).  
  
9. Na **projektu** nabídky, klikněte na tlačítko **zobrazit všechny soubory**.  
  
10. V **Průzkumníku řešení**, rozbalte **Můj projekt** složky. Dvakrát klikněte AssemblyInfo.vb. Do souboru přidejte následující atribut.  
  
    ```vb  
    <Assembly: ImportedFromTypeLib("")>  
    ```  
  
     Uložte soubor.  
  
11. Uložte projekt.  
  
12. Klikněte pravým tlačítkem na projekt TypeEquivalenceInterface a klikněte na tlačítko **sestavení**. Soubor DLL knihovny tříd jsou kompilované a uložit na zadaná sestavení výstupní cestu (například C:\TypeEquivalenceSample).  
  
## <a name="creating-a-runtime-class"></a>Vytvoření třídy modulu Runtime  
  
#### <a name="to-create-the-type-equivalence-runtime-project"></a>Vytvoření projektu typu ekvivalenční modulu runtime  
  
1.  V sadě Visual Studio na **soubor** nabídky, přejděte na příkaz **nový** a pak klikněte na **projektu**.  
  
2.  V **nový projekt** dialogovém **typy projektů** podokně, ujistěte se, že **Windows** je vybrána. Vyberte **knihovny tříd** v **šablony** podokně. V **název** zadejte `TypeEquivalenceRuntime`a potom klikněte na **OK**. Vytvoření nového projektu.  
  
3.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na soubor Class1.vb a klikněte na **přejmenovat**. Přejmenujte soubor `SampleClass.vb` a stiskněte klávesu ENTER. Přejmenování souboru také přejmenuje třídy pro `SampleClass`. Tato třída se implementovat `ISampleInterface` rozhraní.  
  
4.  Klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na tlačítko **vlastnosti**. Klikněte **zkompilovat** kartě. Nastavit výstupní cesta do stejného umístění, které jste použili v TypeEquivalenceInterface projektu, například `C:\TypeEquivalenceSample`.  
  
5.  Při úpravách stále vlastností projektu, klikněte **podpisování** karta. Vyberte **podepsání sestavení** možnost. V **vyberte soubor klíče se silným názvem** seznamu, klikněte na tlačítko **< nová... >**. V **název souboru klíče** zadejte `key.snk`. Vymazat **chránit Moje soubor klíče s heslem** zaškrtávací políčko. Click **OK**.  
  
6.  Klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na tlačítko **přidat odkaz na**. Klikněte **Procházet** kartě a přejděte do složky výstupní cesta. Vyberte soubor TypeEquivalenceInterface.dll a klikněte na tlačítko **OK**.  
  
7.  Na **projektu** nabídky, klikněte na tlačítko **zobrazit všechny soubory**.  
  
8.  V **Průzkumníku řešení**, rozbalte **odkazy** složky. Vyberte odkaz na TypeEquivalenceInterface. V okně Vlastnosti pro odkaz na TypeEquivalenceInterface nastavit **konkrétní verzi** vlastnost **False**.  
  
9. Přidejte následující kód do souboru SampleClass třídy pro vytvoření třídy SampleClass.  
  
    ```vb  
    Imports TypeEquivalenceInterface  
  
    Public Class SampleClass  
        Implements ISampleInterface  
  
        Private p_UserInput As String  
        Public ReadOnly Property UserInput() As String Implements ISampleInterface.UserInput  
            Get  
                Return p_UserInput  
            End Get  
        End Property  
  
        Public Sub GetUserInput() Implements ISampleInterface.GetUserInput  
            Console.WriteLine("Please enter a value:")  
            p_UserInput = Console.ReadLine()  
        End Sub  
    End Class  
    ```  
  
10. Uložte projekt.  
  
11. Klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na tlačítko **sestavení**. Soubor DLL knihovny tříd jsou kompilované a uložit na zadaná sestavení výstupní cestu (například C:\TypeEquivalenceSample).  
  
## <a name="creating-a-client-project"></a>Vytvoření projektu klienta  
  
#### <a name="to-create-the-type-equivalence-client-project"></a>Vytvoření projektu klienta ekvivalenční typu  
  
1.  V sadě Visual Studio na **soubor** nabídky, přejděte na příkaz **nový** a pak klikněte na **projektu**.  
  
2.  V **nový projekt** dialogovém **typy projektů** podokně, ujistěte se, že **Windows** je vybrána. Vyberte **konzolové aplikace** v **šablony** podokně. V **název** zadejte `TypeEquivalenceClient`a potom klikněte na **OK**. Vytvoření nového projektu.  
  
3.  Klikněte pravým tlačítkem na projekt TypeEquivalenceClient a klikněte na tlačítko **vlastnosti**. Klikněte **zkompilovat** kartě. Nastavit výstupní cesta do stejného umístění, které jste použili v TypeEquivalenceInterface projektu, například `C:\TypeEquivalenceSample`.  
  
4.  Klikněte pravým tlačítkem na projekt TypeEquivalenceClient a klikněte na tlačítko **přidat odkaz na**. Klikněte **Procházet** kartě a přejděte do složky výstupní cesta. Vyberte soubor TypeEquivalenceInterface.dll (ne TypeEquivalenceRuntime.dll) a klikněte na tlačítko **OK**.  
  
5.  Na **projektu** nabídky, klikněte na tlačítko **zobrazit všechny soubory**.  
  
6.  V **Průzkumníku řešení**, rozbalte **odkazy** složky. Vyberte odkaz na TypeEquivalenceInterface. V okně Vlastnosti pro odkaz na TypeEquivalenceInterface nastavit **vložit zprostředkovatel komunikace s objekty typy** vlastnost **True**.  
  
7.  Přidejte následující kód do souboru Module1.vb vytvoření programu klienta.  
  
    ```vb  
    Imports TypeEquivalenceInterface  
    Imports System.Reflection  
  
    Module Module1  
  
        Sub Main()  
            Dim sampleAssembly = Assembly.Load("TypeEquivalenceRuntime")  
            Dim sampleClass As ISampleInterface = CType( _  
                sampleAssembly.CreateInstance("TypeEquivalenceRuntime.SampleClass"), ISampleInterface)  
            sampleClass.GetUserInput()  
            Console.WriteLine(sampleClass.UserInput)  
            Console.WriteLine(sampleAssembly.GetName().Version)  
            Console.ReadLine()  
        End Sub  
  
    End Module  
    ```  
  
8.  Stisknutím klávesy CTRL + F5 sestavit a spustit program.  
  
## <a name="modifying-the-interface"></a>Úprava rozhraní  
  
#### <a name="to-modify-the-interface"></a>Chcete-li upravit rozhraní  
  
1.  V sadě Visual Studio na **soubor** nabídky, přejděte na příkaz **otevřete**a potom klikněte na **projekt nebo řešení**.  
  
2.  V **otevřeného projektu** dialogové okno, klikněte pravým tlačítkem na projekt TypeEquivalenceInterface a pak klikněte na tlačítko **vlastnosti**. Klikněte **aplikace** kartě. Klikněte **informací o sestavení** tlačítko. Změna **verze sestavení** a **verze souboru** hodnoty k `2.0.0.0`.  
  
3.  Otevřete soubor ISampleInterface.vb. Přidejte následující řádek kódu rozhraní ISampleInterface.  
  
    ```vb  
    Function GetDate() As Date  
    ```  
  
     Uložte soubor.  
  
4.  Uložte projekt.  
  
5.  Klikněte pravým tlačítkem na projekt TypeEquivalenceInterface a klikněte na tlačítko **sestavení**. Nová verze souboru třídy knihovny DLL je zkompilovat a uloží do výstupní cesta zadaná sestavení (například C:\TypeEquivalenceSample).  
  
## <a name="modifying-the-runtime-class"></a>Úprava Runtime – třída  
  
#### <a name="to-modify-the-runtime-class"></a>Chcete-li upravit runtime – třída  
  
1.  V sadě Visual Studio na **soubor** nabídky, přejděte na příkaz **otevřete**a potom klikněte na **projekt nebo řešení**.  
  
2.  V **otevřeného projektu** dialogové okno pole, klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na tlačítko **vlastnosti**. Klikněte **aplikace** kartě. Klikněte **informací o sestavení** tlačítko. Změna **verze sestavení** a **verze souboru** hodnoty k `2.0.0.0`.  
  
3.  Otevřete SampleClass.vbfile. Přidejte následující řádky kódu do třídy SampleClass.  
  
```vb  
Public Function GetDate() As DateTime Implements ISampleInterface.GetDate  
    Return Now  
End Function  
```  
  
     Save the file.  
  
4.  Uložte projekt.  
  
5.  Klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na tlačítko **sestavení**. Aktualizovaná verze souboru třídy knihovny DLL je zkompilovat a uloží do výstupní cesta dříve zadané sestavení (například C:\TypeEquivalenceSample).  
  
6.  V Průzkumníku souborů otevřete složku výstupu cestu (například C:\TypeEquivalenceSample). Dvakrát klikněte na TypeEquivalenceClient.exe ke spuštění programu. Program se projeví novou verzi sestavení TypeEquivalenceRuntime bez nutnosti znovu kompilovány.  
  
## <a name="see-also"></a>Viz také  
 [/ Link (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/link.md)  
 [Programování konceptů](../../../../visual-basic/programming-guide/concepts/index.md)  
 [Programování se sestaveními](../../../../framework/app-domains/programming-with-assemblies.md)  
 [Sestavení a globální mezipaměti sestavení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)
