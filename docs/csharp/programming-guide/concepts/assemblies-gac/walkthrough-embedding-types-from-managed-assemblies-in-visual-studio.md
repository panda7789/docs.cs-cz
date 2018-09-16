---
title: 'Návod: Vložení typů ze spravovaných sestavení v sadě Visual Studio (C#)'
ms.date: 07/20/2015
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
ms.openlocfilehash: 1900c62d1ebaf611f141f8f1bdf95f8d11f82140
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/16/2018
ms.locfileid: "45668389"
---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-c"></a>Návod: Vložení typů ze spravovaných sestavení v sadě Visual Studio (C#)
Pokud jste pro vložení informací o typu ze spravovaných sestavení se silným názvem, můžete volně zkombinujte typy v aplikaci dosáhnout nezávislosti na verzi. To znamená váš program může zapisovat používat typy z více verzí aplikace spravované knihovny aniž byste museli překompilují. pro každou verzi.  
  
 Typ vložení se často používá se spoluprací COM, jako je například aplikace, která používá objekty automatizace z aplikace Microsoft Office. Vložení informací o typu umožňuje jednomu sestavení programu pracovat s různými verzemi sady Microsoft Office na různých počítačích. Ale můžete použít také typ vkládání pomocí plně spravované řešení.  
  
 Lze jej vkládat informace o typu ze sestavení, která má následující vlastnosti:  
  
-   Sestavení poskytuje aspoň jedno veřejných rozhraní.  
  
-   Vložená rozhraní je opatřen poznámkou `ComImport` atribut a `Guid` atribut (a jedinečný identifikátor GUID).  
  
-   Sestavení je opatřen poznámkou `ImportedFromTypeLib` atribut nebo `PrimaryInteropAssembly` atribut a úrovni sestavení `Guid` atribut. (Ve výchozím nastavení, zahrnují šablony projektů Visual C# úrovni sestavení `Guid` atribut.)  
  
 Po zadání veřejného rozhraní, která může být vložen, můžete vytvořit modul runtime třídy, které implementují tato rozhraní. Klientský program může potom můžete vložit informace o těchto rozhraní typu v době návrhu pomocí odkazu na sestavení, které obsahuje veřejné rozhraní a nastavení `Embed Interop Types` vlastnosti odkazu na `True`. Jedná se o ekvivalent používání kompilátoru příkazového řádku a odkazování na sestavení s použitím `/link` – možnost kompilátoru. Klientská aplikace může pak načíst instance objektů modulu runtime typu těchto rozhraní. Pokud vytvoříte novou verzi vašich sestavení silným názvem modulu runtime, není potřeba klientský program překompilují se aktualizovaný modul runtime sestavení. Místo toho klientskou aplikaci dál používat, podle toho, která verze sestavení modulu runtime je k dispozici, pomocí informací o vloženém typu pro veřejné rozhraní.  
  
 Vzhledem k tomu, že primární funkce vkládání typ pro podporu vkládání informací o typu ze sestavení vzájemné spolupráce COM se při vložení informací o typu do plně spravované řešení platí následující omezení:  
  
-   Jsou vloženy pouze atributy specifické pro zprostředkovatele komunikace s objekty COM; Další atributy se ignorují.  
  
-   Pokud typ používá obecné parametry a vložený typ je typ obecný parametr, tento typ nelze použít přes hranice sestavení. Příklady přes hranice sestavení, jsou volání metody z jiného sestavení nebo typ odvozený od typu definované v jiném sestavení.  
  
-   Konstanty nejsou vložené.  
  
-   <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> Třída nepodporuje vložený typ jako klíč. Můžete implementovat vlastní typ slovníku pro podporu vložený typ jako klíč.  
  
 V tomto návodu provedete následující:  
  
-   Vytvořte sestavení se silným názvem, který má veřejné rozhraní, který obsahuje informace o typu, který může být vložen.  
  
-   Vytvořte sestavení silným názvem modulu runtime, který implementuje veřejných rozhraní.  
  
-   Vytvořte program klienta, který se vloží informace o typu z veřejného rozhraní a vytvoří instanci třídy v sestavení modulu runtime.  
  
-   Upravit a znovu sestavte sestavení modulu runtime.  
  
-   Spusťte klientskou aplikaci, která věděli, že nová verze sestavení modulu runtime používá bez nutnosti znovu kompilovat program klienta.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-an-interface"></a>Vytvoření rozhraní  
  
#### <a name="to-create-the-type-equivalence-interface-project"></a>Vytvoření projektu rozhraní rovnocennosti typu  
  
1.  V sadě Visual Studio na **souboru** nabídce zvolte **nový** a potom klikněte na tlačítko **projektu**.  
  
2.  V **nový projekt** v dialogu **typy projektů** podokno, ujistěte se, že **Windows** zaškrtnuto. Vyberte **knihovny tříd** v **šablony** podokně. V **název** zadejte `TypeEquivalenceInterface`a potom klikněte na tlačítko **OK**. Vytvoření nového projektu.  
  
3.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na soubor Class1.cs a klikněte na tlačítko **přejmenovat**. Přejmenujte soubor na `ISampleInterface.cs` a stiskněte klávesu ENTER. Přejmenování souboru se také přejmenujte třídu na `ISampleInterface`. Tato třída bude reprezentovat veřejného rozhraní pro třídu.  
  
4.  Klikněte pravým tlačítkem na projekt TypeEquivalenceInterface a klikněte na tlačítko **vlastnosti**. Klikněte na tlačítko **sestavení** kartu. Nastavte výstupní cesta platná umístění na vašem vývojovém počítači, jako je třeba `C:\TypeEquivalenceSample`. Toto umístění se taky použije v pozdějším kroku v tomto názorném postupu.  
  
5.  Při úpravách stále vlastnosti projektu, klikněte na tlačítko **podepisování** kartu. Vyberte **podepsat sestavení** možnost. V **vyberte soubor klíče se silným názvem** klikněte na možnost **< Nový … >**. V **název souboru klíče** zadejte `key.snk`. Zrušte **chránit můj soubor klíče s heslem** zaškrtávací políčko. Klikněte na tlačítko **OK**.  
  
6.  Otevřete soubor ISampleInterface.cs. Přidejte následující kód do souboru třídy ISampleInterface k vytvoření ISampleInterface rozhraní.  
  
    ```csharp  
    using System;  
    using System.Runtime.InteropServices;  
  
    namespace TypeEquivalenceInterface  
    {  
        [ComImport]  
        [Guid("8DA56996-A151-4136-B474-32784559F6DF")]  
        public interface ISampleInterface  
        {  
            void GetUserInput();  
            string UserInput { get; }  
        }  
    }  
    ```  
  
7.  Na **nástroje** nabídky, klikněte na tlačítko **Create Guid**. V **Create GUID** dialogové okno, klikněte na tlačítko **formát registru** a potom klikněte na tlačítko **kopírování**. Klikněte na tlačítko **ukončovací**.  
  
8.  V `Guid` atribut, odstraňte ukázkový identifikátor GUID a vložte identifikátor GUID, který jste zkopírovali **Create GUID** dialogové okno. Odebrat složené závorky ({}) ze zkopírovaného identifikátor GUID.  
  
9. V **Průzkumníka řešení**, rozbalte **vlastnosti** složky. Poklikejte na soubor AssemblyInfo.cs. Přidejte následující atribut souboru.  
  
    ```csharp  
    [assembly: ImportedFromTypeLib("")]  
    ```  
  
     Uložte soubor.  
  
10. Uložte projekt.  
  
11. Klikněte pravým tlačítkem na projekt TypeEquivalenceInterface a klikněte na tlačítko **sestavení**. Soubor DLL knihovny tříd je zkompilován a uloží do zadané sestavení výstupní cestu (například C:\TypeEquivalenceSample).  
  
## <a name="creating-a-runtime-class"></a>Vytvoření třídy modulu Runtime  
  
#### <a name="to-create-the-type-equivalence-runtime-project"></a>Vytvoření projektu typu ekvivalence modulu runtime  
  
1.  V sadě Visual Studio na **souboru** nabídky, přejděte k **nový** a potom klikněte na tlačítko **projektu**.  
  
2.  V **nový projekt** v dialogu **typy projektů** podokno, ujistěte se, že **Windows** zaškrtnuto. Vyberte **knihovny tříd** v **šablony** podokně. V **název** zadejte `TypeEquivalenceRuntime`a potom klikněte na tlačítko **OK**. Vytvoření nového projektu.  
  
3.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na soubor Class1.cs a klikněte na tlačítko **přejmenovat**. Přejmenujte soubor na `SampleClass.cs` a stiskněte klávesu ENTER. Přejmenování souboru třídy, která se také přejmenuje `SampleClass`. Tato třída implementuje `ISampleInterface` rozhraní.  
  
4.  Klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na tlačítko **vlastnosti**. Klikněte na tlačítko **sestavení** kartu. Nastavte výstupní cestu do stejného umístění, například použít v projektu TypeEquivalenceInterface `C:\TypeEquivalenceSample`.  
  
5.  Při úpravách stále vlastnosti projektu, klikněte na tlačítko **podepisování** kartu. Vyberte **podepsat sestavení** možnost. V **vyberte soubor klíče se silným názvem** klikněte na možnost **< Nový … >**. V **název souboru klíče** zadejte `key.snk`. Zrušte **chránit můj soubor klíče s heslem** zaškrtávací políčko. Klikněte na tlačítko **OK**.  
  
6.  Klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na tlačítko **přidat odkaz**. Klikněte na tlačítko **Procházet** kartu a přejděte do složky cesta pro výstup. Vyberte soubor TypeEquivalenceInterface.dll a klikněte na tlačítko **OK**.  
  
7.  V **Průzkumníka řešení**, rozbalte **odkazy** složky. Vyberte odkaz TypeEquivalenceInterface. V okně Vlastnosti pro odkaz na TypeEquivalenceInterface nastavit **konkrétní verzi** vlastnost **False**.  
  
8.  Přidejte následující kód do souboru třídy SampleClass SampleClass třídu vytvořte.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using TypeEquivalenceInterface;  
  
    namespace TypeEquivalenceRuntime  
    {  
        public class SampleClass : ISampleInterface  
        {  
            private string p_UserInput;  
            public string UserInput { get { return p_UserInput; } }  
  
            public void GetUserInput()  
            {  
                Console.WriteLine("Please enter a value:");  
                p_UserInput = Console.ReadLine();  
            }  
        }  
    )  
    ```  
  
9. Uložte projekt.  
  
10. Klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na tlačítko **sestavení**. Soubor DLL knihovny tříd je zkompilován a uloží do zadané sestavení výstupní cestu (například C:\TypeEquivalenceSample).  
  
## <a name="creating-a-client-project"></a>Vytvoření projektu klienta  
  
#### <a name="to-create-the-type-equivalence-client-project"></a>Vytvoření projektu klienta rovnocennosti typu  
  
1.  V sadě Visual Studio na **souboru** nabídky, přejděte k **nový** a potom klikněte na tlačítko **projektu**.  
  
2.  V **nový projekt** v dialogu **typy projektů** podokno, ujistěte se, že **Windows** zaškrtnuto. Vyberte **konzolovou aplikaci** v **šablony** podokně. V **název** zadejte `TypeEquivalenceClient`a potom klikněte na tlačítko **OK**. Vytvoření nového projektu.  
  
3.  Klikněte pravým tlačítkem na projekt TypeEquivalenceClient a klikněte na tlačítko **vlastnosti**. Klikněte na tlačítko **sestavení** kartu. Nastavte výstupní cestu do stejného umístění, například použít v projektu TypeEquivalenceInterface `C:\TypeEquivalenceSample`.  
  
4.  Klikněte pravým tlačítkem na projekt TypeEquivalenceClient a klikněte na tlačítko **přidat odkaz**. Klikněte na tlačítko **Procházet** kartu a přejděte do složky cesta pro výstup. Vyberte soubor TypeEquivalenceInterface.dll (ne TypeEquivalenceRuntime.dll) a klikněte na tlačítko **OK**.  
  
5.  V **Průzkumníka řešení**, rozbalte **odkazy** složky. Vyberte odkaz TypeEquivalenceInterface. V okně Vlastnosti pro odkaz na TypeEquivalenceInterface nastavit **Embed Interop Types** vlastnost **True**.  
  
6.  Přidejte následující kód do souboru Program.cs vytvořte klientský program.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using TypeEquivalenceInterface;  
    using System.Reflection;  
  
    namespace TypeEquivalenceClient  
    {  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                Assembly sampleAssembly = Assembly.Load("TypeEquivalenceRuntime");  
                ISampleInterface sampleClass =   
                    (ISampleInterface)sampleAssembly.CreateInstance("TypeEquivalenceRuntime.SampleClass");  
                sampleClass.GetUserInput();  
                Console.WriteLine(sampleClass.UserInput);  
                Console.WriteLine(sampleAssembly.GetName().Version.ToString());  
                Console.ReadLine();  
            }  
        }  
    }  
    ```  
  
7.  Stisknutím kláves CTRL + F5 sestavte a spusťte program.  
  
## <a name="modifying-the-interface"></a>Úprava rozhraní  
  
#### <a name="to-modify-the-interface"></a>Chcete-li změnit rozhraní  
  
1.  V sadě Visual Studio na **souboru** nabídky, přejděte k **otevřít**a potom klikněte na tlačítko **projekt či řešení**.  
  
2.  V **otevřít projekt** dialogové okno, klikněte pravým tlačítkem na projekt TypeEquivalenceInterface a potom klikněte na tlačítko **vlastnosti**. Klikněte na tlačítko **aplikace** kartu. Klikněte na tlačítko **informace o sestavení** tlačítko. Změnit **verze sestavení** a **verze souboru** hodnoty `2.0.0.0`.  
  
3.  Otevřete soubor SampleInterface.cs. Přidejte následující řádek kódu do rozhraní ISampleInterface.  
  
    ```csharp  
    DateTime GetDate();  
    ```  
  
     Uložte soubor.  
  
4.  Uložte projekt.  
  
5.  Klikněte pravým tlačítkem na projekt TypeEquivalenceInterface a klikněte na tlačítko **sestavení**. Novou verzi souboru DLL knihovny třídy je zkompilován a uloží do zadané výstupní cesty zadané sestavení (například C:\TypeEquivalenceSample).  
  
## <a name="modifying-the-runtime-class"></a>Úprava třídy modulu Runtime  
  
#### <a name="to-modify-the-runtime-class"></a>Chcete-li změnit třídy modulu runtime  
  
1.  V sadě Visual Studio na **souboru** nabídky, přejděte k **otevřít**a potom klikněte na tlačítko **projekt či řešení**.  
  
2.  V **otevřít projekt** dialogovém poli, klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na tlačítko **vlastnosti**. Klikněte na tlačítko **aplikace** kartu. Klikněte na tlačítko **informace o sestavení** tlačítko. Změnit **verze sestavení** a **verze souboru** hodnoty `2.0.0.0`.  
  
3.  Otevřete soubor SampleClass.cs. Přidejte následující řádky kódu do třídy SampleClass.  
  
    ```csharp  
    public DateTime GetDate()  
    {  
        return DateTime.Now;  
    }  
    ```  
  
     Uložte soubor.  
  
4.  Uložte projekt.  
  
5.  Klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na tlačítko **sestavení**. Aktualizovanou verzi souboru DLL knihovny třídy je zkompilován a uložen v sestavení dříve zadaná výstupní cesta (například C:\TypeEquivalenceSample).  
  
6.  V Průzkumníku souborů otevřete složku výstupu cestu (například C:\TypeEquivalenceSample). Dvakrát klikněte na panel TypeEquivalenceClient.exe ke spuštění programu. Program bude odrážet nové verze sestavení TypeEquivalenceRuntime bez nutnosti znovu zkompilovat.  
  
## <a name="see-also"></a>Viz také

- [/ Link (možnosti kompilátoru C#)](../../../../csharp/language-reference/compiler-options/link-compiler-option.md)  
- [Průvodce programováním v jazyce C#](../../../../csharp/programming-guide/index.md)  
- [Programování se sestaveními](../../../../framework/app-domains/programming-with-assemblies.md)  
- [Sestavení a globální mezipaměti sestavení (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)
