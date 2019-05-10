---
title: 'Návod: Vložení typů ze spravovaných sestavení v sadě Visual Studio (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 56ed12ba-adff-4e9c-a668-7fcba80c4795
ms.openlocfilehash: 18f22a771ab7279f177fe39d8c372a8517056890
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754827"
---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-visual-basic"></a>Návod: Vložení typů ze spravovaných sestavení v sadě Visual Studio (Visual Basic)

Pokud jste pro vložení informací o typu ze spravovaných sestavení se silným názvem, můžete volně zkombinujte typy v aplikaci dosáhnout nezávislosti na verzi. To znamená váš program může zapisovat používat typy z více verzí aplikace spravované knihovny aniž byste museli překompilují. pro každou verzi.

Typ vložení se často používá se spoluprací COM, jako je například aplikace, která používá objekty automatizace z aplikace Microsoft Office. Vložení informací o typu umožňuje jednomu sestavení programu pracovat s různými verzemi sady Microsoft Office na různých počítačích. Ale můžete použít také typ vkládání pomocí plně spravované řešení.

Lze jej vkládat informace o typu ze sestavení, která má následující vlastnosti:

- Sestavení poskytuje aspoň jedno veřejných rozhraní.

- Vložená rozhraní je opatřen poznámkou `ComImport` atribut a `Guid` atribut (a jedinečný identifikátor GUID).

- Sestavení je opatřen poznámkou `ImportedFromTypeLib` atribut nebo `PrimaryInteropAssembly` atribut a úrovni sestavení `Guid` atribut. (Ve výchozím nastavení, zahrnují šablony projektů Visual Basic úrovni sestavení `Guid` atribut.)

Po zadání veřejného rozhraní, která může být vložen, můžete vytvořit modul runtime třídy, které implementují tato rozhraní. Klientský program může potom můžete vložit informace o těchto rozhraní typu v době návrhu pomocí odkazu na sestavení, které obsahuje veřejné rozhraní a nastavení `Embed Interop Types` vlastnosti odkazu na `True`. Jedná se o ekvivalent používání kompilátoru příkazového řádku a odkazování na sestavení s použitím `/link` – možnost kompilátoru. Klientská aplikace může pak načíst instance objektů modulu runtime typu těchto rozhraní. Pokud vytvoříte novou verzi vašich sestavení silným názvem modulu runtime, není potřeba klientský program překompilují se aktualizovaný modul runtime sestavení. Místo toho klientskou aplikaci dál používat, podle toho, která verze sestavení modulu runtime je k dispozici, pomocí informací o vloženém typu pro veřejné rozhraní.

Vzhledem k tomu, že primární funkce vkládání typ pro podporu vkládání informací o typu ze sestavení vzájemné spolupráce COM se při vložení informací o typu do plně spravované řešení platí následující omezení:

- Jsou vloženy pouze atributy specifické pro zprostředkovatele komunikace s objekty COM; Další atributy se ignorují.

- Pokud typ používá obecné parametry a vložený typ je typ obecný parametr, tento typ nelze použít přes hranice sestavení. Příklady přes hranice sestavení, jsou volání metody z jiného sestavení nebo typ odvozený od typu definované v jiném sestavení.

- Konstanty nejsou vložené.

- <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> Třída nepodporuje vložený typ jako klíč. Můžete implementovat vlastní typ slovníku pro podporu vložený typ jako klíč.

 V tomto návodu provedete následující:

- Vytvořte sestavení se silným názvem, který má veřejné rozhraní, který obsahuje informace o typu, který může být vložen.

- Vytvořte sestavení silným názvem modulu runtime, který implementuje veřejných rozhraní.

- Vytvořte program klienta, který se vloží informace o typu z veřejného rozhraní a vytvoří instanci třídy v sestavení modulu runtime.

- Upravit a znovu sestavte sestavení modulu runtime.

- Spusťte klientskou aplikaci, která věděli, že nová verze sestavení modulu runtime používá bez nutnosti znovu kompilovat program klienta.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="creating-an-interface"></a>Vytvoření rozhraní

#### <a name="to-create-the-type-equivalence-interface-project"></a>Vytvoření projektu rozhraní rovnocennosti typu

1. V sadě Visual Studio na **souboru** nabídky, přejděte k **nový** a potom klikněte na tlačítko **projektu**.

2. V **nový projekt** v dialogu **typy projektů** podokno, ujistěte se, že **Windows** zaškrtnuto. Vyberte **knihovny tříd** v **šablony** podokně. V **název** zadejte `TypeEquivalenceInterface`a potom klikněte na tlačítko **OK**. Vytvoření nového projektu.

3. V **Průzkumníka řešení**, klikněte pravým tlačítkem na soubor Class1.vb a klikněte na tlačítko **přejmenovat**. Přejmenujte soubor na `ISampleInterface.vb` a stiskněte klávesu ENTER. Přejmenování souboru se také přejmenujte třídu na `ISampleInterface`. Tato třída bude reprezentovat veřejného rozhraní pro třídu.

4. Klikněte pravým tlačítkem na projekt TypeEquivalenceInterface a klikněte na tlačítko **vlastnosti**. Klikněte na tlačítko **kompilaci** kartu. Nastavte výstupní cesta platná umístění na vašem vývojovém počítači, jako je třeba `C:\TypeEquivalenceSample`. Toto umístění se taky použije v pozdějším kroku v tomto názorném postupu.

5. Při úpravách stále vlastnosti projektu, klikněte na tlačítko **podepisování** kartu. Vyberte **podepsat sestavení** možnost. V **vyberte soubor klíče se silným názvem** klikněte na možnost **< Nový … >**. V **název souboru klíče** zadejte `key.snk`. Zrušte **chránit můj soubor klíče s heslem** zaškrtávací políčko. Klikněte na **OK**.

6. Otevřete soubor ISampleInterface.vb. Přidejte následující kód do souboru třídy ISampleInterface k vytvoření ISampleInterface rozhraní.

    ```vb
    Imports System.Runtime.InteropServices

    <ComImport()>
    <Guid("8DA56996-A151-4136-B474-32784559F6DF")>
    Public Interface ISampleInterface
        Sub GetUserInput()
        ReadOnly Property UserInput As String
    End Interface
    ```

7. Na **nástroje** nabídky, klikněte na tlačítko **Create Guid**. V **Create GUID** dialogové okno, klikněte na tlačítko **formát registru** a potom klikněte na tlačítko **kopírování**. Klikněte na tlačítko **ukončovací**.

8. V `Guid` atribut, odstraňte ukázkový identifikátor GUID a vložte identifikátor GUID, který jste zkopírovali **Create GUID** dialogové okno. Odebrat složené závorky ({}) ze zkopírovaného identifikátor GUID.

9. Na **projektu** nabídky, klikněte na tlačítko **zobrazit všechny soubory**.

10. V **Průzkumníka řešení**, rozbalte **Můj projekt** složky. Dvakrát klikněte AssemblyInfo.vb. Přidejte následující atribut souboru.

    ```vb
    <Assembly: ImportedFromTypeLib("")>
    ```

    Uložte soubor.

11. Uložte projekt.

12. Klikněte pravým tlačítkem na projekt TypeEquivalenceInterface a klikněte na tlačítko **sestavení**. Soubor DLL knihovny tříd je zkompilován a uloží do zadané sestavení výstupní cestu (například C:\TypeEquivalenceSample).

## <a name="creating-a-runtime-class"></a>Vytvoření třídy modulu Runtime

#### <a name="to-create-the-type-equivalence-runtime-project"></a>Vytvoření projektu typu ekvivalence modulu runtime

1. V sadě Visual Studio na **souboru** nabídky, přejděte k **nový** a potom klikněte na tlačítko **projektu**.

2. V **nový projekt** v dialogu **typy projektů** podokno, ujistěte se, že **Windows** zaškrtnuto. Vyberte **knihovny tříd** v **šablony** podokně. V **název** zadejte `TypeEquivalenceRuntime`a potom klikněte na tlačítko **OK**. Vytvoření nového projektu.

3. V **Průzkumníka řešení**, klikněte pravým tlačítkem na soubor Class1.vb a klikněte na tlačítko **přejmenovat**. Přejmenujte soubor na `SampleClass.vb` a stiskněte klávesu ENTER. Přejmenování souboru třídy, která se také přejmenuje `SampleClass`. Tato třída implementuje `ISampleInterface` rozhraní.

4. Klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na tlačítko **vlastnosti**. Klikněte na tlačítko **kompilaci** kartu. Nastavte výstupní cestu do stejného umístění, například použít v projektu TypeEquivalenceInterface `C:\TypeEquivalenceSample`.

5. Při úpravách stále vlastnosti projektu, klikněte na tlačítko **podepisování** kartu. Vyberte **podepsat sestavení** možnost. V **vyberte soubor klíče se silným názvem** klikněte na možnost **< Nový … >**. V **název souboru klíče** zadejte `key.snk`. Zrušte **chránit můj soubor klíče s heslem** zaškrtávací políčko. Klikněte na **OK**.

6. Klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na tlačítko **přidat odkaz**. Klikněte na tlačítko **Procházet** kartu a přejděte do složky cesta pro výstup. Vyberte soubor TypeEquivalenceInterface.dll a klikněte na tlačítko **OK**.

7. Na **projektu** nabídky, klikněte na tlačítko **zobrazit všechny soubory**.

8. V **Průzkumníka řešení**, rozbalte **odkazy** složky. Vyberte odkaz TypeEquivalenceInterface. V okně Vlastnosti pro odkaz na TypeEquivalenceInterface nastavit **konkrétní verzi** vlastnost **False**.

9. Přidejte následující kód do souboru třídy SampleClass SampleClass třídu vytvořte.

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

11. Klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na tlačítko **sestavení**. Soubor DLL knihovny tříd je zkompilován a uloží do zadané sestavení výstupní cestu (například C:\TypeEquivalenceSample).

## <a name="creating-a-client-project"></a>Vytvoření projektu klienta

#### <a name="to-create-the-type-equivalence-client-project"></a>Vytvoření projektu klienta rovnocennosti typu

1. V sadě Visual Studio na **souboru** nabídky, přejděte k **nový** a potom klikněte na tlačítko **projektu**.

2. V **nový projekt** v dialogu **typy projektů** podokno, ujistěte se, že **Windows** zaškrtnuto. Vyberte **konzolovou aplikaci** v **šablony** podokně. V **název** zadejte `TypeEquivalenceClient`a potom klikněte na tlačítko **OK**. Vytvoření nového projektu.

3. Klikněte pravým tlačítkem na projekt TypeEquivalenceClient a klikněte na tlačítko **vlastnosti**. Klikněte na tlačítko **kompilaci** kartu. Nastavte výstupní cestu do stejného umístění, například použít v projektu TypeEquivalenceInterface `C:\TypeEquivalenceSample`.

4. Klikněte pravým tlačítkem na projekt TypeEquivalenceClient a klikněte na tlačítko **přidat odkaz**. Klikněte na tlačítko **Procházet** kartu a přejděte do složky cesta pro výstup. Vyberte soubor TypeEquivalenceInterface.dll (ne TypeEquivalenceRuntime.dll) a klikněte na tlačítko **OK**.

5. Na **projektu** nabídky, klikněte na tlačítko **zobrazit všechny soubory**.

6. V **Průzkumníka řešení**, rozbalte **odkazy** složky. Vyberte odkaz TypeEquivalenceInterface. V okně Vlastnosti pro odkaz na TypeEquivalenceInterface nastavit **Embed Interop Types** vlastnost **True**.

7. Přidejte následující kód do souboru Module1.vb vytvořit klientskou aplikaci.

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

8. Stisknutím kláves CTRL + F5 sestavte a spusťte program.

## <a name="modifying-the-interface"></a>Úprava rozhraní

#### <a name="to-modify-the-interface"></a>Chcete-li změnit rozhraní

1. V sadě Visual Studio na **souboru** nabídky, přejděte k **otevřít**a potom klikněte na tlačítko **projekt či řešení**.

2. V **otevřít projekt** dialogové okno, klikněte pravým tlačítkem na projekt TypeEquivalenceInterface a potom klikněte na tlačítko **vlastnosti**. Klikněte na tlačítko **aplikace** kartu. Klikněte na tlačítko **informace o sestavení** tlačítko. Změnit **verze sestavení** a **verze souboru** hodnoty `2.0.0.0`.

3. Otevřete soubor ISampleInterface.vb. Přidejte následující řádek kódu do rozhraní ISampleInterface.

    ```vb
    Function GetDate() As Date
    ```

    Uložte soubor.

4. Uložte projekt.

5. Klikněte pravým tlačítkem na projekt TypeEquivalenceInterface a klikněte na tlačítko **sestavení**. Novou verzi souboru DLL knihovny třídy je zkompilován a uloží do zadané výstupní cesty zadané sestavení (například C:\TypeEquivalenceSample).

## <a name="modifying-the-runtime-class"></a>Úprava třídy modulu Runtime

#### <a name="to-modify-the-runtime-class"></a>Chcete-li změnit třídy modulu runtime

1. V sadě Visual Studio na **souboru** nabídky, přejděte k **otevřít**a potom klikněte na tlačítko **projekt či řešení**.

2. V **otevřít projekt** dialogovém poli, klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na tlačítko **vlastnosti**. Klikněte na tlačítko **aplikace** kartu. Klikněte na tlačítko **informace o sestavení** tlačítko. Změnit **verze sestavení** a **verze souboru** hodnoty `2.0.0.0`.

3. Otevřete soubor SampleClass.vb. Přidejte následující řádky kódu do třídy SampleClass.

    ```vb
    Public Function GetDate() As DateTime Implements ISampleInterface.GetDate
        Return Now
    End Function
    ```

    Uložte soubor.

4. Uložte projekt.

5. Klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na tlačítko **sestavení**. Aktualizovanou verzi souboru DLL knihovny třídy je zkompilován a uložen v sestavení dříve zadaná výstupní cesta (například C:\TypeEquivalenceSample).

6. V Průzkumníku souborů otevřete složku výstupu cestu (například C:\TypeEquivalenceSample). Dvakrát klikněte na panel TypeEquivalenceClient.exe ke spuštění programu. Program bude odrážet nové verze sestavení TypeEquivalenceRuntime bez nutnosti znovu zkompilovat.

## <a name="see-also"></a>Viz také:

- [/ Link (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/link.md)
- [Koncepty programování](../../../../visual-basic/programming-guide/concepts/index.md)
- [Programování se sestaveními](../../../../framework/app-domains/programming-with-assemblies.md)
- [Sestavení v .NET](../../../../standard/assembly/index.md)
